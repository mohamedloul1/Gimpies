# 👟 Gimpies – Schoenenwinkelbeheersysteem

Welkom bij het **Gimpies Project**, een schoenenwinkelbeheersysteem ontwikkeld in **Magic XPA** met **SQLite** als backend.

Dit systeem biedt veilige loginfunctionaliteit en verschillende gebruikersrollen met eigen rechten en menu's.

---

## 🔐 Inlogfunctionaliteit

De applicatie bevat een volledige loginflow met:
- Gebruikersnaam + wachtwoordvalidatie
- Controle op `Active` status
- Pogingenteller met blokkering na 3 mislukte pogingen
- Automatische doorverwijzing op basis van gebruikersrol

---

## 👥 Gebruikersrollen & Scenario's

### 👤 Manager

- **Username:** `admin`
- **Password:** `admin123`
- **Rol:** `Manager`

**Kan:**
- Werknemers beheren
- Rapporten bekijken (verkoop, inkoop, voorraad)
- Volledige voorraad beheren

---

### 👤 Verkoopmedewerker

- **Username:** `verkoper`
- **Password:** `verkoop123`
- **Rol:** `Sales`

**Kan:**
- Verkoop uitvoeren
- Voorraad bekijken

**Beperkingen:**
- Geen toegang tot inkoop of gebruikersbeheer

---

### 👤 Inkoopmedewerker

- **Username:** `inkoper`
- **Password:** `inkoop123`
- **Rol:** `Purchaser`

**Kan:**
- Inkoop uitvoeren
- Voorraad aanvullen

**Beperkingen:**
- Geen toegang tot verkoop of rapportages

---

## ❌ Foutafhandeling

| Scenario                              | Systeemreactie                          |
|---------------------------------------|------------------------------------------|
| Verkeerde gebruikersnaam              | `"Gebruiker niet gevonden of inactief"`  |
| Verkeerd wachtwoord                   | `"Wachtwoord incorrect"` + pogingenteller |
| 3 foute pogingen                      | `"Te veel pogingen. Applicatie sluit af"`|
| Account is inactief (`Active = False`) | `"Je account is niet actief"`            |

---

## 🗂 Structuur

- **EMPLOYEE**: Beheert gebruikers, rollen en active status
- **BRAND**, **SHOE_TYPE**, **SIZE**, **COLOR**: Referentietabellen
- **SHOE**: Beheert voorraad per combinatie
- **PURCHASE**, **SALE**: Transactiegeschiedenis
- **Virtuele invoervelden**: Voor loginformulier

---

## 🧪 Testgebruikers (in database)

```sql
INSERT INTO EMPLOYEE (Username, Password, Role, Active) VALUES
('admin', 'admin123', 'Manager', 1),
('verkoper', 'verkoop123', 'Sales', 1),
('inkoper', 'inkoop123', 'Purchaser', 1);
