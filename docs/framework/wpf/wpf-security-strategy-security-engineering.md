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
ms.openlocfilehash: fd29696d88eba5c1363464334b63cb2ab0df4a0e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210165"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategia zabezpieczeń WPF - projekt zabezpieczeń
Wiarygodne technologie komputerowe to inicjatywa firmy Microsoft, zapewniających produkcji bezpiecznego kodu. To kluczowy element wiarygodne technologie komputerowe [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Jest praktykę, który jest używany w połączeniu z standardowa inżynieryjnym ułatwiają dostarczanie bezpiecznego kodu. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Składa się z dziesięciu fazy, które łączą najlepsze rozwiązania z ujęcie w formalne ramy measurability oraz dodatkowe struktury, w tym:  
  
-   Analiza projekt zabezpieczeń  
  
-   Kontroli jakości oparte na narzędziu  
  
-   Testy penetracyjne  
  
-   Przegląd zabezpieczeń końcowe  
  
-   Zarządzanie zabezpieczeniami produktu wersji wpisu  
  
## <a name="wpf-specifics"></a>Charakterystyka WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Zespół inżynierów i stosuje rozszerza [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], połączenie obejmuje następujące aspekty klucza:  
  
 [Modelowanie zagrożeń](#threat_modeling)  
  
 [Narzędzia do edycji i analizy zabezpieczeń](#tools)  
  
 [Techniki testowania](#techniques)  
  
 [Zarządzanie kodem krytycznym](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Modelowanie zagrożeń jest podstawowym składnikiem [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]i jest używana do profilu systemu, aby określić potencjalnych luk w zabezpieczeniach. Po zidentyfikowaniu luk w zabezpieczeniach, modelowanie zagrożeń gwarantuje również, że zostały spełnione odpowiednie środki zaradcze.  
  
 Na wysokim poziomie modelowanie zagrożeń obejmuje następujące kroki klucza przy użyciu magazynu połówce, na przykład:  
  
1.  **Identyfikowanie zasobów**. Zasoby w magazynie połówce może obejmować pracowników, bezpiecznym miejscu, kasy i spisu.  
  
2.  **Wyliczanie punktów wejścia**. Punkty wejścia w magazynie połówce może obejmować frontonu i drzwi Wstecz, systemu windows, ładowanie dock i klimatyzacji.  
  
3.  **Badanie ataków na zasoby przy użyciu punktów wejścia**. Jeden możliwych ataków skierowania sklepu połówce *bezpieczne* zasobów za pomocą *klimatyzacja* punkt wejścia; klimatyzacja jednostką może być unscrewed umożliwia bezpiecznie można ściągnąć, za jego pośrednictwem i poza Magazyn.  
  
 Modelowanie zagrożeń są stosowane w całym [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] i obejmuje następujące elementy:  
  
-   Sposób, w jaki [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analizator składni odczytuje pliki mapuje tekstu do odpowiedniej klasy modelu obiektów i tworzy rzeczywisty kod.  
  
-   Jak uchwyt okna (hWnd) jest tworzony, wysyła wiadomości i jest używany do renderowania zawartości okna.  
  
-   Sposób powiązania danych uzyskuje zasoby i wchodzi w interakcję z systemu.  
  
 Te modele zagrożeń są ważne dla identyfikacji wymagań dotyczących projektowania zabezpieczeń i zagrożeń spectre podczas procesu projektowania.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Analiza źródła i narzędzia do edycji  
 Oprócz kod zabezpieczający ręcznego przeglądu elementów [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] zespół używa kilku narzędzi do analizy źródła i skojarzone zmiany do zmniejszenia luk w zabezpieczeniach. Szeroki zakres źródła, narzędzia są używane i obejmują następujące elementy:  
  
-   **FXCop**: umożliwia znalezienie typowych problemów z zabezpieczeniami w kodzie zarządzanym, począwszy od zasady dziedziczenia do użycia zabezpieczeń dostępu kodu jak bezpiecznie współpracować z kodem niezarządzanym. Zobacz [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Prefiks/Prefast**: formatu luk w zabezpieczeniach znajduje i typowe problemy z zabezpieczeniami w niezarządzanym kodzie, takich jak przekroczenia buforu ciągu problemów i sprawdzania błędów.  
  
-   **Zakaz dostępu do interfejsów API**: Wyszukiwanie źródła kodu w celu identyfikowania przypadkowego funkcje, które są dobrze znane powoduje problemy z zabezpieczeniami, takich jak `strcpy`. Po zidentyfikowaniu tych funkcji są zastępowane rozwiązań alternatywnych, które są większe bezpieczeństwo.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Techniki testowania  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] korzysta z rozmaitych zabezpieczeń testowania technik, które obejmują:  
  
-   **Testowanie Whitebox**: testerów wyświetlić kod źródłowy, a następnie skompiluj luki w testach  
  
-   **Testowanie Blackbox**: testerów próbuje znaleźć zabezpieczeń luki, sprawdzając interfejsu API i funkcje, a następnie spróbuj na ataki produktu.  
  
-   **Cofa problemy dotyczące zabezpieczeń z innymi produktami**: w stosownych przypadkach, sprawdzane są problemy z zabezpieczeniami z produktów pokrewnych. Na przykład odpowiednie wariantów około 60 problemy z bezpieczeństwem dotyczące [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] zostały zidentyfikowane i próby ich zastosowanie do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Na podstawie narzędzia do testów Penetracyjnych, za pośrednictwem plików, ocena**: ocena pliku to wykorzystania czytnik plików wejściowych zakresu przy użyciu różnych danych wejściowych. Jednym z przykładów w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] których jest używana ta technika jest pod kątem błędów w kodzie dekodowanie obrazu.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Zarządzanie kodem krytycznym  
 Dla [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tworzy piaskownicy zabezpieczeń przy użyciu .NET Framework — Obsługa znakowania i śledzenia kod zabezpieczenia krytyczny, który podnosi poziom uprawnień uprawnienia (zobacz **zabezpieczenia-krytyczny metodologii** w [WPF Strategia zabezpieczeń — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Taki kod, na kod krytyczny dla bezpieczeństwa, biorąc pod uwagę wymagania dotyczące jakości wysokiego poziomu zabezpieczeń, odbiera dodatkowego poziomu źródła zarządzania kontrolą i bezpieczeństwem danych inspekcji. Około 5 – 10% z [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] składa się z kodu zabezpieczenia krytyczny, który zostanie oceniony przez dedykowany zespół recenzowania. Kod źródłowy i procesu ewidencjonowania jest zarządzana przez śledzenie kodu krytycznego dla zabezpieczeń i mapowanie każda jednostka krytyczny (czyli metodzie, która zawiera kod krytyczny) do znaku w stanie wyłączonym. Logowanie w stanie wyłączonym obejmują nazwy co najmniej jednego recenzenta. Każdy dzienną kompilacją zestawu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] porównuje kod krytyczny jak w poprzednich kompilacji w celu wyszukania niezatwierdzonych zmian. Jeśli inżynier modyfikuje kod krytyczny bez zgody od zespołu recenzowania, jest zidentyfikowany i stała się natychmiast. Ten proces umożliwia aplikacji i konserwacji szczególnie wysoki poziom kontroli nad [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kodu w piaskownicy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../docs/framework/wpf/security-wpf.md)  
 [Zabezpieczenie częściowej relacji zaufania WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategia zabezpieczeń WPF — zabezpieczenia platformy](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Wiarygodne technologie komputerowe](https://www.microsoft.com/mscorp/twc/default.mspx)  
 [Modelowanie aplikacji zagrożeń](https://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [Wytyczne dotyczące zabezpieczeń: .NET Framework 2.0](https://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
