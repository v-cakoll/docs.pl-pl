---
title: "Wskazówki: Hosting zegara WPF w Win32"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e5aa633e3d788ac8acaa09684c92b8608e7cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Wskazówki: Hosting zegara WPF w Win32
Aby umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, użyj <xref:System.Windows.Interop.HwndSource>, zapewniające HWND, który zawiera Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości. Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, nadanie mu podobna do właściwości CreateWindow parametrów.  Następnie można sprawdzić <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, która ma w nim.  Ponadto możesz uzyskać HWND z <xref:System.Windows.Interop.HwndSource>. W tym przewodniku ilustruje sposób tworzenia mieszane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, która reimplements systemu operacyjnego **właściwości daty i godziny** okna dialogowego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Zobacz [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Jak używać tego samouczka  
 Ten samouczek koncentruje się na ważnych czynności produkcji współdziałanie aplikacji. Samouczek nie jest obsługiwana przez próbki [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051), ale ten przykład jest odbicia produktu końcowego. W tym samouczku dokumentów kroki tak, jakby były uruchamianie z istniejącym [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu własny, być może istniejącego projektu, a dodawania hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikacji. Możesz porównać produktu zakończenia z [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Przewodnik Windows Presentation Framework wewnątrz Win32 (HwndSource)  
 Na poniższym rysunku przedstawiono danego produktu zakończenia tego samouczka:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 Utwórz ponownie tego okna dialogowego przez utworzenie C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]i przy użyciu edytora okien dialogowych, aby utworzyć następujące:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Nie trzeba używać [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] do używania <xref:System.Windows.Interop.HwndSource>, i nie trzeba użyć C++, aby zapisać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy, ale jest dość typowy sposób przeprowadzenia i pozwala również na stopniowym wyjaśnienie samouczka).  
  
 Należy wykonać pięć podetapów konkretnego celu umieść [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara w oknie dialogowym:  
  
1.  Włącz Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu do wywoływania z kodu zarządzanego (**/CLR**), zmieniając ustawienia projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> w oddzielnych bibliotekach DLL.  
  
3.  Powiązanie tej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wewnątrz <xref:System.Windows.Interop.HwndSource>.  
  
4.  Pobierz HWND tego <xref:System.Windows.Controls.Page> przy użyciu <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwości.  
  
5.  Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] decyzji o tym, gdzie umieścić HWND w większy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji  
  
## <a name="clr"></a>/ CLR  
 Pierwszym krokiem jest włączenie tej niezarządzanych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt na taki, który można wywołać kodu zarządzanego.  Użyj opcji kompilatora/CLR, która połączy niezbędne chcesz używać i Dostosuj metody Main do użycia z bibliotek DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Aby włączyć korzystanie z kodu zarządzanego wewnątrz projektu C++: kliknij prawym przyciskiem myszy na win32clock projektu i wybierz **właściwości**.  Na **ogólne** strony właściwości (ustawienie domyślne), zmienić obsługi plików wykonywalnych języka aby `/clr`.  
  
 Następnie dodaj odwołania do bibliotek DLL niezbędne do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: plików PresentationCore.dll, PresentationFramework.dll System.dll, WindowsBase.dll, UIAutomationProvider.dll i UIAutomationTypes.dll. (Instrukcjami przyjęto założenie, że system operacyjny jest instalowany na dysku C:.)  
  
1.  Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** i w tym oknie dialogowym:  
  
2.  Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** .  
  
3.  Kliknij przycisk **Dodaj nowe odwołanie**, kliknij kartę przeglądania, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.  
  
4.  Powtórz tę procedurę dla PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  Powtórz tę procedurę dla WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  Powtórz tę procedurę dla UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  Powtórz tę procedurę dla UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Kliknij przycisk **Dodaj nowe odwołanie**, wybierz System.dll i kliknij przycisk **OK**.  
  
9. Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.  
  
 Na koniec należy dodać `STAThreadAttribute` do `_tWinMain` metoda do użycia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Ten atrybut informuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] który podczas inicjuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], należy użyć modelu komórek wielowątkowych pojedynczego (STA), który jest konieczny do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Utwórz stronę Windows Presentation Framework  
 Następnie Utwórz bibliotekę DLL, która definiuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Często jest najłatwiejsza do utworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako aplikacja autonomiczna i zapisu i debugowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części w ten sposób.  Po zakończeniu tego projektu mogą być uwzględniane biblioteki DLL przez kliknięcie prawym przyciskiem myszy projekt, klikając **właściwości**, przechodząc do aplikacji i zmiana typu danych wyjściowych biblioteki klas systemu Windows.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Projektu biblioteki dll można połączyć z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (rozwiązania, które zawiera dwa projekty) — kliknij prawym przyciskiem myszy rozwiązanie, wybierz opcję **projektu Add\Existing**.  
  
 Można użyć tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biblioteki dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt, musisz dodać odwołanie:  
  
