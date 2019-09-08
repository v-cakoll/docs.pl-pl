---
title: Zabezpieczenia serwera SQL
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791622"
---
# <a name="sql-server-security"></a>Zabezpieczenia serwera SQL
SQL Server ma wiele funkcji, które obsługują tworzenie bezpiecznych aplikacji baz danych.  
  
 Typowe zagadnienia dotyczące zabezpieczeń, takie jak kradzież danych lub Vandalism, są stosowane niezależnie od używanej wersji programu SQL Server. Integralność danych powinna również być traktowana jako problem z zabezpieczeniami. Jeśli dane nie są chronione, istnieje możliwość, że może stać się bezwartościowe w przypadku, gdy jest dozwolone manipulowanie danymi ad hoc, a dane są przypadkowo lub złośliwie modyfikowane z nieprawidłowymi wartościami lub usunięte całkowicie. Ponadto występują często wymagania prawne, które muszą być przestrzegane, takie jak prawidłowy Magazyn informacji poufnych. Przechowywanie niektórych rodzajów danych osobowych odbywa się całkowicie w zależności od ustawodawstwa, które mają zastosowanie w danej jurysdykcji.  
  
 Każda wersja SQL Server ma inne funkcje zabezpieczeń, podobnie jak każda wersja systemu Windows, z nowszymi wersjami, które mają ulepszone funkcje przed wcześniejszymi. Ważne jest, aby zrozumieć, że funkcje zabezpieczeń same nie mogą zagwarantować bezpiecznej aplikacji bazy danych. Każda aplikacja bazy danych jest unikatowa w wymaganiach, środowisku wykonawczym, modelu wdrażania, lokalizacji fizycznej i populacji użytkowników. Niektóre aplikacje, które są objęte zakresem lokalnym, mogą wymagać tylko minimalnego poziomu zabezpieczeń, podczas gdy inne aplikacje lokalne lub aplikacje wdrożone za pośrednictwem Internetu mogą wymagały rygorystycznych środków zabezpieczeń oraz ciągłego monitorowania i oceny.  
  
 Wymagania dotyczące zabezpieczeń aplikacji bazy danych SQL Server należy traktować w czasie projektowania, a nie jako zostawiać. Wczesne ocenianie zagrożeń w cyklu programowania pozwala wyeliminować potencjalne uszkodzenia w przypadku wykrycia luki w zabezpieczeniach.  
  
 Nawet jeśli początkowy projekt aplikacji jest dźwiękowy, nowe zagrożenia mogą pojawić się w miarę rozwoju systemu. Dzięki utworzeniu wielu linii obrony w bazie danych można zminimalizować szkody spowodowane naruszeniem zabezpieczeń. Pierwszym wierszem obrony jest zredukowanie obszaru podatności na ataki przez nigdy nie przyznanie więcej uprawnień niż jest to absolutnie konieczne.  
  
 W tematach w tej sekcji przedstawiono krótkie opisy funkcji zabezpieczeń w SQL Server, które są istotne dla deweloperów, z linkami do odpowiednich tematów w temacie SQL Server Books Online i inne zasoby, które zapewniają bardziej szczegółowy zakres.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń serwera SQL](overview-of-sql-server-security.md)  
 Opisuje funkcje architektury i zabezpieczeń SQL Server.  
  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](application-security-scenarios-in-sql-server.md)  
 Zawiera tematy omawiające różne scenariusze zabezpieczeń aplikacji dla aplikacji ADO.NET i SQL Server.  
  
 [Bezpieczeństwo programu SQL Server Express](sql-server-express-security.md)  
 Opisuje zagadnienia dotyczące zabezpieczeń SQL Server Express.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
[Security Center dla aparatu bazy danych SQL Server i Azure SQL Database](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Opisuje zagadnienia dotyczące zabezpieczeń SQL Server i Azure SQL Database.

[Zagadnienia dotyczące zabezpieczeń instalacji SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Opisuje zagadnienia dotyczące zabezpieczeń, które należy wziąć pod uwagę przed instalacją SQL Server.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](../securing-ado-net-applications.md)
- [SQL Server i ADO.NET](index.md)
