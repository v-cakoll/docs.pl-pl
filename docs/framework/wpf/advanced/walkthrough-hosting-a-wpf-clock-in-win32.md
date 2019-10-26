---
title: 'Wskazówki: Hosting zegara WPF w Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 42ed51a1a1ce59b6a3cc3319d86d3a7445403ce4
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919742"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Wskazówki: Hosting zegara WPF w Win32

Aby umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz aplikacji [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], użyj <xref:System.Windows.Interop.HwndSource>, która zapewnia Właściwość HWND, która zawiera zawartość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Najpierw utwórz <xref:System.Windows.Interop.HwndSource>, podając parametry IT podobne do okna. Następnie poinformuj <xref:System.Windows.Interop.HwndSource> o zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]j, która ma być wewnątrz niej. Na koniec można uzyskać wartość parametru HWND z <xref:System.Windows.Interop.HwndSource>. W tym instruktażu pokazano, jak utworzyć mieszany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, która ponownie implementuje okno dialogowe **Właściwości daty i godziny** systemu operacyjnego.

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Jak korzystać z tego samouczka

Ten samouczek koncentruje się na ważnych krokach tworzenia aplikacji międzyoperacyjnej. Ten samouczek jest obsługiwany przez przykładową próbkę [Międzyoperacyjną z zegarem Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale ten przykład stanowi odbicie produktu końcowego. W tym samouczku przedstawiono kroki, tak jak w przypadku rozpoczęcia pracy z istniejącym [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektem, prawdopodobnie istniejącym projektem i dodaniem hostowanego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikacji. Możesz porównać produkt końcowy z [próbką międzyoperacyjną zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Przewodnik dotyczący struktury prezentacji systemu Windows w systemie Win32 (HwndSource)

Na poniższej ilustracji przedstawiono zamierzony produkt końcowy tego samouczka:

![Zrzut ekranu przedstawiający okno dialogowe Właściwości daty i godziny.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

To okno dialogowe można utworzyć ponownie, tworząc projekt C++ Win32 w programie Visual Studio i używając edytora okien dialogowych, aby utworzyć następujące elementy:

![Okno dialogowe Właściwości daty i godziny ponownego utworzenia](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Nie musisz używać programu Visual Studio, aby używać <xref:System.Windows.Interop.HwndSource>i nie musisz używać C++ do pisania programów[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], ale jest to dość typowy sposób na to to, i dowiesz się również, jak najlepiej wykonać krokowe wyjaśnienie samouczka).

Należy wykonać pięć konkretnych podkroków, aby w oknie dialogowym umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar:

1. Zezwól projektowi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] na wywoływanie kodu zarządzanego ( **/CLR**) przez zmianę ustawień projektu w programie Visual Studio.

2. Utwórz<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]w oddzielnej bibliotece DLL.

3. Umieść ten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> w <xref:System.Windows.Interop.HwndSource>.

4. Pobierz Właściwość HWND dla tego <xref:System.Windows.Controls.Page> przy użyciu właściwości <xref:System.Windows.Interop.HwndSource.Handle%2A>.

5. Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], aby zdecydować, gdzie umieścić Właściwość HWND w większej aplikacji [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]

## <a name="clr"></a>/CLR

Pierwszym krokiem jest przekształcenie niezarządzanego projektu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] na taki, który może wywołać kod zarządzany. Używasz opcji kompilatora/CLR, która będzie łączyć się z niezbędnymi bibliotekami DLL, których chcesz użyć, i Dostosuj metodę Main do użycia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Aby umożliwić korzystanie z kodu zarządzanego w C++ projekcie: kliknij prawym przyciskiem myszy projekt win32clock i wybierz polecenie **Właściwości**. Na stronie właściwości **Ogólne** (wartość domyślna) Zmień obsługę środowiska uruchomieniowego języka wspólnego na `/clr`.

Następnie Dodaj odwołania do bibliotek DLL niezbędnych dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: 'Presentationcore. dll, platformie docelowej. dll, system. dll, 'Windowsbase. dll, UIAutomationProvider. dll i UIAutomationTypes. dll. (W poniższych instrukcjach przyjęto założenie, że system operacyjny jest zainstalowany na dysku C: dysk).

1. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** i wewnątrz tego okna dialogowego:

2. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .

3. Kliknij przycisk **Dodaj nowe odwołanie**, kliknij przycisk Przeglądaj kartę, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.

4. Powtórz dla platformie docelowej. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Powtórz dla 'Windowsbase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Powtórz dla UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Powtórz dla UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję System. dll, a następnie kliknij przycisk **OK**.

9. Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.

 Na koniec Dodaj `STAThreadAttribute` do metody `_tWinMain` do użycia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Ten atrybut zawiera informacje o środowisku uruchomieniowym języka wspólnego (CLR), który podczas inicjowania Component Object Model (COM) powinien używać jednowątkowego modelu Apartment (STA), który jest niezbędny dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).

## <a name="create-a-windows-presentation-framework-page"></a>Tworzenie strony struktury prezentacji systemu Windows

Następnie utworzysz bibliotekę DLL, która definiuje<xref:System.Windows.Controls.Page>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Często najłatwiejszym rozwiązaniem jest utworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> jako aplikacji autonomicznej, a następnie zapisanie i debugowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]j części. Po wykonaniu tych czynności projekt można przekształcić w bibliotekę DLL, klikając prawym przyciskiem myszy projekt, klikając polecenie **Właściwości**, przechodząc do aplikacji i zmieniając typ danych wyjściowych na bibliotekę klas systemu Windows.

Projekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll można następnie połączyć z projektem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (jedno rozwiązanie zawierające dwa projekty) — kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz pozycję **projekt Add\Existing**.

Aby użyć tej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll z projektu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], należy dodać odwołanie:

1. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .

2. Kliknij przycisk **Dodaj nowe odwołanie**.

3. Kliknij kartę **projekty** . Wybierz pozycję WPFClock, a następnie kliknij przycisk OK.

4. Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.

## <a name="hwndsource"></a>HwndSource

Następnie użyj <xref:System.Windows.Interop.HwndSource>, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> wyglądać jak HWND. Ten blok kodu zostanie dodany do C++ pliku:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 Jest to długi fragment kodu, który może korzystać z pewnych wyjaśnień. Pierwsza część to różne klauzule, dzięki czemu nie trzeba w pełni kwalifikować wszystkich wywołań:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Następnie zdefiniujesz funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość, umieści <xref:System.Windows.Interop.HwndSource> wokół niej i zwróci wartość HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, którego parametry są podobne do okna:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

Następnie utworzysz klasę zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], wywołując jej Konstruktor:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Następnie nawiążesz połączenie ze stroną <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 A w ostatnim wierszu Zwróć wartość HWND dla <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Pozycjonowanie parametru HWND

Teraz, gdy masz Właściwość HWND, która zawiera zegar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], musisz umieścić ten HWND w oknie dialogowym [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Jeśli wiesz tylko, gdzie umieścić Właściwość HWND, wystarczy przekazać ten rozmiar i lokalizację do zdefiniowanej wcześniej funkcji `GetHwnd`. Jednak w celu zdefiniowania okna dialogowego użyto pliku zasobów, dlatego nie należy dokładnie sprawdzić, gdzie są umieszczone dowolne z tych elementów. Możesz użyć edytora okna dialogowego programu Visual Studio, aby umieścić w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontrolkę STATYCZNą, w której ma zostać umieszczony zegar ("Wstaw zegar tutaj") i użyć, aby określić położenie zegara [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Gdy obsłużysz WM_INITDIALOG, użyj `GetDlgItem`, aby pobrać właściwość HWND dla symbolu zastępczego STATIC:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Następnie można obliczyć rozmiar i położenie tego symbolu zastępczego STATYCZNie, aby można było umieścić zegar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tym miejscu:

Prostokąt;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Następnie Ukryj symbol zastępczy STATIC:

```cpp
ShowWindow(placeholder, SW_HIDE);
```

I Utwórz w tej lokalizacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ową Właściwość zegara:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Aby zapewnić ciekawy samouczek i utworzyć rzeczywisty zegar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], musisz utworzyć kontrolkę zegar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tym momencie. Można to zrobić głównie w znaczniku, z zaledwie kilkoma programami obsługi zdarzeń w kodzie. Ponieważ ten samouczek dotyczy operacji międzyoperacyjnych, a nie informacje o projekcie kontroli, pełny kod dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar jest dostarczany w tym miejscu jako blok kodu, bez odrębnych instrukcji dotyczących tworzenia go lub co oznacza każda część. Możesz poeksperymentować z tym kodem, aby zmienić wygląd i działanie lub funkcjonalność formantu.

Oto znacznik:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

A oto towarzyszący kod w tle:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Końcowy wynik wygląda następująco:

![Okno dialogowe Właściwości daty i godziny końcowego wyniku](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Aby porównać wynik końcowy z kodem, który wygenerował ten zrzut ekranu, zobacz [przykład międzyoperacyjna](https://go.microsoft.com/fwlink/?LinkID=160051)w systemie Win32.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przykład międzyoperacyjności zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051)
