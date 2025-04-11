# Webová aplikace pro správu skladu a prodejů na stánku

## 1. Účel aplikace



Aplikace slouží pro správu fyzického skladu sportovního merche prodávaného na stánku během zápasů nebo jiných akcí. Umožňuje jednoduše zobrazit produkty, odečíst prodané kusy, sledovat stav zásob a zaznamenávat všechny změny v databázi.

Každý fyzický produkt má na sobě QR kód s odkazem na detail daného produktu. Při prodeji obsluha kód načte a klikne na tlačítko „Odečíst 1 ks“..
:::success

Cílem aplikace je umožnit dynamické automatické doplňování nabídky zboží na základě skutečných prodejů. Produkty, které klesnou pod minimální zásobu, budou dovyrobeny v přednastaveném počtu a doplňeny do stánku.
:::
---

## 2. Uživatelé a prostředí

- Online aplikace optimalizovaná primárně pro mobilní zařízení (telefony, tablety).
- Přístup mají zástupci sportovních klubů a my jako poskytovatel systému.
- Každý uživatel je přiřazen ke konkrétnímu klubu a vidí pouze produkty svého klubu.
- Jeden uživatel může být přiřazen k více klubům.

---

## 3. Funkce aplikace

### 3.1 Obrazovky

#### 1. Provoz (hlavní obrazovka)
- Seznam všech produktů, které mají `active = true`
- Viditelný počet skladem
- Textové vyhledávání
- Tlačítko pro spuštění čtečky QR kódů
- Po načtení QR se otevře detail daného produktu

#### 2. Detail produktu
- Viditelné informace:
  - Název
  - Cena
  - Aktuální stav skladem
  - Minimální zásoba
  - Doplňovat na
  - Počet k doplnění (vypočítané)
- Editovatelné hodnoty:
  - Přímé nastavení počtu skladem
- Tlačítka:
  - „Naskladnit +1“
  - „Vyskladnit -1“

#### 3. Nastavení produktu
- Formulář pro úpravu základních parametrů produktu:
  - Aktivní (ano/ne)
  - Cena
  - Doplňovat (ano/ne)
  - Min. zásoba
  - Doplnit na

#### 4. Historie (log změn)
- Seznam změn skladových zásob pro daný klub
- Obsahuje:
  - Produkt
  - Změna
  - Nový stav
  - Datum a čas
  - IP adresa

---

### 3.2 Přihlášení a správa uživatelů

- Přihlášení přes e-mail a heslo
- Uživatelský účet obsahuje:
  - E-mail
  - Hash hesla
  - Seznam klubů, ke kterým má uživatel přístup
- V budoucnu možnost správy přístupů přes administrační rozhraní

---

## 4. Návrh technologického stacku

- **Frontend:** Vue 3 + Vite
- **Backend:** Node.js (Express)
- **Databáze:** PostgreSQL (Supabase)
- **Komunikace:** REST API (Axios)
- **Architektura:** oddělený frontend a backend

---

## 5. Scénáře použití

- Uživatel se přihlásí a je automaticky přesměrován do pohledu „Provoz“.
- Na stánku obsluha načte QR kód produktu → otevře se jeho detail.
- Kliknutím na „Vyskladnit -1 ks“ odečte stav a vytvoří se log.
- V historii si může uživatel zpětně ověřit všechny změny.
- Po odehráném zápasu se my podíváme do pohledu provoz a klubu dovyrobíme produkty, kde je hodnota Doplnit > 0

---