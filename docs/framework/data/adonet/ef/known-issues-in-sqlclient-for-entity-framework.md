---
title: Znane problemy w SqlClient programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: c1353444415ddd2305a73d14bacf1bb33a931929
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537582"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Znane problemy w SqlClient programu Entity Framework
W tej sekcji opisano znane problemy związane z .NET Framework Data Provider for SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Końcowe spacje w funkcje ciągów  
 Program SQL Server ignoruje spacje końcowe w wartości ciągu. W związku z tym przekazywanie spacje końcowe w ciągu może prowadzić do nieoczekiwanych rezultatów, a nawet awarii.  
  
 Jeśli musisz mieć spacji w ciągu, należy rozważyć dołączenie biały znak na końcu, tak, aby program SQL Server nie przycinania ciągu. Jeśli spacje końcowe nie są wymagane, ich przycięcia przed przekazaniem ich szczegółów w potoku zapytania.  
  
## <a name="right-function"></a>RIGHT — funkcja  
 Jeśli innej niż`null` wartość jest przekazywany jako pierwszy argument, a 0 jest przekazywany jako drugi argument `RIGHT(nvarchar(max)`, 0`)` lub `RIGHT(varchar(max)`, 0`)`, `NULL` zostanie zwrócona wartość zamiast `empty` ciągu.  
  
## <a name="cross-and-outer-apply-operators"></a>Operatory Zastosuj krzyżowe i zewnętrzne  
 KRZYŻOWE i operatora OUTER APPLY operatory zostały wprowadzone w [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. W niektórych przypadkach potoku zapytania może wygenerować instrukcji języka Transact-SQL, która zawiera operatory CROSS APPLY i/lub operatora OUTER APPLY. Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje programu SQL Server starszych niż [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], nie obsługuje tych operatorów, takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, które mogą prowadzić do występowania CROSS APPLY i/lub operatora OUTER APPLY operatory w zapytaniu dane wyjściowe:  
  
-   Skorelowane podzapytanie za pomocą stronicowania.  
  
-   `AnyElement` Na skorelowane podzapytanie lub generowane przez nawigacji kolekcji.  
  
-   LINQ zapytania używające grupowanie metod, które akceptują selektor elementu.  
  
-   Zapytanie, w którym CROSS APPLY lub operatora OUTER APPLY jest jawnie określona  
  
-   Zapytanie, które ma DEREF skonstruować za pośrednictwem konstrukcję REF.  
  
## <a name="skip-operator"></a>SKIP — Operator  
 Jeśli używasz [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY-key kolumn może zwracać nieprawidłowe wyniki. Więcej niż określoną liczbę wierszy może zostać pominięta, jeżeli kolumnę niebędącą kolumną klucza zawiera zduplikowane dane. Jest to spowodowane jak SKIP jest tłumaczony na [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Na przykład, w następującym zapytaniu więcej niż pięć wierszy może zostać pominięta, jeżeli `E.NonKeyColumn` zawiera zduplikowane wartości:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Wersja serwera SQL poprawne  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Cele [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytań w zależności od wersji programu SQL Server, który jest określony w `ProviderManifestToken` atrybutu elementu schematu w pliku modelu (ssdl) magazynu. Ta wersja mogą się różnić od wersję używanego serwera SQL nawiązano połączenie. Na przykład, jeśli używasz programu SQL Server 2005 Twoja `ProviderManifestToken` 2008 wygenerowany ma ustawioną wartość atrybutu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytania nie może być wykonywany na serwerze. Na przykład zapytanie, które korzysta z typów czasu nową datę, które zostały wprowadzone w programie SQL Server 2008 nie będzie wykonywał we wcześniejszych wersjach programu SQL Server. Jeśli używasz programu SQL Server 2005, Twoja `ProviderManifestToken` atrybutu jest równa 2000, wygenerowany [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytanie może być mniejsza zoptymalizowane pod kątem lub mogą wystąpić wyjątek, który mówi, że zapytanie nie jest obsługiwany. Aby uzyskać więcej informacji zobacz sekcję operatory Zastosuj krzyżowe i zewnętrzne w we wcześniejszej części tego tematu.  
  
 Niektóre zachowania bazy danych są zależne od poziomu zgodności ustawiony na bazie danych. Jeśli Twoje `ProviderManifestToken` 2005 ma ustawioną wartość atrybutu używanej wersji programu SQL Server jest 2005, a poziom zgodności bazy danych jest ustawiony na "80" (SQL Server 2000), wygenerowany [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] będą przeznaczone dla programu SQL Server 2005, ale nie może być wykonywany zgodnie z oczekiwaniami, ze względu na Ustawienie poziomu zgodności. Na przykład jeśli nazwę kolumny na liście klauzuli ORDER BY pasuje do nazwy kolumny w selektorze może spowodować utratę informacji szeregowania.  
  
## <a name="nested-queries-in-projection"></a>Zapytania zagnieżdżone w projekcji  
 Zapytania zagnieżdżone w klauzuli projekcji może uzyskać przetłumaczone na zapytania formułuje iloczyn na serwerze. Na niektórych serwerach zaplecza, w tym SQL Server może to spowodować tabeli bazy danych TempDB, aby pobrać dość duży. Może to obniżyć wydajność serwera.  
  
 Oto przykład zagnieżdżonych zapytania w klauzuli projekcji:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Serwer wygenerowany identyfikator GUID wartości tożsamości  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsługuje serwera wartości generowanych przez identyfikator GUID typu tożsamości, ale dostawca musi obsługiwać, zwracając wartość, tożsamością wygenerowaną przez serwer po wstawieniu wiersza. Począwszy od programu SQL Server 2005, może zwrócić typ identyfikator GUID generowany przez serwer w bazie danych programu SQL Server za pośrednictwem [klauzuli OUTPUT](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Zobacz też  
 [Element SqlClient programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
