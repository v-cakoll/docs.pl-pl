---
title: Ustawienia rejestru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186172"
---
# <a name="cleartype-registry-settings"></a>Ustawienia rejestru ClearType
Ten temat zawiera omówienie ustawień rejestru Microsoft ClearType, które są używane przez aplikacje WPF.  

<a name="overview"></a>
## <a name="technology-overview"></a>Przegląd technologii  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje, które renderują tekst na urządzeniu wyświetlającym, używają funkcji ClearType, aby zapewnić lepsze wrażenia z czytania. ClearType to technologia oprogramowania opracowana przez firmę Microsoft, która poprawia czytelność tekstu na istniejących monitorach LCD (Wyświetlacze Ciekłokrystaliczne), takich jak ekrany laptopów, ekrany Pocket PC i monitory płaskoekranowe. Funkcja ClearType działa poprzez dostęp do poszczególnych pionowych kolorowych elementów paska w każdym pikselu ekranu LCD. Aby uzyskać więcej informacji na temat ClearType, zobacz [ClearType Overview](cleartype-overview.md).  
  
 Tekst renderowany za pomocą cleartype może wyglądać znacznie inaczej podczas wyświetlania na różnych urządzeniach wyświetlających. Na przykład niewielka liczba monitorów implementuje elementy koloru w paski w kolorze niebieskim, zielonym, czerwonym, a nie bardziej powszechnej kolejności czerwony, zielony, niebieski (RGB).  
  
 Tekst renderowany za pomocą cleartype może również znacznie się różnić podczas wyświetlania przez osoby o różnym poziomie czułości kolorów. Niektóre osoby mogą wykryć niewielkie różnice w kolorze lepiej niż inne.  
  
 W każdym z tych przypadków ClearType funkcje muszą być modyfikowane w celu zapewnienia najlepszego doświadczenia czytania dla każdej osoby.  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]określa cztery ustawienia rejestru do sterowania funkcjami ClearType:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Poziom ClearType|Opisuje poziom wyrazistości kolorów ClearType.|  
|Poziom gamma|W tym artykule opisano poziom składnika koloru piksela dla urządzenia wyświetlającego.|  
|Struktura pikseli|W tym artykule opisano rozmieszczenie pikseli dla urządzenia wyświetlającego.|  
|Poziom kontrastu tekstu|Opisuje poziom kontrastu wyświetlanego tekstu.|  
  
 Dostęp do tych ustawień można uzyskać za pomocą zewnętrznego narzędzia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konfiguracyjnego, które wie, jak odwoływać się do zidentyfikowanych ustawień rejestru ClearType. Te ustawienia można również utworzyć lub zmodyfikować, uzyskując dostęp do wartości bezpośrednio za pomocą Edytora rejestru systemu Windows.  
  
 Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawienia rejestru ClearType nie są ustawione (co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest stanem domyślnym), aplikacja odpytyje informacje o parametrach systemu Windows w celu uzyskania ustawień wygładzania czcionek.  
  
