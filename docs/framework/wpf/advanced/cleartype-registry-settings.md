---
title: Ustawienia rejestru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: cacdc47a35bfd197bcac29edc6f7c780d3b8578f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cleartype-registry-settings"></a>Ustawienia rejestru ClearType
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] ustawień rejestru, które są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, które renderowania tekstu można używać urządzeń wyświetlania [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcji umożliwia czytanie rozszerzoną. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest to technologia oprogramowania opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] która poprawia czytelność tekstu w istniejących LCDs (należy zmienić.), takie jak ekranów komputerów przenośnych, Pocket PC ekrany i prosty monitory. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Uzyskiwanie dostępu do elementów usługi stripe poszczególnych pionowy kolorów w każdym pikselu ciekłokrystalicznym utworów. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], zobacz [omówienie ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Tekst, który jest odwzorowywany z [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] może się pojawić różne podczas wyświetlania na różnych urządzeniach wyświetlania. Na przykład niewielka liczba monitorów zaimplementować kolor elementów usługi stripe w kolejności niebieski, zielony, czerwony zamiast częściej czerwony, zielony, niebieski ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) kolejności.  
  
 Tekst, który jest odwzorowywany z [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] może również zostać wyświetlony różne widzianego przez osoby o różnej czułości kolorów. Niektóre osoby mogą wykryć niewielkie różnice w kolorze lepszą niż inne.  
  
 W każdym z tych przypadków [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcje muszą zostać zmodyfikowane w celu zapewnienia najlepiej odczytywania środowisko dla każdego.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Określa czterech ustawień rejestru umożliwiające sterowanie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcje:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom|Opisuje poziom [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kolor przejrzystości.|  
|Poziom gamma|Opisuje poziom składnika kolor pikseli na urządzeniu.|  
|Struktura pikseli|W tym artykule opisano układ pikseli na urządzeniu.|  
|Poziom kontrastu tekstu|Opisuje poziom kontrastu wyświetlanego tekstu.|  
  
 Te ustawienia można uzyskać przez narzędzie zewnętrzne konfiguracji, który potrafi do odwołania wskazywanego przez nią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawień rejestru. Te ustawienia można również utworzony lub zmodyfikowany, uzyskując dostęp do wartości bezpośrednio za pomocą [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytor rejestru.  
  
 Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawienia rejestru nie są ustawione (które jest w stanie domyślna), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapytania aplikacji [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] informacje o systemie parametry dla wygładzanie ustawienia czcionki.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat wyliczania nazwy wyświetlane urządzenia, zobacz `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcji.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Poziom ClearType  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Poziom pozwala na dostosowanie renderowanie tekstu na podstawie liter kolorów i osoby z punktu widzenia użytkownika. Dla niektórych użytkowników, renderowanie tekstu, który używa [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] na najwyższym poziomie nie tworzy najlepiej odczytywania środowisko.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Poziom jest wartość całkowita z zakresu od 0 do 100. Jest to domyślny poziom 100, co oznacza, że [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] korzysta z funkcji maksymalną kolor elementów usługi stripe urządzenia. Jednak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziomu 0 renderuje tekstu jako tekstu zawierającego skali odcieni szarości. Przez ustawienie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziomu gdzieś w przedziale od 0 do 100, możesz utworzyć poziom pośredni odpowiedni do wrażliwości kolor danej osoby.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Lokalizacja ustawienia rejestru dla [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom jest ustawieniem użytkownika, które odpowiada nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia ekranu dla użytkownika `ClearTypeLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienie w Edytorze rejestru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom.  
  
 ![Ustawienia ClearType w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje renderowania tekstu w jednym z obu dwóch trybów z włączonymi i wyłączonymi [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Jeśli tekst jest renderowany bez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], jest ona określana jako renderowania skali odcieni szarości.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Poziom gamma  
 Poziom gamma odnosi się do rożne relacji między pikseli i jasności. Ustawienie poziomu gamma powinny odpowiadać właściwości fizyczne urządzenia wyświetlającego; w przeciwnym razie mogą wystąpić zakłócenia w renderowanym danych wyjściowych. Na przykład test może pojawić się zbyt szeroki lub zbyt ograniczone lub obrzeża kolorów nie mogą pojawiać się na krawędzi pionowy rdzenie symboli.  
  
 Poziom gamma jest wartość całkowita z zakresu od 1000 do 2200. Domyślny poziom to 1900 roku.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienie poziomu lokalizację gamma rejestru jest ustawienie komputera lokalnego, umożliwiająca nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia ekranu dla użytkownika `GammaLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu gamma.  
  
 ![Ustawienia ClearType w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Struktura pikseli  
 Struktura pikseli opisuje typ pikseli, które składają się na urządzeniu. Struktura pikseli jest zdefiniowany jako jeden z trzech typów:  
  
|Typ|Wartość|Opis|  
|----------|-----------|-----------------|  
|Płaski|0|Dla urządzenia wyświetlania nie ma żadnych struktury pikseli. Oznacza to, że w obszarze pikseli są Rozmieść równomiernie źródła światła dla każdego koloru — jest to określane jako renderowania skali odcieni szarości. To jest sposób standard wyświetlania działa urządzenie. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nigdy nie jest stosowany do renderowanego tekstu.|  
|RGB|1|Urządzenia wyświetlającego ma następującą liczbę pikseli, które składają się z trzech rozkłada w następującej kolejności: czerwony, zielony i niebieski. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest stosowany do renderowanego tekstu.|  
|BGR|2|Urządzenia wyświetlającego ma następującą liczbę pikseli, które składają się z trzech rozkłada w następującej kolejności: niebieski, zielony i kolor czerwony. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest stosowany do renderowanego tekstu. Zwróć uwagę, jak jest odwrócony kolejności z typem RGB.|  
  
 Struktura pikseli odpowiada wartość całkowitą z zakresu od 0 do 2. Domyślny poziom to 0, co reprezentuje strukturę płaskiej pikseli.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat wyliczania nazwy wyświetlane urządzenia, zobacz `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcji.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienia lokalizacji dla struktury pikseli rejestru jest ustawienie komputera lokalnego, umożliwiająca nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia ekranu dla użytkownika `PixelStructure` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla struktury pikseli.  
  
 ![Ustawienia ClearType w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Poziom kontrastu tekstu  
 Poziom kontrastu tekstu pozwala na dostosowanie renderowanie tekstu w oparciu o szerokości stem symboli. Poziom kontrastu tekst jest wartość całkowita z zakresu od 0 do 6 — im jest większa wartość całkowitą, szersze stem. Domyślny poziom to 1.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienia lokalizacji dla poziomu kontrastu tekst rejestru jest ustawienie poszczególnych użytkowników, umożliwiająca nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia ekranu dla użytkownika `TextContrastLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu kontrastu tekstu.  
  
 ![Ustawienia ClearType w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Zobacz też  
 [ClearType — przegląd](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Antialiasingu ClearType](https://msdn.microsoft.com/library/dd183433(v=vs.85).aspx)
