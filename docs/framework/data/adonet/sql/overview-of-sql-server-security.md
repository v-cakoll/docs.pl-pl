---
title: Omówienie zabezpieczeń programu SQL Server
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: 8000e88de70706c7bb8ec39a05beea4605208b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591719"
---
# <a name="overview-of-sql-server-security"></a>Omówienie zabezpieczeń programu SQL Server
Strategii ochronę w głębi z nakładającymi się warstw zabezpieczeń, to najlepszy sposób na zagrożenia bezpieczeństwa licznika. SQL Server udostępnia architekturę zabezpieczeń, która umożliwia administratorów baz danych i deweloperom tworzenie aplikacji w bezpiecznej bazie danych i licznik zagrożenia. Każda wersja programu SQL Server zostały udoskonalone w poprzednich wersjach programu SQL Server wraz z wprowadzeniem nowych funkcji. Zabezpieczeń nie jest dostarczany w polu. Każda aplikacja jest unikatowa w jej wymagania dotyczące zabezpieczeń. Deweloperzy muszą poznać kombinację funkcji i funkcje są najbardziej odpowiednie do licznika znanymi zagrożeniami i przewidywać zagrożenia, które mogą się pojawić w przyszłości.  
  
 Wystąpienie programu SQL Server zawiera hierarchiczną kolekcję jednostek, rozpoczynając od serwera. Każdy serwer zawiera wiele baz danych, a każda baza danych zawiera kolekcję obiektów zabezpieczanych. Co zabezpieczanych programu SQL Server ma skojarzone *uprawnienia* , może zostać przydzielony *jednostki*, czyli pojedynczej, grupy lub proces udzielony dostęp do programu SQL Server. Struktura zabezpieczeń programu SQL Server zarządza dostępem do zabezpieczanych obiektów za pomocą *uwierzytelniania* i *autoryzacji*.  
  
-   Uwierzytelnianie to proces logowania do serwera SQL, podmiot zabezpieczeń za pomocą którego żąda dostępu, przesyłając poświadczenia, które ocenia serwera. Uwierzytelnianie ustala tożsamość użytkownika lub procesu uwierzytelniane.  
  
-   Autoryzacja to proces określania, że zasoby zabezpieczanego podmiot zabezpieczeń mogą uzyskiwać dostęp do i jakie operacje są dozwolone dla tych zasobów.  
  
 Tematy w tej sekcji opisano podstawy zabezpieczeń programu SQL Server, linków do pełną dokumentację w odpowiedniej wersji programu SQL Server — książki Online.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 W tym artykule opisano identyfikatory logowania i uwierzytelniania w programie SQL Server i zawiera łącza do dodatkowych zasobów.  
  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 W tym artykule opisano stałe role serwera i bazy danych, role bazy danych niestandardowych i wbudowanych kont i zawiera łącza do dodatkowych zasobów.  
  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Zawiera opis obiektu rozdzielenie własność i schemat użytkownika i zawiera łącza do dodatkowych zasobów.  
  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 W tym artykule opisano, udzielanie uprawnień za pomocą zasadę najmniejszych uprawnień i zawiera łącza do dodatkowych zasobów.  
  
 [Szyfrowanie danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 W tym artykule opisano opcje szyfrowania danych w programie SQL Server i zawiera łącza do dodatkowych zasobów.  
  
 [Zabezpieczenia integracji CLR w programie SQL Server](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Zawiera łącza do zasobów zabezpieczenia integracji CLR.  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
