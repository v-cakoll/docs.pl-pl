---
title: Strategia zabezpieczeń WPF - projekt zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: d5bcd5b06f6d922b29c2a494f1f63da1217e2b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817873"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategia zabezpieczeń WPF - projekt zabezpieczeń
Wiarygodne technologie obliczeniowe to inicjatywa firmy Microsoft do zapewnienia produkcji bezpiecznego kodu. Kluczowym elementem wiarygodnej inicjatywy komputerowej jest [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Jest to technika inżynieryjna, która jest używana w połączeniu ze standardowymi procesami konstrukcyjnymi w celu ułatwienia dostarczania bezpiecznego kodu. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Składa się z dziesięciu faz, które łączą najlepsze rozwiązania z formalization, mierzalną i dodatkową strukturą, w tym:  
  
- Analiza projektu zabezpieczeń  
  
- Sprawdzanie jakości oparte na narzędziu  
  
- Testowanie penetracji  
  
- Ostateczne przeglądy zabezpieczeń  
  
- Zarządzanie zabezpieczeniami produktu po wydaniu  
  
## <a name="wpf-specifics"></a>Specyficzne dla WPF  
 Zespół inżynieryjny stosuje i [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]rozszerza kombinację, która zawiera następujące kluczowe aspekty: [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]  
  
 [Modelowanie zagrożeń](#threat_modeling)  
  
 [Narzędzia do analizy i edycji zabezpieczeń](#tools)  
  
 [Techniki testowania](#techniques)  
  
 [Krytyczne Zarządzanie kodem](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Modelowanie zagrożeń jest podstawowym składnikiem [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]programu i służy do profilowania systemu w celu określenia potencjalnych luk w zabezpieczeniach. Po zidentyfikowaniu luk w zabezpieczeniach modelowanie zagrożeń gwarantuje również, że są odpowiednie środki zaradcze.  
  
 Na wysokim poziomie modelowanie zagrożeń obejmuje następujące podstawowe kroki, używając sklepu spożywczego jako przykładu:  
  
1. **Identyfikowanie zasobów**. Zasoby sklepu spożywczego mogą obejmować pracowników, bezpieczne rejestry kasowe i spis.  
  
2. **Wyliczanie punktów wejścia**. Punkty wejścia w sklepie spożywczym mogą obejmować drzwi z przodu i tyłu, system Windows, zadokowany ładunek i jednostki klimatyzacyjne.  
  
3. **Badanie ataków na zasoby przy użyciu punktów wejścia**. Jeden z możliwych ataków może wskazywać na *bezpieczny* zasób sklepu spożywczego za pośrednictwem punktu wejścia *warunkowego stanu powietrza* . Jednostka stanu powietrza może być odkręcana, aby umożliwić bezpieczne ściąganie jej do i z magazynu.  
  
 Modelowanie zagrożeń jest stosowane [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] w całym systemie i obejmuje następujące elementy:  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] Jak Analizator odczytuje pliki, mapuje tekst do odpowiednich klas modelu obiektów i tworzy rzeczywisty kod.  
  
- Sposób tworzenia uchwytu okna (hWnd), wysyłania komunikatów i służy do renderowania zawartości okna.  
  
- Sposób powiązania danych uzyskuje zasoby i współdziała z systemem.  
  
 Te modele zagrożeń są ważne w przypadku identyfikowania wymagań związanych z projektowaniem zabezpieczeń i łagodzenia zagrożeń podczas procesu tworzenia oprogramowania.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Narzędzia do analizy źródłowej i edycji  
 Oprócz ręcznych elementów [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]kontroli kodu zabezpieczeń [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , zespół używa kilku narzędzi do analizy źródłowej i skojarzonych modyfikacji w celu zmniejszenia luk w zabezpieczeniach. Używane są szeroką gamę narzędzi źródłowych, które obejmują następujące elementy:  
  
- **FXCop**: Znajduje typowe problemy z zabezpieczeniami w kodzie zarządzanym od reguł dziedziczenia do użycia w celu zabezpieczenia dostępu kodu w celu bezpiecznego współdziałania z kodem niezarządzanym. Zobacz [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefiks/szybka szybkość**: Znajdowanie luk w zabezpieczeniach i typowych problemów z zabezpieczeniami w niezarządzanym kodzie, takich jak przepełnienia buforu, problemy z ciągami formatowania i sprawdzanie błędów.  
  
- **Zablokowane interfejsy API**: Przeszukuje kod źródłowy, aby identyfikować przypadkowe użycie funkcji, które są dobrze znane dla spowodowania problemów z `strcpy`zabezpieczeniami, takich jak. Po zidentyfikowaniu te funkcje są zastępowane alternatywami, które są bardziej bezpieczne.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniki testowania  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Program korzysta z różnych technik testowania zabezpieczeń, które obejmują:  
  
- **Testowanie Whitebox**: Testerzy wyświetlają kod źródłowy, a następnie kompilują testy wykorzystujące luki w zabezpieczeniach.
  
- **Testowanie Blackbox**: Testerzy próbują znaleźć luki w zabezpieczeniach, sprawdzając interfejs API i funkcje, a następnie próbę ataku na produkt.  
  
- **Rozwiązywanie problemów z zabezpieczeniami z innych produktów**: W razie potrzeby są testowane problemy z zabezpieczeniami pokrewnych produktów. Na przykład odpowiednie warianty około 60 problemów z zabezpieczeniami programu Internet Explorer zostały zidentyfikowane i podjęto próbę ich zastosowania [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]do programu.  
  
- **Testowanie penetracji plików w oparciu o narzędzia**: Rozmyty plik to wykorzystanie zakresu wejściowego czytnika plików za pomocą różnych danych wejściowych. Przykładem, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] w którym ta technika jest używana, jest sprawdzenie niepowodzenia w kodzie dekodowania obrazu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Krytyczne Zarządzanie kodem  
 W programie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] program tworzy piaskownicę zabezpieczeń przy użyciu .NET Framework obsługi oznaczania i śledzenia kodu o krytycznym poziomie zabezpieczeń, który podnosi uprawnienia (patrz metodologia krytyczna dla zabezpieczeń w temacie strategia zabezpieczeń WPF-Platforma [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] [ Bezpieczeństwo](wpf-security-strategy-platform-security.md)). Zgodnie z wymaganiami dotyczącymi wysokiej jakości zabezpieczeń w kodzie krytycznym zabezpieczeń, taki kod otrzymuje dodatkowy poziom kontroli zarządzania źródła i inspekcji zabezpieczeń. Około 5% do 10% [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] składa się z kodu krytycznego pod względem zabezpieczeń, który jest przeglądany przez dedykowanego zespołu ds. recenzji. Kod źródłowy i proces ewidencjonowania są zarządzane przez śledzenie kodu krytycznego zabezpieczeń i mapowanie każdej krytycznej jednostki (tj. metody zawierającej kod krytyczny) do jej stanu rejestracji. Stan wylogowywania obejmuje nazwy jednego lub kilku recenzentów. Każda codzienna kompilacja [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porównuje kod krytyczny z tym w poprzednich kompilacjach w celu sprawdzenia niezatwierdzonych zmian. Jeśli inżynier modyfikuje kod krytyczny bez zgody zespołu recenzowania, zostanie on zidentyfikowany i rozwiązany od razu. Ten proces umożliwia stosowanie i konserwację szczególnie wysokiego poziomu kontroli nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kodem piaskownicy.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](security-wpf.md)
- [Zabezpieczenie częściowej relacji zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Wiarygodne przetwarzanie](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Zabezpieczenia w programie .NET](../../standard/security/index.md)
