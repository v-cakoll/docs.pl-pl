---
title: Używanie domeny aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674896"
---
# <a name="using-application-domains"></a>Używanie domeny aplikacji
Domen aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego. Są one tworzone i uruchamiane wewnątrz procesu. Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, czyli aplikacji, które są odpowiedzialne za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji. Host środowiska uruchomieniowego tworzy proces i domyślnej domeny aplikacji i uruchamia kodu zarządzanego wewnątrz niego. Hosty środowiska uruchomieniowego obejmują usługę ASP.NET, Microsoft Internet Explorer oraz powłoki Windows.  
  
 W przypadku większości aplikacji nie trzeba tworzyć własną domenę aplikacji. host środowiska uruchomieniowego tworzy wszystkie domeny aplikacji konieczne. Można jednak utworzyć i skonfigurować domeny dodatkowych aplikacji, jeśli Twoja aplikacja potrzebuje do izolowania kodu lub do użycia i zwalnianie bibliotek DLL.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 W tym artykule opisano, jak programowo utworzyć domenę aplikacji.  
  
 [Instrukcje: Zwolnienie domeny aplikacji](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 W tym artykule opisano, jak programowo zwolnienie domeny aplikacji.  
  
 [Instrukcje: Konfigurowanie domeny aplikacji](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Wprowadzenie do konfigurowania domeny aplikacji.  
  
 [Pobieranie informacji o instalacji z domeny aplikacji](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 W tym artykule opisano sposób pobierania informacji o instalacji z domeny aplikacji.  
  
 [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 W tym artykule opisano sposób ładowania zestawu do domeny aplikacji.  
  
 [Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 W tym artykule opisano, jak pobrać informacje o zestawie.  
  
 [Kopiowanie zestawów w tle](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Opisuje sposób kopiowania w tle zezwala na aktualizacje do zestawów, gdy są one używane oraz skonfigurować kopiowania w tle.  
  
 [Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 W tym artykule wyjaśniono, jak otrzymasz powiadomienie, że wygenerowany został wyjątek, zanim środowiska uruchomieniowego języka wspólnego została rozpoczęta, wyszukując obsługi wyjątków.  
  
 [Rozwiązywanie załadowań zestawów](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Ten artykuł zawiera wskazówki na temat korzystania z <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby rozwiązać błędy ładowania zestawu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AppDomain>  
 Reprezentuje domenę aplikacji. Zawiera metody służące do tworzenia i kontrolowania domen aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie funkcji, wykonywane przez zestawy.  
  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 W tym artykule opisano sposób tworzenia, zaloguj się i ustawianie atrybutów zestawów.  
  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 W tym artykule opisano sposób tworzenia zestawów dynamicznych.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Omówienie odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.
