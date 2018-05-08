---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 5e4363ada4ebdb94801378bc61139f68085b462d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securing-adonet-applications"></a>Zabezpieczanie aplikacji ADO.NET
Pisanie zabezpieczonej aplikacji ADO.NET obejmuje więcej niż unikanie wspólnej kodowania problemów, takich jak nie Walidacja danych wejściowych użytkownika. Aplikacja, która uzyskuje dostęp do danych ma wiele punktów potencjalnych awarii, które osoba atakująca może wykorzystać do pobrania, manipulowania lub zniszczenie poufnych danych. W związku z tym ważne jest zrozumienie wszystkie aspekty zabezpieczeń w procesie modelowania w fazie projektowania aplikacji, w celu jego ostatecznego wdrażaniem i konserwacją bieżących zagrożeń.  
  
 .NET Framework zapewnia wiele klas przydatne, usług i narzędzi do zabezpieczania i administrowania nim aplikacje baz danych. Środowisko uruchomieniowe języka wspólnego (CLR) udostępnia środowisko bezpieczne dla kodu do uruchomienia, z zabezpieczeń dostępu kodu (CAS) dodatkowo ograniczyć uprawnienia kodu zarządzanego. Następujące zabezpieczonych danych access praktyk kodowania ogranicza uszkodzeń, które mogą być spowodowane potencjalnym osobom atakującym.  
  
 Pisanie kodu bezpiecznego nie chronią przed luk w zabezpieczeniach sam, podczas pracy z niezarządzane zasoby, takie jak bazy danych. Serwer baz danych, takich jak SQL Server ma swoje własne systemy zabezpieczeń, które zwiększenia poziomu bezpieczeństwa, implementując poprawnie. Jednak nawet źródła danych przy użyciu systemu skuteczną ochronę można zaatakowany w przypadku ataków, jeśli nie został prawidłowo skonfigurowany.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń](../../../../docs/framework/data/adonet/security-overview.md)  
 Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.  
  
 [Bezpieczny dostęp do danych](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Opisuje sposób pracy z danymi ze źródła zabezpieczonych danych.  
  
 [Zabezpieczanie aplikacje klienckich](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń dla aplikacji klienckich.  
  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 W tym artykule opisano, jak urzędy certyfikacji mogą pomóc chronić ADO.NET kodu. Omówiono także sposób pracy z częściowa relacja zaufania.  
  
 [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Opisuje opcje szyfrowania dla aplikacji ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Opisuje funkcje zabezpieczeń programu SQL Server z punktu widzenia dewelopera.  
  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 W tym artykule opisano zabezpieczenia dla aplikacji programu Entity Framework.  
  
 [Zabezpieczenia](../../../../docs/standard/security/index.md)  
 Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET Framework.  
  
 [Narzędzia zabezpieczeń](http://msdn.microsoft.com/library/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 Narzędzia .NET framework do zabezpieczania i administrowanie zasadami zabezpieczeń.  
  
 [Zasoby służące do tworzenia bezpiecznych aplikacji](http://msdn.microsoft.com/library/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 Zawiera łącza do tematów do tworzenia bezpiecznego aplikacji.  
  
 [Bibliografia dotycząca zabezpieczeń](/visualstudio/ide/security-bibliography)  
 Zawiera linki do zasobów zewnętrznych dostępna online i drukowania.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
