---
title: Dublowania w programie SQL Server bazy danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a955f62aa1e7b2f025a621840753e2213fcefe7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="database-mirroring-in-sql-server"></a>Dublowania w programie SQL Server bazy danych
Funkcja dublowania baz danych w programie SQL Server pozwala na zachowanie kopiowania lub dublowania bazy danych programu SQL Server na serwerze wstrzymania. Dublowanie gwarantuje, że dwa osobne kopie danych istnieje przez cały czas, wysokiej dostępności i ukończyć nadmiarowość danych. Dostawcy danych programu .NET dla programu SQL Server obsługuje niejawne dublowania bazy danych, dzięki czemu deweloper nie trzeba podejmować żadnych działań lub pisania kodu, gdy została skonfigurowana dla bazy danych programu SQL Server. Ponadto <xref:System.Data.SqlClient.SqlConnection> obiektu obsługuje tryb jawne połączenie, który umożliwia podanie nazwy serwera partnerskiego trybu failover w <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Ma miejsce następująca sekwencja uproszczony zdarzeń dla <xref:System.Data.SqlClient.SqlConnection> obiektu, którego celem jest skonfigurowany dla funkcji dublowania bazy danych:  
  
1.  Aplikacja kliencka połączy się z główną bazą danych, a serwer odsyła nazwę serwera partnerskiego, które następnie są buforowane na kliencie.  
  
2.  Jeśli serwer zawierający główna baza danych nie powiedzie się lub połączenie zostanie przerwane, stan połączenia i transakcji zostaną utracone. Aplikacja kliencka próbuje ponownie ustanowić połączenia z główną bazą danych i nie powiedzie się.  
  
3.  Przezroczysty następnie aplikacja kliencka próbuje nawiązać połączenie z duplikatu bazy danych na serwer partnerski. Jeśli próba powiedzie się, połączenie jest przekierowywany do duplikatu bazy danych, która staje się nowego podmiotu zabezpieczeń bazy danych.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Określanie serwer partnerski trybu Failover w parametrach połączenia  
 Jeśli podasz nazwę serwera partnerskiego trybu failover w parametrach połączenia klienta niewidocznie prób połączenia z serwer partnerski trybu failover, jeśli główna baza danych jest niedostępna, jeśli aplikacja kliencka pierwszy raz łączy.  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 Jeśli pominięto nazwę serwera partnerskiego trybu failover i główna baza danych jest niedostępny podczas aplikacja kliencka pierwszy raz łączy następnie <xref:System.Data.SqlClient.SqlException> jest wywoływane.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> jest poprawnie otwarty, jest zwracany przez serwer Nazwa partnera pracy awaryjnej i zastępuje wszelkie wartości dostarczone w parametrach połączenia.  
  
> [!NOTE]
>  Nazwa początkowego wykazu lub bazy danych należy jawnie określić w parametrach połączenia dla scenariuszy dublowania bazy danych. Jeśli klient otrzymuje informacje trybu failover na połączenie, które nie mają jawnie określona początkowego wykazu lub bazy danych, informacje trybu failover nie są buforowane, a aplikacja nie będzie podejmował prób w przypadku awarii podmiotu zabezpieczeń serwera w trybie Failover. Jeśli parametry połączenia ma wartość serwer partnerski trybu failover, ale żadnej wartości dla początkowego wykazu lub bazy danych, `InvalidArgumentException` jest wywoływane.  
  
## <a name="retrieving-the-current-server-name"></a>Pobieranie bieżącej nazwy serwera  
 W przypadku trybu failover, możesz pobrać nazwę serwera, do którego bieżące połączenie jest rzeczywiście połączony przy użyciu <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu. Poniższy fragment kodu pobiera nazwę aktywnego serwera, przy założeniu, że zmienna połączenia odwołuje się do otwartego <xref:System.Data.SqlClient.SqlConnection>.  
  
 Po wystąpieniu zdarzenia pracy awaryjnej i połączenia się przełączone do serwer duplikatu **źródła danych** właściwości jest aktualizowana w celu odzwierciedlenia nazwy duplikatu.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Zachowanie funkcji dublowania SqlClient  
 Klient zawsze próbuje nawiązać połączenia z bieżącym serwerze dublowanym. W przypadku niepowodzenia podejmuje serwer partnerski trybu failover. Jeśli już duplikatu bazy danych została przełączona na głównej roli na serwerze partnerskim, połączenie powiedzie się i nowe mapowanie dublowany podmiot zabezpieczeń są wysyłane do klienta i w pamięci podręcznej przez czas ich istnienia wywołujący <xref:System.AppDomain>. Nie są przechowywane w magazynie trwałe i nie jest dostępna dla kolejnych połączeń w innej **elementu AppDomain** lub inny proces. Jednak nie jest dostępny do kolejnych połączeń, w tym samym **elementu AppDomain**. Uwaga to inny **elementu AppDomain** lub proces uruchomiony na tym samym lub innym komputerze zawsze ma puli połączeń, a te połączenia nie są resetowane. W takim przypadku głównej bazy danych ulegnie awarii, każdy proces lub **elementu AppDomain** raz kończy się niepowodzeniem i puli są automatycznie usuwane.  
  
> [!NOTE]
>  Funkcja dublowania obsługi na serwerze jest skonfigurowana na podstawie na bazę danych. Jeśli operacje manipulacji danych są wykonywane w innych bazach danych nie są uwzględniane w zestawie principal/duplikatu, przy użyciu nazwy wieloczęściowej lub zmieniając bieżącej bazy danych zmiany tych baz danych nie są propagowane w przypadku awarii. Nie zostanie wygenerowany błąd modyfikacji danych w bazie danych, która nie jest dublowana. Deweloper musi być możliwy wpływ takich operacji.  
  
## <a name="database-mirroring-resources"></a>Zasoby dublowania bazy danych  
 Dokumentacja koncepcyjna i informacji na temat konfigurowania wdrażania i administrowania dublowania, zobacz następujące zasoby w programie SQL Server — książki Online.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Funkcja dublowania baz danych](http://msdn.microsoft.com/library/bb934127.aspx) w dokumentacji SQL Server Books Online|Opisuje sposób instalowania i konfigurowania funkcji dublowania w programie SQL Server.|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
