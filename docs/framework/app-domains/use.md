---
title: "Używanie domeny aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eade3728c8a51785214cf3d8de53d8a64a668f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-application-domains"></a>Używanie domeny aplikacji
Domeny aplikacji Podaj jednostkę izolacji dla środowiska CLR. Są one tworzone i uruchamiane wewnątrz procesu. Domeny aplikacji są zwykle tworzone przez host czasu wykonywania, który jest odpowiedzialny za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji aplikacji. Host czasu wykonywania tworzy proces i domyślnej domeny aplikacji i uruchamia kod zarządzany wewnątrz niej. Hosty środowiska uruchomieniowego obejmują ASP.NET, programu Microsoft Internet Explorer i powłoki systemu Windows.  
  
 Dla większości aplikacji nie trzeba tworzyć własne domenę aplikacji. host czasu wykonywania utworzy wszystkie domeny aplikacji to konieczne. Można jednak utworzyć i skonfigurować domeny dodatkowych aplikacji, jeśli aplikacja musi izolowanie kodu lub użycia i zwolnić biblioteki dll.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: tworzenie domeny aplikacji](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 Opisuje sposób programowego tworzenia domeny aplikacji.  
  
 [Instrukcje: zwolnienie domeny aplikacji](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 Opisuje sposób programowego wyładować domeny aplikacji.  
  
 [Instrukcje: konfigurowanie domeny aplikacji](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 Wprowadzenie do konfigurowania domeny aplikacji.  
  
 [Pobieranie informacji o instalacji z domeny aplikacji](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 Opisuje sposób pobrać informacji o instalacji z domeny aplikacji.  
  
 [Instrukcje: ładowanie zestawów do domeny aplikacji](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 Opisuje sposób załadować zestawu do domeny aplikacji.  
  
 [Instrukcje: uzyskiwanie informacji dotyczących typów i elementów członkowskich z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Zawiera opis sposobu pobierania informacji o zestawie.  
  
 [Kopiowanie zestawów w tle](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 W tym artykule opisano, jak kopiowanie w tle umożliwia aktualizacji do zestawów, gdy są one używane i sposobie konfigurowania kopiowanie w tle.  
  
 [Instrukcje: odbieranie powiadomień o wyjątkach pierwszej szansy](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 W tym artykule wyjaśniono, jak możesz otrzymywać powiadomienia, który zgłosił wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczął wyszukiwanie programy obsługi wyjątków.  
  
 [Rozwiązywanie załadowań zestawów](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 Ten artykuł zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby naprawić błędy ładowania zestawu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.AppDomain>  
 Reprezentuje domeny aplikacji. Udostępnia metody tworzenia i kontrolowania domen aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie funkcji wykonywane przez zestawy.  
  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.  
  
 [Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Opisuje sposób tworzenia zestawów dynamicznych.  
  
 [Domeny aplikacji](../../../docs/framework/app-domains/application-domains.md)  
 Omówienie koncepcyjne domen aplikacji.  
  
 [Odbicie — omówienie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.
