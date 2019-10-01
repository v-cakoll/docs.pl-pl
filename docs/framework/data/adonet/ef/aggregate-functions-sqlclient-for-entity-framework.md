---
title: Funkcje agregujące (SqlClient dla Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700057"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funkcje agregujące (SqlClient dla Entity Framework)
Dostawca danych .NET Framework dla SQL Server (SqlClient) udostępnia funkcje agregujące. Funkcje agregujące wykonują obliczenia na zestawie wartości wejściowych i zwracają wartość. Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.  
  
 Poniżej przedstawiono funkcje agregujące SqlClient.  

## <a name="avgexpression"></a>Średnia (wyrażenie)

Zwraca średnią wartości w kolekcji. Wartości null są ignorowane.

**Argumenty**

@No__t-0, `Int64`, `Double` i `Decimal`.

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG (kolekcja)
 
 Zwraca sumę kontrolną wartości w kolekcji. Wartości null są ignorowane.
 
 **Argumenty**
 
 Kolekcja (`Int32`).
 
 **Wartość zwracana**
 
 @No__t-0.
 
 **Przykład**
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a>COUNT (wyrażenie)

Zwraca liczbę elementów w kolekcji jako `Int32`.

**Argumenty**

Kolekcja @ no__t-0T >, gdzie T jest jednym z następujących typów:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (niezwrócone w SQL Server 2000)|

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a>COUNT_BIG (wyrażenie)
 
Zwraca liczbę elementów w kolekcji jako `bigint`.
 
 **Argumenty**
 
 Kolekcja (T), gdzie T jest jednym z następujących typów:
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid` (niezwrócone w SQL Server 2000)|

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX (wyrażenie)

Zwraca maksymalną wartość kolekcji.

**Argumenty**

Kolekcja (T), gdzie T jest jednym z następujących typów: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN (wyrażenie)

Zwraca minimalną wartość w kolekcji.

**Argumenty**

Kolekcja (T), gdzie T jest jednym z następujących typów: 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV (wyrażenie)

Zwraca statystyczne odchylenie standardowe wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP (wyrażenie)

Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUM (wyrażenie)

Zwraca sumę wszystkich wartości w kolekcji.

**Argumenty**

Kolekcja (T), gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double`, `Decimal`.

**Wartość zwracana**

Typ `expression`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR (wyrażenie)

Zwraca wariancję statystyczną wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>VARP (wyrażenie)

Zwraca wariancję statystyczną dla populacji dla wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja (`Double`).

**Wartość zwracana**

@No__t-0.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a>Zobacz także

- [Funkcje agregujące (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Jednostki języka SQL](./language-reference/entity-sql-language.md)
- [Funkcje agregujące Canonical](./language-reference/aggregate-canonical-functions.md)
