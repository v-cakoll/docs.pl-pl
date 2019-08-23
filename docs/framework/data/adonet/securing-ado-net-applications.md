---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: d4c9c21f4d1f4a08ca6d676ee7b4c9e80709ba19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963122"
---
# <a name="securing-adonet-applications"></a>Zabezpieczanie aplikacji ADO.NET
Pisanie zabezpieczonej aplikacji ADO.NET obejmuje więcej niż uniknięcie wspólnego kodowania pułapek, takie jak nieweryfikowanie danych wejściowych użytkownika. Aplikacja, która uzyskuje dostęp do danych, ma wiele potencjalnych punktów awarii, których atakujący może wykorzystać do pobierania, manipulowania lub niszczenia poufnych danych. W związku z tym ważne jest, aby zrozumieć wszystkie aspekty zabezpieczeń, od procesu modelowania zagrożeń podczas fazy projektowania aplikacji, do ostatecznego wdrożenia i trwającej konserwacji.  
  
 .NET Framework zawiera wiele przydatnych klas, usług i narzędzi do zabezpieczania i administrowania aplikacjami baz danych. Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia bezpieczne dla typów środowisko kodu do uruchamiania w programie, a zabezpieczenia dostępu kodu (CAS) ograniczają dalsze uprawnienia do kodu zarządzanego. Zgodnie z bezpiecznymi praktykami kodowania dostępu do danych ograniczają szkody, które mogą zostać spowodowane przez potencjalną osobę atakującą.  
  
 Pisanie bezpiecznego kodu nie chroni przed atakami z użyciem niezarządzanych zasobów, takich jak bazy danych. Większość baz danych serwera, takich jak SQL Server, ma własne systemy zabezpieczeń, które zwiększają bezpieczeństwo po poprawnym wdrożeniu. Jednak nawet źródło danych z niezawodnym systemem zabezpieczeń może być ofiarą ataku, jeśli nie jest odpowiednio skonfigurowany.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń](../../../../docs/framework/data/adonet/security-overview.md)  
 Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.  
  
 [Bezpieczny dostęp do danych](../../../../docs/framework/data/adonet/secure-data-access.md)  
 Opisuje sposób pracy z danymi z zabezpieczonego źródła danych.  
  
 [Zabezpieczanie aplikacje klienckich](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 Opisuje zagadnienia dotyczące zabezpieczeń aplikacji klienckich.  
  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 Opisuje, jak urzędy certyfikacji mogą chronić kod ADO.NET. Omówiono również sposób pracy z częściowym zaufaniem.  
  
 [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 Opisuje opcje szyfrowania dla aplikacji ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 Opisuje funkcje zabezpieczeń SQL Server z perspektywy dewelopera.  
  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 Opisuje zabezpieczenia Entity Framework aplikacji.  
  
 [Zabezpieczenia](../../../standard/security/index.md)  
 Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET.  
  
 [Narzędzia zabezpieczeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 .NET Framework narzędzia do zabezpieczania zasad zabezpieczeń i administrowania nimi.  
  
 [Zasoby do tworzenia bezpiecznych aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Zawiera łącza do tematów dotyczących tworzenia bezpiecznych aplikacji.  
  
 [Bibliografia dotycząca zabezpieczeń](/visualstudio/ide/security-bibliography)  
 Oferuje linki do zasobów zewnętrznych dostępnych w trybie online i drukowania.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
