---
title: Zabezpieczenia serwera SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4b8eafeedd03097488b1493b5654db360eab94fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-security"></a>Zabezpieczenia serwera SQL
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]oferuje wiele funkcji, które obsługują tworzenie bezpiecznej bazie danych aplikacji.  
  
 Typowe kwestie dotyczące zabezpieczeń, takich jak dane przed kradzieżą lub vandalism, zastosuj niezależnie od wersji [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] używasz. Integralność danych, należy również uwzględnić jako problem z zabezpieczeniami. Jeśli dane nie są chronione, istnieje możliwość, że może stać się Optymalizacja manipulowania danymi ad hoc jest dozwolone, a dane są przypadkowego lub umyślnego modyfikacji z nieprawidłowymi wartościami lub całkowicie usunięte. Ponadto istnieją często wymagań prawnych, które należy przestrzegać, takie jak poprawny magazyn informacji poufnych. Przechowywanie niektóre rodzaje danych osobowych jest proscribed całkowicie, w zależności od prawa, które są stosowane w określonej właściwości.  
  
 Każda wersja programu [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ma funkcje zabezpieczeń, tak jak w przypadku każdej wersji systemu Windows, w nowszych wersjach o rozszerzoną funkcjonalność przez wcześniejsze. Należy zrozumieć, że tylko funkcje zabezpieczeń nie może zagwarantować aplikacji bezpiecznej bazie danych. Każda aplikacja bazy danych jest unikatowa w wymagania, środowiska wykonawczego, model wdrażania, lokalizacji fizycznej i użytkowników. Niektóre aplikacje, które znajdują się lokalnie w zakresie może być konieczne jedynie minimalne zabezpieczenia inne aplikacje lokalne lub aplikacje wdrożone za pośrednictwem Internetu, mogą wymagać środków bezpieczeństwa oraz ciągłego monitorowania i oceny.  
  
 Wymagania zabezpieczeń [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] aplikacji bazy danych należy rozważyć podczas projektowania, a nie jako zbagatelizowane. Oceny zagrożeń wczesnym etapie cyklu programowanie daje możliwość ograniczyć potencjalne szkody wszędzie tam, gdzie zostanie wykryte zagrożenie.  
  
 Nawet w przypadku początkowego projektu aplikacji dźwięku, w miarę rozwoju środowisko systemu mogą pojawić się nowych zagrożeń. Dzięki tworzeniu wielu linii obrony wokół bazy danych, można zminimalizować szkody spowodowane naruszenia zabezpieczeń. Pierwszą linię obrony jest zmniejszenie powierzchni ataku przez nigdy, do udzielania więcej uprawnień niż jest to bezwzględnie konieczne.  
  
 Tematy w tej sekcji Zwięźle opisz funkcji zabezpieczeń w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] istotnych dla deweloperów, linki do powiązanych tematów w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online i innych zasobów, które zapewniają szczegółowe pokrycia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń serwera SQL](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Zawiera opis funkcji architekturze i zabezpieczeniach [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Scenariusze zabezpieczeń aplikacji w programie SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Zawiera tematy dyskutować różne scenariusze zabezpieczeń aplikacji dla ADO.NET i [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] aplikacji.  
  
 [Bezpieczeństwo programu SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia i ochrona (aparat bazy danych)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]— Książki Online security tematów.  
  
 [Zagadnienia dotyczące zabezpieczeń dla programu SQL Server](http://go.microsoft.com/fwlink/?LinkId=98587)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]— Książki Online security tematów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