1.  Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** .  
  
2.  Kliknij przycisk **Dodaj nowe odwołanie**.  
  
3.  Kliknij przycisk **projekty** kartę.  Wybierz WPFClock, kliknij przycisk OK.  
  
4.  Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.  
  
## <a name="hwndsource"></a>HwndSource  
 Następnie użyj <xref:System.Windows.Interop.HwndSource> aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wyglądać HWND.  Możesz dodać ten blok kodu do pliku C++:  
  
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
  
 Jest to długo fragment kodu używanego wyjaśnień.  Pierwsza część jest różnych klauzule, dzięki czemu nie trzeba do pełnej kwalifikacji wszystkie wywołania:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Definiuje funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości naraża <xref:System.Windows.Interop.HwndSource> wokół i zwraca HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, którego parametry są podobne do właściwości CreateWindow:  
  
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
  
 Następnie możesz utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości przez wywołanie jego konstruktora klasy:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Następnie połącz stronę, aby <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 I w ostatnim wierszu zwracać HWND dla <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Pozycjonowanie Hwnd  
 Teraz, gdy masz HWND, który zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, musisz umieścić tego HWND wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego.  Jeśli wiedział właśnie, gdzie umieścić HWND możesz po prostu przejdzie tego rozmiar i położenie do `GetHwnd` funkcji zdefiniowanej w wcześniej.  Ale użyć pliku zasobu do definiowania okna dialogowego, tak, aby dokładnie się, gdzie umieszczane są żadnego z parametrów hWnd.  Można użyć [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] Edytor okien dialogowych, aby umieścić [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC kontrolować miejscu zegara, aby przejść ("Insert zegara tutaj") i użyj jej położenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara.  
  
 W przypadku, gdy obsługa WM_INITDIALOG, użyj `GetDlgItem` można pobrać HWND symbolu zastępczego STATYCZNĄ:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Można obliczyć, rozmiar i położenie tego symbolu statyczna, więc można umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara w tym miejscu:  
  
 Prostokąt RECT;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 Następnie można ukryć symbol zastępczy STATYCZNĄ:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 I Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara HWND w tej lokalizacji:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Aby interesujące samouczka i do tworzenia rzeczywistych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, musisz utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara formantu w tym momencie. To przede wszystkim w znaczniku, należy się z kilku obsługi zdarzeń w CodeBehind. Ponieważ w tym samouczku jest dotyczące współdziałanie i nie projektu kontroli, uzupełnianie kodu dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar jest dostarczany jako blok kodu bez odrębny instrukcje dotyczące jego budowania lub oznacza każdej części. Możesz eksperymentować ten kod, aby zmienić wygląd i działanie lub funkcji formantu.  
  
 Oto kod znaczników:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 A Oto towarzyszący kodem:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 Wynik końcowy wygląda następująco:  
  
 ![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 Aby porównać wyników zakończenia kod wytworzonego tego zrzutu ekranu, zobacz [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.HwndSource>  
 [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051)
