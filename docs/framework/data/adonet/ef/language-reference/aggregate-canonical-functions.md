---
title: Funkcje agregujące Canonical
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: e4772176130fc72a22645462921c90dd5b7967b2
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752274"
---
# <a name="aggregate-canonical-functions"></a>Funkcje agregujące Canonical

Agregacje są wyrażeniami, które zmniejszenie szereg wartości wejściowych do, na przykład pojedynczej wartości. Agregacje są zwykle używane w połączeniu z klauzulą GROUP BY Wybierz wyrażenie, a istnieją ograniczenia, na którym mogą być używane.

## <a name="aggegate-entity-sql-canonical-functions"></a>Funkcje canonical Aggegate jednostki SQL

Dostępne są następujące funkcje agregujące canonical jednostki SQL.

### <a name="avgexpression"></a>AVG(Expression)

Zwraca średnią wartości innych niż null.

**Argumenty**

`Int32`, `Int64`, `Double`, I `Decimal`.

**Wartość zwracana**

Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a>BigCount(expression)

Zwraca rozmiar agregacji, łącznie z wartościami null i zduplikowane.

**Argumenty**

Dowolnego typu.

**Wartość zwracana**

`Int64`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a>Count(Expression) 

Zwraca rozmiar agregacji, łącznie z wartościami null i zduplikowane.

**Argumenty**

Dowolnego typu.

**Wartość zwracana**

`Int32`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a>MAX(Expression)

Zwraca maksymalną liczbę wartości innych niż null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Wartość zwracana**

Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a>Min(Expression)

Zwraca wartość minimalną wartość inną niż null.

**Argumenty**

A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.

**Wartość zwracana**

Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a>StDev(expression)

Zwraca odchylenie standardowe wartości innych niż null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a>StDevP(expression)

Zwraca odchylenie standardowe populacji dla wszystkich wartości.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a>Sum(Expression)

Zwraca sumę wartości innych niż null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a>Var(Expression)

Zwraca wariancję wszystkich wartości innych niż null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a>VarP(expression)

Zwraca wariancję populacji dla wszystkich wartości innych niż null.

**Argumenty**

`Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.

**Przykład**

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Wartości zagregowane z kolekcji

Opartego na kolekcji wartości zagregowanych (kolekcji funkcji) działają na kolekcji i zwracają wartość. Na przykład jeśli zamówienia to zbiór wszystkich zamówień, można obliczyć Najwcześniejsza data wysyłki za pomocą następującego wyrażenia:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Wyrażenia wewnątrz opartego na kolekcji wartości zagregowane są obliczane w bieżącym zakresie rozpoznawania nazw otoczenia.

## <a name="group-based-aggregates"></a>Agregacje oparte na grupach

Oparte na grupach agregacje są obliczane przez grupę, zgodnie z definicją w klauzuli GROUP BY. Dla każdej grupy w wyniku oddzielne agregacji jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczania agregacji. Użycie klauzuli group by w wyrażeniu wybierz tylko grupowanie nazwy wyrażeń, agregacje lub wyrażenia stałe mogą być obecne w projekcji lub klauzuli order by.

W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Istnieje możliwość mają oparte na grupach agregacji bez jawnego-klauzuli group by w wyrażeniu SELECT. W takim przypadku wszystkie elementy są traktowane jako pojedynczej grupy. Jest to równoważne określania grupowanie oparte na stałą. Weźmy na przykład, następujące wyrażenie:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

To jest odpowiednikiem następujących czynności:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Wyrażenia wewnątrz agregacji oparte na grupach są obliczane w zakresie rozpoznawania nazw, które będą widoczne dla wyrażenie klauzuli WHERE.

Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], oparte na grupach agregacji można również określić wszystkie lub modyfikator DISTINCT. Jeśli modyfikator DISTINCT jest określony, duplikaty są eliminowane z agregacji kolekcja wejściowa przed agregacji jest kolumną obliczaną. Jeśli określono wszystkie modyfikator (lub jeśli określono nie modyfikator), jest wykonywane nie wyeliminowania zduplikowanych.  

## <a name="see-also"></a>Zobacz także

[Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
