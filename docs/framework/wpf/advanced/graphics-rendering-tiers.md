---
title: Poziomy zmiany grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: 4f9de7736851027c9f6b851984953e37b96d456a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547898"
---
# <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki
Warstwa renderowania określa poziom możliwości sprzętowe grafiki i wydajności dla urządzenia z systemem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  

  
<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Sprzęt grafiki  
 Funkcje sprzętu grafiki, że większość wpływ poziomy warstwy renderowania to:  
  
-   **Ilość pamięci RAM wideo** określa ilość pamięci wideo na sprzęcie grafiki, rozmiaru i liczby buforów, które mogą służyć do składania grafiki.  
  
-   **Program do cieniowania pikseli** programu do cieniowania pikseli jest grafiki, funkcji, który oblicza wyniki na podstawie każdego piksela przetwarzania. W zależności od rozdzielczości grafiki wyświetlane może istnieć kilka milionów pikseli, które muszą być przetworzone dla każdej ramce wyświetlania.  
  
-   **Program do cieniowania wierzchołków** grafiki, funkcji, który wykonuje operacji matematycznych na dane wierzchołków obiektu przetwarzania jest cieniowania wierzchołków.  
  
-   **Obsługa multitekstur** Obsługa multitekstur odwołuje się do możliwość zastosowania co najmniej dwa różne tekstury podczas mieszania operacji na obiekcie grafiki 3D. Stopień multitexture pomocy technicznej jest określana przez liczbę jednostek multitexture na sprzęcie grafiki.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Renderowanie definicje warstw  
 Funkcje sprzętowe grafiki stwierdzenie, renderowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Systemu definiuje trzy warstwy renderowania:  
  
-   **Renderowanie warstwy 0** nie przyspieszanie sprzętowe grafiki. Wszystkie funkcje graficzne Użyj przyspieszenia oprogramowania. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersja jest starsza niż wersja 9.0.  
  
-   **Renderowanie warstwy 1** niektóre funkcje grafiki wykorzystują przyspieszanie sprzętowe grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersji jest większa niż lub równa wersji 9.0.  
  
-   **Renderowanie warstwy 2** przyspieszanie sprzętowe grafiki używać większości jej funkcji grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersji jest większa niż lub równa wersji 9.0.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Właściwości umożliwia pobieranie warstwy renderowania w czasie wykonywania aplikacji. Aby sprawdzić, czy urządzenie obsługuje niektóre funkcje przyspieszane sprzętowo grafiki korzystasz z warstwy renderowania. Aplikację można następnie automatycznie podjąć różne ścieżki w czasie wykonywania w zależności od warstwy renderowania obsługiwane przez urządzenie.  
  
### <a name="rendering-tier-0"></a>Renderowanie warstwy 0  
 Renderowanie warstwy wartość 0 oznacza brak grafiki nie przyspieszanie sprzętowe są dostępne dla aplikacji na urządzeniu. Na tym poziomie warstwy powinien założyć, renderowana przez oprogramowanie z nie przyspieszanie sprzętowe wszystkie grafiki. Funkcja ta warstwa odpowiada [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] wersję, która jest mniejsza niż 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Renderowanie warstwy 1 i renderowania warstwy 2  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4 renderowania warstwy 1 został zdefiniowany ponownie obejmujący tylko grafiki sprzęt obsługuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 lub nowszej. Grafika sprzęt obsługuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 lub 8 jest teraz zdefiniowany jako renderowania warstwy 0.  
  
 Renderowanie wartość warstwy 1 lub 2 oznacza, że większość funkcji grafiki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyje przyspieszanie sprzętowe, jeśli zasoby systemowe niezbędne są dostępne i nie zostały wyczerpane. Odpowiada to [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] wersję, która jest większa niż lub równa 9.0.  
  
 W poniższej tabeli przedstawiono różnice w grafiki wymagania sprzętowe dla renderowania warstwy 1 i renderowania warstwy 2:  
  
|Funkcja|Warstwy 1|Warstwy 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Wersja|Musi być większa lub równa 9.0.|Musi być większa lub równa 9.0.|  
|Ilość pamięci RAM wideo|Musi być większa lub równa 60MB.|Musi być większa niż lub równy 120MB.|  
|Program do cieniowania pikseli|Poziom wersji musi być większa lub równa 2.0.|Poziom wersji musi być większa lub równa 2.0.|  
|Program do cieniowania wierzchołków|Nie jest wymagany.|Poziom wersji musi być większa lub równa 2.0.|  
|Multitexture jednostki|Nie jest wymagany.|Liczba jednostek musi być większa lub równa 4.|  
  
 Następujące funkcje i możliwości są sprzętu przyspieszony dla renderowania warstwy 1 i renderowania warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Renderowanie 2D|Renderowanie najbardziej 2D jest obsługiwana.|  
