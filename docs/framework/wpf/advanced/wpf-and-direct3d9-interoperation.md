---
title: "WPF i Direct3D9 — Współdziałanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1bd4d7486f546a340a4c722d140c6c7f5cee707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF i Direct3D9 — Współdziałanie
W aplikacji Windows Presentation Foundation (WPF) może zawierać Direct3D9 treść. W tym temacie opisano, jak utworzyć Direct3D9 zawartość, tak aby wydajnie współdziała również z WPF.  
  
> [!NOTE]
>  Używając Direct3D9 zawartości na platformie WPF, należy wziąć pod uwagę o wydajności. Aby uzyskać więcej informacji o tym, jak zoptymalizować wydajność, zobacz [zagadnienia dotyczące wydajności Direct3D9 i współdziałanie WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Wyświetl buforów  
 <xref:System.Windows.Interop.D3DImage> Klasa zarządza dwa bufory wyświetlania, które są nazywane *buforu zapasowego* i *front buforu*. Buforu zapasowego jest obszar Direct3D9. Zmiany buforu zapasowego są kopiowane do przodu do przodu buforu podczas wywoływania <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody.  
  
 Na poniższej ilustracji przedstawiono relację między buforu zapasowego i front buforu.  
  
 ![Wyświetlania obiektu D3DImage](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Tworzenie urządzenia Direct3D9  
 Do renderowania zawartości Direct3D9, należy utworzyć Direct3D9 urządzenia. Istnieją dwa obiekty Direct3D9, których można utworzyć urządzenia, `IDirect3D9` i `IDirect3D9Ex`. Obiekty te umożliwiają utworzenie `IDirect3DDevice9` i `IDirect3DDevice9Ex` urządzeń, odpowiednio.  
  
 Utwórz urządzenie, wywołując jedną z poniższych metod.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 W systemie Windows Vista lub nowszego systemu operacyjnego za pomocą `Direct3DCreate9Ex` metody za pomocą wyświetlania, która jest skonfigurowana do używania modelu wyświetlić sterowników systemu Windows (WDDM). Użyj `Direct3DCreate9` metody dla innych platform.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostępność metody Direct3DCreate9Ex  
 Ma d3d9.dll `Direct3DCreate9Ex` metody tylko w systemie Windows Vista lub nowszego systemu operacyjnego. Jeśli bezpośrednio połączony funkcji w systemie Windows XP, aplikacji nie powiodło się ładowanie. Aby określić, czy `Direct3DCreate9Ex` metoda jest obsługiwana, załadowanie biblioteki DLL i wyszukać adres procesem. Poniższy kod przedstawia sposób testowania dla `Direct3DCreate9Ex` metody. Na przykład pełny kod, zobacz [wskazówki: tworzenie zawartości Direct3D9 dla hostingu na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Tworzenie HWND  
 Tworzenie urządzenia wymaga HWND. Ogólnie rzecz biorąc należy utworzyć fikcyjny HWND dla Direct3D9 do użycia. Poniższy przykład kodu pokazuje, jak utworzyć HWND zastępczego.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Obecny parametrów  
 Tworzenia urządzenia wymaga również `D3DPRESENT_PARAMETERS` struktury, ale tylko kilka parametrów są ważne. Te parametry są wybrane, aby zminimalizować zużycie pamięci.  
  
 Ustaw `BackBufferHeight` i `BackBufferWidth` pól do 1. Ustawienie 0 powoduje, że ich ustawioną wymiary HWND.  
  
 Zawsze wartość `D3DCREATE_MULTITHREADED` i `D3DCREATE_FPU_PRESERVE` flagi, aby uniknąć uszkodzenia pamięci używanej przez Direct3D9 i uniemożliwić zmianę ustawień FPU Direct3D9.  
  
 Poniższy kod przedstawia sposób inicjowania `D3DPRESENT_PARAMETERS` struktury.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Tworzenie obiektu docelowego renderowania buforu zapasowego  
 Aby wyświetlić zawartość Direct3D9 <xref:System.Windows.Interop.D3DImage>, powierzchni Direct3D9 Utwórz i przypisz go przez wywołanie metody <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> — metoda.  
  
### <a name="verifying-adapter-support"></a>Weryfikowanie, czy karta pomocy technicznej.  
 Przed utworzeniem powierzchni, sprawdź, czy wszystkie karty obsługuje powierzchni właściwości, które są wymagane. Nawet w przypadku renderowania tylko do jednej karty okna WPF mogą być wyświetlane wszystkie karty w systemie. Zawsze należy zapisać Direct3D9 kod, który obsługuje konfiguracji wielu kart, a wszystkie karty, aby uzyskać pomoc, należy sprawdzić, ponieważ WPF może przenieść powierzchni spośród dostępnych kart sieciowych.  
  
 Poniższy przykład kodu pokazuje, jak można sprawdzić wszystkie karty w systemie Direct3D9 obsługują.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Tworzenie powierzchni  
 Przed utworzeniem powierzchni, sprawdź, czy możliwości urządzenia obsługują dobrą wydajność, na docelowy system operacyjny. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności Direct3D9 i współdziałanie WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Po zweryfikowaniu możliwości urządzenia, możesz utworzyć powierzchni. Poniższy przykładowy kod przedstawia sposób tworzenia obiektu docelowego renderowania.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 W systemie Windows Vista i nowszych systemów operacyjnych, które są skonfigurowane do używania WDDM, można utworzyć tekstury docelowych renderowania i przekazać powierzchnię poziom 0 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody. Ta metoda nie jest zalecane w systemie Windows XP, ponieważ nie można utworzyć tekstury docelowej blokować renderowania i zmniejszy wydajności.  
  
## <a name="handling-device-state"></a>Obsługa stanu urządzenia  
 <xref:System.Windows.Interop.D3DImage> Klasa zarządza dwa bufory wyświetlania, które są nazywane *buforu zapasowego* i *front buforu*. Buforu zapasowego jest obszar Direct3D.  Zmiany buforu zapasowego są kopiowane do przodu do przodu buforu podczas wywoływania <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody, w którym jest wyświetlana na urządzeniu. Czasami front buforu staje się niedostępna. Ten brak dostępności może być spowodowane blokady ekranu, wyłączne aplikacje Direct3D pełnego ekranu, przełączanie użytkowników lub inne działania systemu. W takim przypadku aplikacji WPF jest powiadamiany o Obsługa <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzeń.  Sposób odpowiadania przez aplikację do przodu buforu niedostępności zależy od tego, czy włączono WPF wrócił do renderowania oprogramowania. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Metoda ma przeciążenia, które przyjmuje parametr, który określa, czy WPF powraca do renderowania oprogramowania.  
  
 Podczas wywoływania <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> przeciążenia lub zadzwoń <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> przeciążenia z `enableSoftwareFallback` parametru `false`, system renderowania zwalnia jego odwołania do buforu zapasowego podczas front buforu staje się niedostępny i nie ma wyświetlane. Gdy front buforu jest ponownie dostępny, system renderowania zgłasza <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzeń do powiadamiania aplikacji WPF.  Można utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzeń, aby ponownie uruchomić renderowania ponownie, podając prawidłowy powierzchni Direct3D. Aby ponownie uruchomić renderowania, należy wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Podczas wywoływania <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> przeciążenia z `enableSoftwareFallback` ustawiona `true`, system renderowania ma zachowywać odwołanie do buforu zapasowego, gdy front buforu jest niedostępna, więc nie trzeba wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> po pierwszej Bufor jest ponownie dostępny.  
  
 Podczas renderowania oprogramowania jest włączone, mogą wystąpić sytuacje, gdy urządzenie użytkownika przestanie być dostępny, ale system renderowania ma zachowywać odwołanie do powierzchni Direct3D. Aby sprawdzić, czy urządzenie Direct3D9 jest niedostępny, należy wywołać `TestCooperativeLevel` metody. Aby sprawdzić połączenie urządzenia Direct3D9Ex `CheckDeviceState` metody, ponieważ `TestCooperativeLevel` metoda jest przestarzała i zawsze zwraca sukces. Jeśli urządzenie użytkownika stanie się niedostępny, wywołanie <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> zwolnienia odwołania w WPF do buforu zapasowego.  Jeśli zachodzi potrzeba zresetowania urządzenia, wywołanie <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> z `backBuffer` ustawiona `null`, a następnie wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ponownie, podając `backBuffer` ustawioną prawidłową powierzchni Direct3D.  
  
 Wywołanie `Reset` metody pozwoli na odzyskanie nieprawidłowe urządzenie tylko wtedy, gdy wdrożenie funkcji obsługi wielu kart. W przeciwnym razie zwolnić wszystkie interfejsy Direct3D9 i ponownie utwórz je całkowicie. Jeśli układ karty uległ zmianie, nie są aktualizowane obiektów Direct3D9 utworzonych przed zmianą.  
  
## <a name="handling-resizing"></a>Obsługa zmiana rozmiaru  
 Jeśli <xref:System.Windows.Interop.D3DImage> jest wyświetlana z rozdzielczością innego niż jego mają macierzysty rozmiar jest skalowana zgodnie z bieżącą <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, ale <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> zastępuje <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Jeśli potrzebujesz wyższej rozdzielczości, należy utworzyć nową powierzchni, gdy kontener <xref:System.Windows.Interop.D3DImage> zmienia rozmiar.  
  
 Istnieją trzy metody możliwe do obsługi zmiany rozmiaru.  
  
-   Uczestniczyć w systemie układ i Utwórz nowy obszar, gdy zmienia się rozmiar. Nie twórz zbyt wiele powierzchnie, ponieważ może wyczerpać lub fragmentu pamięci wideo.  
  
-   Poczekaj, aż na czas określony czas, aby utworzyć nowy obszar nie przeprowadzono zdarzenie zmiany rozmiaru.  
  
-   Utwórz <xref:System.Windows.Threading.DispatcherTimer> kontrole wymiarów kontenera kilka razy na sekundę.  
  
## <a name="multi-monitor-optimization"></a>Monitor wielu optymalizacji  
 Znacznie zmniejszenie wydajności mogą powstawać podczas renderowania systemu przenosi <xref:System.Windows.Interop.D3DImage> do innego monitora.  
  
 Na WDDM, tak długo, jak monitory są na tym samym wideo karty i używa `Direct3DCreate9Ex`, nie istnieje żadne zmniejszenie wydajności. Jeśli monitorów znajdują się w oddzielnych kart wideo, wydajność jest obniżona. W systemie Windows XP zawsze jest zmniejszenie wydajności.  
  
 Gdy <xref:System.Windows.Interop.D3DImage> przenosi inny monitor w odpowiedniej karty, aby przywrócić dobrą wydajność można utworzyć nowego powierzchni.  
  
 Aby uniknąć spadek wydajności, pisania kodu, w szczególności w przypadku wielu monitora. Poniższa lista przedstawia sposób pisania kodu wielu monitora.  
  
1.  Znajdowanie punktu <xref:System.Windows.Interop.D3DImage> przestrzeni ekranu z `Visual.ProjectToScreen` metody.  
  
2.  Użyj `MonitorFromPoint` GDI metody do znalezienia monitor, który wyświetla punktu.  
  
3.  Użyj `IDirect3D9::GetAdapterMonitor` metody do znalezienia która karta Direct3D9 monitor znajduje się na.  
  
4.  Jeśli karta nie jest taka sama jak karty z buforu zapasowego, Utwórz nowy buforu zapasowego na nowy monitor i przypisz je do <xref:System.Windows.Interop.D3DImage> buforu zapasowego.  
  
> [!NOTE]
>  Jeśli <xref:System.Windows.Interop.D3DImage> pokrywającej monitory wydajności będzie zajmować dużo czasu, chyba że w przypadku WDDM i `IDirect3D9Ex` na jednej karcie. Nie istnieje sposób do zwiększenia wydajności w tej sytuacji.  
  
 Poniższy przykład kodu pokazuje, jak można znaleźć bieżącego monitora.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Zaktualizuj monitor po <xref:System.Windows.Interop.D3DImage> zmiany rozmiaru lub położenia kontenera lub aktualizacji monitora przy użyciu `DispatcherTimer` który aktualizuje kilka razy na sekundę.  
  
## <a name="wpf-software-rendering"></a>Renderowanie oprogramowania WPF  
 WPF synchronicznie renderuje w wątku interfejsu użytkownika w oprogramowaniu w następujących sytuacjach.  
  
-   Drukowanie  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Gdy wystąpi jedno z tych sytuacji, wywołań systemowych renderowania <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metody, aby skopiować buforu sprzętu do oprogramowania. Domyślna implementacja wywołuje `GetRenderTargetData` metody z obszar. Ponieważ to wywołanie odbywa się poza wzorcem Zablokuj/Odblokuj, może nie. W takim przypadku `CopyBackBuffer` metoda zwraca `null` i nie jest wyświetlany żadnego obrazu.  
  
 Można zastąpić <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metody wywoływać implementację podstawową i jeśli zwróci ona `null`, może zwrócić symbol zastępczy <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Można też wdrożyć własne renderowania oprogramowania zamiast kontaktować się z podstawowej implementacji.  
  
> [!NOTE]
>  Jeśli całkowicie renderowania WPF w oprogramowaniu, <xref:System.Windows.Interop.D3DImage> nie jest wyświetlany, ponieważ WPF nie ma front buforu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.D3DImage>  
 [Zagadnienia dotyczące wydajności Direct3D9 i współdziałanie z WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Wskazówki: Tworzenie zawartości Direct3D9 hostingu na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Wskazówki: Obsługa Direct3D9 zawartości na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
