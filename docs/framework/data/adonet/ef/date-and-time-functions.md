---
title: Funkcje daty i godziny
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 56ef2f0b0a62f6b2cf6db5fe2c6713c58228ff6f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556875"
---
# <a name="date-and-time-functions"></a>Funkcje daty i godziny
.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje daty i godziny, które wykonują operacje na `System.DateTime` wartość wejściowa i zwracają `string`, numerycznego, lub `System.DateTime` wartość wyniku. Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje. W poniższej tabeli przedstawiono SqlClient funkcji daty i godziny.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Zwraca nowy `DateTime` wartość, która opiera się na dodanie interwału do określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: Element `String` reprezentujący część daty, na którym ma zostać zwrócona nowa wartość.<br /><br /> `number``Int32`, `Int64`, `Decimal`, Lub `Double` wartość używana do następującej `datepart`.<br /><br /> `date:` Wyrażenie, które zwraca `DateTime`, lub `DateTimeOffset`, lub `Time` z dokładnością = [0-7] lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Nowy `DateTime`, lub `DateTimeOffset`, lub `Time` wartości z dokładnością = [0-7].<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Zwraca liczbę daty i godziny granice progów między dwoma określonymi datami.<br /><br /> **Argumenty**<br /><br /> `datepart`: Element `String` reprezentujący część daty do obliczenia różnicy.<br /><br /> `startdate`: Począwszy od daty w obliczeniach jest wyrażeniem, które zwraca `DateTime`, lub `DateTimeOffset`, lub `Time` wartości z dokładnością = [0-7] lub ciąg znaków w formacie daty.<br /><br /> `enddate:` Datę końcową w obliczeniach jest wyrażeniem, które zwraca `DateTime`, lub `DateTimeOffset`, lub `Time` wartości z dokładnością = [0-7] lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Zwraca ciąg znaków reprezentujący określonej daty określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: Element `String` reprezentujący część daty, na którym ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie, które zwraca `DateTime,` lub `DateTimeOffset`, lub `Time` wartości z dokładnością = [0-7] lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Ciąg znaków reprezentujący określonej daty określonej daty.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Zwraca liczbę całkowitą reprezentującą określoną datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: Element `String` reprezentujący część daty, na którym ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie, które zwraca `DateTime,` lub `DateTimeOffset,` lub `Time` wartości z dokładnością = [0-7] lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Określony datepart określonej daty, jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Zwraca dzień określona data jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Dzień określonej daty, jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Generuje bieżącą datę i czas w wewnętrznym formacie programu SQL Server dla wartości daty/godziny.<br /><br /> **Wartość zwracana**<br /><br /> Bieżącej systemowej daty i godziny jako `DateTime` z dokładnością do 3.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Tworzy wartość daty/godziny w formacie UTC (Coordinated Universal Time lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość z dokładnością do 3 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Zwraca miesiąc określona data jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> W miesiącu, w określonym dniu jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Zwraca rok z określonej daty, jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Rok od określonej daty, jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Zwraca `DateTime` wartość z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime` wartość z dokładnością do 7.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Tworzy wartość daty/godziny w formacie UTC (Coordinated Universal Time lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość z dokładnością = 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Zwraca `DateTimeOffset` z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset` wartość z dokładnością do 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Aby uzyskać więcej informacji o funkcji daty i godziny, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Zobacz też  
 [Klient SQL dla funkcji programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
