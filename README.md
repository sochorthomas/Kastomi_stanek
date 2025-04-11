# Webová aplikace pro správu skladu a prodejů na stánku

## 1. Účel aplikace

Tato webová aplikace slouží pro správu fyzického skladu sportovního merche prodávaného na stánku během zápasů nebo jiných akcí. Umožňuje jednoduše zobrazit produkty, odečíst prodané kusy, sledovat stav zásob a zaznamenávat všechny změny v databázi. Každý fyzický produkt má na sobě qr kod s odkazem na detail daného produktu. Při prodeji obsluh

## 2. Uživatelé a prostředí

- Online aplikace primárně pro telefony a tablety.
- Přístup mají zástupci klubu a zároveň my, jako poskytovatel
- Každý uživatel je přiřazen ke konkrétnímu klubu a vidí pouze produkty svého klubu.

## 3. Funkce aplikace

### 3.1 Seznam produktů

- Zobrazí se seznam všech produktů dostupných pro přihlášeného uživatele.
    - Tam bude možné nastavit pro produkt jeho obecná nastavení, jako jestli má být aktivní, jaká je cena, zda jej doplňovat apod.
     - U produktu lze nastavit:
     - aktivní (active)
     - zda ho automaticky doplňovat (auto_refill)
     - počet skladem (stock)
     - minimální množství (min_stock)
     - na kolik doplňovat (refill_to)
     - počet k doplnění: výpočet (refill_to - stock)
     
- Pokud bude mít produkt Aktivní = 1, zobrazí se v aplikaci v pohledu ,,Provoz".
    - Tam půjde po rozkliknutí produktu Přidat/Vyskladnit, nebo nastavit přesný počet skladem.
    

### 3.2 Barevné označení stavu skladu

- zelená = dostatek zásob
- oranžová = pod ideálním stavem
- červená = pod minimálním množstvím

### 3.3 Prodej produktu

- U každého produktu je tlačítko "Prodat".
- Kliknutí odečte 1 kus a aktualizuje zásobu.
- Změna se zapíše do databáze i do historie.

### 3.4 Logování změn

- Každá změna se ukládá do tabulky `stock_logs`, která obsahuje:
  - ID produktu
  - množství změny (např. -1)
  - nový stav zásoby
  - IP adresa
  - čas změny

### 3.5 Zobrazení historie

- Aplikace má stránku /log, kde je vidět historie změn produktů.
- Aktuálně pro produkt s ID 1.
- V budoucnu výpis podle všech produktů nebo dle výběru.

### 3.6 Přihlášení a správa uživatelů

- Uživatel se přihlašuje pomocí e-mailu a hesla.
- Po přihlášení má přístup pouze ke svým datům (produkty vlastního klubu).
- Každý uživatel je vázán na jeden klub (`club_id`).
- V budoucnu může být správa uživatelů řešena i přes administrační rozhraní.

## 4. Logika a validace

- Doplnit = refill_to - stock, minimálně 0
- Prodej je možný jen pokud stock > 0
- Změny probíhají transakčně (změna + log)

## 5. Použité technologie

- Frontend: Vue 3 + Vite
- Backend: Node.js (Express)
- Databáze: PostgreSQL (Supabase)
- API: REST, Axios
- Architektura: oddělený frontend a backend

## 6. Příklady použití

- Uživatel se přihlásí, vidí jen produkty svého klubu.
- Klikne na „Prodat“ → stav se sníží o 1 a zapíše se změna.
- Při nízkém stavu je produkt barevně zvýrazněn.
- Na stránce „Historie změn“ vidí log transakcí.

