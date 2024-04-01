---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.5
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# SQL WHERE

Die WHERE-Klausel wird verwendet, um Datensätze zu filtern.

Sie wird verwendet, um nur diejenigen Datensätze zu extrahieren, die eine bestimmte Bedingung erfüllen.


Hinweis: Die WHERE-Klausel wird nicht nur in SELECT-Anweisungen verwendet, sondern auch in UPDATE, DELETE usw.!

## Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

#### Beispieltabelle

Unten sehen Sie eine Auswahl aus der Tabelle "Customers", die in den Beispielen verwendet wird:

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå       | S-958 22   | Sweden  |


## Textfelder vs. Numerische Felder

SQL erfordert einfache Anführungszeichen um Textwerte (die meisten Datenbanksysteme erlauben auch doppelte Anführungszeichen).

Numerische Felder sollten jedoch nicht in Anführungszeichen eingeschlossen werden:

```sql
SELECT * FROM Customers
WHERE CustomerID=1;
```

| CustomerID | CustomerName       | ContactName | Address       | City   | PostalCode | Country |
|------------|--------------------|-------------|---------------|--------|------------|---------|
|          1 | Alfreds Futterkiste | Maria Anders| Obere Str. 57 | Berlin |      12209 | Germany |