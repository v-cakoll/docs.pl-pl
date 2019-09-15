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
ms.openlocfilehash: ad05d005ece4a52e2df0dbb7e044522db58f1787
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971858"
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
  
 [Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim z zestawu](../reflection-and-codedom/get-type-member-information.md)  
 Opisuje sposób pobierania informacji o zestawie.  
  
 [Kopiowanie zestawów w tle](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 Opisuje, w jaki sposób kopiowanie w tle umożliwia aktualizowanie zestawów, gdy są używane, oraz sposób konfigurowania kopiowania w tle.  
  
 [Instrukcje: Odbieraj powiadomienia o wyjątkach pierwszej szansy](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 Wyjaśnia, jak można odebrać powiadomienie zgłoszone przez wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczęło wyszukiwanie obsługi wyjątków.  
  
 [Rozwiązywanie załadowań zestawów](../../standard/assembly/resolve-loads.md)  
 Zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia do rozwiązywania niepowodzeń ładowania zestawu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AppDomain>  
 Reprezentuje domenę aplikacji. Zapewnia metody tworzenia i kontrolowania domen aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zestawy w środowisku .NET](../../standard/assembly/index.md)  
 Zawiera przegląd funkcji wykonywanych przez zestawy.  
  
 [Programowanie za pomocą zestawów](../../standard/assembly/program.md)  
 Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.  
  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Opisuje sposób tworzenia zestawów dynamicznych.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Przegląd odbicia](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
