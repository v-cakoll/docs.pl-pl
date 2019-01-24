---
title: Hosting zawartości Win32 w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: fa0457cd44304084355f3882d9fc5c82b29c4827
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725471"
---
# <a name="hosting-win32-content-in-wpf"></a>Hosting zawartości Win32 w WPF
## <a name="prerequisites"></a>Wymagania wstępne  
 Zobacz [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Przewodnik po Win32 w Windows Presentation Framework (HwndHost)  
 Ponowne użycie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, używa <xref:System.Windows.Interop.HwndHost>, czyli formant, który sprawia, że parametrów hWnd wyglądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  Podobnie jak <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> jest prosty do użycia: pochodzić od <xref:System.Windows.Interop.HwndHost> i wdrożenie `BuildWindowCore` i `DestroyWindowCore` metod, tworzy swoje <xref:System.Windows.Interop.HwndHost> klasę pochodną i umieścić go w programie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja.  
  
 Jeśli Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiki jest już spakowane w postaci kontrolki, wówczas `BuildWindowCore` implementacja jest nieco więcej niż wywołanie `CreateWindow`.  Na przykład, aby utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX, kontrolka [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 Jednak Załóżmy, że [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod nie jest na taki Rozrost niezależna? Jeśli tak, możesz utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego pole i osadzić jego zawartość do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  Pokazano to w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], chociaż są również można to zrobić w innym języku lub w wierszu polecenia.  
  
 Uruchom proste okno dialogowe, który jest skompilowany w [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.  
  
 Następnie wprowadzić okna dialogowego do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:  
  
-   Skompilować [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako zarządzany (`/clr`)  
  
-   Włącz okno dialogowe do kontrolki  
  
-   Definiowanie klasy pochodnej <xref:System.Windows.Interop.HwndHost> z `BuildWindowCore` i `DestroyWindowCore` metody  
  
-   Zastąp `TranslateAccelerator` metodę do obsługi kluczy okna dialogowego  
  
-   Zastąp `TabInto` metody w celu obsługi tabulacji  
  
-   Zastąp `OnMnemonic` metody w celu obsługi klawiszy skrótu  
  
-   Utwórz wystąpienie <xref:System.Windows.Interop.HwndHost> podklasy i umieść je w obszarze po prawej stronie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] — element  
  
### <a name="turn-the-dialog-into-a-control"></a>Włącz okno dialogowe do kontrolki  
 Okno dialogowe można przekształcić w podrzędny HWND przy użyciu stylów WS_CHILD i DS_CONTROL.  Przejdź do pliku zasobów (.rc), gdzie są zdefiniowane okna dialogowego i Znajdź początek definicji w oknie dialogowym:  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 Zmień drugi wiersz do:  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 Ta akcja nie pełni spakujesz ją w kontrolce niezależna; nadal należy wywołać `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] może przetwarzać komunikatów, ale zmiana sterowania zapewnia prosty sposób umieszczania te kontrolki wewnątrz innego HWND.  
  
## <a name="subclass-hwndhost"></a>HwndHost podklasy  
 Zaimportuj następujące przestrzenie nazw:  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 Następnie Utwórz klasę pochodną z <xref:System.Windows.Interop.HwndHost> i zastąpić `BuildWindowCore` i `DestroyWindowCore` metody:  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 W tym miejscu możesz użyć `CreateDialog` utworzyć okno dialogowe, które naprawdę jest formantem.  Ponieważ jest to jedna z pierwszych metod o nazwie wewnątrz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], należy również wykonać niektóre standardowe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicjowanie przez wywołanie funkcji będzie definiujesz nowszym wywołuje `InitializeGlobals()`:  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
```  
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Zastąp metodę TranslateAccelerator do obsługi kluczy okna dialogowego  
 Po uruchomieniu tego przykładu, otrzymamy formantu w oknie dialogowym, które wyświetla, ale go będzie Ignoruj wszystkie klawiatury przetwarzania tego sprawia, że okno dialogowe funkcjonalności okno dialogowe.  Teraz należy zastąpić `TranslateAccelerator` implementacji (które pochodzą z `IKeyboardInputSink`, interfejs, <xref:System.Windows.Interop.HwndHost> implementuje).  Ta metoda jest wywoływana, gdy aplikacja otrzymuje przetłumaczyła i WM_SYSKEYDOWN.  
  
```  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 Jest to duża ilość kodu w jeden element, aby go użyć niektórych bardziej szczegółowe wyjaśnienia.  Najpierw kod za pomocą [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; należy pamiętać, że jest już makrem o nazwie `TranslateAccelerator`, który jest zdefiniowany w winuser.h:  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 Dlatego upewnij się zdefiniować `TranslateAccelerator` metody i nie `TranslateAcceleratorW` metody.  
  
 Podobnie, istnieje zarówno niezarządzane winuser.h MSG i zarządzany `Microsoft::Win32::MSG` struktury.  Użytkownik może rozróżnić przy użyciu [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operatora.  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 Zarówno wiad mają te same dane, ale czasami jest łatwiej jest pracować przy użyciu definicji niezarządzanych, w tym przykładzie umożliwiają definiowanie procedury konwersji oczywiste:  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 Powrót do `TranslateAccelerator`.  Podstawową zasadą jest, aby wywołać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `IsDialogMessage` dużo pracy, jak to możliwe, ale `IsDialogMessage` nie ma dostępu do żadnego elementu poza okna dialogowego. Po uruchomieniu na karcie użytkownika wokół okna dialogowego klawiszem TAB po ostatniej kontroli w naszym okna dialogowego należy ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] część przez wywołanie metody `IKeyboardInputSite::OnNoMoreStops`.  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 Na koniec Wywołaj `IsDialogMessage`.  Ale jedna obowiązków `TranslateAccelerator` informuje metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tego, czy jego naciśnięcie obsługiwany lub nie. Jeśli nie go obsłużyć, dane wejściowe zdarzenia może służyć do tunelowania i bąbelkowych przez pozostałą część aplikacji. W tym miejscu możesz udostępni niedoskonałość Obsługa messange klawiatury i rodzaj Architektura danych wejściowych w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Niestety `IsDialogMessage` nie może zwracać w jakikolwiek sposób czy obsługuje on określonej naciśnięcia klawisza.  Co gorsza, wywoła `DispatchMessage()` na naciśnięcia klawiszy nie powinien obsługiwać!  Dlatego trzeba będzie odtwarzać `IsDialogMessage`i wywoływać tylko je do kluczy, znasz jego będzie obsługiwać:  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### <a name="override-tabinto-method-to-support-tabbing"></a>Metoda TabInto musi zostać zastąpiona w celu obsługi klawiszem TAB  
 Teraz, że udało Ci się wdrożyć `TranslateAccelerator`, tab wokół, wewnątrz okna dialogowego pole i karty z niej na większą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  Jednak użytkownik nie kartę do okna dialogowego.  Aby rozwiązać, który, możesz zastąpić `TabInto`:  
  
```  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
```  
  
 `TraversalRequest` Parametr informuje, czy akcja karty są karty lub shift.  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Zastąpienie metody OnMnemonic w celu obsługi klawiszy skrótu  
 Obsługa klawiatury jest niemal ukończone, ale jest jedną rzecz Brak — klawiszy skrótu nie działa.  Jeśli użytkownik naciśnie klawisz alt-F, Kowalska fokus nie przejść do tematu "imię:" pole edycji. Dlatego możesz zastąpić `OnMnemonic` metody:  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 Dlaczego nie mogą wywoływać `IsDialogMessage` tutaj?  Mają ten sam problem, jak przed — trzeba będzie mógł poinformować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu czy swój kod obsługi naciśnięcia klawisza lub nie, a `IsDialogMessage` tej czynności nie.  Istnieje również drugi problem, ponieważ `IsDialogMessage` odmówi przetworzenia mnemonik, jeśli ukierunkowanych HWND nie znajduje się w oknie dialogowym.  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>Utwórz wystąpienie klasy pochodnej HwndHost  
 Na koniec teraz wszystkie obsługują karta i klucz znajduje się w miejscu, można umieścić swoje <xref:System.Windows.Interop.HwndHost> do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  W przypadku aplikacji głównej jest napisany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], umieść go w odpowiednim miejscu najłatwiej można pozostawić pustą <xref:System.Windows.Controls.Border> elementu, w którym chcesz umieścić <xref:System.Windows.Interop.HwndHost>.  W tym miejscu Utwórz <xref:System.Windows.Controls.Border> o nazwie `insertHwndHostHere`:  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 Następnie pozostaje tylko do znajdowania dobre miejsce w sekwencji kodu w celu utworzenia wystąpienia <xref:System.Windows.Interop.HwndHost> i połącz go <xref:System.Windows.Controls.Border>.  W tym przykładzie należy go umieścić w Konstruktorze <xref:System.Windows.Window> klasy pochodnej:  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 Poniższych zagadnień:  
  
 ![Zrzut ekranu aplikacji WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>Zobacz także
- [WPF i Win32 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
