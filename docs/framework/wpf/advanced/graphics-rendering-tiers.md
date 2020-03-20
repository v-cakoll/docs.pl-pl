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
ms.openlocfilehash: 3c21ae3d00aa9f1b48a89650430b89ceccb2a1b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186015"
---
# <a name="graphics-rendering-tiers"></a>Poziomy zmiany grafiki
Warstwa renderowania definiuje poziom możliwości sprzętu graficznego i wydajności [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla urządzenia, które uruchamia aplikację.  

<a name="graphics_hardware"></a>
## <a name="graphics-hardware"></a>Sprzęt graficzny  
 Funkcje sprzętu graficznego, które mają największy wpływ na poziomy warstwy renderowania są następujące:  
  
- **Pamięć RAM wideo** Ilość pamięci wideo na sprzęcie graficznym określa rozmiar i liczbę buforów, które mogą być używane do tworzenia grafiki.  
  
- **Moduł cieniujący pikseli** Moduł cieniujący piksel to funkcja przetwarzania grafiki, która oblicza efekty na piksel. W zależności od rozdzielczości wyświetlanej grafiki może istnieć kilka milionów pikseli, które muszą zostać przetworzone dla każdej klatki wyświetlania.  
  
- **Moduł cieniujący wierzchołków** Moduł cieniujący wierzchołków jest funkcją przetwarzania grafiki, która wykonuje operacje matematyczne na danych wierzchołka obiektu.  
  
- **Obsługa multitektury** Obsługa multitekstury odnosi się do możliwości zastosowania dwóch lub więcej odrębnych tekstur podczas operacji mieszania na obiekcie graficznym 3D. Stopień obsługi multitexture zależy od liczby jednostek multitexture na sprzęcie graficznym.  
  
<a name="rendering_tier_definitions"></a>
## <a name="rendering-tier-definitions"></a>Definicje warstw renderowania  
 Funkcje sprzętu graficznego określają możliwości renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje trzy warstwy renderowania:  
  
- **Renderowanie poziomu 0** Brak akceleracji sprzętowej grafiki. Wszystkie funkcje graficzne wykorzystują akcelerację oprogramowania. Poziom wersji DirectX jest mniejszy niż wersja 9.0.  
  
- **Renderowanie poziomu 1** Niektóre funkcje graficzne używają akceleracji sprzętowej grafiki. Poziom wersji DirectX jest większy lub równy wersji 9.0.  
  
- **Renderowanie poziomu 2** Większość funkcji graficznych używa akceleracji sprzętowej grafiki. Poziom wersji DirectX jest większy lub równy wersji 9.0.  
  
 Właściwość <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType> umożliwia pobieranie warstwy renderowania w czasie wykonywania aplikacji. Warstwa renderowania służy do określenia, czy urządzenie obsługuje niektóre funkcje grafiki przyspieszane sprzętowo. Aplikacja może następnie podjąć różne ścieżki kodu w czasie wykonywania w zależności od warstwy renderowania obsługiwane przez urządzenie.  
  
### <a name="rendering-tier-0"></a>Renderowanie poziomu 0  
 Wartość warstwy renderowania 0 oznacza, że nie ma żadnych akceleracji sprzętu graficznego dostępne dla aplikacji na urządzeniu. Na tym poziomie warstwy należy założyć, że wszystkie grafiki będą renderowane przez oprogramowanie bez przyspieszenia sprzętowego. Funkcjonalność tej warstwy odpowiada wersji DirectX, która jest mniejsza niż 9.0.  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>Renderowanie warstwy 1 i renderowania poziomu 2  
  
> [!NOTE]
> Począwszy od programu .NET Framework 4 renderowanie warstwy 1 zostało ponownie zdefiniowane, aby uwzględnić tylko sprzęt graficzny obsługujący technologię DirectX 9.0 lub większą. Sprzęt graficzny obsługujący technologię DirectX 7 lub 8 jest teraz definiowany jako renderowanie w warstwie 0.  
  
 Wartość warstwy renderowania 1 lub 2 oznacza, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] że większość funkcji graficznych będzie używać przyspieszania sprzętowego, jeśli niezbędne zasoby systemowe są dostępne i nie zostały wyczerpane. Odpowiada to wersji DirectX, która jest większa lub równa 9.0.  
  
 W poniższej tabeli przedstawiono różnice w wymaganiach sprzętowych grafiki dla renderowania warstwy 1 i renderowania warstwy 2:  
  
