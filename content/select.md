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

# Die SQL SELECT-Anweisung

Die SELECT-Anweisung wird verwendet, um Daten aus einer Datenbank auszuwählen.

## Syntax
```sql
SELECT column1, column2, ...
FROM table_name;
```

Hierbei sind *column1*, *column2*, ... die Feldnamen der Tabelle, aus der Sie Daten auswählen möchten.

*table_name* steht für den Namen der Tabelle, aus der Sie Daten auswählen möchten.

## Ausgabe von Spalten

Die zu selektierenden Spalten werden in einem SQL-Abfragebefehl zwischen **SELECT** und **FROM** definiert. Sie bestimmen, welche Datenfelder aus der Datenbanktabelle ausgegeben werden sollen.

#### Beispieltabelle

Unten sehen Sie eine Auswahl aus der Tabelle **__Customers__**", die in den Beispielen verwendet wird:

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå       | S-958 22   | Sweden  |

### Ausgabe aller Spalten

Im SQL bezeichnet das Sternchen (*) eine Wildcard, die im **SELECT**-Befehl verwendet wird, um alle Spalten einer Tabelle auszuwählen. Anstatt jede Spalte einzeln zu benennen, holt **SELECT** * einfach alle vorhandenen Spalten und die dazugehörigen Daten.

```sql
SELECT * FROM Customers;
```

### Ausgabe einzelner Spalten

Um spezifische Spalten aus einer Tabelle zu selektieren, listen Sie die Namen der gewünschten Spalten nach dem Befehl **SELECT** auf, getrennt durch Kommas. Zum Beispiel:

```sql
SELECT CustomerName, City FROM Customers;
```

Dieser Befehl wählt nur die Spalten *CustomerName* und *City* aus der Tabelle Kunden.

#### Ergebnis

| CustomerName                         | City       |
|--------------------------------------|------------|
| Alfreds Futterkiste                  | Berlin     |
| Ana Trujillo Emparedados y helados   | México D.F.|
| Antonio Moreno Taquería              | México D.F.|
| Around the Horn                      | London     |
| Berglunds snabbköp                   | Luleå      |
