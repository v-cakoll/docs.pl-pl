---
title: Zabezpieczenia serwera SQL
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 418dbd3e677619721b841736f5b4c1b423ada94b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364210"
---
# <a name="sql-server-security"></a>Zabezpieczenia serwera SQL
Program SQL Server ma wiele funkcji, które obsługują tworzenie bezpiecznej bazie danych aplikacji.  
  
 Typowe kwestie dotyczące zabezpieczeń, takich jak dane przed kradzieżą lub vandalism, zastosuj niezależnie od wersji programu SQL Server są używane. Integralność danych, należy również uwzględnić jako problem z zabezpieczeniami. Jeśli dane nie są chronione, istnieje możliwość, że może stać się Optymalizacja manipulowania danymi ad hoc jest dozwolone, a dane są przypadkowego lub umyślnego modyfikacji z nieprawidłowymi wartościami lub całkowicie usunięte. Ponadto istnieją często wymagań prawnych, które należy przestrzegać, takie jak poprawny magazyn informacji poufnych. Przechowywanie niektóre rodzaje danych osobowych jest proscribed całkowicie, w zależności od prawa, które są stosowane w określonej właściwości.  
  
 Każda wersja programu SQL Server ma funkcje zabezpieczeń, tak jak w przypadku każdej wersji systemu Windows, w nowszych wersjach o rozszerzoną funkcjonalność przez wcześniejsze. Należy zrozumieć, że tylko funkcje zabezpieczeń nie może zagwarantować aplikacji bezpiecznej bazie danych. Każda aplikacja bazy danych jest unikatowa w wymagania, środowiska wykonawczego, model wdrażania, lokalizacji fizycznej i użytkowników. Niektóre aplikacje, które znajdują się lokalnie w zakresie może być konieczne jedynie minimalne zabezpieczenia inne aplikacje lokalne lub aplikacje wdrożone za pośrednictwem Internetu, mogą wymagać środków bezpieczeństwa oraz ciągłego monitorowania i oceny.  
  
 W czasie projektowania, a nie jako zbagatelizowane należy rozważyć wymagania dotyczące zabezpieczeń aplikacji bazy danych programu SQL Server. Oceny zagrożeń wczesnym etapie cyklu programowanie daje możliwość ograniczyć potencjalne szkody wszędzie tam, gdzie zostanie wykryte zagrożenie.  
  
 Nawet w przypadku początkowego projektu aplikacji dźwięku, w miarę rozwoju środowisko systemu mogą pojawić się nowych zagrożeń. Dzięki tworzeniu wielu linii obrony wokół bazy danych, można zminimalizować szkody spowodowane naruszenia zabezpieczeń. Pierwszą linię obrony jest zmniejszenie powierzchni ataku przez nigdy, do udzielania więcej uprawnień niż jest to bezwzględnie konieczne.  
  
 W tematach w tej sekcji opisano krótko funkcji zabezpieczeń w programie SQL Server, które są istotne dla deweloperów, linki do powiązanych tematów w dokumentacji SQL Server — książki Online i innych zasobów, które zapewniają szczegółowe pokrycie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Zawiera opis funkcji architekturze i zabezpieczeniach programu SQL Server.  
  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Zawiera tematy dyskutować różne scenariusze zabezpieczeń aplikacji dla aplikacji ADO.NET i SQL Server.  
  
 [Bezpieczeństwo programu SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń programu SQL Server Express.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
[Centrum zabezpieczeń dla aparatu bazy danych programu SQL Server i bazy danych Azure SQL](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
W tym artykule opisano zagadnienia dotyczące zabezpieczeń programu SQL Server i bazy danych SQL Azure.

[Zagadnienia dotyczące zabezpieczeń dla instalacji serwera SQL](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
W tym artykule opisano zagadnienia dotyczące zabezpieczeń, które należy uwzględnić przed zainstalowaniem programu SQL Server.

## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
