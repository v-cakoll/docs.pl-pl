---
title: WPF i Direct3D9 międzyoperacyjność
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9ec83c48052e1ef29bb91a6b40b7c76f671bb99f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735181"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF i Direct3D9 — Współdziałanie
Możesz dołączyć zawartość Direct3D9 do aplikacji Windows Presentation Foundation (WPF). W tym temacie opisano sposób tworzenia zawartości Direct3D9, tak aby efektywnie współpracowała z WPF.  
  
> [!NOTE]
> W przypadku korzystania z zawartości Direct3D9 w programie WPF należy również pamiętać o wydajności. Aby uzyskać więcej informacji na temat optymalizacji pod kątem wydajności, zobacz [zagadnienia dotyczące wydajności dla współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Bufory wyświetlania  
 Klasa <xref:System.Windows.Interop.D3DImage> zarządza dwoma buforami wyświetlania, które są nazywane *buforem zapasowym* i *buforem przednim*. Bufor zapasowy jest powierzchnią Direct3D9ą. Zmiany buforu zapasowego są kopiowane do przodu do buforu przedniego podczas wywoływania metody <xref:System.Windows.Interop.D3DImage.Unlock%2A>.  
  
 Na poniższej ilustracji przedstawiono relacje między buforem zaplecza i buforem przednim.  
  
 ![Bufory wyświetlania D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Tworzenie urządzenia Direct3D9  
 Aby renderować zawartość Direct3D9, należy utworzyć urządzenie Direct3D9. Istnieją dwa obiekty Direct3D9, których można użyć do utworzenia urządzenia, `IDirect3D9` i `IDirect3D9Ex`. Te obiekty służą do tworzenia odpowiednio `IDirect3DDevice9` i `IDirect3DDevice9Ex` urządzeń.  
  
 Utwórz urządzenie, wywołując jedną z następujących metod.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 W systemie operacyjnym Windows Vista lub nowszym Użyj metody `Direct3DCreate9Ex` z ekranem skonfigurowanym do korzystania z modelu Windows Display Driver Model (WDDM). Użyj metody `Direct3DCreate9` na dowolnej innej platformie.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostępność metody Direct3DCreate9Ex  
 D3d9. dll ma metodę `Direct3DCreate9Ex` tylko w systemie operacyjnym Windows Vista lub nowszym. Jeśli funkcja jest bezpośrednio łączona w systemie Windows XP, nie można załadować aplikacji. Aby określić, czy metoda `Direct3DCreate9Ex` jest obsługiwana, Załaduj bibliotekę DLL i Wyszukaj adres procesu. Poniższy kod przedstawia sposób testowania dla metody `Direct3DCreate9Ex`. Aby uzyskać pełny przykład kodu, zobacz [Przewodnik: Tworzenie zawartości Direct3D9 do hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Tworzenie HWND  
 Tworzenie urządzenia wymaga elementu HWND. Ogólnie rzecz biorąc tworzysz fikcyjny HWND dla Direct3D9 do użycia. Poniższy przykład kodu pokazuje, jak utworzyć fikcyjny HWND.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Parametry obecne  
 Utworzenie urządzenia wymaga również struktury `D3DPRESENT_PARAMETERS`, ale tylko kilka parametrów jest ważnych. Te parametry są wybierane w celu zminimalizowania rozmiaru pamięci.  
  
 Ustaw `BackBufferHeight` i `BackBufferWidth` pól na 1. Ustawienie wartości 0 powoduje, że są one ustawione na wymiary HWND.  
  
 Zawsze ustawiaj flagi `D3DCREATE_MULTITHREADED` i `D3DCREATE_FPU_PRESERVE`, aby zapobiec uszkodzeniu pamięci używanej przez program Direct3D9 i uniemożliwić Direct3D9 zmian ustawień FPU.  
  
 Poniższy kod pokazuje, jak zainicjować strukturę `D3DPRESENT_PARAMETERS`.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Tworzenie celu renderowania buforu zapasowego  
 Aby wyświetlić zawartość Direct3D9 w <xref:System.Windows.Interop.D3DImage>, utworzysz powierzchnię Direct3D9 i przypiszesz ją, wywołując metodę <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
### <a name="verifying-adapter-support"></a>Weryfikowanie obsługi kart  
 Przed utworzeniem powierzchni upewnij się, że wszystkie karty obsługują wymagane właściwości powierzchni. Nawet jeśli przerenderuje tylko jedną kartę, okno WPF może być wyświetlane na dowolnej karcie w systemie. Należy zawsze pisać kod Direct3D9, który obsługuje konfiguracje z wieloma kartami, i należy sprawdzić wszystkie karty, aby uzyskać pomoc techniczną, ponieważ WPF może przenosić powierzchnię między dostępnymi kartami.  
  
 Poniższy przykład kodu pokazuje, jak sprawdzić wszystkie karty w systemie w celu obsługi Direct3D9.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Tworzenie powierzchni  
 Przed utworzeniem powierzchni upewnij się, że możliwości urządzenia obsługują dobrą wydajność w docelowym systemie operacyjnym. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności dla współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Po zweryfikowaniu możliwości urządzenia można utworzyć powierzchnię. Poniższy przykład kodu pokazuje, jak utworzyć obiekt docelowy renderowania.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>Model  
 W systemie Windows Vista i nowszych systemach operacyjnych skonfigurowanych do korzystania z WDDM można utworzyć teksturę docelową renderowania i przekazać powierzchnię poziomu 0 do metody <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>. Ta metoda nie jest zalecana w systemie Windows XP, ponieważ nie można utworzyć wyzamykanej tekstury docelowej renderowania i wydajność zostanie zmniejszona.  
  
## <a name="handling-device-state"></a>Obsługa stanu urządzenia  
 Klasa <xref:System.Windows.Interop.D3DImage> zarządza dwoma buforami wyświetlania, które są nazywane *buforem zapasowym* i *buforem przednim*. Bufor zapasowy jest powierzchnią Direct3D.  Zmiany buforu zapasowego są kopiowane do przodu do buforu przedniego podczas wywoływania metody <xref:System.Windows.Interop.D3DImage.Unlock%2A>, gdzie jest ona wyświetlana na sprzęcie. Czasami bufor przedni jest niedostępny. Brak dostępności może być spowodowany blokowaniem ekranu, wyłącznym aplikacjom Direct3D w trybie pełnoekranowym, przełączaniem użytkownika lub innymi działaniami systemowymi. W takim przypadku aplikacja WPF zostanie powiadomiona o obsłudze zdarzenia <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>.  Sposób, w jaki aplikacja reaguje na przedni bufor staje się niedostępny, zależy od tego, czy WPF jest włączona, aby wrócić do renderowania oprogramowania. Metoda <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ma Przeciążenie, które przyjmuje parametr, który określa, czy WPF powraca do renderowania oprogramowania.  
  
 W przypadku wywołania przeciążenia <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> lub wywołania przeciążenia <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> z parametrem `enableSoftwareFallback` ustawionym na `false`, system renderowania zwalnia jego odwołanie do buforu zapasowego, gdy bufor przedni będzie niedostępny i nic nie zostanie wyświetlone. Po ponownym udostępnieniu buforu przedniego system renderowania zgłasza zdarzenie <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>, aby powiadomić aplikację WPF.  Można utworzyć procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>, aby ponownie uruchomić renderowanie z prawidłową powierzchnią Direct3D. Aby ponownie uruchomić Render, należy wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 W przypadku wywołania przeciążenia <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> z parametrem `enableSoftwareFallback` ustawionym na `true`, system renderowania zachowuje swoje odwołanie do buforu zapasowego, gdy bufor przedni jest niedostępny, więc nie ma potrzeby wywoływania <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>, gdy bufor przedni jest dostępny ponownie.  
  
 Po włączeniu renderowania oprogramowania mogą wystąpić sytuacje, w których urządzenie użytkownika stał się niedostępne, ale system renderowania zachowuje odwołanie do powierzchni Direct3D. Aby sprawdzić, czy urządzenie Direct3D9 jest niedostępne, wywołaj metodę `TestCooperativeLevel`. Aby sprawdzić, czy urządzenia Direct3D9Ex wywołują metodę `CheckDeviceState`, ponieważ metoda `TestCooperativeLevel` jest przestarzała i zawsze zwraca sukces. Jeśli urządzenie użytkownika stanie się niedostępne, wywołaj <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>, aby zwolnić odwołanie WPF do buforu zaplecza.  Jeśli musisz zresetować urządzenie, wywołaj <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> z parametrem `backBuffer` ustawionym na `null`, a następnie Wywołaj <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ponownie z `backBuffer` ustawionym na prawidłową powierzchnię Direct3D.  
  
 Wywołaj metodę `Reset`, aby przeprowadzić odzyskiwanie z nieprawidłowego urządzenia tylko w przypadku implementacji obsługi wieloadapterowej. W przeciwnym razie Zwolnij wszystkie interfejsy Direct3D9 i utwórz je ponownie. Jeśli układ karty został zmieniony, Direct3D9 obiektów utworzonych przed zmianą nie zostaną zaktualizowane.  
  
## <a name="handling-resizing"></a>Obsługa zmiany rozmiarów  
 Jeśli <xref:System.Windows.Interop.D3DImage> jest wyświetlana w rozdzielczości innej niż jej rozmiar macierzysty, jest skalowana zgodnie z bieżącą <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, z wyjątkiem tego, że <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> jest zastępowany dla <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Jeśli potrzebujesz większej wierności, musisz utworzyć nową powierzchnię, gdy rozmiar <xref:System.Windows.Interop.D3DImage> zmienia się.  
  
 Istnieją trzy możliwe podejścia do obsługi zmiany rozmiarów.  
  
- Weź udział w systemie układu i Utwórz nową powierzchnię po zmianie rozmiaru. Nie należy tworzyć zbyt wielu powierzchni, ponieważ może być wykorzystana lub fragmentacja pamięci wideo.  
  
- Poczekaj, aż nie wystąpiło zdarzenie zmiany rozmiaru w ustalonym czasie, aby utworzyć nową powierzchnię.  
  
- Utwórz <xref:System.Windows.Threading.DispatcherTimer>, który sprawdza wymiary kontenera kilka razy na sekundę.  
  
## <a name="multi-monitor-optimization"></a>Optymalizacja z obsługą kilku monitorów  
 Znacznie zmniejszona wydajność może wynikać z przesunięcia przez system renderowania <xref:System.Windows.Interop.D3DImage> do innego monitora.  
  
 W systemach WDDM, pod warunkiem, że monitory znajdują się na tej samej karcie wideo i używasz `Direct3DCreate9Ex`, nie ma obniżenia wydajności. Jeśli monitory znajdują się na oddzielnych kartach wideo, wydajność jest ograniczona. W systemie Windows XP wydajność jest zawsze ograniczona.  
  
 Gdy <xref:System.Windows.Interop.D3DImage> przechodzi do innego monitora, można utworzyć nową powierzchnię na odpowiedniej karcie w celu przywrócenia dobrej wydajności.  
  
 Aby uniknąć zmniejszenia wydajności, napisz kod przeznaczony dla przypadku wielokrotnego monitorowania. Na poniższej liście przedstawiono jeden ze sposobów pisania kodu z obsługą wielu monitorów.  
  
1. Znajdź punkt <xref:System.Windows.Interop.D3DImage> w obszarze ekranu za pomocą metody `Visual.ProjectToScreen`.  
  
2. Użyj metody `MonitorFromPoint` GDI, aby znaleźć monitor, który wyświetla punkt.  
  
3. Użyj metody `IDirect3D9::GetAdapterMonitor`, aby znaleźć kartę Direct3D9, w której znajduje się monitor.  
  
4. Jeśli karta nie jest taka sama jak karta z buforem zaplecza, Utwórz nowy bufor zapasowy na nowym monitorze i przypisz go do buforu zapasowego <xref:System.Windows.Interop.D3DImage>.  
  
> [!NOTE]
> Jeśli monitoruje <xref:System.Windows.Interop.D3DImage> międzystrefowe, wydajność będzie niska, chyba że w przypadku WDDM i `IDirect3D9Ex` na tej samej karcie. W tej sytuacji nie ma możliwości poprawy wydajności.  
  
 Poniższy przykład kodu pokazuje, jak znaleźć bieżący monitor.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Zaktualizuj monitor po zmianie rozmiaru lub położenia kontenera <xref:System.Windows.Interop.D3DImage> lub zaktualizuj monitor przy użyciu `DispatcherTimer`, który aktualizuje kilka razy na sekundę.  
  
## <a name="wpf-software-rendering"></a>Renderowanie oprogramowania WPF  
 Funkcja WPF renderuje synchronicznie w wątku interfejsu użytkownika w oprogramowaniu w następujących sytuacjach.  
  
- Drukowanie  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Gdy wystąpi jedna z tych sytuacji, system renderowania wywołuje metodę <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>, aby skopiować bufor sprzętowy do oprogramowania. Domyślna implementacja wywołuje metodę `GetRenderTargetData` z powierzchnią. Ponieważ to wywołanie występuje poza wzorcem blokady/odblokowywania, może się nie powieść. W tym przypadku Metoda `CopyBackBuffer` zwraca `null` i nie jest wyświetlany obraz.  
  
 Można zastąpić metodę <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>, wywołać implementację podstawową i jeśli zwróci `null`, można zwrócić <xref:System.Windows.Media.Imaging.BitmapSource>symbolu zastępczego.  
  
 Możesz również zaimplementować własne renderowanie oprogramowania zamiast wywoływania podstawowej implementacji.  
  
> [!NOTE]
> Jeśli WPF jest w pełni renderowana w oprogramowaniu, <xref:System.Windows.Interop.D3DImage> nie jest wyświetlany, ponieważ WPF nie ma buforu frontonu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Przewodnik: tworzenie zawartości Direct3D9 dla hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Przewodnik: hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
