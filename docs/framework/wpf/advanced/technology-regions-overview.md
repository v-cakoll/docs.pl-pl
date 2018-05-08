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
ms.openlocfilehash: 2fef7a0f3b4e01d7ce29baeb70fbdd7ea37f2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="technology-regions-overview"></a>Przegląd Regiony technologiczne
Wiele technologii prezentacji są używane w aplikacji, takich jak WPF, Win32 lub DirectX, należy udostępnić obszarów renderowania w ramach wspólnego okna najwyższego poziomu. W tym temacie opisano problemy, które mogą mieć wpływ na prezentacji i dane wejściowe współdziałanie aplikacji WPF.  
  
## <a name="regions"></a>Regiony  
 W oknie najwyższego poziomu conceptualize który każdego HWND, która składa się z jednej z technologii współdziałanie aplikacji ma własny region (zwane również "powietrznej"). Każdego piksela okna należy dokładnie jeden HWND, który stanowi region tego HWND. (Mówiąc ściślej, jest więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] regionu, jeśli istnieje więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale dla celów tej dyskusji, można założyć, jest tylko jeden). Region oznacza, że wszystkie warstwy lub innych oknach, które będą próbować renderować powyżej piksela okres istnienia aplikacji musi być częścią tej samej technologii poziom renderowania. Próby renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pikseli za pośrednictwem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] prowadzi do niepożądane wyniki i jest niedozwolone w miarę możliwości poprzez współdziałanie [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].  
  
### <a name="region-examples"></a>Przykłady regionu  
 Na poniższej ilustracji przedstawiono aplikację, która łączy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Poszczególnych technologii używa swój własny zestaw oddzielnych, nienakładających pikseli, a nie ma żadnych problemów regionu.  
  
 ![Okno nie ma problemów powietrznej](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle01.png "MigrationInteropArchitectArticle01")  
  
 Załóżmy, że ta aplikacja używa pozycję wskaźnika myszy można utworzyć animację podejmowanych w celu renderowania na jeden z tych trzech regionach. Niezależnie od technologii był odpowiedzialny za animacja się że zasięg technologii naruszyłoby region pozostałe dwa. Na poniższej ilustracji przedstawiono próba renderowania koło WPF nad obszarem Win32.  
  
 ![Diagram międzyoperacyjności](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle02.png "MigrationInteropArchitectArticle02")  
  
 Jest inny naruszenie, Jeśli spróbujesz użyć przezroczystość/alfa mieszania różnych technologii.  Na poniższej ilustracji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] narusza pole [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] i [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] regionów. Ponieważ pikseli, w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pola są półprzezroczyste, ich musi być własnością zarówno [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], która nie jest możliwe.  Dlatego jest inny naruszenie i nie może zostać utworzony.  
  
 ![Diagram międzyoperacyjności](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle03.png "MigrationInteropArchitectArticle03")  
  
 Poprzednie trzy przykłady używane prostokątne regionów, ale są możliwe do różnych kształtów.  Na przykład region może mieć dziury. Na poniższej ilustracji pokazano [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] region prostokątne dziury to rozmiar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] regionów połączone.  
  
 ![Diagram międzyoperacyjności](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle04.png "MigrationInteropArchitectArticle04")  
  
 Regiony mogą być również całkowicie nieprostokątny lub dowolnym kształcie describable przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hrgn — (regionu).  
  
 ![Diagram międzyoperacyjności](../../../../docs/framework/wpf/advanced/media/migrationinteroparchitectarticle05.png "MigrationInteropArchitectArticle05")  
  
## <a name="transparency-and-top-level-windows"></a>Przezroczystość i okien najwyższego poziomu  
 Menedżera okien w systemie Windows tylko naprawdę przetwarza [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] parametrów hWnd. W związku z tym co [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> jest właściwością HWND. <xref:System.Windows.Window> HWND należy przestrzegać dla dowolnego HWND ogólne reguły. W tym HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu można zrobić, niezależnie od ogólnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] obsługuje. Nawet w przypadku interakcji z innych parametrów hWnd na pulpicie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy przestrzegać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przetwarzania i renderowania reguły.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje nieregularnych systemu windows przy użyciu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]— HRGNs nieregularnych systemu windows i windows warstwowego dla alpha każdego piksela.  
  
 Stałe klucze alfa i kolorów nie są obsługiwane.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Okno warstwowego możliwości zależy od platformy.  
  
 Windows warstwowego ułatwia całe okno półprzezroczyste (półprzezroczyste), określając wartość alfa do zastosowania do każdego piksela w oknie.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w rzeczywistości obsługuje każdego piksela alfa, ale jest bardzo trudne do użycia w praktyce programy, ponieważ w tym trybie będą potrzebne do rysowania wszystkich podrzędnych HWND samodzielnie, łącznie z okien dialogowych i listę rozwijaną).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje HRGNs; Istnieją jednak niezarządzanej [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dla tej funkcji. Można użyć platformy wywołania i <xref:System.Windows.Interop.HwndSource> do wywołania odpowiedniego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Aby uzyskać więcej informacji, zobacz [wywoływanie funkcji natywnych z kodu zarządzanego](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwowego systemu windows mają różne możliwości w różnych systemach operacyjnych. Jest to spowodowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] do renderowania, i warstwowego systemu windows zostały przeznaczony głównie do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] renderowania nie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderowania.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sprzęt obsługuje przyspieszony warstwie systemu windows na [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] i nowszych. Przyspieszony sprzętu warstwie systemu windows na [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] wymagana obsługa firmy [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)], więc możliwości zależy od wersji [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] na tej maszynie.  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje przezroczystość koloru kluczy, ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie może zagwarantować do renderowania kolorów zażądać, szczególnie w przypadku, gdy jest renderowanie przyspieszane sprzętowo.  
  
-   Jeśli aplikacja jest uruchomiona [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)], warstwowy windows nad [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] migotać powierzchni podczas [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] renderuje aplikacji.  (Sekwencji renderowania rzeczywistego jest to, że [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] ukrywa okno warstwowych, następnie [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] pobiera, a następnie [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] umieszcza warstwowego okna ponownie).  Z systemem innym niż[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwowego systemu windows ma również tego ograniczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Przewodnik: hosting zegara WPF w Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-clock-in-win32.md)  
 [Hosting zawartości Win32 w WPF](../../../../docs/framework/wpf/advanced/hosting-win32-content-in-wpf.md)
