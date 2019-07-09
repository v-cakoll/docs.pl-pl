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
ms.openlocfilehash: 77694b2a86c91f3e6946ecd50f4765404750f37b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664158"
---
# <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki
Warstwy renderowania definiuje poziom możliwości sprzętu grafiki i wydajności na urządzeniu z systemem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  

<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>Sprzęt graficzny  
 Dostępne są następujące funkcje, możliwości sprzętu graficznego i że mają największy wpływ na poziom warstwy renderowania:  
  
- **Pamięć RAM wideo** określa ilość pamięci wideo na sprzęt graficzny, rozmiar i liczba buforów, które mogą służyć do składania grafiki.  
  
- **Program do cieniowania pikseli** program do cieniowania pikseli jest funkcja, która oblicza wpływ na podstawie każdego piksela GPU. W zależności od rozwiązania wyświetlanych grafiki może być kilka milionów piksele, które muszą być przetworzone w każdej klatce wyświetlania.  
  
- **Program do cieniowania wierzchołków** program do cieniowania wierzchołków jest funkcja, która wykonuje operacje matematyczne na danych wierzchołka obiektu GPU.  
  
- **Obsługa multitekstur** multitekstur pomocy technicznej, który odwołuje się do możliwość stosowania co najmniej dwóch odrębnych tekstury podczas mieszania operacji na obiekcie grafiki 3D. Stopień multitexture pomocy technicznej jest określana przez liczbę jednostek multitexture na sprzęt graficzny.  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>Renderowanie definicje warstw  
 Funkcje, możliwości sprzętu graficznego i określić możliwości renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] System definiuje trzy poziomy renderowania:  
  
- **Renderowanie warstwy 0** nie przyspieszania sprzętowego grafiki. Wszystkie funkcje grafiki Użyj przyspieszenia oprogramowania. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziom wersja jest niższa niż wersja 9.0.  
  
- **Renderowanie warstwy 1** niektóre funkcje grafiki wykorzystują przyspieszanie sprzętowe grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziomie wersji jest większa lub równa wersji 9.0.  
  
- **Renderowanie warstwy 2** większość funkcji grafiki używał przyspieszania sprzętowego grafiki. [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Poziomie wersji jest większa lub równa wersji 9.0.  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> Właściwość pozwala pobrać warstwy renderowania w czasie wykonywania aplikacji. Warstwy renderowania służy do określenia, czy urządzenie obsługuje niektóre funkcje grafiki przyspieszane sprzętowo. Aplikacja może następnie podjąć różne ścieżki w czasie wykonywania, w zależności od warstwy renderowania obsługiwanych przez urządzenie.  
  
### <a name="rendering-tier-0"></a>Renderowanie warstwy 0  
 Warstwy renderowania wartość 0 oznacza, że nie istnieje żadne grafiki przyspieszanie sprzętowe dostępnych dla danej aplikacji na urządzeniu. Na tym poziomie warstwy należy założyć, że renderowana przez oprogramowanie za pomocą nie przyspieszania sprzętowego grafikę. Funkcja ta warstwa odnosi się do [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] wersji, która jest mniejsza niż 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Renderowanie warstwy 1 i renderowanie warstwy 2  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4, renderowanie warstwy 1 został zdefiniowany ponownie obejmujący tylko sprzęt graficzny, która obsługuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 lub nowszej. Sprzęt graficzny, która obsługuje [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 lub 8 jest teraz zdefiniowany jako renderowania warstwy 0.  
  
 Wartość warstwy renderowania 1 lub 2 oznacza, że większość funkcje grafiki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używał przyspieszania sprzętowego, jeśli zasoby systemowe wymagane są dostępne i nie zostały przekroczone. Odpowiada to [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] wersję, która jest większa lub równa 9.0.  
  
 W poniższej tabeli przedstawiono różnice w grafice wymagania sprzętowe do renderowania warstwy 1 i renderowanie warstwy 2:  
  
|Funkcja|Warstwa 1|Warstwa 2|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Wersja|Musi być większa lub równa 9.0.|Musi być większa lub równa 9.0.|  
|Pamięć RAM wideo|Musi być większa niż lub równy 60MB.|Musi być większa niż lub równy 120MB.|  
|Program do cieniowania pikseli|Poziom wersji muszą być większa lub równa wersji 2.0.|Poziom wersji muszą być większa lub równa wersji 2.0.|  
|Program do cieniowania wierzchołków|Nie jest wymagany.|Poziom wersji muszą być większa lub równa wersji 2.0.|  
|Multitexture jednostki|Nie jest wymagany.|Liczba jednostek muszą być większe niż lub równa 4.|  
  
 Następujące funkcje i możliwości są sprzętowe accelerated do renderowania warstwy 1 i renderowanie warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|2D renderowania|Najbardziej 2D renderowania jest obsługiwane.|  
|Rasteryzacja 3D|Większość rasteryzacji 3D jest obsługiwane.|  
|Filtrowanie anizotropowe 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] próbuje korzystać z filtrowaniem anizotropowymo podczas renderowania 3W zawartości. Filtrowanie anizotropowe odnosi się do zwiększenia jakości obrazu tekstur na powierzchniach, które są daleko lub nawisów pod kątem w odniesieniu do aparatu.|  
|Mapowania MIP 3W|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] próbuje użyć mapowania MIP podczas renderowania 3W zawartości. Mapowanie MIP zwiększa jakość tekstury renderowanie, gdy tekstury zajmuje mniejszych pole widzenia w <xref:System.Windows.Controls.Viewport3D>.|  
|Gradienty promieniowe|Obsługiwane, należy unikać użycia <xref:System.Windows.Media.RadialGradientBrush> dużych obiektów.|  
|Obliczenia udziału oświetlenia 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wykonuje oświetlenia każdego wierzchołka, co oznacza, że intensywność światła muszą być obliczane na każdy wierzchołek każdego materiału stosowane do siatki.|  
|Renderowanie tekstu|Renderowanie czcionki podrzędnych pikseli używa programów do cieniowania pikseli dostępne na sprzęt graficzny.|  
  
 Następujące funkcje i możliwości są sprzętowe accelerated tylko w przypadku renderowania warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Wygładzanie 3D|3D wygładzanie jest obsługiwana tylko na systemy operacyjne obsługujące Display modelu sterownika (WDDM) Windows, takich jak [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Następujące funkcje i możliwości są **nie** przyspieszonej sprzętu:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Drukowane zawartości|Cała zawartość drukowanych jest renderowany przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] potoku oprogramowania.|  
