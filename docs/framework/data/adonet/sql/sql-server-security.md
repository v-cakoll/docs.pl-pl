---
title: Zabezpieczenia serwera SQL
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 4aa4feadb6305f8a0ea6f99c2add780d6fca95cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080773"
---
# <a name="sql-server-security"></a>Zabezpieczenia serwera SQL
SQL Server ma wiele funkcji, które obsługują tworzenie aplikacji w bezpiecznej bazie danych.  
  
 Typowe kwestie dotyczące zabezpieczeń, takich jak kradzieżą danych lub vandalism, zastosuj niezależnie od wersji programu SQL Server, którego używasz. Integralność danych, należy również uwzględnić jako problem z zabezpieczeniami. Jeśli dane nie są chronione, istnieje możliwość, że może stać się bezwartościowe manipulacji danych ad hoc jest dozwolone, jeśli danych jest nieodwracalnie lub celowego modyfikacji z nieprawidłowymi wartościami lub całkowicie usunięte. Ponadto są często wymogami prawnymi, które należy przestrzegać, takie jak poprawny magazyn informacji poufnych. Przechowywanie niektóre rodzaje danych osobowych jest proscribed całkowicie, w zależności od ustawowych, które są stosowane w określonej właściwości.  
  
 Każda wersja programu SQL Server ma różnych funkcji zabezpieczeń, tak jak w każdej wersji systemu Windows, w nowszych wersjach o rozszerzoną funkcjonalność przez wcześniejsze. Jest ważne dowiedzieć się, że tylko funkcje zabezpieczeń nie może zagwarantować aplikacji zabezpieczonej bazy danych. Każda aplikacja bazy danych jest unikatowa w wymagania, środowisko wykonawcze, model wdrażania, lokalizacji fizycznej i populacji użytkowników. Niektóre aplikacje, które są lokalne w zakresie może być konieczne tylko minimalne zabezpieczenia innych aplikacji lokalnych lub aplikacje wdrożone za pośrednictwem Internetu, mogą wymagać środków bezpieczeństwa rygorystyczne i ciągłego monitorowania i oceny.  
  
 Wymagania dotyczące zabezpieczeń aplikacji bazy danych programu SQL Server, należy rozważyć w czasie projektowania, nie factum. Ocena zagrożeń na wczesnym etapie cyklu tworzenia oprogramowania daje możliwość ograniczyć potencjalne szkody, wszędzie tam, gdzie zostanie wykryte luki w zabezpieczeniach.  
  
 Nawet jeśli początkowego projektu aplikacji jest dźwięk, miarę rozwoju systemu mogą pojawić się nowe zagrożenia. Tworząc wiele wierszy obrony wokół bazy danych, można zminimalizować szkody spowodowane naruszenia zabezpieczeń. Jest pierwszą linię obrony w celu ograniczenia obszaru powierzchni ataku przez nigdy do niej udzielanie więcej uprawnień niż jest to absolutnie konieczne.  
  
 Tematy w tej sekcji Zwięźle opisz funkcji zabezpieczeń w programie SQL Server, które są istotne dla deweloperów wraz z łączami do powiązanych tematów w dokumentacji SQL Server — książki Online i innych zasobów, które zapewniają bardziej szczegółowe pokrycie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Opisuje funkcje architekturze i zabezpieczeniach programu SQL Server.  
  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Zawiera tematy, omawiając różne scenariusze zabezpieczeń aplikacji dla aplikacji ADO.NET i programu SQL Server.  
  
 [Bezpieczeństwo programu SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń programu SQL Server Express.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
[Centrum zabezpieczeń dla aparatu bazy danych programu SQL Server i usługi Azure SQL Database](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Opisuje zagadnienia zabezpieczeń dotyczące programu SQL Server i usługi Azure SQL Database.

[Zagadnienia dotyczące zabezpieczeń na potrzeby instalacji serwera SQL](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
W tym artykule opisano problemy dotyczące zabezpieczeń, które należy rozważyć przed zainstalowaniem programu SQL Server.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
