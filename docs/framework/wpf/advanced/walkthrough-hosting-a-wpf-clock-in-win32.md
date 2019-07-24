---
title: 'Przewodnik: hostowanie zegara WPF w Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400474"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Przewodnik: hostowanie zegara WPF w Win32

Aby umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, należy <xref:System.Windows.Interop.HwndSource>użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , która zapewnia Właściwość HWND, która zawiera zawartość. Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, podając parametry IT podobne do okna. Następnie poinformuj <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o zawartości, którą chcesz umieścić w niej. Na koniec można uzyskać wartość HWND z <xref:System.Windows.Interop.HwndSource>. W tym instruktażu przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mieszanej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] wewnątrz aplikacji, która ponownie implementuje okno dialogowe **Właściwości daty i godziny** systemu operacyjnego.

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [WPF i Win32](wpf-and-win32-interoperation.md)— współdziałanie.

## <a name="how-to-use-this-tutorial"></a>Jak korzystać z tego samouczka

Ten samouczek koncentruje się na ważnych krokach tworzenia aplikacji międzyoperacyjnej. Ten samouczek jest obsługiwany przez przykładową próbkę Międzyoperacyjną z [zegarem Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale ten przykład stanowi odbicie produktu końcowego. W tym samouczku przedstawiono kroki, tak jak w przypadku rozpoczęcia pracy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z istniejącym projektem, prawdopodobnie istniejącym projektem i dodaniem hostowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Możesz porównać produkt końcowy z próbką [międzyoperacyjną zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Przewodnik dotyczący struktury prezentacji systemu Windows w systemie Win32 (HwndSource)

Na poniższej ilustracji przedstawiono zamierzony produkt końcowy tego samouczka:

![Zrzut ekranu przedstawiający okno dialogowe Właściwości daty i godziny.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

To okno dialogowe można utworzyć ponownie, tworząc projekt C++ Win32 w programie Visual Studio i używając edytora okien dialogowych, aby utworzyć następujące elementy:

![Okno dialogowe Właściwości daty i godziny ponownego utworzenia](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

( [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] Nie musisz <xref:System.Windows.Interop.HwndSource>używać programu, aby korzystać z programu, a nie musisz używać C++ do pisania [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programów, ale jest to dość typowy sposób na to, i dowiesz się, jak najlepiej wykonać krokowe wyjaśnienie samouczka).

Aby włączyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar do okna dialogowego, należy wykonać pięć konkretnych podkroków:

1. Zezwól, aby [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] projektmógłwywołaćkodzarządzany(/CLR)przezzmianęustawieńprojektu[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w.

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Utwórzwoddzielnym<xref:System.Windows.Controls.Page> pliku dll.

3. Umieść ten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> element<xref:System.Windows.Interop.HwndSource>wewnątrz.

4. Pobierz <xref:System.Windows.Interop.HwndSource.Handle%2A> Właściwość HWND dla tego <xref:System.Windows.Controls.Page> elementu przy użyciu właściwości.

5. Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , aby zdecydować, gdzie umieścić Właściwość HWND w większej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji

## <a name="clr"></a>/CLR

Pierwszym krokiem jest przekształcenie tego niezarządzanego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu w taki, który może wywołać kod zarządzany. Używasz opcji kompilatora/CLR, która będzie łączyć się z niezbędnymi bibliotekami DLL, których chcesz użyć, i Dostosuj metodę Main do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]z.

Aby umożliwić korzystanie z kodu zarządzanego w C++ projekcie: Kliknij prawym przyciskiem myszy projekt win32clock i wybierz polecenie **Właściwości**. Na stronie właściwości **Ogólne** (domyślnie) Zmień obsługę środowiska uruchomieniowego języka wspólnego na `/clr`.

Następnie Dodaj odwołania do bibliotek DLL niezbędnych dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: 'Presentationcore. dll, platformie docelowej. dll, system. dll, 'Windowsbase. dll, UIAutomationProvider. dll i UIAutomationTypes. dll. (W poniższych instrukcjach przyjęto założenie, że system operacyjny jest zainstalowany na dysku C: dysk).

1. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** i wewnątrz tego okna dialogowego:

2. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .

3. Kliknij przycisk **Dodaj nowe odwołanie**, kliknij przycisk Przeglądaj kartę, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.

4. Powtórz dla platformie docelowej. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Powtórz dla UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Powtórz dla UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję System. dll, a następnie kliknij przycisk **OK**.

9. Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.

 `STAThreadAttribute` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Na koniec Dodaj do `_tWinMain` metody do użycia z:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Ten atrybut zawiera informacje o środowisku uruchomieniowym języka wspólnego (CLR), [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]który podczas jego inicjowania powinien używać jednowątkowego modelu Apartment (STA), który jest niezbędny [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i).

## <a name="create-a-windows-presentation-framework-page"></a>Tworzenie strony struktury prezentacji systemu Windows

Następnie utworzysz bibliotekę DLL, która definiuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Page> Często najłatwiej jest utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> aplikację jako autonomiczną i napisać i debugować tę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] część. Po wykonaniu tych czynności projekt można przekształcić w bibliotekę DLL, klikając prawym przyciskiem myszy projekt, klikając polecenie **Właściwości**, przechodząc do aplikacji i zmieniając typ danych wyjściowych na bibliotekę klas systemu Windows.

Projekt DLL można następnie połączyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z projektem (jedno rozwiązanie, które zawiera dwa projekty) — kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz pozycję **projekt Add\Existing**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

Aby użyć tej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biblioteki DLL [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z projektu, należy dodać odwołanie:

1. Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .

2. Kliknij przycisk **Dodaj nowe odwołanie**.

3. Kliknij kartę **projekty** . Wybierz pozycję WPFClock, a następnie kliknij przycisk OK.

4. Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.

## <a name="hwndsource"></a>HwndSource

Następnie użyj <xref:System.Windows.Interop.HwndSource> , aby <xref:System.Windows.Controls.Page> wyglądać podobnie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu HWND. Ten blok kodu zostanie dodany do C++ pliku:

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

 Następnie zdefiniujesz funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość, <xref:System.Windows.Interop.HwndSource> umieści ją wokół niej i zwraca wartość HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Najpierw należy utworzyć obiekt <xref:System.Windows.Interop.HwndSource>, którego parametry są podobne do okna:

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

Następnie utworzysz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasę zawartości, wywołując jej Konstruktor:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Następnie nawiążesz połączenie ze stroną <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 I w ostatnim wierszu Zwróć wartość HWND dla <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Pozycjonowanie parametru HWND

Teraz, gdy masz już Właściwość HWND, która [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera zegar, musisz umieścić ten HWND [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie dialogowym. Jeśli wiesz tylko, gdzie umieścić Właściwość HWND, wystarczy przekazać ten rozmiar i lokalizację do `GetHwnd` zdefiniowanej wcześniej funkcji. Jednak w celu zdefiniowania okna dialogowego użyto pliku zasobów, dlatego nie należy dokładnie sprawdzić, gdzie są umieszczone dowolne z tych elementów. Możesz użyć [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] edytora okien dialogowych, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] umieścić formant statyczny w miejscu, w którym ma się znajdować zegar ("Wstaw zegar tutaj") i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyć, aby ustawić zegar.

Gdy obsłużysz WM_INITDIALOG, możesz `GetDlgItem` pobrać właściwość HWND dla symbolu zastępczego static:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Następnie można obliczyć rozmiar i położenie tego symbolu zastępczego statycznie, aby można było umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar w tym miejscu:

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

I Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tej lokalizacji Właściwość HWND zegara:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Aby zapewnić ciekawy samouczek i utworzyć rzeczywisty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar, należy w tym momencie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzyć kontrolkę zegar. Można to zrobić głównie w znaczniku, z zaledwie kilkoma programami obsługi zdarzeń w kodzie. Ponieważ ten samouczek dotyczy operacji międzyoperacyjnych, a nie informacje o projekcie kontroli, pełny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod zegara jest dostarczany w tym miejscu jako blok kodu, bez odrębnych instrukcji dotyczących tworzenia go lub co oznacza każda część. Możesz poeksperymentować z tym kodem, aby zmienić wygląd i działanie lub funkcjonalność formantu.

Oto znacznik:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

A oto towarzyszący kod w tle:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Końcowy wynik wygląda następująco:

![Okno dialogowe Właściwości daty i godziny końcowego wyniku](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Aby porównać wynik końcowy z kodem, który wygenerował ten zrzut ekranu, zobacz przykład międzyoperacyjna w systemie [Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.HwndSource>
- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
- [Przykład międzyoperacyjności zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051)
