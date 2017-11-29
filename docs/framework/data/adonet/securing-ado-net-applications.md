---
title: Zabezpieczanie aplikacji ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 143447020f41368a3553a0c8cda78e80806b75ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
 [Zabezpieczanie aplikacji klienckich](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń dla aplikacji klienckich.  
  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 W tym artykule opisano, jak urzędy certyfikacji mogą pomóc chronić ADO.NET kodu. Omówiono także sposób pracy z częściowa relacja zaufania.  
  
 [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Opisuje opcje szyfrowania dla aplikacji ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Opisuje funkcje zabezpieczeń programu SQL Server z punktu widzenia dewelopera.  
  
 [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 W tym artykule opisano zabezpieczenia dla aplikacji programu Entity Framework.  
  
 [Zabezpieczeń](../../../../docs/standard/security/index.md)  
 Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET Framework.  
  
 [Narzędzia zabezpieczeń](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 Narzędzia .NET framework do zabezpieczania i administrowanie zasadami zabezpieczeń.  
  
 [Zasoby służące do tworzenia bezpiecznych aplikacji](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 Zawiera łącza do tematów do tworzenia bezpiecznego aplikacji.  
  
 [Bibliografia dotyczące zabezpieczeń](/visualstudio/ide/security-bibliography)  
 Zawiera linki do zasobów zewnętrznych dostępna online i drukowania.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
