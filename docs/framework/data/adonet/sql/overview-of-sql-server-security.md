---
title: Przegląd zabezpieczeń serwera SQL
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: 84b6724417d03a30c131700e197744839d3a020d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362237"
---
# <a name="overview-of-sql-server-security"></a>Przegląd zabezpieczeń serwera SQL
Strategii zabezpieczeń obrony z nakładającymi się warstwy zabezpieczeń, to najlepszy sposób na zagrożenia bezpieczeństwa licznika. Program SQL Server stanowi architekturę zabezpieczeń, która umożliwia administratorów bazy danych i deweloperom tworzenie aplikacji w bezpiecznej bazie danych i licznik zagrożeń. Każda wersja programu SQL Server została ulepszona w poprzednich wersjach programu SQL Server wraz z wprowadzeniem nowych funkcji i funkcjonalności. Zabezpieczeń nie jest dostarczany w polu. Każda aplikacja jest unikatowa w jej wymagania dotyczące zabezpieczeń. Deweloperzy muszą zrozumieć, która kombinacja funkcji i funkcji są najbardziej odpowiednie dla licznika znane zagrożenia i przewidywanie zagrożenia, które mogą pojawić się w przyszłości.  
  
 Wystąpienie programu SQL Server zawiera hierarchiczną kolekcję jednostek, począwszy od serwera. Każdy serwer zawiera wiele baz danych, a każda baza danych zawiera kolekcję obiektów możliwych do zabezpieczenia. Każdy serwer SQL zabezpieczanego jest skojarzony *uprawnienia* może zostać przydzielony do *główna*, która jest pojedyncza, grupa lub proces udzielony dostęp do programu SQL Server. Mechanizm zabezpieczeń programu SQL Server zarządza dostępem do zabezpieczanych obiektów za pomocą *uwierzytelniania* i *autoryzacji*.  
  
-   Uwierzytelnianie to proces logowania do programu SQL Server za pomocą którego podmiot zabezpieczeń żąda dostępu poprzez przesłanie poświadczenia, które ocenia serwera. Uwierzytelniania ustalana jest tożsamość użytkownika lub inny proces jest uwierzytelniane.  
  
-   Autoryzacja jest proces określania zabezpieczanego podmiot zabezpieczeń mogą uzyskiwać dostęp do zasobów i jakie operacje są dozwolone dla tych zasobów.  
  
 Tematy w tej sekcji opisano podstawy zabezpieczeń programu SQL Server, tworzenia łączy do pełną dokumentację w odpowiednich wersji programu SQL Server — książki Online.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uwierzytelnianie w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 W tym artykule opisano logowania i uwierzytelniania programu SQL Server i zawiera łącza do dodatkowych zasobów.  
  
 [Serwer i role bazy danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Przedstawiono stałe role serwera i bazy danych, role bazy danych niestandardowych i wbudowanych kont oraz zawiera łącza do dodatkowych zasobów.  
  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Zawiera opis separacji własności i użytkowników schematu obiektu i zawiera łącza do dodatkowych zasobów.  
  
 [Autoryzacja i uprawnienia w programie SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Zawiera opis przyznawania uprawnień przy użyciu zasadą najniższych uprawnień i łącza do dodatkowych zasobów.  
  
 [Szyfrowanie danych w programie SQL Server](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Zawiera opis opcji szyfrowania danych w programie SQL Server i zawiera łącza do dodatkowych zasobów.  
  
 [Zabezpieczenia integracji CLR w programie SQL Server](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Zawiera linki do zasobów zabezpieczeń integracji środowiska CLR.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpieczenia serwera SQL](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
