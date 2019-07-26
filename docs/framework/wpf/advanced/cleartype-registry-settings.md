---
title: Ustawienia rejestru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: db7d6ec5663d657969e1508bd0b9f62c25e491b0
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484676"
---
# <a name="cleartype-registry-settings"></a>Ustawienia rejestru ClearType
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] ustawień rejestru, które są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.  

<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje, które renderują tekst do urządzenia wyświetlającego, używają funkcji ClearType w celu zapewnienia ulepszonego środowiska odczytywania. Technologia ClearType jest technologią oprogramowania opracowaną przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] program, która zwiększa czytelność tekstu w istniejących LCDS (w przypadku wyświetlaczy Liquid Crystal), takich jak ekrany laptopów, urządzenia Pocket PC i monitory płaskoekranowe. Technologia ClearType działa przez uzyskanie dostępu do poszczególnych elementów pasków kolorów w pionie w każdym piksel ekranu LCD. Aby uzyskać więcej informacji na temat technologii ClearType, zobacz [Omówienie technologii ClearType](cleartype-overview.md).  
  
 Tekst renderowany przy użyciu technologii ClearType może wyglądać znacznie inaczej podczas wyświetlania na różnych urządzeniach wyświetlających. Na przykład niewielka liczba monitorów implementuje elementy pasków koloru w kolorze niebieskim, zielonym, czerwonym, a nie na bardziej typowym porządku czerwonym [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)], zielonym, niebieskim ().  
  
 Tekst renderowany przy użyciu technologii ClearType może być również znacznie różny podczas wyświetlania przez użytkowników indywidualnych z różnymi poziomami czułości kolorów. Niektóre osoby mogą wykrywać nieznaczne różnice w kolorze lepszym od innych.  
  
 W każdym z tych przypadków funkcje ClearType muszą być modyfikowane w celu zapewnienia najlepszego środowiska odczytywania dla każdej osoby.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]określa cztery ustawienia rejestru do kontrolowania funkcji technologii ClearType:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Poziom ClearType|Opisuje poziom przejrzystości koloru technologii ClearType.|  
