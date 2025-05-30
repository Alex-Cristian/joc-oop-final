README - Proiect C++: Mosteniri, Exceptii, Polimorfism, Suprascrieri
Descriere generala:
--------------------
Acest proiect C++ simuleaza un mic joc RPG, in care un jucator poate cumpara echipamente
(armuri si arme),
se poate lupta cu un boss si isi poate gestiona inventarul si viata. Scopul proiectului este de a
demonstra
utilizarea avansata a programarii orientate pe obiect (OOP), precum si a bunelor practici in
organizarea modulara a codului.
Concepte implementate:
----------------------
- Mostenire simpla si multipla:
- Clasa de baza abstracta: Item
- Clase derivate: Armor si Weapon (ambele mostenesc din Item)
- Clasa Armor mosteneste si din clasa ID (mostenire multipla)
- Functii virtuale pure si polimorfism:
- Item contine metoda virtuala pura afisare()
- Armor si Weapon implementeaza propria versiune a metodei afisare()
- In main.cpp este folosit vector<Item*> pentru a permite apeluri polimorfice
- Constructori si operatori suprascrisi:
- Armor si Weapon au copy constructori si operator= suprascrisi pentru copiere corecta
- Exceptii:
- La cumparare, daca jucatorul nu are suficienti bani, se arunca std::runtime_error
- Exista blocuri try-catch pentru tratarea si afisarea mesajelor de eroare
- dynamic_cast:
- Se utilizeaza dynamic_cast pentru a identifica la runtime daca un obiect este Armor sau Weapon,
si pentru a accesa metodele proprii (ex: getProtectie(), getDamage())
- STL (Standard Template Library):
- Se folosesc vectori pentru a gestiona lista de iteme din shop si inventarul jucatorului
- Cod curat si modular:
- Codul este impartit in fisiere .h si .cpp separate pentru fiecare clasa
- Nu se foloseste "using namespace std" in fisiere header
- Se folosesc functii const acolo unde este relevant
Structura fisierelor:
---------------------
- Item.h / Item.cpp - Clasa abstracta de baza pentru toate obiectele
- Armor.h / Armor.cpp - Clasa derivata cu protectie, mostenire multipla
- Weapons.h / Weapons.cpp - Clasa derivata cu damage
- Boss.h / Boss.cpp - Clasa cu atac aleatoriu (5-20) si AI simplu
- Player.h / Player.cpp - Clasa jucatorului, cu inventar si viata
- ID.h / ID.cpp - Clasa auxiliara folosita pentru mostenire multipla
- main.cpp - Meniul aplicatiei si logica principala
Functionalitati principale:
---------------------------
- Afisare shop cu iteme din vector<Item*>
- Cumparare item cu verificare fonduri si tratata cu exceptie
- Adaugare item in inventarul jucatorului
- Afisare polimorfica a inventarului
- Lupta cu boss-ul, cu damage aleatoriu (cu probabilitate mica pentru damage mare)
- Dynamic_cast pentru verificare tip concret de item