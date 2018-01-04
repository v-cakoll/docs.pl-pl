---
title: "Wytyczne dotyczące bezpiecznego programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e75f3c74c5966ce5ce22b23f7ba179e903d37aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="secure-coding-guidelines"></a>Wytyczne dotyczące bezpiecznego programowania
Zabezpieczenia oparte na dowód i zabezpieczenia dostępu kodu zapewniają mechanizmy bardzo zaawansowane, jawnej implementacji zabezpieczeń. Większość kodu aplikacji można po prostu użyć infrastruktury wdrożone przez program .NET Framework. W niektórych przypadkach dodatkowe zabezpieczenia aplikacji jest wymagana, utworzony przez rozszerzanie systemu zabezpieczeń lub przy użyciu nowych metod ad hoc.  
  
 Korzystając z uprawnień wymuszane .NET Framework i innych wymuszania w kodzie, powinien ustawienie bariery, aby zapobiec złośliwego kodu uzyskiwania informacje, które nie mają ma ani wykonywać inne akcje niepożądane. Ponadto użytkownik musi równowagę między zabezpieczeń i użyteczność we wszystkich scenariuszach oczekiwanego przy użyciu zaufanego kodu.  
  
 Ten przegląd zawiera opis różnych sposobów, w jaki kod może być przeznaczony do pracy z systemu zabezpieczeń.  
  
## <a name="securing-resource-access"></a>Zabezpieczanie dostępu do zasobów  
 Podczas projektowania i pisania kodu, należy chronić i ograniczenie dostępu kodu do zasobów, szczególnie w przypadku, gdy używany lub wywoływania kodem nieznanego pochodzenia. Należy pamiętać następujące techniki, aby upewnić się, że kod jest bezpieczna:  
  
-   Nie używaj zabezpieczeń dostępu kodu (CAS).  
  
-   Nie należy używać częściowej zaufanego kodu.  
  
-   Nie należy używać funkcji zdalnych .NET.  
  
-   Nie należy używać Distributed Component Object Model (DCOM).  
  
-   Nie należy używać binarne elementy formatujące.  
  
 Zabezpieczenia dostępu kodu ani kod o przezroczystym poziomie zabezpieczeń nie będą obsługiwane jako granice zabezpieczeń z częściowo zaufanego kodu. Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa. Alternatywnych środków bezpieczeństwa są:  
  
-   Wirtualizacja  
  
-   AppContainers  
  
-   Użytkownicy systemu operacyjnego (OS) i uprawnienia  
  
-   Kontenery funkcji Hyper-V  
  
## <a name="security-neutral-code"></a>Kod o neutralnym poziomie bezpieczeństwa  
 Kod o neutralnym poziomie zabezpieczeń nie działa jawne w systemie zabezpieczeń. Działa z uprawnieniami niezależnie od jego odbiera. Chociaż aplikacje, które nie przechwytują wyjątki zabezpieczeń skojarzone z operacjami chroniony (na przykład przy użyciu plików, sieci i tak dalej) może spowodować nieobsługiwany wyjątek, kod o neutralnym poziomie bezpieczeństwa nadal korzysta z zabezpieczeń .NET Framework technologie.  
  
 Biblioteka neutralnym poziomie bezpieczeństwa ma specjalne właściwości, które należy zrozumieć. Załóżmy, że biblioteka zawiera elementy interfejsu API, które pliki lub wywoływanie kodu niezarządzanego; Jeśli w kodzie nie ma odpowiednich uprawnień, nie będzie działał zgodnie z opisem. Jednak nawet, jeśli kod ma uprawnienie, kod źródłowy aplikacji, która wywołuje ona musi mieć uprawnienie do pracy. Jeśli kod wywołujący nie ma odpowiedniego uprawnienia <xref:System.Security.SecurityException> zostanie wyświetlona w wyniku przeszukiwania stosu zabezpieczeń dostępu kodu.  
  
