---
title: Funkcje systemu
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 91c8e178fc6903dddc287ac2ca00c3152a9e3ce7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765727"
---
# <a name="system-functions"></a>Funkcje systemu
.NET Framework Data Provider for SQL Server (SqlClient) zapewnia następujące funkcje systemu:  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Zwraca wartość sumy kontrolnej. `CHECKSUM` jest przeznaczony do użycia w tworzenie indeksów skrótu.<br /><br /> **Argumenty**<br /><br /> `value`: A `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `String`, `Binary`, lub `Guid`. Można określić jedną, dwie lub trzy wartości.<br /><br /> **Wartość zwracana**<br /><br /> Wartość bezwzględna określone wyrażenie.<br /><br /> **Przykład**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Generuje bieżącą datę i godzinę w formacie wewnętrznych programu SQL Server dla `DateTime` wartości dokładności 7 w programie SQL Server 2008 i dokładność 3 programu SQL Server 2005.<br /><br /> **Wartość zwracana**<br /><br /> Bieżącej systemowej daty i godziny jako `DateTime`.<br /><br /> **Przykład**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Zwraca nazwę bieżącego użytkownika.<br /><br /> **Wartość zwracana**<br /><br /> ASCII `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Zwraca liczbę bajtów reprezentujących dowolne wyrażenie.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, lub `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> Rozmiar właściwości jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Zwraca nazwę stacji roboczej.<br /><br /> **Wartość zwracana**<br /><br /> Unicode `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Określa, czy wyrażenie wejściowe jest prawidłową datą.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, lub `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`. Jednego (1), jeśli wyrażenie wejściowe jest prawidłową datą. Wartość zero (0) w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Określa, czy wyrażenie jest prawidłowy typ liczbowy.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, `Int16`, `Int32`, `Int64`, `Single`, `Decimal`, `Double`, `DateTime`, `Time`, `DateTimeOffset`, `String`, `Binary`, lub `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`. Jednego (1), jeśli wyrażenie wejściowe jest prawidłową datą. Wartość zero (0) w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Tworzy unikatową wartość typu Guid.<br /><br /> **Wartość zwracana**<br /><br /> A `Guid`.<br /><br /> **Przykład**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Zwraca nazwę użytkownika bazy danych z numer identyfikacyjny określony.<br /><br /> **Argumenty**<br /><br /> `expression`: `Int32` Numer identyfikacyjny skojarzonych z użytkownikiem bazy danych.<br /><br /> **Wartość zwracana**<br /><br /> Unicode `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Aby uzyskać więcej informacji na temat funkcje ciągów, które obsługuje SqlClient zobacz dokumentację dla używanej wersji programu SQL Server określona w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[System funkcje języka Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115918)|[System funkcje języka Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115917)|[System Functions (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Zobacz też  
 [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
