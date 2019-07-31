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
ms.openlocfilehash: a169064052a567694b1cbd1e2f8ac2f00b047a68
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671833"
---
# <a name="technology-regions-overview"></a>Przegląd Regiony technologiczne
Jeśli w aplikacji jest używanych wiele technologii prezentacji, takich jak WPF, Win32 lub DirectX, muszą one udostępnić obszary renderowania w ramach wspólnego okna najwyższego poziomu. W tym temacie opisano problemy, które mogą mieć wpływ na prezentację i dane wejściowe aplikacji międzyoperacyjnej WPF.  
  
## <a name="regions"></a>Regions  
 W oknie najwyższego poziomu można konceptualizacji, że każdy HWND, który składa się z jednej z technologii aplikacji międzyoperacyjnej, ma własny region (nazywany także "przestrzenią powietrzną"). Każdy piksel w oknie należy do dokładnie jednego elementu HWND, który stanowi region tego elementu HWND. (Dokładnie mówiąc, istnieje więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] region, jeśli istnieje więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale na potrzeby tej dyskusji można założyć, że jest tylko jeden). Region oznacza, że wszystkie warstwy lub inne okna, które próbują renderować powyżej piksela w okresie istnienia aplikacji, muszą być częścią tej samej technologii renderowania. Podjęto próbę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderowania pikseli [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przez potencjalną liczbę niepożądanych wyników i jest niedozwolony przez interfejsy API międzyoperacyjności.  
  
### <a name="region-examples"></a>Przykłady regionów  
 Na poniższej ilustracji przedstawiono aplikację, która Miksuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], DirectX i. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Każda technologia używa własnego, nienakładających się zestawów pikseli i nie ma żadnych problemów z regionem.  
  
 ![Przykład aplikacji, która Miksuje Win32, DirectX i WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Załóżmy, że ta aplikacja używa położenia wskaźnika myszy, aby utworzyć animację, która próbuje renderować wszystkie z tych trzech regionów. Niezależnie od tego, która technologia była odpowiedzialna za samą animację, ta technologia narusza region pozostałych dwóch. Na poniższej ilustracji przedstawiono próbę renderowania kółka WPF w regionie Win32.  
  
 ![Próba renderowania kółka WPF w regionie Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Inne naruszenie polega na tym, że próbujesz użyć mieszania folii/alfa między różnymi technologiami.  Na poniższej ilustracji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pole narusza [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] regiony i program DirectX. Ze względu na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to, że piksele w tym polu są częściowo przezroczyste, muszą być wspólne przez program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]DirectX i, co nie jest możliwe.  Jest to inne naruszenie i nie można go skompilować.  
  
 ![Diagram przedstawiający pole WPF narusza regiony Win32 i DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 W poprzednich trzech przykładach użyto prostokątnych regionów, ale różne kształty są możliwe.  Na przykład region może mieć otwór. Na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] region z prostokątnym otworem, czyli rozmiar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] połączonych regionów i programu DirectX.  
  
 ![Diagram, który pokazuje Region Win32 z prostokątnym otworem.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Regiony mogą być również całkowicie nieprostokątne lub dowolnego kształtu describable przez [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HRGN (region).  
  
 ![Diagram, który pokazuje Region nieprostokątny.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Przezroczystość i okna najwyższego poziomu  
 Menedżer okien w systemie Windows tylko naprawdę przetwarza [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] HWND. W związku z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tym, co <xref:System.Windows.Window> jest HWND. <xref:System.Windows.Window> Właściwość HWND musi przestrzegać ogólnych reguł dla dowolnego elementu HWND. W tym elemencie HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod może wykonywać wszelkie ogólne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługa interfejsów API. Jednak w przypadku interakcji z innymi atrybutami HWND na pulpicie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] należy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] przestrzegać zasad przetwarzania i renderowania.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje okna nieprostokątne za pomocą [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] interfejsów API — HRGNs dla okien nieprostokątnych i warstwowych okien dla alfa w pikselach.  
  
 Stałe klucze alfa i kolorowe nie są obsługiwane.  [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]funkcje okna warstwowego różnią się w zależności od platformy.  
  
 Okna z warstwami mogą być przezroczyste w całym oknie (częściowo przezroczyste) przez określenie wartości alfa, która ma być stosowana do każdego piksela w oknie.  ([!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w rzeczywistości obsługuje alfa w pikselach, ale jest to bardzo trudne do użycia w praktycznych programach, ponieważ w tym trybie należy samodzielnie narysować dowolny podrzędny element HWND, w tym okna dialogowe i listy rozwijane).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje HRGNs; nie ma jednak żadnych zarządzanych interfejsów API dla tej funkcji. Można użyć wywołania platformy i <xref:System.Windows.Interop.HwndSource> wywołać odpowiednie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] interfejsy API. Aby uzyskać więcej informacji, zobacz [wywoływanie funkcji natywnych z kodu zarządzanego](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]okna z warstwami mają różne możliwości w różnych systemach operacyjnych. Jest to spowodowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tym, że program używa DirectX do renderowania, a warstwowe okna zostały głównie zaprojektowane do renderowania GDI, a nie renderowania DirectX.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje przyspieszane sprzętowo okna w [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] systemie i nowszych wersjach. Przyspieszane sprzętowo okna [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)] z warstwami są obsługiwane przez program Microsoft DirectX, dzięki czemu możliwości będą zależeć od wersji programu Microsoft DirectX na tym komputerze.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Program nie obsługuje przezroczystych kluczy kolorów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ponieważ nie może gwarantować dokładnego koloru, szczególnie gdy renderowanie jest przyspieszane sprzętowo.  
  
- Jeśli aplikacja jest uruchomiona w [!INCLUDE[TLA2#tla_winxp](../../../../includes/tla2sharptla-winxp-md.md)]systemie, okna warstwowe na wierzchu programu DirectX są migotane, gdy aplikacja DirectX jest renderowana.  (Rzeczywista sekwencja renderowania polega na tym, że system Microsoft Windows GDI (GDI) ukrywa okno warstwowe, następnie program DirectX rysuje, a następnie system Microsoft Windows GDI (GDI) umieszcza ponownie okno warstwowe).  W przypadku[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okien nienależących do warstwowego obowiązuje również ograniczenie.  
  
## <a name="see-also"></a>Zobacz także

- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przewodnik: Hostowanie zegara WPF w Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hosting zawartości Win32 w WPF](hosting-win32-content-in-wpf.md)
