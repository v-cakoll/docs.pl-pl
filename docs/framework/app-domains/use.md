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
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2019
ms.locfileid: "61674896"
---
# <a name="using-application-domains"></a>Używanie domeny aplikacji
Domeny aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego. Są one tworzone i uruchamiane w ramach procesu. Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, który jest aplikacją odpowiedzialną za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji. Host środowiska uruchomieniowego tworzy proces i domyślną domenę aplikacji, a następnie uruchamia zarządzany kod. Hosty środowiska uruchomieniowego obejmują ASP.NET, program Microsoft Internet Explorer i powłokę systemu Windows.  
  
 W przypadku większości aplikacji nie trzeba tworzyć własnej domeny aplikacji. Host środowiska uruchomieniowego tworzy wszystkie wymagane domeny aplikacji. Można jednak utworzyć i skonfigurować dodatkowe domeny aplikacji, jeśli aplikacja wymaga odizolowania kodu lub użycia i zwolnienia bibliotek DLL.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Opisuje sposób programowego tworzenia domeny aplikacji.  
  
 [Instrukcje: Zwalnianie domeny aplikacji](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Opisuje sposób programowego zwalniania domeny aplikacji.  
  
 [Instrukcje: Konfigurowanie domeny aplikacji](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Zawiera wprowadzenie do konfigurowania domeny aplikacji.  
  
 [Pobieranie informacji o instalacji z domeny aplikacji](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Opisuje sposób pobierania informacji o instalacji z domeny aplikacji.  
  
 [Instrukcje: Ładowanie zestawów do domeny aplikacji](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Opisuje sposób ładowania zestawu do domeny aplikacji.  
  
 [Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Opisuje sposób pobierania informacji o zestawie.  
  
 [Kopiowanie zestawów w tle](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Opisuje, w jaki sposób kopiowanie w tle umożliwia aktualizowanie zestawów, gdy są używane, oraz sposób konfigurowania kopiowania w tle.  
  
 [Instrukcje: Odbieraj powiadomienia o wyjątkach pierwszej szansy](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Wyjaśnia, jak można odebrać powiadomienie zgłoszone przez wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczęło wyszukiwanie obsługi wyjątków.  
  
 [Rozwiązywanie załadowań zestawów](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia do rozwiązywania niepowodzeń ładowania zestawu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AppDomain>  
 Reprezentuje domenę aplikacji. Zapewnia metody tworzenia i kontrolowania domen aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera przegląd funkcji wykonywanych przez zestawy.  
  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.  
  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Opisuje sposób tworzenia zestawów dynamicznych.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
