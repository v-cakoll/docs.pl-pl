---
title: Strategia bezpieczeństwa i inżynieria
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
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174566"
---
# <a name="wpf-security-strategy---security-engineering"></a>Strategia zabezpieczeń WPF - projekt zabezpieczeń
Trustworthy Computing to inicjatywa firmy Microsoft zapewniająca produkcję bezpiecznego kodu. Kluczowym elementem inicjatywy Trustworthy Computing jest cykl rozwoju zabezpieczeń firmy Microsoft (SDL). SDL jest praktyką inżynieryjną, która jest używana w połączeniu ze standardowymi procesami inżynieryjnymi w celu ułatwienia dostarczania bezpiecznego kodu. SDL składa się z dziesięciu etapów, które łączą najlepsze praktyki z formalizacją, mierzalnością i dodatkową strukturą, w tym:  
  
- Analiza projektu zabezpieczeń  
  
- Kontrole jakości oparte na narzędziach  
  
- Testy penetracyjne  
  
- Ostateczna recenzja zabezpieczeń  
  
- Zarządzanie zabezpieczeniami produktów po wydaniu po wydaniu  
  
## <a name="wpf-specifics"></a>Specyfika WPF  
 Zespół [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] inżynierów stosuje i rozszerza SDL, którego połączenie obejmuje następujące kluczowe aspekty:  
  
 [Modelowanie zagrożeń](#threat_modeling)  
  
 [Narzędzia do analizy i edycji zabezpieczeń](#tools)  
  
 [Techniki testowania](#techniques)  
  
 [Krytyczne zarządzanie kodem](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a>Modelowanie zagrożeń  
 Modelowanie zagrożeń jest podstawowym składnikiem SDL i służy do profilowania systemu w celu określenia potencjalnych luk w zabezpieczeniach. Po zidentyfikowaniu luk w zabezpieczeniach modelowanie zagrożeń zapewnia również odpowiednie środki zaradcze.  
  
 Na wysokim poziomie modelowanie zagrożeń obejmuje następujące kluczowe kroki przy użyciu sklepu spożywczego jako przykładu:  
  
1. **Identyfikacja zasobów**. Aktywa sklepu spożywczego mogą obejmować pracowników, sejf, kasy fiskalne i zapasy.  
  
2. **Wyliczanie punktów wejścia**. Punkty wejścia do sklepu spożywczego mogą obejmować przednie i tylne drzwi, okna, rampę załadunkową i klimatyzatory.  
  
3. **Badanie ataków na zasoby przy użyciu punktów wejścia**. Jeden z możliwych ataków może być wymierzony w *bezpieczny* atut sklepu spożywczego przez punkt wejścia *do klimatyzacji;* klimatyzator może zostać odkręcony, aby umożliwić podciągnięcie sejfu przez nią i ze sklepu.  
  
 Modelowanie zagrożeń jest stosowane [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] w całym i obejmuje następujące elementy:  
  
- Jak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] analizator odczytuje pliki, mapuje tekst do odpowiednich klas modelu obiektu i tworzy rzeczywisty kod.  
  
- Jak uchwyt okna (hWnd) jest tworzony, wysyła wiadomości i jest używany do renderowania zawartości okna.  
  
- Jak powiązanie danych uzyskuje zasoby i współdziała z systemem.  
  
 Te modele zagrożeń są ważne dla identyfikacji wymagań dotyczących projektowania zabezpieczeń i ograniczania zagrożeń podczas procesu tworzenia.  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a>Narzędzia do analizy i edycji źródeł  
 Oprócz ręcznych elementów przeglądu kodu zabezpieczeń [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] SDL zespół używa kilku narzędzi do analizy źródła i skojarzonych zmian w celu zmniejszenia luk w zabezpieczeniach. Do szerokiej gamy narzędzi źródłowych jest wiele narzędzi źródłowych, w tym następujące elementy:  
  
- **FXCop**: Wyszukuje typowe problemy z zabezpieczeniami w kodzie zarządzanym, począwszy od reguł dziedziczenia do użycia zabezpieczeń dostępu do kodu do bezpiecznego współdziałania z kodem niezarządzanym. Zobacz [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefiks/prefaszysta:** Wyszukuje luki w zabezpieczeniach i typowe problemy z zabezpieczeniami w niezarządzanym kodzie, takie jak przekroczenia buforu, problemy z ciągami formatu i sprawdzanie błędów.  
  
- **Zablokowane interfejsy API: Wyszukuje**kod źródłowy w celu zidentyfikowania przypadkowego użycia funkcji, które są dobrze znane z powodowania problemów z zabezpieczeniami, takich jak `strcpy`. Po zidentyfikowaniu te funkcje są zastępowane alternatywami, które są bezpieczniejsze.  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a>Techniki testowania  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]wykorzystuje różne techniki testowania zabezpieczeń, które obejmują:  
  
- **Whitebox Testing:** Testerzy wyświetlą kod źródłowy, a następnie skoszą testów wykorzystujących luki.
  
- **Testowanie blackbox:** Testerzy próbują znaleźć luki w zabezpieczeniach, sprawdzając interfejs API i funkcje, a następnie spróbuj zaatakować produkt.  
  
- **Cofanie problemów z zabezpieczeniami z innych produktów:** W stosownych przypadkach testowane są problemy z zabezpieczeniami powiązanych produktów. Na przykład zidentyfikowano odpowiednie warianty około sześćdziesięciu problemów z zabezpieczeniami [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]programu Internet Explorer i wypróbowano ich zastosowanie do programu .  
  
- **Testy penetracyjne oparte na narzędziach poprzez rozmycie plików:** Rozmycie plików to wykorzystanie zakresu danych wejściowych czytnika plików za pośrednictwem różnych wejść. Jednym z [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] przykładów, w którym ta technika jest używana jest sprawdzenie, czy błąd w kodzie dekodowania obrazu.  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a>Krytyczne zarządzanie kodem  
 W przypadku aplikacji przeglądarki XAML [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] (XBAPs) tworzy piaskownicę zabezpieczeń przy użyciu platformy .NET Framework do oznaczania i śledzenia kodu o krytycznym znaczeniu dla zabezpieczeń, który podnosi uprawnienia (zobacz **Metodologia krytyczna dla zabezpieczeń** w [strategii zabezpieczeń WPF — zabezpieczenia platformy).](wpf-security-strategy-platform-security.md) Biorąc pod uwagę wymagania dotyczące wysokiej jakości zabezpieczeń dla kodu krytycznego dla zabezpieczeń, taki kod otrzymuje dodatkowy poziom kontroli zarządzania źródłem i inspekcji zabezpieczeń. Około 5% do 10% [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] składa się z kodu krytycznego dla zabezpieczeń, który jest sprawdzany przez dedykowany zespół recenzentów. Kod źródłowy i proces ewidencjonowania jest zarządzany przez śledzenie kodu krytycznego zabezpieczeń i mapowanie każdej jednostki krytycznej (tj. metody, która zawiera kod krytyczny) do stanu wylogowania. Stan wyłączenia zawiera nazwy jednego lub więcej recenzentów. Każda dzienna [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kompilacja porównuje kod krytyczny z kodem w poprzednich kompilacjach, aby sprawdzić, czy nie zostały zatwierdzone zmiany. Jeśli inżynier modyfikuje kod krytyczny bez zgody zespołu recenzującego, zostanie on natychmiast zidentyfikowany i naprawiony. Ten proces umożliwia stosowanie i utrzymanie szczególnie wysoki [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] poziom kontroli nad kodem piaskownicy.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia](security-wpf.md)
- [Częściowe zabezpieczenia zaufania WPF](wpf-partial-trust-security.md)
- [Strategia zabezpieczeń WPF — zabezpieczenia platformy](wpf-security-strategy-platform-security.md)
- [Godne zaufania komputery](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Zabezpieczenia w .NET](../../standard/security/index.md)
