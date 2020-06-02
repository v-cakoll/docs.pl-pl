---
title: Przegląd zabezpieczeń serwera SQL
description: Dowiedz się więcej o architekturze zabezpieczeń SQL Server, aby zrozumieć, które funkcje i liczniki znane zagrożenia, i zaprzewidywania przyszłych zagrożeń.
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: c423a408e607c51c048ad08b91122a1fe06e31b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286278"
---
# <a name="overview-of-sql-server-security"></a>Przegląd zabezpieczeń serwera SQL
Strategia obrony szczegółowej z nakładającymi się warstwami zabezpieczeń jest najlepszym sposobem na licznik zagrożeń bezpieczeństwa. SQL Server zapewnia architekturę zabezpieczeń, która została zaprojektowana tak, aby umożliwić administratorom baz danych i deweloperom tworzenie bezpiecznych aplikacji baz danych i zagrożeń. Każda wersja SQL Server została ulepszona w poprzednich wersjach SQL Server z wprowadzeniem nowych funkcji i funkcji. Jednak zabezpieczenia nie są dostarczane w tym polu. Każda aplikacja jest unikatowa w wymaganiach dotyczących zabezpieczeń. Deweloperzy muszą zrozumieć, którą kombinację funkcji i funkcji są najbardziej odpowiednie do określenia znanych zagrożeń, oraz do przewidywania zagrożeń, które mogą wystąpić w przyszłości.  
  
 Wystąpienie SQL Server zawiera hierarchiczną kolekcję jednostek, rozpoczynając od serwera. Każdy serwer zawiera wiele baz danych, a każda baza danych zawiera kolekcję obiektów zabezpieczanych. Każde SQL Server zabezpieczane ma powiązane *uprawnienia* , które mogą zostać przyznane *podmiotowi zabezpieczeń*, który jest osobą, grupą lub procesem udzielonym dostępu do SQL Server. SQL Server Framework zabezpieczeń zarządza dostępem do obiektów zabezpieczanych za pomocą *uwierzytelniania* i *autoryzacji*.  
  
- Uwierzytelnianie to proces logowania do SQL Server, za pomocą którego podmiot zabezpieczeń żąda dostępu przez przesłanie poświadczeń przesyłanych przez serwer. Uwierzytelnianie ustala tożsamość uwierzytelnianego użytkownika lub procesu.  
  
- Autoryzacja to proces określania, które zasoby, do których ma dostęp podmiot zabezpieczeń, i które operacje są dozwolone dla tych zasobów.  
  
 Tematy w tej sekcji dotyczą SQL Server podstawowych zabezpieczeń, które udostępniają linki do kompletnej dokumentacji w odpowiedniej wersji usługi SQL Server Books Online.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uwierzytelnianie w programie SQL Server](authentication-in-sql-server.md)  
 Zawiera opis logowania i uwierzytelniania w SQL Server i zawiera linki do dodatkowych zasobów.  
  
 [Serwer i role bazy danych w programie SQL Server](server-and-database-roles-in-sql-server.md)  
 Opisuje stałe role serwera i bazy danych, niestandardowe role baz danych oraz wbudowane konta i oferuje linki do dodatkowych zasobów.  
  
 [Własność i oddzielenie schematu użytkownika w programie SQL Server](ownership-and-user-schema-separation-in-sql-server.md)  
 Opisuje własność obiektu i separację schematów użytkownika oraz zawiera linki do dodatkowych zasobów.  
  
 [Autoryzacja i uprawnienia w programie SQL Server](authorization-and-permissions-in-sql-server.md)  
 Opisuje udzielanie uprawnień przy użyciu zasady najniższych uprawnień i oferuje linki do dodatkowych zasobów.  
  
 [Szyfrowanie danych w programie SQL Server](data-encryption-in-sql-server.md)  
 Opisuje opcje szyfrowania danych w SQL Server i zawiera linki do dodatkowych zasobów.  
  
 [Zabezpieczenia integracji CLR w programie SQL Server](clr-integration-security-in-sql-server.md)  
 Oferuje linki do zasobów zabezpieczeń integracji środowiska CLR.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [Zabezpieczenia serwera SQL](sql-server-security.md)
- [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
