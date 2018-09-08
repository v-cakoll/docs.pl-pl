---
title: 'Wskazówki: Hosting zegara WPF w Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: ce8209c89430988f57c211d388c6e73b2dc17004
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178328"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Wskazówki: Hosting zegara WPF w Win32
Umieszczenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, używa <xref:System.Windows.Interop.HwndSource>, zapewniającą HWND, który zawiera Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, nadając mu parametry, podobnie jak CreateWindow.  A następnie poinformuj <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, która ma wewnątrz niego.  Na koniec Uzyskaj HWND z <xref:System.Windows.Interop.HwndSource>. W tym instruktażu pokazano, jak tworzyć mieszane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikację, która reimplements systemu operacyjnego **właściwości daty i godziny** okna dialogowego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Zobacz [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Jak korzystać z tego samouczka  
 Ten samouczek koncentruje się na ważnych kroków tworzenia współdziałanie aplikacji. Samouczek opiera się na przykład, [przykład współdziałanie zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale ta przykładowe dane stanowią odbijającą produktu końcowego. W tym samouczku dokumenty kroki tak, jakby były uruchamianie z istniejącym [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] własny projekt, prawdopodobnie istniejącego projektu i możesz dodawania hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikacji. Możesz porównać swojego produktu końcowego, zapewniając [przykład współdziałanie zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Przewodnik po Windows Presentation Framework wewnątrz Win32 (HwndSource)  
 Na poniższym rysunku przedstawiono zamierzony produkt końcowy w części tego samouczka:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 Utwórz ponownie tego okna dialogowego, tworząc C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]i przy użyciu edytora okien dialogowych, aby utworzyć następujące:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Nie trzeba używać [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] używać <xref:System.Windows.Interop.HwndSource>, i nie trzeba używać języka C++ do pisania [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programów, ale jest dość typowy sposób przeprowadzenia i pozwala również na stopniowym wyjaśnienie samouczka).  
  
 Należy wykonać pięć podrzędne określonego celu umieść [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara do okna dialogowego:  
  
1.  Włączanie usługi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt, aby wywoływać kod zarządzany (**/CLR**), zmieniając ustawienia projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> w oddzielnym pliku DLL.  
  
3.  Umieścić te [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wewnątrz <xref:System.Windows.Interop.HwndSource>.  
  
4.  Uzyskać HWND, <xref:System.Windows.Controls.Page> przy użyciu <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwości.  
  
5.  Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zdecydować, gdzie umieścić HWND w obrębie większej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji  
  
## <a name="clr"></a>/ CLR  
 Pierwszym krokiem jest do włączenia niezarządzanych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt na taki, który można wywoływać kod zarządzany.  Użyj opcji kompilatora/CLR, która połączy się odpowiednie biblioteki DLL chcesz użyć, a następnie dostosować metody Main, do użytku z programem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Aby włączyć korzystanie z kodu zarządzanego wewnątrz projektu C++: kliknij prawym przyciskiem myszy nad projektem win32clock, a następnie wybierz pozycję **właściwości**.  Na **ogólne** strony właściwości (ustawienie domyślne), zmień środowisko uruchomieniowe języka wspólnego techniczną, aby `/clr`.  
  
 Następnie dodaj odwołania do biblioteki DLL jest niezbędne do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll i UIAutomationTypes.dll. (Instrukcjami przyjęto założenie, że system operacyjny jest zainstalowany na dysku C:.)  
  
1.  Kliknij prawym przyciskiem myszy projekt win32clock, a następnie wybierz pozycję **odwołania...** , a w tym oknie dialogowym:  
  
2.  Kliknij prawym przyciskiem myszy projekt win32clock, a następnie wybierz pozycję **odwołania...** .  
  
3.  Kliknij przycisk **Dodaj nowe odwołanie**, kliknij kartę przeglądania, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.  
  
4.  Powtórz tę procedurę dla PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  Powtórz tę procedurę dla WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  Powtórz tę procedurę dla UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  Powtórz tę procedurę dla UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Kliknij przycisk **Dodaj nowe odwołanie**wybierz System.dll i kliknij **OK**.  
  
9. Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.  
  
 Na koniec należy dodać `STAThreadAttribute` do `_tWinMain` metoda do użycia z usługą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Ten atrybut instruuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , gdy inicjuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], powinna korzystać modelu komórek wielowątkowych pojedynczego (STA), co jest niezbędne do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Tworzenie strony Windows Presentation Framework  
 Następnie należy utworzyć bibliotekę DLL, która definiuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Najłatwiej utworzyć jest często [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako autonomiczną aplikacją i pisanie i debugowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części w ten sposób.  Po zakończeniu tego projektu mogą być uwzględniane biblioteki DLL przez kliknięcie prawym przyciskiem myszy projekt, klikając **właściwości**, przechodząc do aplikacji i zmiana typu danych wyjściowych biblioteki klas Windows.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Projekt dll można połączyć z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (jednego rozwiązania, które zawiera dwa projekty) — kliknij prawym przyciskiem myszy na rozwiązanie, wybierz opcję **projektu Add\Existing**.  
  
 Aby używać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biblioteki dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu, musisz dodać odwołanie:  
  
1.  Kliknij prawym przyciskiem myszy projekt win32clock, a następnie wybierz pozycję **odwołania...** .  
  
2.  Kliknij przycisk **Dodaj nowe odwołanie**.  
  
3.  Kliknij przycisk **projektów** kartę.  Wybierz WPFClock, kliknij przycisk OK.  
  
4.  Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.  
  
## <a name="hwndsource"></a>HwndSource  
 Następnie użyj <xref:System.Windows.Interop.HwndSource> się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wyglądać HWND.  Ten blok kodu, możesz dodać do pliku C++:  
  
```  
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
  
 Jest to długi fragment kodu, które mogły korzystać z niektórych wyjaśnienie.  Pierwsza część jest różne klauzule, dzięki czemu nie trzeba do pełnej kwalifikacji wszystkie wywołania:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Definiuje funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości umieszcza <xref:System.Windows.Interop.HwndSource> wokół i zwraca HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, której parametry są podobne do CreateWindow:  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 Następnie tworzymy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości klasy przez wywołanie jego konstruktora:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Następnie połącz stronę, aby <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 I w ostatnim wierszu zwracają HWND uzyskać <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Pozycjonowanie Hwnd  
 Teraz, gdy masz HWND, który zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, musisz umieścić ten HWND wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego.  Jeśli dokonywano po prostu, gdzie umieścić HWND możesz po prostu przejdzie ten rozmiar i położenie do `GetHwnd` wcześniej zdefiniowaną funkcję.  Ale plik zasobu jest używane do definiowania okna dialogowego, dzięki czemu wiadomo dokładnie żadnego z parametrów hWnd gdzie są umieszczone.  Możesz użyć [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] Edytor okien dialogowych, aby umieścić [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATYCZNE kontrolować, gdzie chcesz zegara, aby przejść ("Insert zegar tutaj") i używać go do pozycji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara.  
  
 W przypadku, gdy należy obsługiwać / / Złap, możesz użyć `GetDlgItem` można pobrać HWND symbolu zastępczego statyczna:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Możesz następnie obliczyć rozmiary i położenie tego symbolu zastępczego statyczna, dzięki czemu można umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara w tym miejscu:  
  
 Prostokąt Prostokąt;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 Następnie możesz ukryć symbolu zastępczego statyczna:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 I Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara HWND w tej lokalizacji:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Samouczek interesujących oraz do tworzenia rzeczywistych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, należy utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar na tym etapie kontroli. Możecie więc przede wszystkim w znaczniku, za pomocą zaledwie kilku obsługi zdarzeń w związanym z kodem. Ponieważ w tym samouczku jest międzyoperacyjność — informacje i nie dotyczących projektowania kontroli, uzupełnianie kodu dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar znajduje się tutaj jako blok kodu bez dyskretnych instrukcji na temat budowania go lub co oznacza każda część. Możesz eksperymentować, ten kod, aby zmienić wygląd i działanie lub funkcje formantu.  
  
 Oto znaczniki:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 A Oto towarzyszący kodem:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Wynik końcowy wygląda następująco:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 Aby porównać wynik końcowy Twojego kodu, który tego zrzutu ekranu, zobacz [przykład współdziałanie zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Przykład współdziałanie zegara systemu Win32](https://go.microsoft.com/fwlink/?LinkID=160051)