|Rasteryzacji 3D|Większość rasteryzacji 3D jest obsługiwana.|  
|Filtrowanie anizotropowych 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] próbuje użyć anizotropowej filtrowania podczas renderowania 3W zawartości. Filtrowanie anizotropowej odwołuje się do udoskonalanie jakości obrazu tekstur na powierzchni, które są daleko i nawisów pod kątem względem aparatu.|  
|Mapowanie MCI 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] próbuje użyć mapowania MCI podczas renderowania 3W zawartości. Mapowanie MCI zwiększa jakość renderowania tekstury tekstury zajmuje mniejszych widzenia pola w <xref:System.Windows.Controls.Viewport3D>.|  
|Gradientu promieniowego|Obsługiwane, należy unikać użycia <xref:System.Windows.Media.RadialGradientBrush> na dużych obiektów.|  
|Obliczenia oświetlenia 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonuje oświetlenia wierzchołków, co oznacza, że intensywność światła muszą zostać obliczone na każdy wierzchołek każdego materiału zastosowane do siatki.|  
|Renderowanie tekstu|Podrzędne pikseli czcionki renderowania używa programów do cieniowania pikseli dostępne na sprzęcie grafiki.|  
  
 Następujące funkcje i możliwości są sprzętu przyspieszony tylko w przypadku renderowania warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Wygładzanie 3D|Wygładzanie 3D jest obsługiwana tylko na systemy operacyjne obsługujące Display Model sterownika (WDDM) systemu Windows, takich jak [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Następujące funkcje i możliwości są **nie** przyspieszony sprzętu:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Wydruk|Cała zawartość drukowanych jest renderowany przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potoku oprogramowania.|  
|Rasteryzacji zawartości, która używa <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Zawartość renderowany przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> metody <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Ułożenie sąsiadujące zawartość, która używa <xref:System.Windows.Media.TileBrush>|Wszelkie rozmieszczany zawartości, w którym <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.TileBrush> ma ustawioną wartość <xref:System.Windows.Media.TileMode.Tile>.|  
|Powierzchnie przekracza rozmiar maksymalny tekstury sprzętu grafiki|Dla większości sprzętu grafiki dużych powierzchni są rozmiar 2048 x 2048 lub 4096 x 4096 pikseli.|  
|Każde działanie, którego wideo wymaganie pamięci RAM przekracza ilość pamięci sprzętu grafiki|Użycie pamięci RAM wideo aplikacji można monitorować za pomocą narzędzia Perforator, który znajduje się w [pakiet wydajności WPF](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e) w zestawie Windows SDK.|  
|Warstwowego systemu windows|Zezwalaj warstwowego windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje do renderowania zawartości ekranu w oknie nieregularnych. W systemach operacyjnych obsługuje wyświetlania modelu sterownika (WDDM) systemu Windows, takich jak [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)], warstwowego systemu windows są przyspieszony sprzętu. W innych systemach takich jak [!INCLUDE[winxp](../../../../includes/winxp-md.md)], warstwowego systemu windows są renderowane przez oprogramowanie z nie przyspieszanie sprzętowe.<br /><br /> Można włączyć warstwowego systemu windows w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przez ustawienie następujących <xref:System.Windows.Window> właściwości:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Inne zasoby  
 Następujące zasoby mogą ułatwiają analizowanie charakterystyki wydajności Twojego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
### <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia cztery ustawienia rejestru dla kontrolowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję Przyspieszanie sprzętowe**|Określa, czy powinno być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość wielopróbkowego**|Określa stopień multisampling dla antialiasingu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] zawartości.|  
|**Wymagane sterownik wideo daty ustawienie**|Określa, czy system wyłącza przyspieszanie sprzętowe sterowniki wydane zanim listopad 2004.|  
|**Opcja rasteryzator odwołania**|Określa, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy używać rasteryzator odwołania.|  
  
 Te ustawienia są dostępne dla dowolnego narzędzia konfiguracji zewnętrznego, który potrafi odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawień rejestru. Te ustawienia można również utworzony lub zmodyfikowany, uzyskując dostęp do wartości bezpośrednio za pomocą [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytor rejestru. Aby uzyskać więcej informacji, zobacz [ustawienia rejestru renderowania grafiki](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Narzędzia profilowania wydajności WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia zestaw narzędzi, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określić typy optymalizacji wydajności, które można zastosować profilowania wydajności. W poniższej tabeli wymieniono profilowania narzędzia, które są uwzględniane w wydajności [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] narzędzia pakiet wydajności WPF:  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Perforator|Służy do analizowania sposób renderowania.|  
|Visual Profiler|Użyj do profilowania stosowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usług, takich jak układ i obsługi przez elementy w drzewie wizualnym zdarzeń.|  
  
 Pakiet wydajności WPF udostępnia rozbudowane, graficzny widok danych dotyczących wydajności. Aby uzyskać więcej informacji na temat narzędzi wydajności WPF, zobacz [pakiet wydajności WPF](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e).  
  
### <a name="directx-diagnostic-tool"></a>Narzędzie diagnostyczne DirectX  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Narzędzia diagnostycznego, Dxdiag.exe zaprojektowano w celu ułatwienia rozwiązywania problemów [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]— problemy związane z. Domyślny folder instalacji dla [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] narzędzia diagnostycznego jest:  
  
 `~\Windows\System32`  
  
 Po uruchomieniu [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] narzędzia diagnostycznego, okno główne zawiera zestaw kart, które umożliwiają wyświetlanie i diagnozowanie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-powiązane informacje. Na przykład **systemu** zawiera informacje o systemie o komputerze oraz określa wersję [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] zainstalowane na tym komputerze.  
  
 ![Screenhot: Narzędzie diagnostyczne DirectX](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Narzędzie diagnostyczne DirectX głównego okna  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.RenderCapability>  
 <xref:System.Windows.Media.RenderOptions>  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Pakiet wydajności WPF](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)  
 [Ustawienia rejestru renderowania grafiki](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)  
 [Animacja — porady i wskazówki](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
