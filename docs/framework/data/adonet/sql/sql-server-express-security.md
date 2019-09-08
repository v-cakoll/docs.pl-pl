---
title: Bezpieczeństwo programu SQL Server Express
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: 55f1d141e50ed7afd851d7330cfaf2e3b6380f18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791689"
---
# <a name="sql-server-express-security"></a>Bezpieczeństwo programu SQL Server Express
Microsoft SQL Server Express Edition (SQL Server Express) jest oparta na Microsoft SQL Server i obsługuje większość funkcji aparatu bazy danych. Jest ona zaprojektowana tak, że nieistotne funkcje i łączność sieciowa są domyślnie wyłączone. Pozwala to zmniejszyć obszar powierzchni dostępny dla ataku złośliwego użytkownika.  
  
 SQL Server Express jest zazwyczaj instalowany jako nazwane wystąpienie. Domyślna nazwa wystąpienia to `SQLExpress`. Nazwane wystąpienie jest identyfikowane przez nazwę sieciową komputera oraz nazwę wystąpienia określoną podczas instalacji.  
  
## <a name="network-access"></a>Dostęp do sieci  
 Ze względów bezpieczeństwa protokoły sieciowe są domyślnie wyłączone w SQL Server Express. Zapobiega to atakom spoza użytkowników, którzy mogą naruszyć bezpieczeństwo komputera, który hostuje wystąpienie SQL Server Express. Należy jawnie włączyć łączność sieciową i uruchomić usługę SQL Server Browser, aby połączyć się z wystąpieniem SQL Server Express z innego komputera.  
  
 Po włączeniu łączności sieciowej wystąpienie SQL Server Express ma takie same wymagania dotyczące zabezpieczeń co inne wersje SQL Server.  
  
## <a name="user-instances"></a>Wystąpienia użytkownika  
 Wystąpienie użytkownika jest osobnym wystąpieniem aparatu bazy danych SQL Server Express, który jest generowany przez wystąpienie nadrzędne SQL Server Express. Głównym celem wystąpienia użytkownika jest umożliwienie użytkownikom z systemem Windows w ramach konta użytkownika z najniższymi uprawnieniami, aby mieć uprawnienia administratora`sysadmin`systemu w wystąpieniu SQL Server Express na swoim komputerze lokalnym. Wystąpienia użytkownika nie są przeznaczone dla użytkowników, którzy są administratorami systemu na swoich komputerach.  
  
 Wystąpienie użytkownika jest generowane na podstawie wystąpienia podstawowego SQL Server lub SQL Server Express w imieniu użytkownika. Jest on uruchamiany jako proces użytkownika w kontekście zabezpieczeń systemu Windows użytkownika, a nie jako usługa. Identyfikatory logowania SQL Server są niedozwolone; Obsługiwane są tylko nazwy logowania systemu Windows. Zapobiega to wykonywaniu przez oprogramowanie w wystąpieniu użytkownika zmian w całym systemie, których użytkownik nie ma uprawnień do wykonania. Wystąpienie użytkownika jest również nazywane wystąpieniem podrzędnym lub klientem i jest czasami określane przy użyciu akronima RANU ("Uruchom jako normalny użytkownik").  
  
 Każde wystąpienie użytkownika jest odizolowane od jego wystąpienia nadrzędnego i innych wystąpień użytkownika uruchomionych na tym samym komputerze. Bazy danych zainstalowane w wystąpieniach użytkownika są otwierane tylko w trybie jednego użytkownika. wielu użytkowników nie może połączyć się z nimi. Replikacja, zapytania rozproszone i połączenia zdalne są wyłączone dla wystąpień użytkownika. Po nawiązaniu połączenia z wystąpieniem użytkownika użytkownicy nie mają żadnych specjalnych uprawnień do wystąpienia nadrzędnego SQL Server Express.  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
 Aby uzyskać więcej informacji na temat SQL Server Express, zobacz następujące zasoby.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition Books Online](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Kompletna dokumentacja programu SQL Server 2005 Express Edition.|  
|[Wystąpienia użytkownika dla użytkowników niebędących administratorami](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) w SQL Server książki online|Opisuje sposób tworzenia i wdrażania wystąpień użytkownika.|  
|[Wystąpienia użytkownika programu SQL Server Express](sql-server-express-user-instances.md)|Opisuje możliwości wystąpienia użytkownika w aplikacji ADO.NET. Zawiera informacje na temat sposobu włączania wystąpienia użytkownika i łączenia się z wystąpieniem użytkownika przy <xref:System.Data.SqlClient.SqlConnection>użyciu scenariuszy wystąpienia użytkownika, okresu istnienia wystąpień i wystąpień użytkownika.|  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia serwera SQL](sql-server-security.md)
- [Wystąpienia użytkownika programu SQL Server Express](sql-server-express-user-instances.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
