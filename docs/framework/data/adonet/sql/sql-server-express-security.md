---
title: Zabezpieczenia programu SQL Server Express
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: 736c450d944efe7e6a69e16e00e1c96f0a868697
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485589"
---
# <a name="sql-server-express-security"></a>Zabezpieczenia programu SQL Server Express
Microsoft SQL Server Express Edition, (SQL Server Express) jest oparty na programie Microsoft SQL Server i obsługuje większość funkcji aparatu bazy danych. Zaprojektowano tak, aby mniej ważne funkcje i połączenie sieciowe są domyślnie wyłączone. Powoduje to zmniejszenie obszaru powierzchni dostępne ataku przez złośliwego użytkownika.  
  
 SQL Server Express jest zazwyczaj instalowany jako nazwane wystąpienie. Domyślna nazwa wystąpienia to `SQLExpress`. Nazwane wystąpienie jest identyfikowane przez nazwę sieciową komputera, a także nazwę wystąpienia, który jest określany podczas instalacji.  
  
## <a name="network-access"></a>Dostęp do sieci  
 Ze względów bezpieczeństwa protokoły sieciowe są domyślnie wyłączona, w programie SQL Server Express. Pozwala to zapobiec atakom, od użytkowników zewnętrznych, które mogą negatywnie wpłynąć na komputerze, który hostuje wystąpienie programu SQL Server Express. Należy jawnie włączyć łączność sieciową i uruchom usługę SQL Server Browser do połączenia z wystąpieniem programu SQL Server Express z innego komputera.  
  
 Gdy połączenie sieciowe jest włączone, wystąpienie programu SQL Server Express ma takie same wymagania dotyczące zabezpieczeń, jak inne wersje programu SQL Server.  
  
## <a name="user-instances"></a>Wystąpienia użytkownika  
 Wystąpienia użytkownika jest osobnego wystąpienia programu SQL Server Express aparat bazy danych jest generowany przez nadrzędne wystąpienie programu SQL Server Express. Podstawowym celem wystąpienia użytkownika jest umożliwienie użytkownikom z systemem Windows przy użyciu konta użytkownika uprawnień, aby administrator systemu (`sysadmin`) uprawnienia w wystąpieniu programu SQL Server Express na komputerze lokalnym. Wystąpienia użytkownika nie są przeznaczone dla użytkowników, którzy są administratorami systemu na swoich komputerach.  
  
 Wystąpienia użytkownika jest generowany na podstawie podstawowego wystąpienia programu SQL Server lub SQL Server Express w imieniu użytkownika. Działa jako proces użytkownika w kontekście zabezpieczeń Windows użytkownika, a nie jako usługa. Logowania do programu SQL Server są niedozwolone; obsługiwane są tylko Windows logowania. Zapobiega to oprogramowanie wykonywania w wystąpieniu użytkownika, możliwość dokonywania zmian całego systemu, które użytkownik nie musiałby uprawnień do wprowadzania. Wystąpienia użytkownika jest także znana jako wystąpienia podrzędne lub klienta, a nazywa się czasem przy użyciu akronim RANU ("Uruchom jako zwykły użytkownik").  
  
 Każde wystąpienie użytkownika jest izolowane od jego wystąpienie nadrzędne i od innych wystąpień użytkownika na tym samym komputerze. Baza danych zainstalowana na wystąpieniach użytkowników są otwierane w trybie jednego użytkownika. wielu użytkowników nie może nawiązać z nimi. Replikacja, zapytania rozproszone i połączenia zdalne są wyłączone dla wystąpienia użytkownika. Po podłączeniu do wystąpienia użytkownika, użytkownicy nie mają żadnych specjalnych uprawnień w wystąpieniu programu SQL Server Express nadrzędnej.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat programu SQL Server Express zobacz następujące zasoby.  
  
|||  
|-|-|  
|[SQL Server — książki Online](https://msdn.microsoft.com/library/bb543165.aspx)|Zawiera dokumentację dla programu SQL Server Express.|  
|[Nawiązywanie połączenia z SQL Server Express](https://msdn.microsoft.com/library/ms165679.aspx) w SQL Server — książki Online|Opisuje sposób używania programu SQL Server Express Edition w sieci.|  
|[Program Microsoft SQL Server 2005 Express Edition — książki Online](https://msdn.microsoft.com/library/ms165706.aspx)|Pełna dokumentacja dotycząca programu SQL Server 2005 Express Edition.|  
|[Wystąpienia użytkownika dla użytkowników niebędących administratorami](https://msdn.microsoft.com/library/ms143684.aspx) w SQL Server — książki Online|Opisuje sposób tworzenia i wdrażania wystąpienia użytkownika.|  
|[Wystąpienia użytkownika programu SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|W tym artykule opisano możliwości wystąpienia użytkownika w aplikacji ADO.NET. Zawiera informacje o tym, jak włączyć wystąpienia użytkownika, nawiązać połączenie z wystąpieniem użytkownika za pomocą <xref:System.Data.SqlClient.SqlConnection>, okres istnienia wystąpienia użytkownika i scenariuszy wystąpienia użytkownika.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Wystąpienia użytkownika programu SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