> [!NOTE]
> Aby uzyskać informacje na temat wyliczania nazw urządzeń wyświetlających, zobacz funkcję `SystemParametersInfo`Win32.  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>Poziom ClearType  
 Poziom ClearType umożliwia dostosowanie renderowania tekstu na podstawie czułości kolorów i percepcji danej osoby. Dla niektórych osób renderowanie tekstu, który używa ClearType na najwyższym poziomie nie daje najlepsze środowisko czytania.  
  
 Poziom ClearType jest wartością całkowitą, która waha się od 0 do 100. Domyślny poziom to 100, co oznacza, że ClearType wykorzystuje maksymalną możliwość elementów paska kolorów urządzenia wyświetlającego. Jednak poziom ClearType 0 renderuje tekst w skali szarości. Ustawiając poziom ClearType gdzieś między 0 i 100, można utworzyć poziom pośredni, który jest odpowiedni dla poszczególnych czułości kolorów.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu ClearType jest ustawieniem indywidualnego użytkownika, które odpowiada określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlającego `ClearTypeLevel` dla użytkownika zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienie Edytor rejestru dla poziomu ClearType.  
  
 ![ClearType ustawienia w Edytorze rejestru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje renderować tekst w jednym z dwóch trybów, z i bez ClearType. Gdy tekst jest renderowany bez ClearType, jest określany jako renderowanie w skali szarości.  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Poziom gamma  
 Poziom gamma odnosi się do nieliniowej relacji między wartością piksela a luminancją. Ustawienie poziomu gamma powinno odpowiadać fizycznym cechom urządzenia wyświetlającego; w przeciwnym razie mogą wystąpić zniekształcenia w renderowanym wyjściu. Na przykład tekst może wydawać się zbyt szeroki lub zbyt wąski, lub kolorowe frędzle mogą pojawić się na krawędziach pionowych łodyg glifów.  
  
 Poziom gamma jest wartością całkowitą, która waha się od 1000 do 2200. Domyślny poziom to 1900.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu gamma jest ustawieniem komputera lokalnego, które odpowiada określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlającego `GammaLevel` dla użytkownika zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienie Edytor rejestru dla poziomu gamma.  
  
 ![Ustawienia poziomu gamma ClearType w Edytorze rejestru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>Struktura pikseli  
 Struktura pikseli opisuje typ pikseli, które tworzą urządzenie wyświetlające. Struktura pikseli jest zdefiniowana jako jeden z trzech typów:  
  
|Typ|Wartość|Opis|  
|----------|-----------|-----------------|  
|Płaskie|0|Urządzenie wyświetlające nie ma struktury pikseli. Oznacza to, że źródła światła dla każdego koloru są równomiernie rozłożone na obszarze piksela — jest to nazywane renderowaniem w skali szarości. Tak działa standardowe urządzenie wyświetlające. ClearType nigdy nie jest stosowany do renderowanego tekstu.|  
|RGB|1|Urządzenie wyświetlające ma piksele, które składają się z trzech pasków w następującej kolejności: czerwonej, zielonej i niebieskiej. ClearType jest stosowany do renderowanego tekstu.|  
|Bgr|2|Urządzenie wyświetlające ma piksele, które składają się z trzech pasków w następującej kolejności: niebieski, zielony i czerwony. ClearType jest stosowany do renderowanego tekstu. Zwróć uwagę, jak zamówienie jest odwrócone od typu RGB.|  
  
 Struktura pikseli odpowiada wartości całkowitej, która waha się od 0 do 2. Domyślnym poziomem jest 0, który reprezentuje strukturę płaskiego piksela.  
  
> [!NOTE]
> Aby uzyskać informacje na temat wyliczania nazw urządzeń wyświetlających, zobacz funkcję `EnumDisplayDevices`Win32.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla struktury pikseli jest ustawieniem komputera lokalnego, które odpowiada określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlającego `PixelStructure` dla użytkownika zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienie Edytor rejestru dla struktury pikseli.  
  
 ![Ustawienia poziomu gamma ClearType w Edytorze rejestru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>Poziom kontrastu tekstu  
 Poziom kontrastu tekstu umożliwia dostosowanie renderowania tekstu na podstawie szerokości trzpienia glifów. Poziom kontrastu tekstu jest wartością całkowitą, która waha się od 0 do 6 — im większa wartość całkowita, tym szersza trzpień. Domyślny poziom to 1.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu kontrastu tekstu jest ustawieniem indywidualnym użytkownika, które odpowiada określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlającego `TextContrastLevel` dla użytkownika zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienie Edytor rejestru dla poziomu kontrastu tekstu.  
  
 ![ClearType ustawienia w Edytorze rejestru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Zobacz też

- [ClearType — przegląd](cleartype-overview.md)
- [ClearType Antialiasing](/windows/desktop/gdi/cleartype-antialiasing)
