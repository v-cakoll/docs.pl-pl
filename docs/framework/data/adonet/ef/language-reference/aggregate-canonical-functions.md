---
title: "Canonical funkcje agregujące"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 071c6b41d24465a599afa87a296c0797e8ca6ed9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="aggregate-canonical-functions"></a>Canonical funkcje agregujące

Agregacje są wyrażeń, które zmniejszenie szereg wartości wejściowe do, na przykład pojedyncza wartość. Agreguje zwykle są używane w połączeniu z klauzulą GROUP BY wyrażenie SELECT, a istnieją ograniczenia, w którym mogą być używane.

W poniższej tabeli przedstawiono wartości zagregowanej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.

| Funkcja | Opis |
| -------- | ----------- |
| `Avg(expression)` | Zwraca średnią z wartości inne niż null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, I `Decimal`.<br><br>**Wartość zwracana**<br><br>Typ `expression`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)][!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)] |
| `BigCount(expression)` | Zwraca rozmiar agregacji wartości null i zduplikowane.<br><br>**Argumenty**<br><br>Dowolnego typu.<br><br>**Wartość zwracana**<br><br>`Int64`.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)][!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)] |
| `Count(expression)` | Zwraca rozmiar agregacji wartości null i zduplikowane.<br><br>**Argumenty**<br><br>Dowolnego typu.<br><br>**Wartość zwracana**<br><br>`Int32`.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)][!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)] |
| `Max(expression)` | Zwraca maksymalną wartość inną niż null.<br><br>**Argumenty**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Wartość zwracana**<br><br>Typ `expression`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)][!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)] |
| `Min(expression)` | Zwraca minimalną wartość inną niż null.<br><br>**Argumenty**<br><br>A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.<br><br>**Wartość zwracana**<br><br>Typ `expression`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)][!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)] |
| `StDev(expression)` | Zwraca odchylenie standardowe wartości inne niż null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Wartość zwracana**<br><br>A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)][!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)] |
| `StDevP(expression)` | Zwraca odchylenie standardowe populacji wszystkich wartości.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Wartość zwracana**<br><br>A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)][!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)] |
| `Sum(expression)` | Zwraca sumę wartości innych niż null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Wartość zwracana**<br><br>A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)][!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)] |
| `Var(expression)` | Zwraca wariancję wszystkich wartości innych niż null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Wartość zwracana**<br><br>A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)][!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)] |
| `VarP(expression)` | Zwraca wariancję populacji wszystkich wartości innych niż null.<br><br>**Argumenty**<br><br>`Int32`, `Int64`, `Double`, `Decimal`.<br><br>**Wartość zwracana**<br><br>A `Double`. `Null`, jeśli wszystkie wartości wejściowe są `null` wartości.<br><br>**Przykład** [!code-csharp [DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)][!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] |

Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework funkcji](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).

## <a name="collection-based-aggregates"></a>Agreguje opartego na kolekcji

Oparte na kolekcji wartości zagregowanych (kolekcji funkcji) działają na kolekcje i zwracać wartość. Na przykład jeśli zamówień to zbiór wszystkich zleceń, można obliczyć Najwcześniejsza data wysyłki z następującym wyrażeniem:

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

Wyrażenia w kolekcji na podstawie wartości zagregowane są obliczane w zakresie bieżącego otoczenia rozpoznawania nazw.

## <a name="group-based-aggregates"></a>Na podstawie grupy agregacji

Na podstawie grupy agregacje są obliczane w grupie zgodnie z definicją w klauzuli GROUP BY. Dla każdej grupy w wyniku oddzielne agregacji jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczania agregacji. Użycie klauzuli group by w wyrażeniu Wybierz grupowanie tylko nazwy wyrażeń, agregacje lub wyrażenia stałe mogą być obecne w projekcji lub klauzuli order by.

W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu:

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

Istnieje możliwość ma agregacji na podstawie grupy bez jawnego-klauzuli group by w wyrażeniu SELECT. W takim przypadku wszystkie elementy są traktowane jako pojedynczej grupy. Jest to odpowiednik określania grupowanie oparte na stałą. Wykonaj, na przykład poniższe wyrażenie:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

Jest to równoważne z następujących czynności:

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

Wyrażenia wewnątrz wartości zagregowanej na podstawie grupy są przetwarzane w zakresie rozpoznawania nazw, które będą widoczne dla wyrażenia klauzuli WHERE.

Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregacje na podstawie grupy można również określić wszelkie lub modyfikator DISTINCT. Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji zagregowanej wejściowych przed agregacji jest obliczana. Jeśli określono wszystkie modyfikator (lub modyfikator nie jest określony), jest wykonywane nie zduplikowane eliminacji.  

## <a name="see-also"></a>Zobacz także

[Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
