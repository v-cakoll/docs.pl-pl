---
title: Funkcje agregujące (SqlClient programu Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: f2f2b557cd9f126ddd513a0f42d3ac95114c3822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606783"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funkcje agregujące (SqlClient programu Entity Framework)
.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje agregujące. Funkcje agregujące wykonywanie obliczeń na zestaw wartości wejściowych i zwracają wartość. Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.  
  
 Dostępne są następujące funkcje agregujące SqlClient.  

## <a name="avgexpression"></a>AVG(Expression)

Zwraca średnią z wartości w kolekcji. Wartości null są ignorowane.

**Argumenty**

`Int32`, `Int64`, `Double`, I `Decimal`.

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a>CHECKSUM_AGG(Collection)
 
 Zwraca sumę kontrolną wartości w kolekcji. Wartości null są ignorowane.
 
 **Argumenty**
 
 Kolekcja (`Int32`).
 
 **Wartość zwracana**
 
 `Int32`.
 
 **Przykład**
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>Count(Expression)

Zwraca liczbę elementów w kolekcji jako `Int32`.

**Argumenty**

Kolekcja\<T >, gdzie T jest jednym z następujących typów:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (nie jest zwracana w programie SQL Server 2000)|

**Wartość zwracana**

`Int32`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
[! code-sql[SQLSERVER_COUNT # pojęcia EntityServices punktu dystrybucji](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)
 
## <a name="countbigexpression"></a>COUNT_BIG(Expression)
 
 Zwraca liczbę elementów w kolekcji jako `bigint`.
 
 **Argumenty**
 
 Collection(T), gdzie T jest jednym z następujących typów:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (nie jest zwracana w programie SQL Server 2000)|

**Wartość zwracana**

`Int64`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(Expression)

Zwraca maksymalną wartość w kolekcji.

**Argumenty**

Collection(T), gdzie T jest jednym z następujących typów: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(Expression)

Zwraca minimalną wartość w kolekcji.

**Argumenty**

Collection(T), gdzie T jest jednym z następujących typów: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>StDev(Expression)

Zwraca statystyczne odchylenie standardowe wszystkich wartości określonego wyrażenia.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

A `Double`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP(Expression)

Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości określonego wyrażenia.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

A `Double`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM(Expression)

Zwraca sumę wszystkich wartości w kolekcji.

**Argumenty**

Collection(T), gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(Expression)

Zwraca statystyczną wariancję wszystkich wartości określonego wyrażenia.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

A `Double`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP(Expression)

Zwraca statystyczne wariancję populacji dla wszystkich wartości podanego wyrażenia.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

A `Double`.

**Przykład**

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Zobacz także

Aby uzyskać więcej informacji na temat funkcji agregujących, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:

- **SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))
- **Program SQL Server 2008 lub nowszy:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)

- [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Funkcje agregujące Canonical](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