|Rasteryzowany zawartości, który używa <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Żadnej zawartości, renderowane przy użyciu <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> metody <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Fragmentacji zawartość, która używa <xref:System.Windows.Media.TileBrush>|Sąsiadująco dowolnej zawartości, w którym <xref:System.Windows.Media.TileBrush.TileMode%2A> właściwość <xref:System.Windows.Media.TileBrush> ustawiono <xref:System.Windows.Media.TileMode.Tile>.|  
|Powierzchniach, które przekracza rozmiar maksymalny tekstury sprzętu graficznego.|W przypadku większości sprzęt graficzny dużych powierzchni są 2048 x 2048 lub 4096 x 4096 pikseli.|  
|Wszelkie operacje, w których wideo wymagań pamięci RAM przekracza ilość pamięci, możliwości sprzętu graficznego|Możesz monitorować użycie pamięci RAM wideo w aplikacji za pomocą narzędzia Perforator, który znajduje się w [pakiet wydajności WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) w zestawie Windows SDK.|  
|Warstwowej systemu windows|System windows warstwowych na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji do renderowania zawartości ekranu w oknie prostokątny. W systemach operacyjnych obsługują Display modelu sterownika (WDDM) Windows, takich jak [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] i [!INCLUDE[win7](../../../../includes/win7-md.md)], warstwowej systemu windows są accelerated sprzętu. W innych systemach takich jak [!INCLUDE[winxp](../../../../includes/winxp-md.md)], warstwowej systemu windows są renderowane przez oprogramowanie, które nie przyspieszanie sprzętowe.<br /><br /> Możesz włączyć warstwowej okna w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ustawiając następujące <xref:System.Windows.Window> właściwości:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>Inne zasoby  
 Następujące zasoby mogą pomóc w analizie charakterystyki wydajności usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
### <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia cztery ustawienia rejestru dla kontrolowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję Przyspieszanie sprzętowe**|Określa, czy powinno być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość wielopróbkowego**|Określa stopień multisampling antyaliasingu do zawartości 3D.|  
|**Wymagany sterownik wideo daty ustawienie**|Określa, czy system wyłącza przyspieszanie sprzętowe dla sterowników wydanych przed listopada 2004.|  
|**Za pomocą opcji rasteryzatora odwołanie**|Określa, czy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy używać rasteryzatora odwołania.|  
  
 Te ustawienia są dostępne dla dowolnego narzędzia konfiguracji zewnętrznego, który wie, jak utworzyć odwołanie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawień rejestru. Te ustawienia można również utworzone lub zmodyfikowane, uzyskując dostęp do wartości bezpośrednio przy użyciu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Edytora rejestru. Aby uzyskać więcej informacji, zobacz [ustawienia rejestru renderowania grafiki](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Narzędzia profilowania wydajności WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia zestaw narzędzi, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określ typy tych optymalizacji wydajności, które można zastosować profilowania wydajności. W poniższej tabeli wymieniono wydajności, narzędzia, które są objęte profilowania [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] narzędzia pakiet wydajności WPF:  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Perforator|Na użytek analizując zachowanie renderowania.|  
|Visual Profiler|Na użytek profilowania użytkowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usługi, takie jak układ i obsługi przez elementy w drzewie wizualnym zdarzeń.|  
  
 Pakiet wydajności WPF zapewnia rozbudowane, graficzny widok danych dotyczących wydajności. Aby uzyskać więcej informacji na temat narzędzia do oceny wydajności WPF, zobacz [pakiet wydajności WPF](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Narzędzie diagnostyczne DirectX  
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] Narzędzie diagnostyczne, Dxdiag.exe zaprojektowano w celu ułatwienia rozwiązywania problemów z [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]— problemy związane z usługą. Domyślny folder instalacji dla [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] jest narzędzie do diagnostyki:  
  
 `~\Windows\System32`  
  
 Po uruchomieniu [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] narzędzia diagnostycznego okno główne zawiera zbiór kart, które umożliwiają wyświetlanie i diagnozowanie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]-powiązane informacje. Na przykład **systemu** zawiera informacje o systemie o komputerze oraz określa wersję [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] zainstalowanej na komputerze.  
  
 ![Screenhot: DirectX Diagnostic Tool](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Narzędzie diagnostyczne DirectX głównego okna.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Ustawienia rejestru renderowania grafiki](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Animacja — porady i wskazówki](../graphics-multimedia/animation-tips-and-tricks.md)
