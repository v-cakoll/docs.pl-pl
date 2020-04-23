---
title: Używanie domeny aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: 6ee02a3f27a645f19fd6a327052939586fac4aa9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645429"
---
# <a name="using-application-domains"></a>Używanie domeny aplikacji

Domeny aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego. Są one tworzone i uruchamiane w ramach procesu. Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, który jest aplikacją odpowiedzialną za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji. Host środowiska uruchomieniowego tworzy proces i domyślną domenę aplikacji, a następnie uruchamia zarządzany kod. Hosty środowiska uruchomieniowego obejmują ASP.NET, program Microsoft Internet Explorer i powłokę systemu Windows.  
  
W przypadku większości aplikacji nie trzeba tworzyć własnej domeny aplikacji. Host środowiska uruchomieniowego tworzy wszystkie wymagane domeny aplikacji. Można jednak utworzyć i skonfigurować dodatkowe domeny aplikacji, jeśli aplikacja wymaga odizolowania kodu lub użycia i zwolnienia bibliotek DLL.  
  
## <a name="in-this-section"></a>W tej sekcji  

[Porady: tworzenie domeny aplikacji](how-to-create-an-application-domain.md)  
Opisuje sposób programowego tworzenia domeny aplikacji.  
  
[Porady: zwolnienie domeny aplikacji](how-to-unload-an-application-domain.md)  
Opisuje sposób programowego zwalniania domeny aplikacji.  
  
[Porady: konfigurowanie domeny aplikacji](how-to-configure-an-application-domain.md)  
Zawiera wprowadzenie do konfigurowania domeny aplikacji.  
  
[Pobieranie informacji o instalacji z domeny aplikacji](retrieve-setup-information.md)  
Opisuje sposób pobierania informacji o instalacji z domeny aplikacji.  
  
[Instrukcje: ładowanie zestawów do domeny aplikacji](how-to-load-assemblies-into-an-application-domain.md)  
Opisuje sposób ładowania zestawu do domeny aplikacji.  
  
[Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu](../reflection-and-codedom/get-type-member-information.md)  
Opisuje sposób pobierania informacji o zestawie.  
  
[Kopiowanie zestawów w tle](shadow-copy-assemblies.md)  
Opisuje, w jaki sposób kopiowanie w tle umożliwia aktualizowanie zestawów, gdy są używane, oraz sposób konfigurowania kopiowania w tle.  
  
[Instrukcje: odbieranie powiadomień o wyjątkach pierwszej szansy](how-to-receive-first-chance-exception-notifications.md)  
Wyjaśnia, jak można odebrać powiadomienie zgłoszone przez wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczęło wyszukiwanie obsługi wyjątków.  
  
[Rozwiązywanie załadowań zestawów](../../standard/assembly/resolve-loads.md)  
Zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia do rozwiązywania niepowodzeń ładowania zestawu.  
  
## <a name="reference"></a>Dokumentacja  

<xref:System.AppDomain>  
Reprezentuje domenę aplikacji. Zapewnia metody tworzenia i kontrolowania domen aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
[Zestawy w środowisku .NET](../../standard/assembly/index.md)  
Zawiera przegląd funkcji wykonywanych przez zestawy.  
  
[Programowanie za pomocą zestawów](../../standard/assembly/index.md)  
Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.  
  
[Emitowanie dynamicznych metod i zestawów](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Opisuje sposób tworzenia zestawów dynamicznych.  
  
[Domeny aplikacji](application-domains.md)  
Omówienie koncepcyjne domen aplikacji.  
  
[Przegląd odbicia](../reflection-and-codedom/reflection.md)  
Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
