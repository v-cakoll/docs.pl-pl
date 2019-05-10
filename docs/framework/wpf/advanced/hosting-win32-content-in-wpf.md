---
title: Hosting zawartości Win32 w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 390f63fca912de6de2a1349363e239eb603df549
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750617"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="91c9c-102">Hosting zawartości Win32 w WPF</span><span class="sxs-lookup"><span data-stu-id="91c9c-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91c9c-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="91c9c-103">Prerequisites</span></span>

<span data-ttu-id="91c9c-104">Zobacz [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="91c9c-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="91c9c-105">Przewodnik po Win32 w Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="91c9c-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="91c9c-106">Ponowne użycie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, używa <xref:System.Windows.Interop.HwndHost>, czyli formant, który sprawia, że parametrów hWnd wyglądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="91c9c-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="91c9c-107">Podobnie jak <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> jest prosty do użycia: pochodzić od <xref:System.Windows.Interop.HwndHost> i wdrożenie `BuildWindowCore` i `DestroyWindowCore` metod, tworzy swoje <xref:System.Windows.Interop.HwndHost> klasę pochodną i umieścić go w programie usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja.</span><span class="sxs-lookup"><span data-stu-id="91c9c-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="91c9c-108">Jeśli Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiki jest już spakowane w postaci kontrolki, wówczas `BuildWindowCore` implementacja jest nieco więcej niż wywołanie `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="91c9c-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="91c9c-109">Na przykład, aby utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX, kontrolka [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="91c9c-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>

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

<span data-ttu-id="91c9c-110">Jednak Załóżmy, że [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod nie jest na taki Rozrost niezależna?</span><span class="sxs-lookup"><span data-stu-id="91c9c-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="91c9c-111">Jeśli tak, możesz utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego pole i osadzić jego zawartość do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91c9c-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="91c9c-112">Pokazano to w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], chociaż są również można to zrobić w innym języku lub w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="91c9c-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="91c9c-113">Uruchom proste okno dialogowe, który jest skompilowany w [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="91c9c-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>

<span data-ttu-id="91c9c-114">Następnie wprowadzić okna dialogowego do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="91c9c-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="91c9c-115">Skompilować [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako zarządzany (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="91c9c-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>

- <span data-ttu-id="91c9c-116">Włącz okno dialogowe do kontrolki</span><span class="sxs-lookup"><span data-stu-id="91c9c-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="91c9c-117">Definiowanie klasy pochodnej <xref:System.Windows.Interop.HwndHost> z `BuildWindowCore` i `DestroyWindowCore` metody</span><span class="sxs-lookup"><span data-stu-id="91c9c-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="91c9c-118">Zastąp `TranslateAccelerator` metodę do obsługi kluczy okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="91c9c-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="91c9c-119">Zastąp `TabInto` metody w celu obsługi tabulacji</span><span class="sxs-lookup"><span data-stu-id="91c9c-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="91c9c-120">Zastąp `OnMnemonic` metody w celu obsługi klawiszy skrótu</span><span class="sxs-lookup"><span data-stu-id="91c9c-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="91c9c-121">Utwórz wystąpienie <xref:System.Windows.Interop.HwndHost> podklasy i umieść je w obszarze po prawej stronie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] — element</span><span class="sxs-lookup"><span data-stu-id="91c9c-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="91c9c-122">Włącz okno dialogowe do kontrolki</span><span class="sxs-lookup"><span data-stu-id="91c9c-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="91c9c-123">Okno dialogowe można przekształcić w podrzędny HWND przy użyciu stylów WS_CHILD i DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="91c9c-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="91c9c-124">Przejdź do pliku zasobów (.rc), gdzie są zdefiniowane okna dialogowego i Znajdź początek definicji w oknie dialogowym:</span><span class="sxs-lookup"><span data-stu-id="91c9c-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="91c9c-125">Zmień drugi wiersz do:</span><span class="sxs-lookup"><span data-stu-id="91c9c-125">Change the second line to:</span></span>

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="91c9c-126">Ta akcja nie pełni spakujesz ją w kontrolce niezależna; nadal należy wywołać `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] może przetwarzać komunikatów, ale zmiana sterowania zapewnia prosty sposób umieszczania te kontrolki wewnątrz innego HWND.</span><span class="sxs-lookup"><span data-stu-id="91c9c-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="91c9c-127">HwndHost podklasy</span><span class="sxs-lookup"><span data-stu-id="91c9c-127">Subclass HwndHost</span></span>

