---
title: Funkcje agregujące Canonical
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251354"
---
# <a name="aggregate-canonical-functions"></a>Funkcje agregujące Canonical

Agregaty są wyrażeniami, które redukują serię wartości wejściowych, na przykład pojedynczą wartość. Agregaty są zwykle używane w połączeniu z klauzulą GROUP BY wyrażenia SELECT, a istnieją ograniczenia dotyczące miejsca, w którym można ich używać.

## <a name="aggregate-entity-sql-canonical-functions"></a>Agreguj Entity SQL funkcje kanoniczne

Poniżej znajdują się wartości zagregowane Entity SQL funkcje kanoniczne.

### <a name="avgexpression"></a>Średnia (wyrażenie)

Zwraca średnią wartości innych niż null.

**Argumenty**

`Int32`, ,,`Double`I .`Decimal` `Int64`

**Wartość zwracana**

Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount (wyrażenie)

Zwraca rozmiar zagregowany, w tym wartość null i zduplikowane wartości.

**Argumenty**

Dowolny typ.

**Wartość zwracana**

A `Int64`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count (wyrażenie)

Zwraca rozmiar zagregowany, w tym wartość null i zduplikowane wartości.

**Argumenty**

Dowolny typ.

**Wartość zwracana**

A `Int32`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>Max (wyrażenie)

Zwraca wartość maksymalną wartości różną od null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Wartość zwracana**

Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min (wyrażenie)

Zwraca wartość minimalną wartości innych niż null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Wartość zwracana**

Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev (wyrażenie)

Zwraca odchylenie standardowe wartości innych niż null.

**Argumenty**

`Int32` ,`Int64` ,`Decimal`, .`Double`

**Wartość zwracana**

A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP (wyrażenie)

Zwraca odchylenie standardowe dla populacji wszystkich wartości.

**Argumenty**

`Int32` ,`Int64` ,`Decimal`, .`Double`

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>Sum (wyrażenie)

Zwraca sumę wartości innych niż null.

**Argumenty**

`Int32` ,`Int64` ,`Decimal`, .`Double`

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var (wyrażenie)

Zwraca wariancję wszystkich wartości innych niż null.

**Argumenty**

`Int32` ,`Int64` ,`Decimal`, .`Double`

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP (wyrażenie)

Zwraca wariancję populacji dla wszystkich wartości innych niż null.

**Argumenty**

`Int32` ,`Int64` ,`Decimal`, .`Double`

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL. Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Agregacje oparte na kolekcjach

Agregacje oparte na kolekcjach (funkcje kolekcji) działają na kolekcjach i zwracają wartość. Na przykład jeśli zamówienia są kolekcją wszystkich zamówień, można obliczyć najwcześniejszą datę wysyłki przy użyciu następującego wyrażenia:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Wyrażenia wewnątrz agregacji opartych na kolekcjach są oceniane w ramach bieżącego zakresu rozpoznawania nazw otoczenia.

## <a name="group-based-aggregates"></a>Agregacje oparte na grupach

Agregacje oparte na grupach są obliczane na podstawie grupy zgodnie z definicją w klauzuli GROUP BY. Dla każdej grupy w wyniku oddzielna wartość zagregowana jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczenia agregacji. Gdy klauzula GROUP by jest używana w wyrażeniu SELECT, w klauzuli projekcji lub order by może występować tylko nazwa wyrażenia grupującego, agregacje lub wyrażenia stałe.

Poniższy przykład oblicza średnią ilość zamówioną dla każdego produktu:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

Możliwe jest posiadanie agregacji opartej na grupach bez jawnej klauzuli Group by w wyrażeniu SELECT. W takim przypadku wszystkie elementy są traktowane jako pojedyncze grupy. Jest to równoważne określeniu grupowania na podstawie stałej. Zrób to na przykład następujące wyrażenie:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Jest to równoważne z następującymi:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Wyrażenia wewnątrz agregacji opartej na grupach są oceniane w zakresie rozpoznawania nazw, który byłby widoczny dla wyrażenia klauzuli WHERE.

Podobnie jak w języku Transact-SQL, agregacje oparte na grupach mogą również określać Modyfikatory ALL lub DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji agregacji danych wejściowych przed obliczaniem agregacji. Jeśli modyfikator ALL jest określony (lub jeśli nie określono modyfikatora), nie jest wykonywane żadne duplikowanie eliminacji.

## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](canonical-functions.md)
