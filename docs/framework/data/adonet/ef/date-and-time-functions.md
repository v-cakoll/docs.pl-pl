---
title: Funkcje daty i godziny
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: fe70795ba98cf500f2066980d259ff995c3398e0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251645"
---
# <a name="date-and-time-functions"></a>Funkcje daty i godziny
.NET Framework dostawca danych for SQL Server (SqlClient) zawiera funkcje daty i godziny, które wykonują operacje na `System.DateTime` wartości wejściowej i `string`zwracają wynik, wartość numeryczną lub `System.DateTime` wartości. Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje. W poniższej tabeli przedstawiono funkcje daty i godziny SqlClient.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Zwraca nową `DateTime` wartość opartą na dodawaniu interwału do określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `number`: `Int32`, ,,`Decimal` `datepart`Lub wartośćużywanadoprzyrostu`Double`. `Int64`<br /><br /> `date:`Wyrażenie zwracające wartość `DateTime` `DateTimeOffset`, `Time` lub lub z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Nowa `DateTime`, lub `DateTimeOffset`lub `Time` wartość o precyzji = [0-7].<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Zwraca liczbę granic daty i godziny przekroczenia między dwoma określonymi datami.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Reprezentuje część daty, aby obliczyć różnicę.<br /><br /> `startdate`: Data początkowa obliczenia jest wyrażeniem zwracającym `DateTime`wartość, lub `DateTimeOffset`lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> `enddate:`Data końcowa obliczenia jest wyrażeniem zwracającym `DateTime`wartość, lub `DateTimeOffset`lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Zwraca ciąg znaków reprezentujący określoną wartość parametru datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające `DateTime,` wartość lub `DateTimeOffset`, lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Ciąg znaków reprezentujący określoną wartość parametru datepart określoną datę.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Zwraca liczbę całkowitą reprezentującą określoną wartość parametru datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String` Reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające `DateTime,` wartość lub `DateTimeOffset,` lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Określona wartość parametru datepart określonego dnia, jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Zwraca dzień z określonej daty jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Dzień określonego dnia jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Tworzy bieżącą datę i godzinę w SQL Server wewnętrznym formacie dla wartości DateTime.<br /><br /> **Wartość zwracana**<br /><br /> Bieżąca data i godzina `DateTime` systemowa z dokładnością 3.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Tworzy wartość DateTime w formacie UTC (uniwersalny czas koordynowany lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość z dokładnością 3 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Zwraca miesiąc z określoną datą jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Miesiąc określonego dnia jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Zwraca rok z określonej daty jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Rok określonego dnia jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|`DateTime` Zwraca wartość z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość z dokładnością do 7.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Tworzy wartość DateTime w formacie UTC (uniwersalny czas koordynowany lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość o dokładności = 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|`DateTimeOffset` Zwraca z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> `DateTimeOffset` Wartość z dokładnością 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Aby uzyskać więcej informacji na temat funkcji usługi Data i godzina obsługiwanych przez program SqlClient, zapoznaj się z dokumentacją dla SQL Server wersji określonej w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115908)|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115909)|[Funkcje daty i godziny (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Zobacz także

- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
