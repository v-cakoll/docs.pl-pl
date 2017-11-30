---
title: "SQL Server Express zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2052656a524eafd7b9a137ac7d5006aba53fc075
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-express-security"></a>SQL Server Express zabezpieczeń
Microsoft SQL Server Express Edition, (SQL Server Express) jest oparta na programie Microsoft SQL Server i obsługuje większość funkcji aparatu bazy danych. Zaprojektowano go tak, aby mniej ważne funkcje i łączność sieciową są domyślnie wyłączone. Zmniejsza to powierzchnia dostępne ataku przez złośliwego użytkownika.  
  
 SQL Server Express jest zazwyczaj instalowany jako nazwane wystąpienie. Domyślna nazwa wystąpienia to `SQLExpress`. Nazwane wystąpienie jest identyfikowane przez nazwę sieciową komputera oraz nazwa wystąpienia, który jest określany podczas instalacji.  
  
## <a name="network-access"></a>Dostęp do sieci  
 Ze względów bezpieczeństwa protokołów sieciowych są domyślnie wyłączona w programie SQL Server Express. Pozwala to zapobiec atakom od użytkowników zewnętrznych, które mogłyby naruszyć komputera hostującego wystąpienie programu SQL Server Express. Należy jawnie włączyć łączność sieciową i uruchom usługę SQL Server Browser nawiązać połączenia z wystąpieniem programu SQL Server Express z innego komputera.  
  
 Gdy połączenie sieciowe jest włączone, wystąpienia programu SQL Server Express ma te same wymagania zabezpieczeń, co inne wersje programu SQL Server.  
  
## <a name="user-instances"></a>Wystąpienia użytkownika  
 Wystąpienia użytkownika jest osobnego wystąpienia programu SQL Server Express aparatu bazy danych jest generowany przez nadrzędny wystąpienie programu SQL Server Express. Podstawowym celem wystąpienia użytkownika jest umożliwienie użytkownicy korzystający z systemu Windows przy użyciu konta użytkownika uprawnień, poproś administratora systemu (`sysadmin`) uprawnienia w wystąpieniu programu SQL Server Express na komputerze lokalnym. Wystąpienia użytkownika nie są przeznaczone dla użytkowników, którzy są administratorami systemu na swoich komputerach.  
  
 Wystąpienia użytkownika jest generowany na podstawie podstawowego wystąpienia programu SQL Server lub SQL Server Express w imieniu użytkownika. Jest uruchamiana jako proces użytkownika w kontekście zabezpieczeń systemu Windows użytkownika, nie jako usługa. Logowania do programu SQL Server są niedozwolone; obsługiwane są tylko nazwy logowania systemu Windows. Zapobiega to oprogramowanie wykonywania w wystąpieniu użytkownika z wprowadzania zmian całego systemu, które użytkownik nie będą miały uprawnienia do wprowadzania. Wystąpienia użytkownika jest nazywane również wystąpienia podrzędnej lub klienta, a jest czasami określana za pomocą akronim RANU ("Uruchom jako zwykłego użytkownika").  
  
 Każde wystąpienie użytkownika jest izolowane od jego wystąpienie nadrzędne i z innych wystąpień użytkownika uruchomionych na tym samym komputerze. Baza danych zainstalowana na wystąpieniach użytkowników są otwarte w trybie jednego użytkownika. wielu użytkowników nie można się z nimi łączyć. Funkcje replikacji, zapytania rozproszone i połączenia zdalne są wyłączone dla wystąpienia użytkownika. Po podłączeniu do wystąpienia użytkownika, użytkownicy nie mają żadnych specjalnych uprawnień na wystąpienie programu SQL Server Express nadrzędne.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat programu SQL Server Express zobacz następujące zasoby.  
  
|||  
|-|-|  
|[SQL Server — książki Online](http://msdn.microsoft.com/library/bb543165.aspx)|Zawiera dokumentacja programu SQL Server Express.|  
|[Nawiązywanie połączenia z program SQL Server Express](http://msdn.microsoft.com/library/ms165679.aspx) w dokumentacji SQL Server Books Online|Informacje dotyczące używania programu SQL Server Express Edition w sieci.|  
|[Microsoft SQL Server 2005 Express Edition — książki Online](http://msdn.microsoft.com/library/ms165706.aspx)|Pełną dokumentację SQL Server 2005 Express Edition.|  
|[Wystąpienia użytkownika dla użytkowników niebędących administratorami](http://msdn.microsoft.com/library/ms143684.aspx) w dokumentacji SQL Server Books Online|Opisuje sposób tworzenia i wdrażania wystąpienia użytkownika.|  
|[Wystąpienia programu SQL Server Express użytkownika](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Zawiera opis możliwości wystąpienia użytkownika w aplikacji ADO.NET. Zawiera informacje o tym, jak włączyć wystąpienia użytkownika, nawiązać połączenia z wystąpieniem użytkownika przy użyciu <xref:System.Data.SqlClient.SqlConnection>, okres istnienia wystąpienia użytkownika i scenariuszy wystąpienia użytkownika.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Wystąpienia programu SQL Server Express użytkownika](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
