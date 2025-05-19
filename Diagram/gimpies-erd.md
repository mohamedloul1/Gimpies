
---

### ✅ Aanpassing: Volledig werkende Markdown inhoud

Hieronder heb ik het helemaal goed gezet voor gebruik in een `.md`-bestand dat Mermaid ondersteunt:

```markdown
# Gimpies ERD Diagram (Mermaid)

```mermaid
erDiagram

EMPLOYEE {
  int EmployeeID PK
  string Username
  string Password
  string Role
  boolean Active
}

BRAND {
  int BrandID PK
  string Name
}

SHOETYPE {
  int TypeID PK
  string Name
  int BrandID FK
}

SIZE {
  int SizeID PK
  int Value
}

COLOR {
  int ColorID PK
  string Name
}

SHOE {
  int ShoeID PK
  int BrandID FK
  int TypeID FK
  int SizeID FK
  int ColorID FK
  int Quantity
  decimal Price
}

PURCHASE {
  int PurchaseID PK
  int EmployeeID FK
  int ShoeID FK
  int Quantity
  datetime Timestamp
}

SALE {
  int SaleID PK
  int EmployeeID FK
  int ShoeID FK
  int Quantity
  datetime Timestamp
  decimal TotalPrice
}

SHOETYPE ||--o{ BRAND : "belongs to"
SHOE }o--|| BRAND : "has"
SHOE }o--|| SHOETYPE : "has"
SHOE }o--|| SIZE : "has"
SHOE }o--|| COLOR : "has"
PURCHASE }o--|| EMPLOYEE : "performed by"
PURCHASE }o--|| SHOE : "adds to"
SALE }o--|| EMPLOYEE : "performed by"
SALE }o--|| SHOE : "includes"
