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

# SQL GROUP BY

Die **GROUP BY**-Anweisung gruppiert Zeilen mit denselben Werten in Zusammenfassungszeilen, beispielsweise "die Anzahl der Kunden in jedem Land finden".

Die GROUP BY-Anweisung wird häufig mit Aggregatfunktionen ([COUNT()](./count.md), [MAX()](./min_max.md), [MIN()](./min_max.md), [SUM()](./sum.md), [AVG()](./avg.md)) verwendet, um das Ergebnis nach einer oder mehreren Spalten zu gruppieren.

## Syntax
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
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

## Beispiele

Die folgende SQL-Anweisung listet die Anzahl der Kunden in jedem Land auf:

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

**Ergebnis:**
| COUNT(CustomerID) | Country |
|--------------------|---------|
|                  1 | Germany |
|                  2 | Mexico  |
|                  1 | Sweden  |
|                  1 | UK      |

Die folgende SQL-Anweisung listet die Anzahl der Kunden in jedem Land auf, sortiert von hoch nach niedrig:

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

**Ergebnis:**
| COUNT(CustomerID) | Country |
|--------------------|---------|
|                  2 | Mexico  |
|                  1 | Germany |
|                  1 | Sweden  |
|                  1 | UK      |

Hier sind die beiden Tabellen übersetzt in Markdown:

#### Beispieltabelle

Nachfolgend eine Auswahl aus der Tabelle **__Orders__** in der Northwind-Musterdatenbank:

| OrderID | CustomerID | EmployeeID | OrderDate  | ShipperID |
|---------|------------|------------|------------|-----------|
| 10248   | 90         | 5          | 1996-07-04 | 3         |
| 10249   | 81         | 6          | 1996-07-05 | 1         |
| 10250   | 34         | 4          | 1996-07-08 | 2         |

Und eine Auswahl aus der Tabelle **__Shippers__**:

| ShipperID | ShipperName      |
|-----------|------------------|
| 1         | Speedy Express   |
| 2         | United Package   |
| 3         | Federal Shipping |

[LEFT JOIN](./left_join.md) Erklärung.

Die folgende SQL-Anweisung listet die Anzahl der Bestellungen auf, die von jedem Versandunternehmen gesendet wurden:

```sql
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```

**Ergebnis:**
| ShipperName      | NumberOfOrders |
|------------------|----------------|
| Federal Shipping | 1              |
| Speedy Express   | 1              |
| United Package   | 1              |
