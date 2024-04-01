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

# SELECT DISTINCT

Die Anweisung SELECT DISTINCT wird verwendet, um nur unterschiedliche (einzigartige) Werte zurückzugeben.

Innerhalb einer Tabelle enthält eine Spalte oft viele doppelte Werte; und manchmal möchten Sie nur die unterschiedlichen (distinct) Werte auflisten.

## Syntax
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

#### Beispieltabelle

Unten sehen Sie eine Auswahl aus der Tabelle **__Customers__**", die in den Beispielen verwendet wird:

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå       | S-958 22   | Sweden  |

## SELECT-Beispiel ohne DISTINCT

Wenn Sie das Schlüsselwort DISTINCT weglassen, gibt der SQL-Befehl den Wert "Land" aus allen Datensätzen der Tabelle "Kunden" zurück:

```sql
SELECT Country FROM Customers;
```

| Country |
|---------|
| Germany |
| Mexico  |
| Mexico  |
| UK      |
| Sweden  |

## SELECT-Beispiel mit DISTINCT

Durch die Verwendung des Schlüsselworts DISTINCT werden alle doppelten Werte entfernt:

```sql
SELECT DISTINCT Country FROM Customers;
```

| Country |
|---------|
| Germany |
| Mexico  |
| UK      |
| Sweden  |

Mexico kam zweimal vor, aber durch die Verwendung von DISTINCT wird es nur einmal angezeigt.

## Count ohne Distinct

Erklärung was die Funktion COUNT macht: [COUNT](./count.md)

Die Funktion COUNT gibt die Anzahl der Zeilen zurück, die in einer Abfrage ausgewählt wurden. Ohne DISTINCT werden alle 5 Zeilen gezählt. 

```sql
SELECT COUNT(DISTINCT Country) FROM Customers;
```

| COUNT(Country) |
|----------------|
|              5 |


## Count mit Distinct

Durch die Verwendung des Schlüsselworts DISTINCT in einer Funktion namens COUNT können wir die Anzahl der verschiedenen Länder zurückgeben.

```sql
SELECT COUNT(DISTINCT Country) FROM Customers;
```

| COUNT(DISTINCT Country) |
|--------------------------|
|                        4 |
