---
title: Hosting zawartości Win32 w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: ee260d58cdb4dc971fc32ca5c889b459b6a48489
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484740"
---
# <a name="hosting-win32-content-in-wpf"></a>Hosting zawartości Win32 w WPF

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [WPF i Win32](wpf-and-win32-interoperation.md)— współdziałanie.

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Przewodnik po Win32 wewnątrz struktury prezentacji systemu Windows (HwndHost)

Aby ponownie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] użyć zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz aplikacji, <xref:System.Windows.Interop.HwndHost>należy użyć, która jest formantem, który sprawia, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] że właściwość HWND wygląda jak zawartość. `BuildWindowCore` <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost> `DestroyWindowCore` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Na przykład <xref:System.Windows.Interop.HwndHost> , jest to proste do użycia: pochodne od i Implementuj metody, a następnie Utwórz wystąpienie klasy pochodnej i umieść je wewnątrz <xref:System.Windows.Interop.HwndSource> Aplikacja.

Jeśli logika jest już spakowana jako kontrolka, Twoja `BuildWindowCore` implementacja jest nieco `CreateWindow`większa niż wywołanie. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Na przykład, aby utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] formant ListBox w: C++

```cpp
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

Ale Załóżmy, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] że kod nie jest całkowicie zawarty? Jeśli tak, możesz utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno dialogowe i osadzić jego zawartość w większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Przykład pokazuje to w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] i C++, chociaż jest to również możliwe w innym języku lub w wierszu polecenia.

Zacznij od prostego okna dialogowego, które jest kompilowane do C++ [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.

Następnie wprowadź okno dialogowe do większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:

- Kompiluj jako zarządzany (`/clr`) [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]

- Przekształcanie okna dialogowego w kontrolkę

- Zdefiniuj klasę <xref:System.Windows.Interop.HwndHost> pochodną metod with `BuildWindowCore` i `DestroyWindowCore`

- Override `TranslateAccelerator` — Metoda do obsługi klawiszy okna dialogowego

- Override `TabInto` — Metoda do obsługi tabulacji

- Override `OnMnemonic` — Metoda do obsługi symboli

- Utwórz wystąpienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podklasy i umieść ją pod prawidłowym elementem <xref:System.Windows.Interop.HwndHost>

### <a name="turn-the-dialog-into-a-control"></a>Przekształcanie okna dialogowego w kontrolkę

Okno dialogowe można przekształcić w podrzędny element HWND przy użyciu stylów WS_CHILD i DS_CONTROL. Przejdź do pliku zasobów (. RC), w którym zdefiniowano okno dialogowe, a następnie Znajdź początek definicji okna dialogowego:

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

Zmień drugi wiersz na:

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Ta akcja nie powoduje całkowitego spakowania jej w celu samodzielnego sterowania; nadal konieczne jest wywołanie metody `IsDialogMessage()` w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] taki sposób, że może przetwarzać niektóre komunikaty, ale zmiana kontrolki zapewnia prostą metodę umieszczania tych kontrolek wewnątrz innego elementu HWND.

## <a name="subclass-hwndhost"></a>HwndHost podklasy

Zaimportuj następujące przestrzenie nazw:

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

Następnie Utwórz klasę <xref:System.Windows.Interop.HwndHost> pochodną i `BuildWindowCore` Przesłoń metody i `DestroyWindowCore` :

```cpp
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

W tym miejscu użyjesz, `CreateDialog` aby utworzyć okno dialogowe, które jest naprawdę formantem. Ponieważ jest to jedna z pierwszych metod wywoływanych wewnątrz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], należy również wykonać kilka standardowych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicjacji, wywołując funkcję, którą określisz później, o nazwie `InitializeGlobals()`:

```cpp
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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Zastąp metodę TranslateAccelerator, aby obsłużyć klawisze dialogu

Jeśli ten przykład został uruchomiony teraz, zobaczysz kontrolkę okna dialogowego, która wyświetla, ale zignorujesz wszystkie przetwarzanie klawiatury, które powoduje okno dialogowe funkcjonalne. Należy teraz zastąpić `TranslateAccelerator` implementację (która pochodzi z `IKeyboardInputSink`interfejsu, który <xref:System.Windows.Interop.HwndHost> implementuje). Ta metoda jest wywoływana, gdy aplikacja odbiera PRZETŁUMACZYŁA i WM_SYSKEYDOWN.

```cpp
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

