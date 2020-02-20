---
title: Funkcje daty i godziny
ms.date: 03/30/2017
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
ms.openlocfilehash: 39bbc2bff378ff4434df6f33a1b175055f2e5800
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452516"
---
# <a name="date-and-time-functions"></a>Funkcje daty i godziny
.NET Framework Dostawca danych for SQL Server (SqlClient) zawiera funkcje daty i godziny, które wykonują operacje na `System.DateTime` wartości wejściowej i zwracają wynik `string`, liczbowy lub `System.DateTime` wartości. Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient. Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje. W poniższej tabeli przedstawiono funkcje daty i godziny SqlClient.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`DATEADD(datepart, number, date)`|Zwraca nową wartość `DateTime`, która jest oparta na dodawaniu interwału do określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, który reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `number`: wartość `Int32`, `Int64`, `Decimal`lub `Double` używana do przyrostu `datepart`.<br /><br /> `date:` wyrażenie, które zwraca `DateTime`, lub `DateTimeOffset`lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Nowa wartość `DateTime`lub `DateTimeOffset`lub `Time` z dokładnością = [0-7].<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(datepart,startdate,enddate)`|Zwraca liczbę granic daty i godziny przekroczenia między dwoma określonymi datami.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, który reprezentuje część daty, aby obliczyć różnicę.<br /><br /> `startdate`: Data początkowa obliczenia jest wyrażeniem zwracającym wartość `DateTime`lub `DateTimeOffset`lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> `enddate:` datą końcową obliczenia jest wyrażenie, które zwraca `DateTime`, lub `DateTimeOffset`lub `Time` wartość z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(datepart, date)`|Zwraca ciąg znaków reprezentujący określoną wartość parametru datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, który reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające `DateTime,` lub `DateTimeOffset`lub `Time` wartość z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Ciąg znaków reprezentujący określoną wartość parametru datepart określoną datę.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(datepart, date)`|Zwraca liczbę całkowitą reprezentującą określoną wartość parametru datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: `String`, który reprezentuje część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające wartość `DateTime,` lub `DateTimeOffset,` lub `Time` z dokładnością = [0-7] lub ciągiem znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Określony parametr datepart określonej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(date)`|Zwraca dzień z określonej daty jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Dzień określonej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Tworzy bieżącą datę i godzinę w SQL Server wewnętrznym formacie dla wartości DateTime.<br /><br /> **Wartość zwracana**<br /><br /> Bieżąca data i godzina systemowa jako `DateTime` z dokładnością do 3.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Tworzy wartość DateTime w formacie UTC (uniwersalny czas koordynowany lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> Wartość `DateTime` z dokładnością 3 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(date)`|Zwraca miesiąc z określoną datą jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Miesiąc podanej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(date)`|Zwraca rok z określonej daty jako liczbę całkowitą.<br /><br /> **Argumenty**<br /><br /> `date`: wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Rok dla określonej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Zwraca wartość `DateTime` z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> Wartość `DateTime` z dokładnością do 7.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Tworzy wartość DateTime w formacie UTC (uniwersalny czas koordynowany lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> Wartość `DateTime` z dokładnością = 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Zwraca `DateTimeOffset` z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> Wartość `DateTimeOffset` z dokładnością 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Aby uzyskać więcej informacji na temat funkcji usługi Data i godzina obsługiwanych przez program SqlClient, zobacz [typy danych daty i godziny oraz funkcje (Transact-SQL)](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).
  
## <a name="see-also"></a>Zobacz też

- [Klient SQL dla funkcji programu Entity Framework](sqlclient-for-ef-functions.md)
