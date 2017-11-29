---
title: "Funkcje agregujące (SqlClient Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b60cffd357022454de001986a48ef06bdd1fe3f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>Funkcje agregujące (SqlClient Entity Framework)
.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje agregujące. Funkcje agregujące obliczeń na zestaw wartości wejściowych i zwracać wartość. Te funkcje są w obszarze nazw SqlServer, która jest dostępna, gdy używasz SqlClient. Właściwości przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, które prefiks jest używany przez tego dostawcę dla określonych elementów składowych, takich jak typy i funkcje.  
  
 W poniższej tabeli przedstawiono funkcje agregujące SqlClient.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|Zwraca średnią z wartości w kolekcji.<br /><br /> Wartości null są ignorowane.<br /><br /> **Argumenty**<br /><br /> `Int32`, `Int64`, `Double`, I `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|Zwraca sumę kontrolną wartości w kolekcji.<br /><br /> Wartości null są ignorowane.<br /><br /> **Argumenty**<br /><br /> Kolekcja (`Int32`).<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|Zwraca liczbę elementów w kolekcji jako `Int32`.<br /><br /> **Argumenty**<br /><br /> Kolekcja T gdzie T jest jednym z następujących typów:<br /><br /> `Guid`(nie zwrócił programu SQL Server 2000)<br /><br /> `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, lub `Binary`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|Zwraca liczbę elementów w kolekcji jako `bigint`.<br /><br /> **Argumenty**<br /><br /> Kolekcja T gdzie T jest jednym z następujących typów:<br /><br /> `Guid`(nie zwrócił programu SQL Server 2000), `Boolean`, `Double`, `DateTime`, `DateTimeOffset`, `Time`, `String`, lub `Binary`.<br /><br /> **Wartość zwracana**<br /><br /> `Int64`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|Zwraca maksymalną wartość w kolekcji.<br /><br /> **Argumenty**<br /><br /> Kolekcja T gdzie T jest jednym z następujących typów: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`, `Binary`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|Zwraca minimalną wartość w kolekcji.<br /><br /> **Argumenty**<br /><br /> Kolekcja T gdzie T jest jednym z następujących typów: `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time` , `String`,<br /><br /> `Binary`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|Zwraca statystyczne odchylenie standardowe wszystkich wartości z określonego wyrażenia.<br /><br /> **Argumenty**<br /><br /> Kolekcja (`Double`).<br /><br /> **Wartość zwracana**<br /><br /> A `Double`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości w określonym wyrażeniu.<br /><br /> **Argumenty**<br /><br /> Kolekcja (`Double`).<br /><br /> **Wartość zwracana**<br /><br /> A `Double`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|Zwraca sumę wszystkich wartości w kolekcji.<br /><br /> **Argumenty**<br /><br /> Kolekcja T gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double`, `Decimal`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|Zwraca statystyczną wariancję wszystkich wartości w określonym wyrażeniu.<br /><br /> **Argumenty**<br /><br /> Kolekcja (`Double`).<br /><br /> **Wartość zwracana**<br /><br /> A `Double`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|Zwraca statystyczne wariancję populacji dla wszystkich wartości w określonym wyrażeniu.<br /><br /> **Argumenty**<br /><br /> Kolekcja (`Double`).<br /><br /> **Wartość zwracana**<br /><br /> A `Double`.<br /><br /> **Przykład**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 Aby uzyskać więcej informacji o funkcji agregujących, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określona w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkcje agregujące (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[Funkcje agregujące (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[Funkcje agregujące (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>Zobacz też  
 [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Canonical funkcje agregujące](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