|Funkcja|Warstwa 1|Warstwa 2|  
|-------------|------------|------------|  
|Wersja DirectX|Musi być większa lub równa 9.0.|Musi być większa lub równa 9.0.|  
|Pamięć RAM wideo|Musi być większa lub równa 60MB.|Musi być większa lub równa 120MB.|  
|Moduł cieniujący pikseli|Poziom wersji musi być większy lub równy 2.0.|Poziom wersji musi być większy lub równy 2.0.|  
|Moduł cieniujący wierzchołków|Bez wymogu.|Poziom wersji musi być większy lub równy 2.0.|  
|Jednostki multiteksturowe|Bez wymogu.|Liczba jednostek musi być większa lub równa 4.|  
  
 Następujące funkcje i możliwości są przyspieszane sprzętowo do renderowania warstwy 1 i renderowania warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Renderowanie 2D|Większość renderowania 2D jest obsługiwana.|  
|Rasteryzacja 3D|Większość rasteryzacji 3D jest obsługiwana.|  
|Filtrowanie anizotropowe 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]próbuje użyć filtrowania anizotropowego podczas renderowania zawartości 3D. Filtrowanie anizotropowe odnosi się do poprawy jakości obrazu tekstur na powierzchniach, które są daleko i stromo pod kątem w odniesieniu do aparatu.|  
|Mapowanie 3D MIP|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]podczas renderowania zawartości 3D. Mapowanie MIP poprawia jakość renderowania tekstur, gdy tekstura zajmuje <xref:System.Windows.Controls.Viewport3D>mniejsze pole widzenia w pliku .|  
|Gradienty promieniowe|Podczas gdy obsługiwane, należy <xref:System.Windows.Media.RadialGradientBrush> unikać używania na dużych obiektów.|  
|Obliczenia oświetlenia 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wykonuje oświetlenie na wierzchołek, co oznacza, że natężenie światła musi być obliczone na każdym wierzchołku dla każdego materiału zastosowanego do siatki.|  
|Renderowanie tekstu|Renderowanie czcionek subpikseli wykorzystuje dostępne moduły cieniujące piksele na sprzęcie graficznym.|  
  
 Następujące funkcje i możliwości są przyspieszane sprzętowo tylko do renderowania warstwy 2:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Wygładzenie 3D|Wygładzanie 3D jest obsługiwane tylko w systemach operacyjnych obsługujących model sterownika ekranu systemu Windows (WDDM), takich jak Windows Vista i Windows 7.|  
  
 Następujące funkcje i możliwości **nie** są przyspieszane sprzętowo:  
  
|Funkcja|Uwagi|  
|-------------|-----------|  
|Zawartość drukowana|Cała drukowana zawartość jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowana przy użyciu potoku oprogramowania.|  
|Rasteryzowana zawartość, która używa<xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Wszelkie treści renderowane <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> przy <xref:System.Windows.Media.Imaging.RenderTargetBitmap>użyciu metody .|  
|Zawartość sąsiadująca, która używa<xref:System.Windows.Media.TileBrush>|Wszelkie kafelki zawartości, <xref:System.Windows.Media.TileBrush.TileMode%2A> w <xref:System.Windows.Media.TileBrush> której <xref:System.Windows.Media.TileMode.Tile>właściwość jest ustawiona na .|  
|Powierzchnie, które przekraczają maksymalny rozmiar tekstury sprzętu graficznego|W przypadku większości urządzeń graficznych duże powierzchnie mają rozmiar 2048x2048 lub 4096x4096 pikseli.|  
|Każda operacja, której wymaganie pamięci RAM wideo przekracza pamięć sprzętu graficznego|Użycie pamięci RAM wideo aplikacji można monitorować za pomocą narzędzia Perforator, które znajduje się w [pakiecie WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)) w zestawie Windows SDK.|  
|Okna warstwowe|Okna warstwowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwiają aplikacjom renderowanie zawartości na ekranie w niekrzcielnym oknie. W systemach operacyjnych obsługujących model sterownika ekranu systemu Windows (WDDM), takich jak Windows Vista i Windows 7, okna warstwowe są przyspieszane sprzętowo. W innych systemach, takich jak Windows XP, okna warstwowe są renderowane przez oprogramowanie bez przyspieszania sprzętowego.<br /><br /> Można włączyć okna warstwowe, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ustawiając następujące <xref:System.Windows.Window> właściwości:<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>
## <a name="other-resources"></a>Inne zasoby  
 Następujące zasoby mogą pomóc w analizie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charakterystyki wydajności aplikacji.  
  
