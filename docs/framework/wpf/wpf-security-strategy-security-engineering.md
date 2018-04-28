---
title: Strategia zabezpieczeń WPF - projekt zabezpieczeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79ab5b1a86ad94913750cfb3ec4fdc765db40282
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategia zabezpieczeń WPF - projekt zabezpieczeń
Wiarygodne technologie komputerowe to inicjatywa firmy Microsoft dla zapewnienia produkcji bezpiecznego kodu. Jest kluczowym elementem inicjatywy wiarygodne technologie komputerowe [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Engineering rozwiązaniem, używany w połączeniu z standardowe inżynieryjnym do ułatwienia dostarczania bezpiecznego kodu. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Składa się z 10 fazy, które łączą najlepsze rozwiązania z ujęcie w formalne ramy, measurability i dodatkowe struktury, w tym:  
  
-   Analiza projektu zabezpieczeń  
  
-   Narzędzie oparte jakości kontroli  
  
-   Testowanie penetracji  
  
-   Przegląd końcowy zabezpieczeń  
  
-   Zarządzanie zabezpieczeniami produktu wersji POST  
  
## <a name="wpf-specifics"></a>Szczegóły WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Engineering team zarówno stosuje i rozszerza [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], kombinację obejmuje następujące kluczowe aspekty:  
  
 [Modelowanie zagrożeń](#threat_modeling)  
  
 [Analiza zabezpieczeń oraz narzędzia do edycji](#tools)  
  
 [Techniki testowania](#techniques)  
  
 [Kod krytyczny dla zarządzania](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Modelowanie zagrożeń jest podstawowym składnikiem [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]i jest używany do profilu systemu, aby określić potencjalnych luk w zabezpieczeniach. Po zidentyfikowaniu luk w zabezpieczeniach modelowanie zagrożeń gwarantuje również, że zostały spełnione odpowiednie środki zaradcze.  
  
 Na wysokim poziomie modelowanie zagrożeń obejmuje następujące kroki klucza za pomocą magazynu spożywczych, na przykład:  
  
1.  **Identyfikowanie zasobów**. Zasoby magazynem spożywczych mogą obejmować pracowników, sejfie kasy i spisu.  
  
2.  **Wyliczanie punktów wejścia**. Punkty wejścia magazynem spożywczych może obejmować przodu i drzwi Wstecz, windows, dokowania ładowania i klimatyzacja jednostki.  
  
3.  **Badanie ataków na zasoby przy użyciu punktów wejścia**. Jeden możliwości ataku jest przeznaczona magazynem spożywczych *bezpieczne* zasobów za pomocą *klimatyzacja* punktu wejścia; klimatyzacja jednostką może być unscrewed umożliwia bezpiecznie rama przy jego użyciu i z Magazyn.  
  
 Modelowanie zagrożeń jest stosowana w całym [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] i obejmuje następujące elementy:  
  
-   Jak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analizator odczytuje pliki mapuje tekstu do odpowiedniej klasy modelu obiektów i tworzy rzeczywisty kod.  
  
-   Jak uchwyt okna (hWnd) jest tworzony, wysyła komunikaty i jest używany do renderowania zawartości okna.  
  
-   Sposób powiązania danych uzyskuje zasobów i współdziała z systemu.  
  
 Modele te zagrożenia są ważne w przypadku identyfikowania wymagań dotyczących projektowania zabezpieczeń i środki zaradcze zagrożeń podczas procesu projektowania.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Źródło analizy i narzędzia do edycji  
 Oprócz kodu zabezpieczeń ręczne przeglądu elementów [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] zespół używa kilka narzędzi do analizy źródła i zmiany skojarzone zmniejszyć luk w zabezpieczeniach. Szeroką gamę narzędzi źródła są używane i są następujące:  
  
-   **FXCop**: umożliwia znalezienie typowych problemów z zabezpieczeniami w kodzie zarządzanym od reguł dziedziczenia z użyciem zabezpieczeń dostępu kodu, jak bezpiecznie współdziałanie z kodem niezarządzanym. Zobacz [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Prefiks/Prefast**: luki w zabezpieczeniach znajduje i typowych problemów z zabezpieczeniami za pomocą kodu niezarządzanego, takie jak przepełnienia buforu formatu ciągu problemów i sprawdzania błędów.  
  
-   **Interfejsy API zakazane**: Wyszukiwanie źródła kodu, aby zidentyfikować przypadkowego funkcje, które są dobrze znanego powoduje problemy z zabezpieczeniami, takich jak `strcpy`. Po zidentyfikowaniu te funkcje są zastępowane rozwiązań alternatywnych, które są większe bezpieczeństwo.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniki testowania  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] używa różnorodnych narzędzi zabezpieczeń testowania techniki, które obejmują:  
  
-   **Testowanie Whitebox**: testerów wyświetlić kodu źródłowego i późniejszego kompilowania wykorzystać testów  
  
-   **Testowanie Blackbox**: testerów prób znalezienia zabezpieczeń wykorzystuje, sprawdzając interfejsu API i funkcje, a następnie spróbuj na ataki produktu.  
  
-   **Regresję problemy dotyczące zabezpieczeń z innymi produktami**: stosownych sprawdzane są problemy z zabezpieczeniami z pokrewnych produktów. Na przykład odpowiednie wariantów około sześćdziesiąt problemy z bezpieczeństwem dotyczące [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] zostały zidentyfikowane i nastąpiła dla możliwości ich zastosowania do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Na podstawie narzędzia penetracji testowanie za pomocą pliku Fuzzing**: plik fuzzing jest wykorzystanie czytnik plików wejściowych zakresu za pomocą różnych danych wejściowych. Jednym z przykładów w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] gdy ta metoda jest używana jest sprawdzenie niepowodzenia w obrazie dekodowania kodu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Kod krytyczny dla zarządzania  
 Dla [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tworzy piaskownicy zabezpieczeń przy użyciu platformy .NET Framework — Obsługa oznaczenie i śledzenia kod krytyczny dla zabezpieczeń, który zostanie uprawnień (zobacz **krytyczny dla zabezpieczeń metodologii** w [WPF Strategia zabezpieczeń - zabezpieczeń platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Taki kod na kod krytyczny dla zabezpieczeń ze względu na wymagania jakości wysokiego poziomu zabezpieczeń, otrzymuje dodatkowego poziomu inspekcji zabezpieczeń i kontroli zarządzania źródła. Około 5 – 10% z [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] składa się z kod krytyczny dla zabezpieczeń, który jest rozpatrywana przez dedykowany zespół recenzowania. Kod źródłowy i sprawdzanie w trakcie zarządza śledzenia kodu krytycznego dla zabezpieczeń i mapowanie każdej jednostki krytyczne (np. metody, która zawiera kod krytyczny) do jego Zaloguj się w stanie wyłączonym. Zaloguj się w stanie wyłączonym zawiera nazwy jednego lub więcej recenzentów. Każdy codzienne kompilacji [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porównuje kod krytyczny w tym w wcześniejsze kompilacje, aby sprawdzić niezatwierdzone zmiany. Jeżeli inżyniera modyfikuje kodu krytycznego bez zatwierdzenia od zespołu recenzowania, zidentyfikowane i natychmiast stałej. Ten proces umożliwia aplikacji i konserwacji szczególnie wysoki poziom kontroli nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kodu piaskownicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../docs/framework/wpf/security-wpf.md)  
 [Zabezpieczenie częściowej relacji zaufania WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategia zabezpieczeń WPF — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Wiarygodne technologie komputerowe](http://www.microsoft.com/mscorp/twc/default.mspx)  
 [Modelowanie zagrożeń aplikacji](http://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [Wytyczne dotyczące zabezpieczeń: .NET Framework 2.0](http://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