<span data-ttu-id="91c9c-128">Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="91c9c-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="91c9c-129">Następnie Utwórz klasę pochodną z <xref:System.Windows.Interop.HwndHost> i zastąpić `BuildWindowCore` i `DestroyWindowCore` metody:</span><span class="sxs-lookup"><span data-stu-id="91c9c-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="91c9c-130">W tym miejscu możesz użyć `CreateDialog` utworzyć okno dialogowe, które naprawdę jest formantem.</span><span class="sxs-lookup"><span data-stu-id="91c9c-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="91c9c-131">Ponieważ jest to jedna z pierwszych metod o nazwie wewnątrz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], należy również wykonać niektóre standardowe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicjowanie przez wywołanie funkcji będzie definiujesz nowszym wywołuje `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="91c9c-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="91c9c-132">Zastąp metodę TranslateAccelerator do obsługi kluczy okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="91c9c-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="91c9c-133">Po uruchomieniu tego przykładu, otrzymamy formantu w oknie dialogowym, które wyświetla, ale go będzie Ignoruj wszystkie klawiatury przetwarzania tego sprawia, że okno dialogowe funkcjonalności okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="91c9c-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="91c9c-134">Teraz należy zastąpić `TranslateAccelerator` implementacji (które pochodzą z `IKeyboardInputSink`, interfejs, <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="91c9c-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="91c9c-135">Ta metoda jest wywoływana, gdy aplikacja otrzymuje przetłumaczyła i WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="91c9c-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="91c9c-136">Jest to duża ilość kodu w jeden element, aby go użyć niektórych bardziej szczegółowe wyjaśnienia.</span><span class="sxs-lookup"><span data-stu-id="91c9c-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="91c9c-137">Najpierw kod za pomocą [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; należy pamiętać, że jest już makrem o nazwie `TranslateAccelerator`, który jest zdefiniowany w winuser.h:</span><span class="sxs-lookup"><span data-stu-id="91c9c-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="91c9c-138">Dlatego upewnij się zdefiniować `TranslateAccelerator` metody i nie `TranslateAcceleratorW` metody.</span><span class="sxs-lookup"><span data-stu-id="91c9c-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="91c9c-139">Podobnie, istnieje zarówno niezarządzane winuser.h MSG i zarządzany `Microsoft::Win32::MSG` struktury.</span><span class="sxs-lookup"><span data-stu-id="91c9c-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="91c9c-140">Użytkownik może rozróżnić przy użyciu [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operatora.</span><span class="sxs-lookup"><span data-stu-id="91c9c-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>

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

<span data-ttu-id="91c9c-141">Powrót do `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="91c9c-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="91c9c-142">Podstawową zasadą jest, aby wywołać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `IsDialogMessage` dużo pracy, jak to możliwe, ale `IsDialogMessage` nie ma dostępu do żadnego elementu poza okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="91c9c-142">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="91c9c-143">Po uruchomieniu na karcie użytkownika wokół okna dialogowego klawiszem TAB po ostatniej kontroli w naszym okna dialogowego należy ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] część przez wywołanie metody `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="91c9c-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="91c9c-144">Na koniec Wywołaj `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="91c9c-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="91c9c-145">Ale jedna obowiązków `TranslateAccelerator` informuje metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tego, czy jego naciśnięcie obsługiwany lub nie.</span><span class="sxs-lookup"><span data-stu-id="91c9c-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="91c9c-146">Jeśli nie go obsłużyć, dane wejściowe zdarzenia może służyć do tunelowania i bąbelkowych przez pozostałą część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91c9c-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="91c9c-147">W tym miejscu możesz udostępni niedoskonałość Obsługa messange klawiatury i rodzaj Architektura danych wejściowych w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91c9c-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="91c9c-148">Niestety `IsDialogMessage` nie może zwracać w jakikolwiek sposób czy obsługuje on określonej naciśnięcia klawisza.</span><span class="sxs-lookup"><span data-stu-id="91c9c-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="91c9c-149">Co gorsza, wywoła `DispatchMessage()` na naciśnięcia klawiszy nie powinien obsługiwać!</span><span class="sxs-lookup"><span data-stu-id="91c9c-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="91c9c-150">Dlatego trzeba będzie odtwarzać `IsDialogMessage`i wywoływać tylko je do kluczy, znasz jego będzie obsługiwać:</span><span class="sxs-lookup"><span data-stu-id="91c9c-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="91c9c-151">Metoda TabInto musi zostać zastąpiona w celu obsługi klawiszem TAB</span><span class="sxs-lookup"><span data-stu-id="91c9c-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="91c9c-152">Teraz, że udało Ci się wdrożyć `TranslateAccelerator`, tab wokół, wewnątrz okna dialogowego pole i karty z niej na większą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91c9c-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="91c9c-153">Jednak użytkownik nie kartę do okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="91c9c-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="91c9c-154">Aby rozwiązać, który, możesz zastąpić `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="91c9c-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="91c9c-155">`TraversalRequest` Parametr informuje, czy akcja karty są karty lub shift.</span><span class="sxs-lookup"><span data-stu-id="91c9c-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="91c9c-156">Zastąpienie metody OnMnemonic w celu obsługi klawiszy skrótu</span><span class="sxs-lookup"><span data-stu-id="91c9c-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="91c9c-157">Obsługa klawiatury jest niemal ukończone, ale jest jedną rzecz Brak — klawiszy skrótu nie działa.</span><span class="sxs-lookup"><span data-stu-id="91c9c-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="91c9c-158">Jeśli użytkownik naciśnie klawisz alt-F, Kowalska fokus nie przejść do tematu "imię:" pole edycji.</span><span class="sxs-lookup"><span data-stu-id="91c9c-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="91c9c-159">Dlatego możesz zastąpić `OnMnemonic` metody:</span><span class="sxs-lookup"><span data-stu-id="91c9c-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="91c9c-160">Dlaczego nie mogą wywoływać `IsDialogMessage` tutaj?</span><span class="sxs-lookup"><span data-stu-id="91c9c-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="91c9c-161">Mają ten sam problem, jak przed — trzeba będzie mógł poinformować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu czy swój kod obsługi naciśnięcia klawisza lub nie, a `IsDialogMessage` tej czynności nie.</span><span class="sxs-lookup"><span data-stu-id="91c9c-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="91c9c-162">Istnieje również drugi problem, ponieważ `IsDialogMessage` odmówi przetworzenia mnemonik, jeśli ukierunkowanych HWND nie znajduje się w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="91c9c-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="91c9c-163">Utwórz wystąpienie klasy pochodnej HwndHost</span><span class="sxs-lookup"><span data-stu-id="91c9c-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="91c9c-164">Na koniec teraz wszystkie obsługują karta i klucz znajduje się w miejscu, można umieścić swoje <xref:System.Windows.Interop.HwndHost> do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91c9c-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="91c9c-165">W przypadku aplikacji głównej jest napisany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], umieść go w odpowiednim miejscu najłatwiej można pozostawić pustą <xref:System.Windows.Controls.Border> elementu, w którym chcesz umieścić <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="91c9c-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="91c9c-166">W tym miejscu Utwórz <xref:System.Windows.Controls.Border> o nazwie `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="91c9c-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="91c9c-167">Następnie pozostaje tylko do znajdowania dobre miejsce w sekwencji kodu w celu utworzenia wystąpienia <xref:System.Windows.Interop.HwndHost> i połącz go <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="91c9c-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="91c9c-168">W tym przykładzie należy go umieścić w Konstruktorze <xref:System.Windows.Window> klasy pochodnej:</span><span class="sxs-lookup"><span data-stu-id="91c9c-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="91c9c-169">Poniższych zagadnień:</span><span class="sxs-lookup"><span data-stu-id="91c9c-169">Which gives you:</span></span>

![Zrzut ekranu przedstawiający jest uruchomiona aplikacja WPF.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="91c9c-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91c9c-171">See also</span></span>

- [<span data-ttu-id="91c9c-172">WPF i Win32 — współdziałanie</span><span class="sxs-lookup"><span data-stu-id="91c9c-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
