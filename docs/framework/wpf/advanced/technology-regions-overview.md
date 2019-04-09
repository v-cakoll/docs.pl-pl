---
title: Przegląd Regiony technologiczne
ms.date: 03/30/2017
helpviewer_keywords:
- window regions [WPF]
- Win32 code [WPF], WPF interoperation
- Win32 code [WPF], airspace
- airspace [WPF]
- interoperability [WPF], airspace
- Win32 code [WPF], window regions
ms.assetid: b7cc350f-b9e2-48b1-be14-60f3d853222e
ms.openlocfilehash: 911ba1474677f26a773ff63e958ba0ceedbefd0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100980"
---
# <a name="technology-regions-overview"></a>Przegląd Regiony technologiczne
Wiele technologii prezentacji są używane w aplikacji, takich jak WPF, Win32 lub DirectX, należy udostępnić obszary renderowania w typowych okien najwyższego poziomu. W tym temacie opisano problemy, które mogą mieć wpływ na prezentacji i danych wejściowych dla aplikacji współdziałanie WPF.  
  
## <a name="regions"></a>Regiony  
 W tym oknie najwyższego poziomu wyobrażenie który każdego HWND, który składa się z jednej z technologii współdziałanie aplikacji ma swój własny region (zwane również "powietrznej"). Każdy piksel w oknie należy dokładnie jeden HWND, który stanowi region tego HWND. (Ściśle rzecz ujmując, ma więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] regionu, jeśli istnieje więcej niż jedna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale dla celów tej dyskusji, można założyć, jest tylko jedna). Region oznacza, że wszystkie warstwy lub inne okna, które próbują renderowania powyżej tego piksel w okresie istnienia aplikacji musi być częścią tej samej technologii poziom renderowania. Próby zrenderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pikseli za pośrednictwem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] prowadzi do niepożądanych wyników i jest niedozwolone, jak to możliwe za pomocą międzyoperacyjności [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Przykłady regionu  
 Na poniższej ilustracji przedstawiono aplikację, która jest napisana [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Każda technologia używa swój własny zestaw oddzielnych, nienakładających pikseli, a nie ma żadnych problemów regionu.  
  
 ![Okno które nie ma problemów powietrznej](./media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 Załóżmy, że ta aplikacja używa pozycji wskaźnika myszy do tworzenia animacji podejmowanych w celu renderowania za pośrednictwem dowolnego z tych trzech regionach. Niezależnie od tego, która technologia była odpowiedzialna za animacji, sam technologia ta naruszyłoby region pozostałe dwa. Poniższa ilustracja przedstawia próby renderowania okrąg WPF nad obszarem Win32.  
  
 ![Diagram międzyoperacyjności](./media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 Naruszenie innego jest, Jeśli spróbujesz użyć przezroczystości/alfa mieszania między różnych technologii.  Na poniższej ilustracji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] narusza pole [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] regionów. Ponieważ pikseli, w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pola są półprzezroczyste, będą musieli się być własnością zarówno [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], który nie jest możliwe.  Dlatego jest to innego naruszenia i nie może zostać utworzony.  
  
 ![Diagram międzyoperacyjności](./media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 Poprzednie trzy przykłady używane prostokątnych regionów, ale możliwe są różne kształty.  Na przykład region może mieć dziury. Poniższa ilustracja przedstawia [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regionie prostokątny dziury to rozmiar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] regionów, w połączeniu.  
  
 ![Diagram międzyoperacyjności](./media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 Regiony można też całkowicie nieprostokątne lub dowolnym kształcie describable przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hrgn — (region).  
  
 ![Diagram międzyoperacyjności](./media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## <a name="transparency-and-top-level-windows"></a>Przejrzystość i Windows najwyższego poziomu  
 Menedżer okien w Windows tylko naprawdę przetwarza [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] parametrów hWnd. W związku z tym co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> jest właściwością HWND. <xref:System.Windows.Window> HWND należy przestrzegać zasad ogólnych dla dowolnego HWND. W tym HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu można zrobić, niezależnie od ogólnej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pomocy technicznej. Ale w przypadku interakcji z innych parametrów hWnd na komputerze stacjonarnym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy przestrzegać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przetwarzaniem i renderowaniem reguły.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje okien przy użyciu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— HRGNs okien i okien warstwowej dla alpha każdego piksela.  
  
 Stałe klucze kolor i alpha nie są obsługiwane.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Funkcje okna warstwowej zależą od platformy.  
  
 Warstwowej windows ułatwia całe okno półprzezroczyste (półprzezroczyste), określając wartość alfa do zastosowania do każdego piksela, w oknie.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w rzeczywistości obsługuje każdego piksela alfa, ale jest bardzo trudne do użycia w programach praktycznych, ponieważ w tym trybie będą potrzebne do rysowania wszystkich podrzędnych HWND samodzielnie, łącznie z oknami dialogowymi i list rozwijanych).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje HRGNs; Istnieją jednak niezarządzanej [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dla tej funkcji. Możesz użyć platformy wywołania i <xref:System.Windows.Interop.HwndSource> do wywołania odpowiedniego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Aby uzyskać więcej informacji, zobacz [podczas wywoływania funkcji natywnych z kodu zarządzanego](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna warstwowej mają różne możliwości w różnych systemach operacyjnych. Jest to spowodowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] do renderowania, a windows warstwowej przede wszystkim zostały zaprojektowane dla [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] renderowania nie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderowania.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sprzęt obsługuje przyspieszoną warstwie systemu windows na [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] i nowszych. Sprzęt accelerated warstwie systemu windows na [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] potrzebujesz pomocy technicznej firmy [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)], dzięki czemu możliwości będą zależeć od wersji [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] na tym komputerze.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje przezroczystość koloru kluczy, ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie może zagwarantować do renderowania dokładny kolor zażądano, szczególnie w przypadku renderowanie przyspieszane sprzętowo.  
  
-   Jeśli aplikacja jest uruchomiona [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], warstwie systemu windows, w górnej części [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] powierzchnie zmieniał kolor po [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderuje aplikacji.  (Sekwencji rzeczywiste renderowania jest to, że [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] ukrywa okno warstwowej, następnie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] rysuje, a następnie [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] przywraca okna warstwowej).  Non -[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwowej windows również ma tego ograniczenia.  
  
## <a name="see-also"></a>Zobacz także

- [WPF i Win32 — Współdziałanie](wpf-and-win32-interoperation.md)
- [Przewodnik: hostowanie zegara WPF w Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hosting zawartości Win32 w WPF](hosting-win32-content-in-wpf.md)
