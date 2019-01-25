---
title: WPF i Direct3D9 — Współdziałanie
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9fd5cc270074a3a2845147bcad8baef8d1f8ba2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529414"
---
# <a name="wpf-and-direct3d9-interoperation"></a>WPF i Direct3D9 — Współdziałanie
Może zawierać zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF). W tym temacie opisano sposób tworzenia zawartości Direct3D9 tak, aby skutecznie współdziała również z WPF.  
  
> [!NOTE]
>  Korzystając z zawartości Direct3D9 w WPF, należy również wziąć pod uwagę wydajności. Aby uzyskać więcej informacji na temat zoptymalizować wydajność, zobacz [zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Wyświetlanie buforów  
 <xref:System.Windows.Interop.D3DImage> Klasa zarządza dwóch bufory wyświetlania, które są nazywane *buforu zapasowego* i *frontonu buforu*. Buforu zapasowego jest Twoje Direct3D9 powierzchni. Zmiany do buforu zapasowego są kopiowane do przodu w buforze frontonu po wywołaniu <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody.  
  
 Poniższa ilustracja przedstawia relację między buforu zapasowego i frontonu buforu.  
  
 ![Wyświetlania obiektu D3DImage](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Tworzenie urządzenia Direct3D9  
 Aby renderować Direct3D9 zawartości, należy utworzyć urządzenie Direct3D9. Istnieją dwa obiekty Direct3D9, które można użyć do utworzenia urządzenia `IDirect3D9` i `IDirect3D9Ex`. Umożliwia utworzenie tych obiektów `IDirect3DDevice9` i `IDirect3DDevice9Ex` urządzeń, odpowiednio.  
  
 Utwórz urządzenie, wywołując jedną z następujących metod.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista lub nowszym systemem operacyjnym, użyj `Direct3DCreate9Ex` metody za pomocą wyświetlacza, który jest skonfigurowany do używania modelu wyświetlić Driver Windows (WDDM). Użyj `Direct3DCreate9` metody w jakiejkolwiek innej platformie.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Dostępność metody Direct3DCreate9Ex  
 Ma d3d9.dll `Direct3DCreate9Ex` metody tylko w Windows Vista lub nowszym systemem operacyjnym. Jeśli bezpośrednie łączenie funkcji w systemie Windows XP, aplikacji nie można załadować. Aby określić, czy `Direct3DCreate9Ex` metoda jest obsługiwana, załadować biblioteki DLL i Wyszukaj adres procesory. Poniższy kod pokazuje, jak przetestować `Direct3DCreate9Ex` metody. Na przykład pełny kod, zobacz [instruktażu: Tworzenie zawartości Direct3D9 dla hostingu w WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Tworzenie HWND  
 Tworzenie urządzenia wymaga HWND. Ogólnie rzecz biorąc należy utworzyć fikcyjnego HWND uzyskać Direct3D9 do użycia. Poniższy przykład kodu pokazuje sposób tworzenia HWND zastępczy.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Obecne parametrów  
 Tworzenie urządzenia wymaga również `D3DPRESENT_PARAMETERS` struktury, ale tylko kilka parametrów są ważne. Te parametry są wybierane w celu zminimalizowania zużycia pamięci.  
  
 Ustaw `BackBufferHeight` i `BackBufferWidth` pól do 1. Ustawienie 0 powoduje, że ich można ustawić wymiary HWND.  
  
 Zawsze wartość `D3DCREATE_MULTITHREADED` i `D3DCREATE_FPU_PRESERVE` flagi, aby uniknąć uszkodzenia pamięci używane przez Direct3D9 i uniemożliwia zmienianie ustawień FPU Direct3D9.  
  
 Poniższy kod pokazuje, jak zainicjować `D3DPRESENT_PARAMETERS` struktury.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Tworzenie obiektu docelowego renderowania buforu zapasowego  
 Do wyświetlania zawartości Direct3D9 w <xref:System.Windows.Interop.D3DImage>, możesz utworzyć powierzchni Direct3D9 i przypisać je przez wywołanie metody <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody.  
  
### <a name="verifying-adapter-support"></a>Trwa sprawdzanie obsługi karty  
 Przed utworzeniem powierzchni, sprawdź, czy wszystkie karty obsługują powierzchni właściwości, które są wymagane. Nawet wtedy, gdy Renderuj tylko jedną kartę sieciową, okna WPF mogą być wyświetlane na karcie wszystkie w systemie. Należy zawsze wpisać kod Direct3D9, który obsługuje konfiguracji wielu kart, a ponieważ WPF może przenieść powierzchni wśród dostępnych kart sieciowych, należy sprawdzić wszystkich kart sieciowych do bezpłatnej pomocy technicznej.  
  
 W poniższym przykładzie kodu pokazano, jak można sprawdzić wszystkich kart sieciowych w systemie Direct3D9 obsługują.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Tworzenie powierzchni  
 Przed utworzeniem powierzchni, sprawdź, czy możliwości urządzenia obsługują dobrą wydajność, na docelowy system operacyjny. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Po zweryfikowaniu możliwości urządzenia, możesz utworzyć powierzchni. Poniższy przykład kodu pokazuje sposób tworzenia obiektu docelowego renderowania.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 W systemach Windows Vista i nowszych systemów operacyjnych, które są skonfigurowane do używania WDDM, możesz utworzyć teksturę docelowych renderowania i przekazywać powierzchnię poziom 0 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> metody. To podejście nie jest zalecane w Windows XP, ponieważ nie można utworzyć teksturę docelowego renderowania zamykane, a zostanie ona zredukowana wydajności.  
  
## <a name="handling-device-state"></a>Obsługa stanu urządzenia  
 <xref:System.Windows.Interop.D3DImage> Klasa zarządza dwóch bufory wyświetlania, które są nazywane *buforu zapasowego* i *frontonu buforu*. Buforu zapasowego jest Twoja powierzchni Direct3D.  Zmiany do buforu zapasowego są kopiowane do przodu w buforze frontonu po wywołaniu <xref:System.Windows.Interop.D3DImage.Unlock%2A> metody, w którym jest wyświetlana na sprzęcie. Od czasu do czasu frontonu buforu staje się niedostępny. Ten brak dostępności może być spowodowane zablokowaniem ekranu, pełnego ekranu wyłączne Direct3D aplikacji, przełączanie użytkowników lub inne działania systemu. W takiej sytuacji aplikacji środowiska WPF jest powiadamiany za pomocą obsługi <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzeń.  Jak aplikacja reaguje na przód buforu, staje się niedostępny, zależy od tego, czy WPF jest włączona w celu powrotu do renderowania oprogramowania. <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> Metoda ma przeciążenia, które przyjmuje parametr, który określa, czy WPF powraca do renderowania oprogramowania.  
  
 Gdy wywołujesz <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> przeciążenia, lub zadzwoń <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> przeciążenia z `enableSoftwareFallback` parametr `false`, system renderowania zwalnia swoje odwołanie do buforu zapasowego, gdy front buforu jest niedostępny, a nie oznacza to wyświetlane. Podczas pierwszej bufor będzie znowu dostępna, system renderowania zgłosi <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzenia w celu powiadamiania aplikacji środowiska WPF.  Można utworzyć program obsługi zdarzeń dla <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> zdarzenie, aby ponownie uruchomić renderowania ponownie, podając prawidłowy powierzchni Direct3D. Aby ponownie uruchomić renderowania, należy wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Gdy wywołujesz <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> przeciążenia z `enableSoftwareFallback` parametr `true`, system renderowania zachowuje jego odwołania do buforu zapasowego, gdy front buforu staje się niedostępny, więc nie trzeba wywoływać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> podczas frontonu Bufor jest ponownie dostępny.  
  
 Po włączeniu renderowania oprogramowania mogą wystąpić sytuacje, gdy urządzenie użytkownika staje się niedostępna, ale system renderowania przechowuje odwołania do powierzchni Direct3D. Aby sprawdzić, czy urządzenie Direct3D9 jest niedostępny, należy wywołać `TestCooperativeLevel` metody. Do sprawdzenia połączenia urządzeń Direct3D9Ex `CheckDeviceState` metody, ponieważ `TestCooperativeLevel` metoda jest przestarzała i zawsze zwraca Powodzenie. Jeśli urządzenie użytkownika stał się niedostępny, należy wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> do wydania w WPF odwołania do buforu zapasowego.  Jeśli zajdzie potrzeba zresetowania urządzenia, należy wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> z `backBuffer` parametr `null`, a następnie wywołać <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> ponownie, używając `backBuffer` ustawiony na prawidłowy powierzchni Direct3D.  
  
 Wywołaj `Reset` metodę, aby odzyskać z nieprawidłową urządzenia tylko wtedy, gdy implementacji funkcji obsługi wielu kart. W przeciwnym razie Zwolnij wszystkie interfejsy Direct3D9 i Utwórz ponownie je całkowicie. Jeśli układ karty uległ zmianie, nie są aktualizowane obiektów Direct3D9, utworzonych przed zmianą.  
  
## <a name="handling-resizing"></a>Obsługa zmiany rozmiaru  
 Jeśli <xref:System.Windows.Interop.D3DImage> jest wyświetlany w rozdzielczości niż jego macierzysty rozmiar jest skalowana zgodnie z bieżącą <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, chyba że <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> zostanie zastąpiony <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Jeśli potrzebujesz wyższej jakości, należy utworzyć nowy powierzchni, gdy kontener <xref:System.Windows.Interop.D3DImage> zmienia rozmiar.  
  
 Istnieją trzy możliwe sposoby uchwyt zmiany rozmiaru.  
  
-   Uczestniczą w systemie układ i Utwórz nowe powierzchni, po zmianie rozmiaru. Nie twórz zbyt wielu powierzchniach, ponieważ może wyczerpać lub fragmentu pamięci wideo.  
  
-   Poczekaj, aż nie przeprowadzono zdarzenie zmiany rozmiaru przez stały okres czasu, aby utworzyć nowy powierzchni.  
  
-   Utwórz <xref:System.Windows.Threading.DispatcherTimer> kontrole wymiary kontenera na sekundę.  
  
## <a name="multi-monitor-optimization"></a>Optymalizacja wielu monitorów  
 Znaczne zmniejszenie wydajności może spowodować, gdy system renderowania <xref:System.Windows.Interop.D3DImage> na inny monitor.  
  
 WDDM, tak długo, jak monitory są na tym samym wideo karty i używać `Direct3DCreate9Ex`, nie ma żadnych zmniejszenie wydajności. Jeśli monitorów znajdują się w oddzielnych kart graficznych, wydajność jest ograniczona. Windows XP wydajność, zawsze jest ograniczona.  
  
 Gdy <xref:System.Windows.Interop.D3DImage> przenosi się na inny monitor, możesz utworzyć nowe powierzchni odpowiednie karty, można przywrócić dobrą wydajność.  
  
 Aby uniknąć spadek wydajności, należy napisać kod, szczególnie w przypadku wielu monitorów. Na poniższej liście przedstawiono jeden ze sposobów pisania kodu wielu monitorów.  
  
1.  Znajdź punkt <xref:System.Windows.Interop.D3DImage> w miejsce na ekranie za pomocą `Visual.ProjectToScreen` metody.  
  
2.  Użyj `MonitorFromPoint` GDI metody do znalezienia monitor, który jest wyświetlany punkt.  
  
3.  Użyj `IDirect3D9::GetAdapterMonitor` metody do znalezienia monitor kartę Direct3D9, w której znajduje się na.  
  
4.  Jeśli karta nie jest taka sama jak karty przy użyciu buforu zapasowego, Utwórz nowy buforu zapasowego na nowy monitor i przypisz ją do <xref:System.Windows.Interop.D3DImage> buforu zapasowego.  
  
> [!NOTE]
>  Jeśli <xref:System.Windows.Interop.D3DImage> pokrywającej monitory wydajności będzie wolny, z wyjątkiem w przypadku WDDM i `IDirect3D9Ex` na tej samej karcie. Nie istnieje żaden sposób, aby zwiększyć wydajność w takiej sytuacji.  
  
 Poniższy przykład kodu pokazuje, jak znaleźć bieżącego monitora.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Zaktualizować monitor po <xref:System.Windows.Interop.D3DImage> zmiany rozmiaru lub położenia kontenera lub aktualizacji monitora przy użyciu `DispatcherTimer` , aktualizuje kilka razy na sekundę.  
  
## <a name="wpf-software-rendering"></a>Renderowanie oprogramowania WPF  
 WPF renderuje synchronicznie w wątku interfejsu użytkownika w oprogramowaniu w następujących sytuacjach.  
  
-   Drukowanie  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Gdy wystąpi jedno z tych sytuacji, system renderowania wywołuje <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metoda kopiowania buforu sprzętu do oprogramowania. Domyślna implementacja wywołuje `GetRenderTargetData` metody za pomocą usługi powierzchni. Ponieważ to wywołanie odbywa się poza wzorzec Zablokuj/Odblokuj, może nie. W tym przypadku `CopyBackBuffer` metoda zwraca `null` i obraz nie jest wyświetlany.  
  
 Można zastąpić <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> metodę wywoływać implementację podstawową i jeśli zostanie zwrócona `null`, może zwrócić symbol zastępczy <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Można też wdrożyć własną renderowania oprogramowania zamiast wywoływać implementację podstawową.  
  
> [!NOTE]
>  Jeśli WPF jest całkowicie renderowania w oprogramowaniu, <xref:System.Windows.Interop.D3DImage> nie jest wyświetlany, ponieważ WPF nie ma frontonu buforu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Przewodnik: Tworzenie zawartości Direct3D9 dla hostingu w WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Przewodnik: Hosting zawartości Direct3D9 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
