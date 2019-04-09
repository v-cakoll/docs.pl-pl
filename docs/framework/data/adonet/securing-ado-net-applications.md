---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149386"
---
# <a name="securing-adonet-applications"></a>Zabezpieczanie aplikacji ADO.NET
Zapisywanie bezpiecznych aplikacji ADO.NET obejmuje więcej niż unikanie typowych pułapek kodowania, takie jak nie sprawdzania poprawności danych wejściowych użytkownika. Aplikacja, która uzyskuje dostęp do danych ma wiele potencjalnych punktów awarii, które osoba atakująca może wykorzystać do pobrania, manipulowanie lub zniszczyć poufnych danych. W związku z tym ważne jest zrozumienie wszystkie aspekty zabezpieczeń z procesu w fazie projektowania aplikacji, jego ostatecznej wdrażania i konserwacji do modelowania zagrożeń.  
  
 .NET Framework zawiera wiele klas użyteczne, usług i narzędzi do zabezpieczania i administrowania nim aplikacji baz danych. Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia środowisko bezpieczny dla kodu do uruchomienia, za pomocą zabezpieczeń dostępu kodu (CAS), aby dodatkowo ograniczyć uprawnienia kodu zarządzanego. Po zabezpieczonych danych access kodowania ogranicza uszkodzeń, które mogą być spowodowane potencjalnym osobom atakującym.  
  
 Pisanie bezpiecznego kodu nie zabezpieczyć się przed luk w zabezpieczeniach samodzielnie sprowokowane podczas pracy z niezarządzanych zasobów, takich jak bazy danych. Serwer baz danych, takich jak SQL Server mają własne systemy zabezpieczeń, które zwiększyć poziom bezpieczeństwa w przypadku zaimplementowania poprawnie. Jednak nawet źródła danych w systemie zabezpieczeń można zaatakowany w przypadku ataków, jeśli nie został prawidłowo skonfigurowany.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd zabezpieczeń](../../../../docs/framework/data/adonet/security-overview.md)  
 Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.  
  
 [Bezpieczny dostęp do danych](../../../../docs/framework/data/adonet/secure-data-access.md)  
 W tym artykule opisano sposób pracy z danymi ze źródła zabezpieczonych danych.  
  
 [Zabezpieczanie aplikacji klienckich](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 W tym artykule opisano zagadnienia dotyczące zabezpieczeń dla aplikacji klienckich.  
  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 W tym artykule opisano, jak urzędy certyfikacji mogą chronić kodu ADO.NET. Omówiono również sposób pracy z częściowej relacji zaufania.  
  
 [Bezpieczeństwo danych i poufności informacji](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 W tym artykule opisano opcje szyfrowania dla aplikacji ADO.NET.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 W tym artykule opisano funkcje zabezpieczeń programu SQL Server z perspektywy dewelopera.  
  
 [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 W tym artykule opisano zabezpieczenia dla aplikacji platformy Entity Framework.  
  
 [Zabezpieczenia](../../../../docs/standard/security/index.md)  
 Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń na platformie .NET.  
  
 [Narzędzia zabezpieczeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 Narzędzia programu .NET framework do zabezpieczania i administrowania zasadami zabezpieczeń.  
  
 [Zasoby służące do tworzenia bezpiecznych aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Zawiera łącza do tematów dotyczące tworzenia bezpiecznych aplikacji.  
  
 [Bibliografia dotyczące zabezpieczeń](/visualstudio/ide/security-bibliography)  
 Zawiera łącza do zasobów zewnętrznych, które są dostępne w tryb online i drukowania.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
