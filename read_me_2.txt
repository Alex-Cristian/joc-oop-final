
Proiect: RPG Game - Management de obiecte, inventar și interacțiune cu boss

------------------------------------------------------------
TEMPLATE-URI FOLOSITE
------------------------------------------------------------


1. Clasa template Potion<T>
----------------------------
Această clasă permite folosirea de diferite tipuri de atribute pentru poțiuni:

template<typename T>
class Potion : public Item {
private:
    T effect;
public:
    Potion(std::string name, float price, T effect);
};

Poțiunile pot avea efecte de diferite tipuri (int, float, etc), oferind flexibilitate și modularitate.

------------------------------------------------------------
DESIGN PATTERNS IMPLEMENTATE
------------------------------------------------------------

1. Singleton Pattern – Clasa Boss
----------------------------------
Descriere: Asigură că există o singură instanță de boss în joc.

Implementare:
- Variabilă statică: Boss* instance;
- Constructor privat;
- Metodă statică getInstance() pentru a accesa bossul.

Cod:
Boss* Boss::instance = nullptr;
Boss* Boss::getInstance() {
    if (!instance)
        instance = new Boss();
    return instance;
}

Utilitate: În joc trebuie să existe un singur boss pentru a menține consistența. Acest pattern previne crearea multiplă.

2. Factory Pattern – Clasa PotionFactory
----------------------------------------
Descriere: Creează instanțe de poțiuni centralizat, în funcție de tipul dorit.

Exemplu:
static Potion<int>* createHealthPotion() {
    return new Potion<int>("Health potion", 500, 50, 1);
}

Utilitate: Codul principal (`main.cpp`) este mai curat. Nu mai trebuie să scriem de fiecare dată `new Potion...`, ci folosim `PotionFactory::createHealthPotion()`.

------------------------------------------------------------
Alte concepte utilizate
------------------------------------------------------------

- STL: vector, find, erase, etc. pentru manipularea inventarului și listelor de obiecte.
- Suprascriere operatori: pentru adăugare de obiecte în inventar.
- Funcții virtuale și moștenire: pentru a gestiona ierarhia obiectelor (Item → Potion, Weapon, Armor).
- Encapsulare și constructori: protejarea atributelor, inițializare rapidă.
- Dinamic_cast + RTTI: pentru identificarea tipului obiectului la runtime.