## <a name="application-code-that-is-not-a-reusable-component"></a>Kod aplikacji, która nie jest składnikiem wielokrotnego użytku  
 Jeśli kod jest częścią aplikacji, która nie zostanie wywołana przez inny kod, zabezpieczeń jest prosty i specjalnych kodowania, nie mogą być wymagane. Należy jednak pamiętać, że złośliwy kod może wywołać kodu. Gdy zabezpieczenia dostępu kodu może zatrzymać złośliwego kodu na dostęp do zasobów, taki kod nadal można odczytać wartości pola lub właściwości, które mogą zawierać poufne informacje.  
  
 Ponadto jeśli kod akceptuje dane wejściowe użytkownika z Internetu lub innych niewiarygodnych źródeł, musi być rozważnie złośliwych danych.  
  
## <a name="managed-wrapper-to-native-code-implementation"></a>Zarządzany otok dla implementacji kodu natywnego  
 Zwykle w tym scenariuszu niektóre funkcje przydatne zaimplementowano w kodzie natywnym, który ma być dostępne dla kodu zarządzanego. Zarządzany otok są łatwe do zapisu przy użyciu wywołania albo platformy lub COM interop. Jednak jeśli to zrobisz, wywołań z otoki musi mieć prawa kodu niezarządzanego, aby powiodło się. W obszarze zasady domyślne oznacza to, czy kod pobrany z sieci intranet lub Internet nie będzie działać z otoki.  
  
 Zamiast wskazując wszystkie aplikacje korzystające z tych praw kodu niezarządzanego otoki, lepiej jest udzielić tych uprawnień tylko do kodu otoki. Jeśli podstawową funkcjonalność ujawnia żadnych zasobów i wdrożenia podobnie jest bezpieczne, otoka tylko musi assert jego prawa, co pozwala dowolny kod wywołać przy jego użyciu. W przypadku zasobów kodowania zabezpieczeń powinna być taka sama jak w przypadku kod biblioteki opisany w następnej sekcji. Ponieważ otoka potencjalnie jest ujawniany przez obiekty wywołujące do tych zasobów, dokładne weryfikacji bezpieczeństwa kodu natywnego niezbędne oraz odpowiedzialność otoki.  
  
## <a name="library-code-that-exposes-protected-resources"></a>Kod biblioteki udostępniający chronione zasoby  
 To jest najbardziej wydajne i dlatego potencjalnie niebezpiecznych (Jeśli wykonane nieprawidłowo) podejścia do zabezpieczeń kodowania: biblioteki służy jako interfejs dla innego kodu dostępu do niektórych zasobów, które nie są dostępne tylko jako klasy programu .NET Framework Wymuś uprawnienia do zasobów, których używają. Wszędzie tam, gdzie ujawnia zasobu, kodu musi najpierw zażądać uprawnień dla danego zasobu (to znaczy go należy wykonać sprawdzanie zabezpieczeń) i zwykle assert jego prawa do wykonania bieżącej operacji.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zabezpieczanie danych o stanie](../../../docs/standard/security/securing-state-data.md)|W tym artykule opisano, jak chronić prywatne elementy członkowskie.|  
|[Zabezpieczenia i dane użytkownika](../../../docs/standard/security/security-and-user-input.md)|W tym artykule opisano problemy z zabezpieczeniami dla aplikacji, które akceptuje dane wejściowe użytkownika.|  
|[Zabezpieczenia i sytuacja wyścigu](../../../docs/standard/security/security-and-race-conditions.md)|Opisuje sposób uniknąć wyścigu w kodzie.|  
|[Zabezpieczenia i generowanie kodu na bieżąco](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|W tym artykule opisano problemy z zabezpieczeniami dla aplikacji, które generują kod dynamicznych.|  
|[Zabezpieczenia oparte na rolach](../../../docs/standard/security/role-based-security.md)|W tym artykule opisano zabezpieczenia oparte na rolach .NET Framework szczegółowo i zawiera instrukcje dotyczące używania go w kodzie.|
