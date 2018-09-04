---
title: Ustawienia rejestru ClearType
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: d6a121e2a95ce4005b43937f83c6c74ec7d8f1c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514861"
---
# <a name="cleartype-registry-settings"></a>Ustawienia rejestru ClearType
Ten temat zawiera omówienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] ustawień rejestru, które są używane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Omówienie technologii  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, które renderują tekst do korzystania z urządzenia wyświetlaną [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcji w celu zapewnienia rozszerzonego czytanie. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest to technologia oprogramowanie opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] który poprawia czytelność tekstu na istniejące LCD (należy zmienić.), takie jak ekranów komputerów przenośnych, ekrany Pocket PC i monitory płaskie. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] działa, uzyskując dostęp do poszczególnych kolor pionowych elementy usługi stripe w każdy piksel ekran LCD. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], zobacz [ClearType — Przegląd](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Tekst, który jest renderowany przy użyciu [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] mogą być wyświetlane podczas wyświetlania na różnych urządzeniach wyświetlających różne. Na przykład niewielka liczba monitorów zaimplementować kolorowe elementy usługi stripe w kolejności niebieski, zielony, red, a nie częściej czerwony, zielony, niebieski ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) kolejności.  
  
 Tekst, który jest renderowany przy użyciu [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] może również zostać wyświetlony znacznie różnią się podczas przeglądania przez osoby z różnymi poziomami czułości kolorów. Niektóre osoby mogą wykryć niewielkie różnice w kolorze lepsze niż inne.  
  
 W każdym z tych przypadków [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcje muszą zostać zmodyfikowane w celu zapewnienia najlepszego odczytu środowisko dla poszczególnych osób.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Ustawienia rejestru  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Określa cztery ustawienia rejestru dla kontrolowania [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcje:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom|W tym artykule opisano poziom [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] kolor przejrzystości.|  
|Poziom gamma|W tym artykule opisano poziomu składnika koloru piksela do wyświetlania na urządzeniach.|  
|Struktura pikseli|W tym artykule opisano rozmieszczenie pikseli do wyświetlania na urządzeniach.|  
|Poziom kontrast tekstu|W tym artykule opisano poziom kontrastu wyświetlanego tekstu.|  
  
 Te ustawienia można uzyskać przez narzędzie do konfiguracji zewnętrznego, który wie, jak odwoływać się do wskazywanego przez nią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawień rejestru. Te ustawienia można również utworzone lub zmodyfikowane, uzyskując dostęp do wartości bezpośrednio przy użyciu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytora rejestru.  
  
 Jeśli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] ustawienia rejestru nie są ustawione (co jest domyślnym stanem), [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapytania aplikacji [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] informacje o systemie parametrów do wygładzania ustawienia czcionek.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat wyliczania wyświetlanie nazwy urządzenia, zobacz `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcji.  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Poziom ClearType  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Poziomu pozwala na dostosowanie renderowanie tekstu, na podstawie czułości kolorów i postrzegania indywidualnego. Dla niektórych osób renderowanie tekstu, który używa [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] na najwyższym poziomie nie daje najlepsze środowisko do czytania.  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] Poziom jest liczbą całkowitą z zakresu od 0 do 100. Domyślny poziom to 100, co oznacza, że [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] korzysta z funkcji maksymalnej elementów usługi stripe kolor urządzenia. Jednak [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziomu 0 powoduje wyświetlenie tekstu jako Skala szarości. Ustawiając [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziomu gdzieś między 0 a 100, można utworzyć na poziom pośredni, która będzie odpowiednia dla danej osoby kolor czułości.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Lokalizację ustawień rejestru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom jest ustawienie użytkownika, który odpowiada nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlaną dla użytkownika `ClearTypeLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] poziom.  
  
 ![ClearType ustawień w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje renderowanie tekstu w jednym z albo dwóch trybów z lub bez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Jeśli tekst jest renderowany bez [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], jest ona określana jako renderowania w skali szarości.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Poziom gamma  
 Poziom gamma odnosi się do nieliniowych relacji między pikseli i jasności. Ustawienie poziomie gamma powinien odpowiadać cechy fizyczne urządzenia; w przeciwnym razie mogą wystąpić zakłócenia w wyniku renderowania. Na przykład test może pojawić się zbyt szeroki lub zbyt wąska, lub obrzeża kolorów nie mogą być wyświetlane na krawędzi pionowy rdzenie symbole.  
  
 Poziom gamma jest liczbą całkowitą z zakresu od 1000 do 2200. Domyślny poziom to 1900.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienie poziomie lokalizację gamma rejestru jest ustawienie komputera lokalnego, który odpowiada nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlaną dla użytkownika `GammaLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru dla poziomu gamma.  
  
 ![ClearType ustawień w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Struktura pikseli  
 Struktura pikseli opisuje typ piksele, które składają się na urządzeniu. Struktura pikseli jest zdefiniowany jako jeden z trzech typów:  
  
|Typ|Wartość|Opis|  
|----------|-----------|-----------------|  
|Stosowana jest stała|0|Urządzenia wyświetlającego ma strukturę nie pikseli. Oznacza to, że źródła światła dla każdego koloru zostały rozmieszczone równomiernie w obszarze pikseli — jest to określane jako renderowania w skali szarości. Jest to, jak standardowy wyświetlać działa urządzenie. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] nigdy nie jest stosowany do renderowanej tekstu.|  
|RGB|1|Urządzenia wyświetlającego ma pikseli, które składają się z trzech paski w następującej kolejności: czerwony, zielony i niebieski. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest stosowany do renderowanej tekstu.|  
|BGR|2|Urządzenia wyświetlającego ma pikseli, które składają się z trzech paski w następującej kolejności: niebieski i zielony, a czerwony. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest stosowany do renderowanej tekstu. Zwróć uwagę, jak kolejność jest przeciwny wobec typu RGB.|  
  
 Struktura pikseli odpowiada na wartość całkowitą z zakresu od 0 do 2. Domyślny poziom to 0, co oznacza struktury płaskiej pikseli.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat wyliczania wyświetlanie nazwy urządzenia, zobacz `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcji.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienia lokalizacji dla struktury pikseli rejestru jest ustawienie komputera lokalnego, który odpowiada nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlaną dla użytkownika `PixelStructure` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia ustawienia edytora rejestru w strukturze pikseli.  
  
 ![ClearType ustawień w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Poziom kontrast tekstu  
 Poziom kontrast tekstu można dostosować renderowanie tekstu, w oparciu o szerokości stem symbole. Poziom kontrast tekstu jest liczbą całkowitą z zakresu od 0 do 6 — im większa wartość całkowitą, szerszy stem. Domyślny poziom to 1.  
  
### <a name="registry-setting"></a>Ustawienia rejestru  
 Ustawienia lokalizacji na poziomie kontrast tekstu rejestru jest ustawienie użytkownika, który odpowiada nazwę wyświetlaną określonego urządzenia:  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Dla każdej nazwy urządzenia wyświetlaną dla użytkownika `TextContrastLevel` wartość DWORD jest zdefiniowana. Poniższy zrzut ekranu przedstawia Edytor rejestru ustawienie poziomie kontrast tekstu.  
  
 ![ClearType ustawień w Edytorze rejestru](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Zobacz też  
 [ClearType — przegląd](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Antyaliasing ClearType](/windows/desktop/gdi/cleartype-antialiasing)