Jest to wiele kodu w jednej części, dzięki czemu można użyć bardziej szczegółowych wyjaśnień. Najpierw kod wykorzystujący C++ i C++ makra; należy pamiętać, że istnieje już makro o nazwie `TranslateAccelerator`, które jest zdefiniowane w Winuser. h:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Upewnij się, że zdefiniowano `TranslateAccelerator` metodę, a `TranslateAcceleratorW` nie metodę.

Podobnie istnieje zarówno niezarządzana MSG Winuser. h, jak i zarządzana `Microsoft::Win32::MSG` struktura. Można odróżnić dwa z nich przy użyciu C++ `::` operatora.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
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

Z powrotem `TranslateAccelerator`do. Podstawowa zasada polega na wywołaniu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcji `IsDialogMessage` tak, jak to możliwe, ale `IsDialogMessage` nie ma dostępu do niczego poza oknem dialogowym. Jako karta użytkownika dookoła okna dialogowego, gdy karta jest uruchamiana poza ostatnią kontrolką w naszym oknie dialogowym, należy ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części poprzez wywołanie metody. `IKeyboardInputSite::OnNoMoreStops`

```cpp
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

Na koniec Wywołaj metodę `IsDialogMessage`. Ale jedno z obowiązków `TranslateAccelerator` metody [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest informowanie o tym, czy zostało obsłużone naciśnięcie klawisza. Jeśli go nie obsłuży, zdarzenie wejściowe może tunelować i bąbelkować przez resztę aplikacji. Tutaj zobaczysz Quirk z obsługą klawiatury messange i charakterem architektury wejściowej w programie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Niestety, `IsDialogMessage` nie zwraca w żaden sposób, czy obsługuje określone naciśnięcie klawisza. Nawet gorsze, będzie ona `DispatchMessage()` wywoływała na naciśnięciach klawiszy, które nie powinny być obsługiwane!  W związku z tym trzeba będzie odwrócić `IsDialogMessage`i wywoływać tylko te klucze, które będą obsługiwane:

```cpp
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

### <a name="override-tabinto-method-to-support-tabbing"></a>Zastąp metodę TabInto w celu obsługi tabulacji

Teraz, po zaimplementowaniu `TranslateAccelerator`, użytkownik może umieścić kartę w obszarze okna dialogowego i wylogować się z niego do większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Jednak użytkownik nie może powracać do okna dialogowego. Aby rozwiązać ten problem, przesłonisz `TabInto`:

```cpp
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

`TraversalRequest` Parametr informuje o tym, czy akcja karty jest tabulatorem, czy klawiszem Shift.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Przesłoń metodę do obsługi symboli

Obsługa klawiatury jest niemal ukończona, ale nie ma jednego z nich — nie działa. Jeśli użytkownik naciśnie klawisze ALT-F, fokus Nowak nie Przeskocz do pola edycji imię i nazwisko:. Dlatego nie można zastąpić `OnMnemonic` metody:

```cpp
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

Dlaczego nie wywołuj `IsDialogMessage` tutaj?  Ten sam problem należy wykonać co wcześniej — musisz mieć możliwość informowania kodu o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tym `IsDialogMessage` , czy kod obsłużył naciśnięcie klawisza, czy nie. Występuje również drugi problem, ponieważ `IsDialogMessage` odmówi on, aby przetworzyć polecenie, jeśli fokus jest poza oknem dialogowym.

### <a name="instantiate-the-hwndhost-derived-class"></a>Tworzenie wystąpienia klasy pochodnej HwndHost

Teraz, gdy cała pomoc techniczna Key i Tab jest na miejscu, możesz ją umieścić <xref:System.Windows.Interop.HwndHost> w większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji. Jeśli główna aplikacja jest zapisywana [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najprostszym sposobem umieszczania jej w odpowiednim miejscu jest pozostawienie pustego <xref:System.Windows.Controls.Border> elementu, w którym ma zostać umieszczony <xref:System.Windows.Interop.HwndHost>. W <xref:System.Windows.Controls.Border> tym miejscu utworzysz nazwę `insertHwndHostHere`:

```xaml
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

Następnie wszystko to, co pozostanie, aby znaleźć dobre miejsce w sekwencji kodu w <xref:System.Windows.Interop.HwndHost> celu utworzenia wystąpienia i połączenia <xref:System.Windows.Controls.Border>go z. W tym przykładzie zostanie umieszczony wewnątrz konstruktora dla <xref:System.Windows.Window> klasy pochodnej:

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

Dzięki temu:

![Zrzut ekranu z uruchomioną aplikacją WPF.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Zobacz także

- [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md)
