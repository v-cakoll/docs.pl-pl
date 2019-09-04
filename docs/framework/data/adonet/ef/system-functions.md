---
title: Funkcje systemowe
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248236"
---
# <a name="system-functions"></a>Funkcje systemowe
Dostawca danych .NET Framework dla SQL Server (SqlClient) udostępnia następujące funkcje systemowe:  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Zwraca wartość sumy kontrolnej. `CHECKSUM`jest przeznaczony do użycia podczas tworzenia indeksów skrótu.<br /><br /> **Argumenty**<br /><br /> `value`: A `Boolean`, `Byte`, ,`Int16` ,,`DateTime`, ,,,,lub.`Decimal` `Binary` `String` `Single` `Int32` `Int64` `Double` `Guid` Można określić jedną, dwie lub trzy wartości.<br /><br /> **Wartość zwracana**<br /><br /> Wartość bezwzględna określonego wyrażenia.<br /><br /> **Przykład**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Tworzy bieżącą datę i godzinę w SQL Server wewnętrznym formacie dla `DateTime` wartości z dokładnością 7 w SQL Server 2008 i dokładnością 3 w SQL Server 2005.<br /><br /> **Wartość zwracana**<br /><br /> Bieżąca data i godzina systemowa jako `DateTime`.<br /><br /> **Przykład**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER``()`|Zwraca nazwę bieżącego użytkownika.<br /><br /> **Wartość zwracana**<br /><br /> An ASCII `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Zwraca liczbę bajtów użytych do reprezentowania dowolnego wyrażenia.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Time`, ,,`String`, ,`Binary`, ,`DateTimeOffset`lub `Int32` `Int64` `Single` `Decimal` `Double` `DateTime` `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> Rozmiar właściwości jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Zwraca nazwę stacji roboczej.<br /><br /> **Wartość zwracana**<br /><br /> Unicode `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Określa, czy wyrażenie wejściowe jest prawidłową datą.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Time`, ,,`String`, ,`Binary`, ,`DateTimeOffset`lub `Int32` `Int64` `Single` `Decimal` `Double` `DateTime` `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`. Jeden (1), jeśli wyrażenie wejściowe jest prawidłową datą. Zero (0) w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Określa, czy wyrażenie jest prawidłowym typem liczbowym.<br /><br /> **Argumenty**<br /><br /> `expression`: A `Boolean`, `Byte`, ,`Int16` ,,`Time`, ,,`String`, ,`Binary`, ,`DateTimeOffset`lub `Int32` `Int64` `Single` `Decimal` `Double` `DateTime` `Guid`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`. Jeden (1), jeśli wyrażenie wejściowe jest prawidłową datą. Zero (0) w przeciwnym razie.<br /><br /> **Przykład**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Tworzy unikatową wartość typu GUID.<br /><br /> **Wartość zwracana**<br /><br /> A `Guid`.<br /><br /> **Przykład**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Zwraca nazwę użytkownika bazy danych z określonego numeru identyfikacyjnego.<br /><br /> **Argumenty**<br /><br /> `expression`: Numer `Int32` identyfikacyjny skojarzony z użytkownikiem bazy danych.<br /><br /> **Wartość zwracana**<br /><br /> Unicode `String`.<br /><br /> **Przykład**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Aby uzyskać więcej informacji na temat funkcji ciągów obsługiwanych przez program SqlClient, zapoznaj się z dokumentacją dla SQL Server wersji określonej w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[System Functions Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[System Functions Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[System Functions (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Zobacz także

- [Jednostki języka SQL](./language-reference/entity-sql-language.md)
- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
