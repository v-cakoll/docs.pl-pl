---
title: Funkcje agregujące (SqlClient for Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150652"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funkcje agregujące (SqlClient for Entity Framework)
Dostawca danych programu .NET Framework dla programu SQL Server (SqlClient) udostępnia funkcje agregujące. Funkcje agregowane wykonują obliczenia na zestawie wartości wejściowych i zwracają wartość. Te funkcje znajdują się w obszarze nazw SqlServer, który jest dostępny podczas korzystania z SqlClient. Właściwość obszaru nazw dostawcy umożliwia entity framework, który prefiks jest używany przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.  
  
 Poniżej przedstawiono funkcje agregujące SqlClient.  

## <a name="avgexpression"></a>AVG(wyrażenie)

Zwraca średnią wartości w kolekcji. Wartości null są ignorowane.

**Argumenty**

An `Int32` `Int64`, `Double`, `Decimal`i .

**Wartość zwracana**

Typ . `expression`

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a>CHECKSUM_AGG(kolekcja)

 Zwraca sumę kontrolną wartości w kolekcji. Wartości null są ignorowane.

 **Argumenty**

 Kolekcja(`Int32`).

 **Wartość zwracana**

 An `Int32`.

 **Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a>COUNT(wyrażenie)

Zwraca liczbę elementów w kolekcji jako plik `Int32`.

**Argumenty**

Kolekcja\<T>, gdzie T jest jednym z następujących typów:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(nie zwrócono w programie SQL Server 2000)|

**Wartość zwracana**

An `Int32`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a>COUNT_BIG(wyrażenie)

Zwraca liczbę elementów w kolekcji jako `bigint`.

 **Argumenty**

 Kolekcja(T), gdzie T jest jednym z następujących typów:

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|`Guid`(nie zwrócono w programie SQL Server 2000)|

**Wartość zwracana**

An `Int64`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a>MAX(wyrażenie)

Zwraca maksymalną wartość kolekcji.

**Argumenty**

Kolekcja(T), gdzie T jest jednym z następujących typów:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ . `expression`

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a>MIN(wyrażenie)

Zwraca minimalną wartość w kolekcji.

**Argumenty**

Kolekcja(T), gdzie T jest jednym z następujących typów:

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

**Wartość zwracana**

Typ . `expression`

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a>STDEV(wyrażenie)

Zwraca statystyczne odchylenie standardowe wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja(`Double`).

**Wartość zwracana**

Klasa `Double`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a>STDEVP(wyrażenie)

Zwraca statystyczne odchylenie standardowe dla populacji dla wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja(`Double`).

**Wartość zwracana**

Klasa `Double`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a>SUMA(wyrażenie)

Zwraca sumę wszystkich wartości w kolekcji.

**Argumenty**

Kolekcja(T), gdzie T jest jednym z `Int32` `Int64`następujących `Double` `Decimal`typów: , , .

**Wartość zwracana**

Typ . `expression`

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a>VAR(wyrażenie)

Zwraca wariancję statystyczną wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja(`Double`).

**Wartość zwracana**

Klasa `Double`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a>WARIANCJA(wyrażenie)

Zwraca wariancję statystyczną dla populacji dla wszystkich wartości w określonym wyrażeniu.

**Argumenty**

Kolekcja(`Double`).

**Wartość zwracana**

Klasa `Double`.

**Przykład**

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a>Zobacz też

- [Funkcje agregowane (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [Jednostki języka SQL](./language-reference/entity-sql-language.md)
- [Funkcje agregujące Canonical](./language-reference/aggregate-canonical-functions.md)
