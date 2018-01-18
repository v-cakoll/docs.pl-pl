---
title: Znane problemy w SqlClient Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3fb62e266ee6f0ca7957667d7c41fbd90dd34d32
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Znane problemy w SqlClient Entity Framework
W tej sekcji opisano znane problemy związane z dostawcy danych programu .NET Framework dla programu SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Spacje końcowe w funkcje ciągów  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]ignoruje spacje końcowe w wartości ciągu. W związku z tym przekazywanie spacje końcowe w ciągu może spowodować nieprzewidywalne skutki, nawet błędów.  
  
 Jeśli musisz mieć końcowe spacje w ciągu, należy rozważyć dodanie biały znak na końcu, tak aby [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nie trim ciąg. Jeśli spacje końcowe nie są wymagane, powinien zostać przycięty przed są one przekazywane w dół potoku zapytania.  
  
## <a name="right-function"></a>RIGHT — funkcja  
 Jeśli niż`null` wartość jest przekazywana jako pierwszy argument i 0 jest przekazywany jako drugi argument `RIGHT(nvarchar(max)`, 0`)` lub `RIGHT(varchar(max)`, 0`)`, `NULL` wartość zwracana zamiast `empty` ciągu.  
  
## <a name="cross-and-outer-apply-operators"></a>Operatory Zastosuj między i zewnętrzne  
 MIĘDZY i operatora OUTER APPLY operatory zostały wprowadzone w systemie [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. W niektórych przypadkach potoku zapytania może powodować generowanie instrukcji języka Transact-SQL, która zawiera operatory CROSS zastosowania i/lub operatora OUTER APPLY. Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wcześniejszy niż [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], nie obsługują tych operatorów, przetwarzanie takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.  
  
 Poniżej przedstawiono niektóre typowe scenariusze, które mogą prowadzić do obecności CROSS zastosowania i/lub operatora OUTER APPLY operatorów w zapytaniu danych wyjściowych:  
  
-   Podzapytania skorelowane z stronicowania.  
  
-   `AnyElement` Na skorelowane podzapytania lub utworzonej przez nawigacji kolekcji.  
  
-   LINQ zapytań używających grupowanie metod, które akceptują selektorem elementu.  
  
-   Zapytanie, w którym CROSS ZASTOSOWAĆ lub zewnętrznej jest jawnie określone  
  
-   Utworzyć kwerendę, która ma DEREF za pośrednictwem konstrukcję REF.  
  
## <a name="skip-operator"></a>SKIP — Operator  
 Jeśli używasz [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY na niekluczowe może zwracać niepoprawne wyniki. Więcej niż określoną liczbę wierszy mogły zostać pominięte, jeśli kolumna klucza ma zduplikowane dane w nim. Jest to spowodowane jak SKIP jest translacja dla [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Na przykład w następującym zapytaniu więcej niż pięć wierszy mogły zostać pominięte Jeśli `E.NonKeyColumn` zawiera zduplikowane wartości:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Przeznaczenie do wersji serwera SQL poprawne oprogramowania  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Celów [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytania oparte na wersji programu SQL Server, który jest określony w `ProviderManifestToken` atrybut elementu schematu w pliku magazynu modelu (ssdl). Ta wersja mogą różnić się od wersji rzeczywiste są podłączone do serwera SQL. Na przykład, jeśli używasz programu SQL Server 2005 ale Twoje `ProviderManifestToken` atrybut ma ustawioną 2008 wygenerowany [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytania nie może wykonać na serwerze. Na przykład kwerendę, która korzysta z typów czasu Nowa data, które zostały wprowadzone w programie SQL Server 2008 nie zostanie wykonany w starszych wersjach programu SQL Server. Jeśli używasz programu SQL Server 2005, ale Twoje `ProviderManifestToken` atrybut ma ustawioną 2000 wygenerowany [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] zapytanie może być mniejsza zoptymalizowanych pod kątem lub mogą wystąpić wyjątek z informacją, że zapytanie nie jest obsługiwany. Aby uzyskać więcej informacji zobacz sekcję operatory Zastosuj między i zewnętrzne, wcześniej w tym temacie.  
  
 Niektóre zachowania bazy danych zależy od poziomu zgodności, ustaw w bazie danych. Jeśli Twoje `ProviderManifestToken` atrybut ma ustawioną 2005 i SQL Server w wersji jest 2005, ale poziom zgodności bazy danych jest ustawiony na "80" (SQL Server 2000), wygenerowany [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] będzie przeznaczonych dla programu SQL Server 2005, ale może nie zostać wykonana zgodnie z oczekiwaniami ze względu na Ustawienie poziomu zgodności. Na przykład jeśli nazwa kolumny w liście ORDER BY odpowiada nazwie kolumny w selektorze może spowodować utratę porządkowania informacji.  
  
## <a name="nested-queries-in-projection"></a>Zapytania zagnieżdżone w projekcji  
 Zapytania zagnieżdżone w klauzuli projekcji może pobrać przetłumaczyć iloczyn kartezjański zapytania na serwerze. W przypadku niektórych serwerów zaplecza w tym SQL Server może to spowodować tabeli bazy danych TempDB uzyskanie bardzo duże. Może to zmniejszyć wydajność serwera.  
  
 Poniżej przedstawiono przykładowe zapytanie zagnieżdżone w klauzuli projekcji:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Identyfikator GUID wartości tożsamości wygenerowana przez serwer  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsługuje serwer wartości generowanych przez identyfikator GUID typu tożsamości, ale dostawca musi obsługiwać zwracanie wartości generowanych przez serwer tożsamości po został wstawiony wiersz. Począwszy od [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2005, można zwrócić typu GUID generowany przez serwer w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] bazy danych za pośrednictwem [klauzuli OUTPUT](http://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Zobacz też  
 [Element SqlClient programu Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
