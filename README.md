# Webová aplikace pro správu skladu a prodejů na stánku

## 1. Účel aplikace

Tato webová aplikace slouží pro správu fyzického skladu sportovního merche prodávaného na stánku během zápasů nebo jiných akcí. Umožňuje jednoduše zobrazit produkty, odečíst prodané kusy, sledovat stav zásob a zaznamenávat všechny změny v databázi. Každý fyzický produkt má na sobě qr kód s odkazem na detail daného produktu. Při prodeji obsluha kód načte a klikne na Odečíst 1ks. 

Cílem je periodicky doplňovat nabídku zboží dynamicky podle prodejů (produkty, jejichž hotnota klesne )

## 2. Uživatelé a prostředí

- Online aplikace primárně pro telefony a tablety
- Přístup mají zástupci klubu a zároveň my, jako poskytovatel
- Každý uživatel je přiřazen ke konkrétnímu klubu a vidí pouze jeho produkty.

## 3. Funkce aplikace

### 3.1 Obrazovky
1. Provoz - primární obrazovka
    -  Seznam všech produktů, které mají Active = 1
        -  U nich je vidět počet skladem
    -  Textové vyhledávání
    -  Tlačítko pro spuštění čtečky QR kodů
        -  Ta po načtení zobrazí detail daného produktu
1. Detail produktu - po kliknutí na produkt na obrazovce Provoz nebo po načtení QR kodu
    - Viditelné hodnoty (název, doplňovat, cena, minimální zásoba, doplňovat na, doplnit)
    - Editovatelné hodnoty (počet skladem)
    - Tlačítka pro Naskladnění nebo Vyskladnění produktu
1. Nastavení produktu
    - Tady se mění hlavní nastavení produktu
        - Cena
        - Aktivní
        - Doplňovat
        - ... 
1. Historie
    - Pohled na historii pohybů změn skladových zásob



### 3.6 Přihlášení a správa uživatelů

- Uživatel se přihlašuje pomocí e-mailu a hesla.
- Po přihlášení má přístup pouze ke svým datům (produkty vlastního klubu).
- Uživatel může být členem více klubů.



## 5. Návrh stacku

- Frontend: Vue 3 + Vite
- Backend: Node.js (Express)
- Databáze: PostgreSQL (Supabase)
- API: REST, Axios
- Architektura: oddělený frontend a backend

## 6. Příklady použití

- Uživatel se přihlásí, vidí jen produkty svého klubu.
- Pomocí čtečky si načte qr kod produktu a tím se dostane na jeho detail
- Klikne na „Prodat“ → stav se sníží o 1 a zapíše se změna.


