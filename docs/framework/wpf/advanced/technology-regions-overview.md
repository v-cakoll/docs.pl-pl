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
ms.openlocfilehash: 0b6ad222737f992da3074770fb5a2bff17860c00
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740292"
---
# <a name="technology-regions-overview"></a>Przegląd Regiony technologiczne
Jeśli w aplikacji jest używanych wiele technologii prezentacji, takich jak WPF, Win32 lub DirectX, muszą one udostępnić obszary renderowania w ramach wspólnego okna najwyższego poziomu. W tym temacie opisano problemy, które mogą mieć wpływ na prezentację i dane wejściowe aplikacji międzyoperacyjnej WPF.  
  
## <a name="regions"></a>Regions  
 W oknie najwyższego poziomu można konceptualizacji, że każdy HWND, który składa się z jednej z technologii aplikacji międzyoperacyjnej, ma własny region (nazywany także "przestrzenią powietrzną"). Każdy piksel w oknie należy do dokładnie jednego elementu HWND, który stanowi region tego elementu HWND. (Dokładnie mówiąc, istnieje więcej niż jeden region [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jeśli istnieje więcej niż jeden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] HWND, ale do celów tej dyskusji można założyć, że jest tylko jeden). Region oznacza, że wszystkie warstwy lub inne okna, które próbują renderować powyżej piksela w okresie istnienia aplikacji, muszą być częścią tej samej technologii renderowania. Podjęto próbę renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pikseli za pośrednictwem systemu Win32, aby uzyskać niepożądane wyniki i są niedozwolone w miarę możliwości za pośrednictwem interfejsów API operacji międzyoperacyjnych.  
  
### <a name="region-examples"></a>Przykłady regionów  
 Na poniższej ilustracji przedstawiono aplikację, która Miksuje Win32, DirectX i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Każda technologia używa własnego, nienakładających się zestawów pikseli i nie ma żadnych problemów z regionem.  
  
 ![Przykład aplikacji, która Miksuje Win32, DirectX i WPF.](./media/technology-regions-overview/win32-directx-windows-presentation-foundation-application.png)  
  
 Załóżmy, że ta aplikacja używa położenia wskaźnika myszy, aby utworzyć animację, która próbuje renderować wszystkie z tych trzech regionów. Niezależnie od tego, która technologia była odpowiedzialna za samą animację, ta technologia narusza region pozostałych dwóch. Na poniższej ilustracji przedstawiono próbę renderowania kółka WPF w regionie Win32.  
  
 ![Próba renderowania kółka WPF w regionie Win32.](./media/technology-regions-overview/render-windows-presentation-foundation-circle-over-win32-region.png)  
  
 Inne naruszenie polega na tym, że próbujesz użyć mieszania folii/alfa między różnymi technologiami.  Na poniższej ilustracji pole [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] narusza regiony Win32 i DirectX. Ze względu na to, że piksele w tym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polu są częściowo przezroczyste, muszą być one własnością wspólnie przez program DirectX i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], co nie jest możliwe.  Jest to inne naruszenie i nie można go skompilować.  
  
 ![Diagram przedstawiający pole WPF narusza regiony Win32 i DirectX.](./media/technology-regions-overview/windows-foundation-presentation-box-violate-win32-directx-region.png)  
  
 W poprzednich trzech przykładach użyto prostokątnych regionów, ale różne kształty są możliwe.  Na przykład region może mieć otwór. Na poniższej ilustracji przedstawiono region Win32 z prostokątnym otworem. jest to rozmiar połączonych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i regionów DirectX.  
  
 ![Diagram, który pokazuje Region Win32 z prostokątnym otworem.](./media/technology-regions-overview/win32-region-rectangular-hole.png)  
  
 Regiony mogą być również całkowicie nieprostokątne lub dowolnego kształtu describable przez HRGN Win32 (region).  
  
 ![Diagram, który pokazuje Region nieprostokątny.](./media/technology-regions-overview/nonrectangular-win32-region.png)  
  
## <a name="transparency-and-top-level-windows"></a>Przezroczystość i okna najwyższego poziomu  
 Menedżer okien w systemie Windows tylko naprawdę przetwarza HWND Win32. W związku z tym każda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> jest HWND. Właściwość HWND <xref:System.Windows.Window> musi przestrzegać ogólnych reguł dla dowolnego elementu HWND. W tym elemencie HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod może wykonywać wszelkie ogólne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługę interfejsów API. Jednak w przypadku interakcji z innymi atrybutami HWND na pulpicie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] muszą przestrzegać zasad przetwarzania i renderowania Win32.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje nieprostokątne okna przy użyciu interfejsów API Win32 — HRGNs dla okien nieprostokątnych i warstwowych okien dla alfa na piksela.  
  
 Stałe klucze alfa i kolorowe nie są obsługiwane.  Możliwości okna warstwowego Win32 różnią się w zależności od platformy.  
  
 Okna z warstwami mogą być przezroczyste w całym oknie (częściowo przezroczyste) przez określenie wartości alfa, która ma być stosowana do każdego piksela w oknie.  (System Win32 w rzeczywistości obsługuje alfa w pikselach, ale jest to bardzo trudne do użycia w praktycznych programach, ponieważ w tym trybie konieczne jest narysowanie dowolnego elementu podrzędnego HWND, łącznie z okna dialogowe i listy rozwijane).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługuje HRGNs; nie ma jednak żadnych zarządzanych interfejsów API dla tej funkcji. Możesz użyć wywołania platformy i <xref:System.Windows.Interop.HwndSource>, aby wywołać odpowiednie interfejsy API Win32. Aby uzyskać więcej informacji, zobacz [wywoływanie funkcji natywnych z kodu zarządzanego](/cpp/dotnet/calling-native-functions-from-managed-code).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] warstwowe okna mają różne możliwości w różnych systemach operacyjnych. Jest to spowodowane tym, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa DirectX do renderowania, a warstwowe okna zostały głównie zaprojektowane do renderowania GDI, a nie renderowania DirectX.  
  
- WPF obsługuje sprzętowe przyspieszone okna z warstwami.  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie obsługuje przezroczystych klawiszy kolorów, ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nie może zagwarantować dokładnego koloru, szczególnie gdy renderowanie jest przyspieszeniem sprzętowym.  
  
## <a name="see-also"></a>Zobacz także

- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przewodnik: hosting zegara WPF w Win32](walkthrough-hosting-a-wpf-clock-in-win32.md)
- [Hosting zawartości Win32 w WPF](hosting-win32-content-in-wpf.md)
