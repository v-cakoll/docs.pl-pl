---
title: "Hosting zawartości Win32 w WPF"
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
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e82d18cd765fc3ac4f4982a71d187a3741f4f03a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="hosting-win32-content-in-wpf"></a>Hosting zawartości Win32 w WPF
## <a name="prerequisites"></a>Wymagania wstępne  
 Zobacz [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Przewodnik Win32 wewnątrz Windows Presentation Framework (element HwndHost)  
 Ponowne użycie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, użyj <xref:System.Windows.Interop.HwndHost>, która jest formant, który sprawia, że parametrów hWnd wyglądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.  Podobnie jak <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> jest prosty do użycia: pochodzi od <xref:System.Windows.Interop.HwndHost> i wdrożenie `BuildWindowCore` i `DestroyWindowCore` metod, następnie wystąpienia z <xref:System.Windows.Interop.HwndHost> klasy i umieszczenie go w programie z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja.  
  
 Jeśli Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiki już jest dostarczana jako metoda kontrolowania, prawdopodobnie `BuildWindowCore` implementacja jest więcej niż wywołania `CreateWindow`.  Na przykład, aby utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontrolki LISTBOX [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
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
  
 Załóżmy, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod nie jest dość tak niezależne? Jeśli tak, możesz utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego pole i osadzanie jego zawartość w większych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  Pokazano to w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], chociaż jest również można to zrobić w innym języku lub w wierszu polecenia.  
  
 Rozpoczynać się od prostego okno dialogowe, które ma zostać skompilowany w [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.  
  
 Następnie wprowadzić okna dialogowego do większy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:  
  
-   Kompiluj [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako zarządzany (`/clr`)  
  
-   Włącz okna dialogowego w formancie  
  
-   Zdefiniuj klasy pochodnej z <xref:System.Windows.Interop.HwndHost> z `BuildWindowCore` i `DestroyWindowCore` metody  
  
-   Zastąpienie `TranslateAccelerator` można obsłużyć klucze okna dialogowego  
  
-   Zastąpienie `TabInto` metody do obsługi klawisza TAB  
  
-   Zastąpienie `OnMnemonic` metody do obsługi klawiszy skrótu  
  
-   Utwórz wystąpienie <xref:System.Windows.Interop.HwndHost> podklasy i umieszcza je w ramach prawa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu  
  
### <a name="turn-the-dialog-into-a-control"></a>Włącz okna dialogowego w formancie  
 Okno dialogowe można przekształcić w podrzędny HWND przy użyciu stylów ws_child — i DS_CONTROL.  Przejdź do pliku zasobów (.rc), gdzie są zdefiniowane okna dialogowego i Znajdź początek definicji okna dialogowego:  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 Zmień drugi wiersz do:  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 Ta akcja nie pełni pakietów go w autonomiczną kontroli. nadal trzeba wywołać `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] może przetwarzać komunikatów, ale zmiana sterowania zapewnia łatwe umieszczanie tych kontrolek wewnątrz innego HWND.  
  
## <a name="subclass-hwndhost"></a>Element HwndHost podklasy  
 Zaimportuj następujących przestrzeni nazw:  
  
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
  
 Następnie utwórz klasy pochodnej z <xref:System.Windows.Interop.HwndHost> i zastąpić `BuildWindowCore` i `DestroyWindowCore` metod:  
  
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
  
 W tym miejscu użyć `CreateDialog` można utworzyć okna dialogowego, że to naprawdę formantu.  Ponieważ to jest pierwszy metody wywołane wewnątrz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], należy również wykonać niektóre standardowe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicjowania przez wywołanie funkcji, należy zdefiniować zostanie później, o nazwie `InitializeGlobals()`:  
  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Zastępuje metodę TranslateAccelerator w celu obsługi kluczy okna dialogowego  
 W przypadku uruchomienia tego przykładu teraz, jak okna dialogowego kontrolkę wyświetlającą, ale go spowoduje zignorowanie wszystkich klawiatury przetwarzania tego sprawia, że okno dialogowe funkcjonalności okno dialogowe.  Powinny teraz zastępować `TranslateAccelerator` implementacji (która pochodzi z `IKeyboardInputSink`, interfejs który <xref:System.Windows.Interop.HwndHost> implementuje).  Ta metoda jest wywoływana, gdy aplikacja odbiera WM_KEYDOWN i WM_SYSKEYDOWN.  
  
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
  
 To jest dużo kodu w jeden element, aby można było używać niektórych bardziej szczegółowych wyjaśnień.  Najpierw kodu za pomocą [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; należy mieć świadomość, że jest już makrem o nazwie `TranslateAccelerator`, która jest zdefiniowana w winuser.h:  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 Dlatego upewnij się zdefiniować `TranslateAccelerator` metody i nie `TranslateAcceleratorW` metody.  
  
 Podobnie jest niezarządzany winuser.h MSG i zarządzanej `Microsoft::Win32::MSG` struktury.  Można odróżnić między nimi przy użyciu [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operatora.  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 Zarówno wiad mieć tych samych danych, ale czasami jest łatwiejsze do pracy z niezarządzanym definicję, tak w tym przykładzie można zdefiniować procedury konwersji oczywiste:  
  
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
  
 Powrót do `TranslateAccelerator`.  Podstawową zasadą jest wywołanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `IsDialogMessage` jak dużo pracy, jak to możliwe, ale `IsDialogMessage` nie ma dostępu do żadnej poza okna dialogowego. Jak działa na karcie użytkownika wokół okna dialogowego, gdy klawisza TAB poza ostatni formant w naszym okna dialogowego, musisz ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części przez wywołanie metody `IKeyboardInputSite::OnNoMoreStops`.  
  
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
  
 Na koniec wywołania `IsDialogMessage`.  Oprócz jednego obowiązków `TranslateAccelerator` informuje metody [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czy naciśnięcie klawisza obsługiwany lub nie. Jeśli nie obsłużyć, zdarzenie wejściowe może służyć do tunelowania i bąbelków do pozostałej części aplikacji. W tym miejscu będą ujawnia niedoskonałość Obsługa messange klawiatury i rodzaj wejściowych architektury w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Niestety `IsDialogMessage` nie może zwracać w żaden sposób czy obsługi określonego klawisza.  Nawet gorsza wywoła `DispatchMessage()` na naciśnięcia klawiszy nie powinna obsługiwać!  Dlatego trzeba odtwarzanie `IsDialogMessage`i tylko wywołania dla kluczy ją znasz będzie obsługiwać:  
  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a>Metoda musi zostać zastąpiona TabInto do obsługi klawisza TAB  
 Teraz, gdy zostały zaimplementowane `TranslateAccelerator`, tab wokół, w oknie dialogowym karta poza go do większa i pole [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  Jednak użytkownik karcie nie można wrócić do okna dialogowego.  Do rozwiązania, które, Zastąp `TabInto`:  
  
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
  
 `TraversalRequest` Parametr informuje, czy akcja karta jest karty lub shift.  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Zastąp metodę OnMnemonic do obsługi klawiszy skrótu  
 Obsługa klawiatury jest niemal ukończone, ale jest jeden element Brak — klawiszy skrótu nie działają.  Jeśli użytkownik naciśnie klawisz alt-F, Nowak fokus nie przeskoczyć do "imię:" polu edycji. Tak, można zastąpić `OnMnemonic` metody:  
  
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
  
 Dlaczego nie mogą wywoływać `IsDialogMessage` w tym miejscu?  Mają ten sam problem, jak przed — muszą mieć możliwość informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu czy swój kod obsługi naciśnięcie klawisza lub nie, i `IsDialogMessage` nie.  Istnieje również drugi problem, ponieważ `IsDialogMessage` odmówił przetworzenia mnemonik, jeśli ukierunkowanych HWND nie znajduje się w oknie dialogowym.  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>Utwórz wystąpienie klasy pochodnej element HwndHost  
 Ponadto skoro wszystkie obsługują klucza i kartę znajduje się w miejscu, można umieścić Twojej <xref:System.Windows.Interop.HwndHost> na większy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  Jeśli głównej aplikacji jest zapisywany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najprostszym sposobem, aby umieścić go w odpowiednim miejscu jest pozostaw pustą <xref:System.Windows.Controls.Border> elementu, gdzie chcesz umieścić <xref:System.Windows.Interop.HwndHost>.  W tym miejscu Utwórz <xref:System.Windows.Controls.Border> o nazwie `insertHwndHostHere`:  
  
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
  
 Wszystkie opcje, które pozostaje jest znalezienie dobrym miejscem w sekwencji kodu można utworzyć wystąpienia, a następnie <xref:System.Windows.Interop.HwndHost> i połącz go z <xref:System.Windows.Controls.Border>.  W tym przykładzie zostanie umieszcza je w Konstruktorze <xref:System.Windows.Window> klasy:  
  
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
  
 Które zapewnia:  
  
 ![Zrzut ekranu aplikacji WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>Zobacz też  
 [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
