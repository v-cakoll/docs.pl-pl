---
title: Funkcje daty i godziny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 971762d0-663b-4b64-8c61-352a8e6d3949
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3d47b4ced66a8826424cdbb75e5694fadb9038d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="date-and-time-functions"></a>Funkcje daty i godziny
.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje daty i godziny, które wykonują operacje na `System.DateTime` wartość wejściowa i zwracać `string`, numeryczną, lub `System.DateTime` wartość wyniku. Te funkcje są w obszarze nazw SqlServer, która jest dostępna, gdy używasz SqlClient. Właściwości przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, które prefiks jest używany przez tego dostawcę dla określonych elementów składowych, takich jak typy i funkcje. W poniższej tabeli przedstawiono funkcje daty i godziny SqlClient.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`DATEADD(` `datepart`, `number`, `date``)`|Zwraca nowy `DateTime` wartość, która jest oparta na dodanie interwału do określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` reprezentujący część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `number`: `Int32`, `Int64`, `Decimal`, Lub `Double` wartość używana do przyrostu `datepart`.<br /><br /> `date:`Wyrażenie, które zwraca `DateTime`, lub `DateTimeOffset`, lub `Time` z dokładnością = [0-7], lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Nowy `DateTime`, lub `DateTimeOffset`, lub `Time` wartość precyzji = [0-7].<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEADD('day', 22, cast('6/9/2006' as DateTime))`|  
|`DATEDIFF(` `datepart`, `startdate`, `enddate``)`|Zwraca liczbę granice daty i godziny między dwoma określonymi datami.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` reprezentujący część daty do obliczania różnicy.<br /><br /> `startdate`: Datę początkową obliczenie jest wyrażenie zwracające `DateTime`, lub `DateTimeOffset`, lub `Time` wartość precyzji = [0-7], lub ciąg znaków w formacie daty.<br /><br /> `enddate:`Datę końcową obliczenie jest wyrażenie zwracające `DateTime`, lub `DateTimeOffset`, lub `Time` wartość precyzji = [0-7], lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEDIFF('day', cast('6/9/2006' as DateTime),`<br /><br /> `cast('6/20/2006' as DateTime))`|  
|`DATENAME(` `datepart`, `date``)`|Zwraca ciąg znaków reprezentujący określonego datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` reprezentujący część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające `DateTime,` lub `DateTimeOffset`, lub `Time` wartość precyzji = [0-7], lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Ciąg znaków reprezentujący określonego datepart określonej daty.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATENAME('year', cast('6/9/2006' as DateTime))`|  
|`DATEPART(` `datepart`, `date``)`|Zwraca liczbę całkowitą reprezentującą określony datepart określonej daty.<br /><br /> **Argumenty**<br /><br /> `datepart`: A `String` reprezentujący część daty, w której ma zostać zwrócona nowa wartość.<br /><br /> `date`: Wyrażenie zwracające `DateTime,` lub `DateTimeOffset,` lub `Time` wartość precyzji = [0-7], lub ciąg znaków w formacie daty.<br /><br /> **Wartość zwracana**<br /><br /> Określony datepart określonej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DATEPART('year', cast('6/9/2006' as DateTime))`|  
|`DAY(` `date` `)`|Rreturns dnia określonej daty jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością do = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Dzień określonej daty w postaci `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.DAY(cast('6/9/2006' as DateTime))`|  
|`GETDATE()`|Generuje bieżącą datę i godzinę w formacie wewnętrznych programu SQL Server dla wartości daty/godziny.<br /><br /> **Wartość zwracana**<br /><br /> Bieżącej systemowej daty i godziny jako `DateTime` z dokładnością do 3.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETDATE()`|  
|`GETUTCDATE()`|Tworzy wartość daty i godziny w formacie UTC (Coordinated Universal Time lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość o dokładności 3 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.GETUTCDATE()`|  
|`MONTH(` `date` `)`|Zwraca miesiąc od określonej daty jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością do = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Miesiąc od określonej daty jako `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.MONTH(cast('6/9/2006' as DateTime))`|  
|`YEAR(` `date` `)`|Zwraca rok z określoną datą jako liczba całkowita.<br /><br /> **Argumenty**<br /><br /> `date`: Wyrażenie typu `DateTime` lub `DateTimeOffset` z dokładnością do = 0-7.<br /><br /> **Wartość zwracana**<br /><br /> Rok określonej daty w postaci `Int32`.<br /><br /> **Przykład**<br /><br /> `SqlServer.YEAR(cast('6/9/2006' as DateTime))`|  
|`SYSDATETIME()`|Zwraca `DateTime` wartość, z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime` wartość, z dokładnością do 7.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIME()`|  
|`SYSUTCDATE()`|Tworzy wartość daty i godziny w formacie UTC (Coordinated Universal Time lub czas uniwersalny Greenwich).<br /><br /> **Wartość zwracana**<br /><br /> `DateTime` Wartość precyzji = 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSUTCDATE()`|  
|`SYSDATETIMEOFFSET()`|Zwraca `DateTimeOffset` z dokładnością do 7.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset` wartość, z dokładnością do 7 w formacie UTC.<br /><br /> **Przykład**<br /><br /> `SqlServer.SYSDATETIMEOFFSET()`|  
  
 Aby uzyskać więcej informacji na temat funkcji daty i godziny, które obsługuje SqlClient zobacz dokumentację dla używanej wersji programu SQL Server określona w manifeście dostawcy SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funkcje daty i godziny (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115908)|[Funkcje daty i godziny (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=115909)|[Funkcje daty i godziny (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=98360)|  
  
## <a name="see-also"></a>Zobacz też  
 [Klient SQL dla funkcji, Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