### <a name="graphics-rendering-registry-settings"></a>Ustawienie rejestru renderowania grafiki  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia cztery ustawienia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rejestru do kontrolowania renderowania:  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Wyłącz opcję przyspieszenia sprzętowego**|Określa, czy ma być włączone przyspieszanie sprzętowe.|  
|**Maksymalna wartość multipróbki**|Określa stopień wielowymirzalania dla antyaliasing 3-W zawartości.|  
|**Wymagane ustawienie daty sterownika wideo**|Określa, czy system wyłącza akcelerację sprzętową dla sterowników wydanych przed listopadem 2004 r.|  
|**Użyj opcji rasteryzatora referencyjnego**|Określa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czy należy używać rasteryzatora referencyjnego.|  
  
 Dostęp do tych ustawień można uzyskać za pomocą dowolnego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zewnętrznego narzędzia konfiguracyjnego, które wie, jak odwoływać się do ustawień rejestru. Te ustawienia można również utworzyć lub zmodyfikować, uzyskując dostęp do wartości bezpośrednio za pomocą Edytora rejestru systemu Windows. Aby uzyskać więcej informacji, zobacz [Ustawienia rejestru renderowania grafiki](../graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### <a name="wpf-performance-profiling-tools"></a>Narzędzia do profilowania wydajności WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera zestaw narzędzi do profilowania wydajności, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określanie typów optymalizacji wydajności, które można zastosować. W poniższej tabeli wymieniono narzędzia do profilowania wydajności zawarte w narzędziu Zestawu Windows SDK, WPF Performance Suite:  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|Perforator|Służy do analizowania zachowania renderowania.|  
|Visual Profiler|Służy do profilowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korzystania z usług, takich jak układ i obsługa zdarzeń, przez elementy w drzewie wizualizacji.|  
  
 Pakiet WPF Performance Suite zapewnia bogaty, graficzny widok danych o wydajności. Aby uzyskać więcej informacji na temat narzędzi wydajności WPF, zobacz [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100)).  
  
### <a name="directx-diagnostic-tool"></a>Narzędziu diagnostycznym DirectX  
 Narzędzie diagnostyczne DirectX, Dxdiag.exe, zostało zaprojektowane, aby ułatwić rozwiązywanie problemów związanych z programem DirectX. Domyślny folder instalacyjny narzędzia diagnostycznego DirectX to:  
  
 `~\Windows\System32`  
  
 Po uruchomieniu narzędzia diagnostycznego DirectX okno główne zawiera zestaw kart umożliwiających wyświetlanie i diagnozowanie informacji związanych z funkcją DirectX. Na przykład karta **System** zawiera informacje o systemie o komputerze i określa wersję programu DirectX zainstalowaną na komputerze.  
  
 ![Screenhot: Narzędzie diagnostyczne DirectX](./media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
Okno główne narzędzia diagnostycznego DirectX  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.RenderCapability>
- <xref:System.Windows.Media.RenderOptions>
- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))
- [Ustawienia rejestru renderowania grafiki](../graphics-multimedia/graphics-rendering-registry-settings.md)
- [Animacja — porady i wskazówki](../graphics-multimedia/animation-tips-and-tricks.md)
