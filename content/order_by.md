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

# SQL ORDER BY

Das **ORDER BY**-Schlüsselwort wird verwendet, um das Ergebnis in aufsteigender oder absteigender Reihenfolge zu sortieren.

## Syntax
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

#### Beispieltabelle

Unten sehen Sie eine Auswahl aus der Tabelle **__Products__**, die in den Beispielen verwendet wird:

| ProductID |         ProductName         | SupplierID | CategoryID |          Unit          | Price |
|-----------|-----------------------------|------------|------------|------------------------|-------|
|     1     |            Chais            |     1      |     1      | 10 boxes x 20 bags    |  18   |
|     2     |            Chang            |     1      |     1      | 24 - 12 oz bottles    |  19   |
|     3     |        Aniseed Syrup        |     1      |     2      | 12 - 550 ml bottles   |  10   |
|     4     | Chef Anton's Cajun Seasoning|     2      |     2      | 48 - 6 oz jars         |  22   |
|     5     |   Chef Anton's Gumbo Mix    |     2      |     2      | 36 boxes              | 21.35 |

## DESC

Das **ORDER BY**-Schlüsselwort sortiert die Datensätze standardmäßig in aufsteigender Reihenfolge. Verwenden Sie das **DESC**-Schlüsselwort, um die Datensätze in absteigender Reihenfolge zu sortieren.

```sql
SELECT * FROM Products
ORDER BY Price DESC;
```

| ProductID |         ProductName         | SupplierID | CategoryID |          Unit          | Price |
|-----------|-----------------------------|------------|------------|------------------------|-------|
|     4     | Chef Anton's Cajun Seasoning|     2      |     2      | 48 - 6 oz jars         |  22   |
|     5     |   Chef Anton's Gumbo Mix    |     2      |     2      | 36 boxes              | 21.35 |
|     2     |            Chang            |     1      |     1      | 24 - 12 oz bottles    |  19   |
|     1     |            Chais            |     1      |     1      | 10 boxes x 20 bags    |  18   |
|     3     |        Aniseed Syrup        |     1      |     2      | 12 - 550 ml bottles   |  10   |

## Alphabetisch ordnen
Für Zeichenfolgenwerte ordnet das **ORDER BY**-Schlüsselwort alphabetisch an:

```sql
SELECT * FROM Products
ORDER BY ProductName;
```

| ProductID |         ProductName         | SupplierID | CategoryID |          Unit          | Price |
|-----------|-----------------------------|------------|------------|------------------------|-------|
|     3     |        Aniseed Syrup        |     1      |     2      | 12 - 550 ml bottles   |  10   |
|     2     |            Chang            |     1      |     1      | 24 - 12 oz bottles    |  19   |
|     1     |            Chais            |     1      |     1      | 10 boxes x 20 bags    |  18   |
|     4     | Chef Anton's Cajun Seasoning|     2      |     2      | 48 - 6 oz jars         |  22   |
|     5     |   Chef Anton's Gumbo Mix    |     2      |     2      | 36 boxes              | 21.35 |


## Alphabetisch absteigend
Um die Tabelle umgekehrt alphabetisch zu sortieren, verwenden Sie das **DESC**-Schlüsselwort:

```sql
SELECT * FROM Products
ORDER BY ProductName DESC;
```

| ProductID |         ProductName         | SupplierID | CategoryID |          Unit          | Price |
|-----------|-----------------------------|------------|------------|------------------------|-------|
|     3     |        Aniseed Syrup        |     1      |     2      | 12 - 550 ml bottles   |  10   |
|     2     |            Chang            |     1      |     1      | 24 - 12 oz bottles    |  19   |
|     1     |            Chais            |     1      |     1      | 10 boxes x 20 bags    |  18   |
|     4     | Chef Anton's Cajun Seasoning|     2      |     2      | 48 - 6 oz jars         |  22   |
|     5     |   Chef Anton's Gumbo Mix    |     2      |     2      | 36 boxes              | 21.35 |

## ORDER BY Mehrere Spalten
Die folgende SQL-Anweisung wählt alle Kunden aus der Tabelle "Customers" aus und sortiert sie nach der "Country" und der "CustomerName"-Spalte. Das bedeutet, dass sie nach Land sortiert, aber wenn einige Zeilen dasselbe Land haben, werden sie nach CustomerName sortiert:

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

**__Customer__**

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå       | S-958 22   | Sweden  |

### Ergebnis

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå        | S-958 22   | Sweden  |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |

## Verwendung von ASC und DESC
Die folgende SQL-Anweisung wählt alle Kunden aus der Tabelle "Customers" aus und sortiert sie aufsteigend nach der "Country"-Spalte und absteigend nach der "CustomerName"-Spalte:

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

| CustomerID | CustomerName             | ContactName    | Address              | City         | PostalCode | Country |
|------------|--------------------------|----------------|----------------------|--------------|------------|---------|
| 5          | Berglunds snabbköp       | Christina Berglund | Berguvsvägen 8    | Luleå        | S-958 22   | Sweden  |
| 1          | Alfreds Futterkiste      | Maria Anders   | Obere Str. 57        | Berlin       | 12209      | Germany |
| 3          | Antonio Moreno Taquería  | Antonio Moreno | Mataderos 2312       | México D.F.  | 05023      | Mexico  |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo  | Avda. de la Constitución 2222 | México D.F. | 05021 | Mexico  |
| 4          | Around the Horn          | Thomas Hardy   | 120 Hanover Sq.      | London       | WA1 1DP    | UK      |