|Poziom gamma|Opisuje poziom składnika koloru piksela dla urządzenia wyświetlającego.|  
|Struktura pikseli|Opisuje rozmieszczenie pikseli dla urządzenia wyświetlającego.|  
|Poziom kontrastu tekstu|Opisuje poziom kontrastu wyświetlanego tekstu.|  
  
 Dostęp do tych ustawień można uzyskać za pomocą narzędzia konfiguracji zewnętrznej, które wie, jak odwoływać się do zidentyfikowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ustawień rejestru ClearType. Te ustawienia można również utworzyć lub zmodyfikować, uzyskując dostęp do wartości bezpośrednio przy użyciu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] edytora rejestru.  
  
 Jeśli ustawienia rejestru [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ClearType nie są ustawione (czyli stan domyślny), aplikacja wysyła zapytanie o informacje o parametrach systemowych dla ustawień wygładzania czcionek. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
> [!NOTE]
>  Aby uzyskać informacje na temat wyliczania nazw urządzeń wyświetlających `SystemParametersInfo` , zobacz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcję.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Poziom ClearType  
 Poziom ClearType umożliwia dostosowanie renderowania tekstu w oparciu o czułość koloru i percepcję osoby. W przypadku niektórych osób renderowanie tekstu, który używa technologii ClearType na najwyższym poziomie, nie produkuje najlepszego środowiska odczytywania.  
  
 Poziom ClearType jest wartością całkowitą z zakresu od 0 do 100. Domyślnym poziomem jest 100, co oznacza, że technologia ClearType używa maksymalnej możliwości elementów paska kolorów urządzenia wyświetlającego. Jednak poziom ClearType równy 0 renderuje tekst jako szary Skala. Ustawiając poziom ClearType w zakresie od 0 do 100, można utworzyć poziom pośredni, który jest odpowiedni do czułości koloru danej osoby.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu technologii ClearType to pojedyncze ustawienie użytkownika odnoszące się do określonej nazwy urządzenia wyświetlanego:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlanego użytkownika `ClearTypeLevel` zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu technologii ClearType.  
  
 ![Ustawienia technologii ClearType w Edytorze rejestru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje renderują tekst w jednym z dwóch trybów z i bez technologii ClearType. Gdy tekst jest renderowany bez technologii ClearType, jest określany jako szare renderowanie skali.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Poziom gamma  
 Poziom gamma odnosi się do nieliniowej relacji między wartością piksela a luminancją. Ustawienie poziomu gamma powinno odpowiadać charakterystyce fizycznej urządzenia wyświetlającego; w przeciwnym razie zniekształcenia w renderowanych danych wyjściowych może wystąpić. Na przykład test może wydawać się zbyt szerokim lub zbyt wąskim lub naruszyć kolory na krawędziach pionowych łodyg symboli.  
  
 Poziom gamma jest wartością całkowitą z zakresu od 1000 do 2200. Poziom domyślny to 1900.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu gamma jest ustawieniem komputera lokalnego, które odpowiada określonej nazwie wyświetlanej urządzenia:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlanego użytkownika `GammaLevel` zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu gamma.  
  
 ![Ustawienia poziomu gamma ClearType w Edytorze rejestru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Struktura pikseli  
 Struktura pikseli opisuje typ pikseli, które tworzą urządzenie wyświetlające. Struktura pikseli jest definiowana jako jeden z trzech typów:  
  
|Typ|Wartość|Opis|  
|----------|-----------|-----------------|  
|Zryczałtowany|0|Urządzenie wyświetlane nie ma struktury pikseli. Oznacza to, że źródła światła dla każdego koloru są równomiernie rozłożone w obszarze pikseli — jest to nazywane renderowaniem szarym skalowaniem. Jest to sposób działania standardowego urządzenia wyświetlającego. Technologia ClearType nigdy nie jest stosowana do renderowanego tekstu.|  
|RGB|1|Urządzenie wyświetlające ma piksele, które składają się z trzech pasków w następującej kolejności: czerwony, zielony i niebieski. Technologia ClearType jest stosowana do renderowanego tekstu.|  
|BGR|2|Urządzenie wyświetlające ma piksele, które składają się z trzech pasków w następującej kolejności: Blue, Green i Red. Technologia ClearType jest stosowana do renderowanego tekstu. Zwróć uwagę, jak zamówienie jest odwracane od typu RGB.|  
  
 Struktura pikseli odpowiada wartości całkowitej, która mieści się w zakresie od 0 do 2. Poziom domyślny to 0, który reprezentuje strukturę pikseli prostych.  
  
> [!NOTE]
>  Aby uzyskać informacje na temat wyliczania nazw urządzeń wyświetlających `EnumDisplayDevices` , zobacz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcję.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla struktury pikseli to ustawienie komputera lokalnego odpowiadające określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlanego użytkownika `PixelStructure` zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla struktury pikseli.  
  
 ![Ustawienia poziomu gamma ClearType w Edytorze rejestru](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Poziom kontrastu tekstu  
 Poziom kontrastu tekstu umożliwia dostosowanie renderowania tekstu na podstawie szerokości łodyg symboli. Poziom kontrastu tekstu jest wartością całkowitą z zakresu od 0 do 6 — im większa wartość całkowita, tym szerszy. Poziom domyślny to 1.  
  
### <a name="registry-setting"></a>Ustawienie rejestru  
 Lokalizacja ustawienia rejestru dla poziomu kontrastu tekstu to pojedyncze ustawienie użytkownika odpowiadające określonej nazwie urządzenia wyświetlanego:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlanego użytkownika `TextContrastLevel` zdefiniowana jest wartość DWORD. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu kontrastu tekstu.  
  
 ![Ustawienia technologii ClearType w Edytorze rejestru.](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>Zobacz także

- [ClearType — przegląd](cleartype-overview.md)
- [Wygładzanie ClearType](/windows/desktop/gdi/cleartype-antialiasing)
