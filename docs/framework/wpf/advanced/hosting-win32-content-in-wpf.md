---
title: Hostowanie zawartości Win32
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b3113d9f3146e1590363dc9db6f751a429dda74b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747015"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="c2b98-102">Hosting zawartości Win32 w WPF</span><span class="sxs-lookup"><span data-stu-id="c2b98-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2b98-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c2b98-103">Prerequisites</span></span>

<span data-ttu-id="c2b98-104">Zobacz [WPF i Win32 — współdziałanie](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="c2b98-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="c2b98-105">Przewodnik po Win32 wewnątrz struktury prezentacji systemu Windows (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="c2b98-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="c2b98-106">Aby ponownie użyć zawartości Win32 w aplikacjach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], użyj <xref:System.Windows.Interop.HwndHost>, która jest formantem, który sprawia, że elementy HWND wyglądają jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość.</span><span class="sxs-lookup"><span data-stu-id="c2b98-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="c2b98-107">Podobnie jak <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> jest prosta do użycia: pochodzi z <xref:System.Windows.Interop.HwndHost> i Implementuj metody `BuildWindowCore` i `DestroyWindowCore`, a następnie Utwórz wystąpienie <xref:System.Windows.Interop.HwndHost> klasy pochodnej i umieść ją w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2b98-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="c2b98-108">Jeśli logika Win32 jest już spakowana jako kontrolka, wdrożenie `BuildWindowCore` jest nieco więcej niż wywołanie `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="c2b98-109">Na przykład, aby utworzyć formant LISTBOX Win32 w C++:</span><span class="sxs-lookup"><span data-stu-id="c2b98-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="c2b98-110">Ale Załóżmy, że kod Win32 nie jest całkowicie zawarty?</span><span class="sxs-lookup"><span data-stu-id="c2b98-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="c2b98-111">Jeśli tak, możesz utworzyć okno dialogowe Win32 i osadzić jego zawartość w aplikacji o większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2b98-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c2b98-112">Przykład pokazuje to w programie Visual Studio i C++, chociaż jest to również możliwe w innym języku lub w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c2b98-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="c2b98-113">Zacznij od prostego okna dialogowego, które jest kompilowane do projektu C++ dll.</span><span class="sxs-lookup"><span data-stu-id="c2b98-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="c2b98-114">Następnie wprowadź okno dialogowe do większego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c2b98-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="c2b98-115">Kompiluj bibliotekę DLL jako zarządzaną (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="c2b98-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="c2b98-116">Przekształcanie okna dialogowego w kontrolkę</span><span class="sxs-lookup"><span data-stu-id="c2b98-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="c2b98-117">Definiowanie klasy pochodnej <xref:System.Windows.Interop.HwndHost> przy użyciu metod `BuildWindowCore` i `DestroyWindowCore`</span><span class="sxs-lookup"><span data-stu-id="c2b98-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="c2b98-118">Zastąp metodę `TranslateAccelerator`, aby obsłużyć klawisze dialogu</span><span class="sxs-lookup"><span data-stu-id="c2b98-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="c2b98-119">Zastąp metodę `TabInto`, aby obsługiwać tabulację</span><span class="sxs-lookup"><span data-stu-id="c2b98-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="c2b98-120">Zastąp metodę `OnMnemonic`, aby obsługiwała</span><span class="sxs-lookup"><span data-stu-id="c2b98-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="c2b98-121">Utwórz wystąpienie podklasy <xref:System.Windows.Interop.HwndHost> i umieść ją w prawym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elemencie</span><span class="sxs-lookup"><span data-stu-id="c2b98-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="c2b98-122">Przekształcanie okna dialogowego w kontrolkę</span><span class="sxs-lookup"><span data-stu-id="c2b98-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="c2b98-123">Okno dialogowe można przekształcić w podrzędny element HWND przy użyciu stylów WS_CHILD i DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="c2b98-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="c2b98-124">Przejdź do pliku zasobów (. RC), w którym zdefiniowano okno dialogowe, a następnie Znajdź początek definicji okna dialogowego:</span><span class="sxs-lookup"><span data-stu-id="c2b98-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="c2b98-125">Zmień drugi wiersz na:</span><span class="sxs-lookup"><span data-stu-id="c2b98-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="c2b98-126">Ta akcja nie powoduje całkowitego spakowania jej w celu samodzielnego sterowania; nadal musisz wywołać `IsDialogMessage()` tak, aby system Win32 mógł przetworzyć niektóre komunikaty, ale zmiana kontrolki zapewnia prostą metodę umieszczania tych kontrolek wewnątrz innego elementu HWND.</span><span class="sxs-lookup"><span data-stu-id="c2b98-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="c2b98-127">HwndHost podklasy</span><span class="sxs-lookup"><span data-stu-id="c2b98-127">Subclass HwndHost</span></span>

<span data-ttu-id="c2b98-128">Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="c2b98-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="c2b98-129">Następnie Utwórz klasę pochodną <xref:System.Windows.Interop.HwndHost> i Zastąp metody `BuildWindowCore` i `DestroyWindowCore`:</span><span class="sxs-lookup"><span data-stu-id="c2b98-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="c2b98-130">W tym miejscu użyjesz `CreateDialog`, aby utworzyć okno dialogowe, które jest naprawdę formantem.</span><span class="sxs-lookup"><span data-stu-id="c2b98-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="c2b98-131">Ponieważ jest to jedna z pierwszych metod wywoływanych wewnątrz biblioteki DLL, należy również wykonać kilka standardowych inicjacji Win32, wywołując funkcję, która zostanie zdefiniowana później, o nazwie `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="c2b98-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="c2b98-132">Zastąp metodę TranslateAccelerator, aby obsłużyć klawisze dialogu</span><span class="sxs-lookup"><span data-stu-id="c2b98-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="c2b98-133">Jeśli ten przykład został uruchomiony teraz, zobaczysz kontrolkę okna dialogowego, która wyświetla, ale zignorujesz wszystkie przetwarzanie klawiatury, które powoduje okno dialogowe funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c2b98-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="c2b98-134">Teraz należy zastąpić implementację `TranslateAccelerator` (która pochodzi z `IKeyboardInputSink`, interfejsu, który <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="c2b98-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="c2b98-135">Ta metoda jest wywoływana, gdy aplikacja otrzymuje WM_KEYDOWN i WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="c2b98-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="c2b98-136">Jest to wiele kodu w jednej części, dzięki czemu można użyć bardziej szczegółowych wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="c2b98-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="c2b98-137">Najpierw kod wykorzystujący C++ i C++ makra; należy pamiętać, że istnieje już makro o nazwie `TranslateAccelerator`, które jest zdefiniowane w Winuser. h:</span><span class="sxs-lookup"><span data-stu-id="c2b98-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="c2b98-138">Upewnij się, że zdefiniowano metodę `TranslateAccelerator`, a nie metodę `TranslateAcceleratorW`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="c2b98-139">Podobnie istnieje zarówno niezarządzana MSG Winuser. h, jak i zarządzana struktura `Microsoft::Win32::MSG`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="c2b98-140">Można odróżnić dwa z nich przy użyciu operatora C++ `::`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="c2b98-141">Wróć do `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="c2b98-142">Podstawowa zasada polega na wywołaniu funkcji Win32 `IsDialogMessage`, aby wykonać tyle pracy, ile to możliwe, ale `IsDialogMessage` nie ma dostępu do niczego poza oknem dialogowym.</span><span class="sxs-lookup"><span data-stu-id="c2b98-142">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="c2b98-143">Jako karta użytkownika w oknie dialogowym, gdy karta jest uruchamiana poza ostatnią kontrolką w naszym oknie dialogowym, należy ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] część, wywołując `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="c2b98-144">Na koniec Wywołaj `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="c2b98-145">Ale jeden z obowiązków metody `TranslateAccelerator` jest informujący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o tym, czy zostały obsłużone naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="c2b98-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="c2b98-146">Jeśli go nie obsłuży, zdarzenie wejściowe może tunelować i bąbelkować przez resztę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b98-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="c2b98-147">Tutaj zobaczysz Quirk obsługi messange z klawiatury oraz naturę architektury danych wejściowych w systemie Win32.</span><span class="sxs-lookup"><span data-stu-id="c2b98-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="c2b98-148">Niestety `IsDialogMessage` nie zwraca w żaden sposób, czy obsługuje określone naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="c2b98-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="c2b98-149">Nawet gorszy, wywoła `DispatchMessage()` na naciśnięciach klawiszy, które nie powinny obsłużyć!</span><span class="sxs-lookup"><span data-stu-id="c2b98-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="c2b98-150">W związku z tym trzeba będzie odwrócić `IsDialogMessage`i wywołać ją tylko dla kluczy, które są obsługiwane przez Ciebie:</span><span class="sxs-lookup"><span data-stu-id="c2b98-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="c2b98-151">Zastąp metodę TabInto w celu obsługi tabulacji</span><span class="sxs-lookup"><span data-stu-id="c2b98-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="c2b98-152">Teraz, po zaimplementowaniu `TranslateAccelerator`, użytkownik może umieścić kartę w obszarze okna dialogowego i wylogować się z niego do większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b98-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c2b98-153">Jednak użytkownik nie może powracać do okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="c2b98-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="c2b98-154">Aby rozwiązać ten problem, Zastąp `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="c2b98-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="c2b98-155">Parametr `TraversalRequest` informuje o tym, czy akcja karty jest tabulatorem, czy klawiszem Shift.</span><span class="sxs-lookup"><span data-stu-id="c2b98-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="c2b98-156">Przesłoń metodę do obsługi symboli</span><span class="sxs-lookup"><span data-stu-id="c2b98-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="c2b98-157">Obsługa klawiatury jest niemal ukończona, ale nie ma jednego z nich — nie działa.</span><span class="sxs-lookup"><span data-stu-id="c2b98-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="c2b98-158">Jeśli użytkownik naciśnie klawisze ALT-F, fokus Nowak nie Przeskocz do pola edycji imię i nazwisko:.</span><span class="sxs-lookup"><span data-stu-id="c2b98-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="c2b98-159">Dlatego należy zastąpić metodę `OnMnemonic`:</span><span class="sxs-lookup"><span data-stu-id="c2b98-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="c2b98-160">Dlaczego nie należy wywoływać `IsDialogMessage` tym miejscu?</span><span class="sxs-lookup"><span data-stu-id="c2b98-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="c2b98-161">Ten sam problem należy wykonać co wcześniej — musisz mieć możliwość poinformowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodzie, czy kod obsłużył naciśnięcie klawisza, a nie `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="c2b98-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="c2b98-162">Występuje również drugi problem, ponieważ `IsDialogMessage` odmawia przetworzenia elementu, jeśli priorytetowy element HWND nie znajduje się w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="c2b98-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="c2b98-163">Tworzenie wystąpienia klasy pochodnej HwndHost</span><span class="sxs-lookup"><span data-stu-id="c2b98-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="c2b98-164">Teraz, gdy cała obsługa klucza i karty jest na miejscu, możesz umieścić <xref:System.Windows.Interop.HwndHost> w większej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2b98-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="c2b98-165">Jeśli główna aplikacja jest zapisywana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najprostszym sposobem umieszczenia jej w odpowiednim miejscu jest pozostawienie pustego elementu <xref:System.Windows.Controls.Border>, w którym ma zostać umieszczony <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="c2b98-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="c2b98-166">W tym miejscu utworzysz <xref:System.Windows.Controls.Border> o nazwie `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="c2b98-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="c2b98-167">Następnie wszystko to, co pozostanie, aby znaleźć dobre miejsce w sekwencji kodu, aby utworzyć wystąpienie <xref:System.Windows.Interop.HwndHost> i połączyć je z <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="c2b98-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="c2b98-168">W tym przykładzie umieścisz go wewnątrz konstruktora dla klasy pochodnej <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="c2b98-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="c2b98-169">Dzięki temu:</span><span class="sxs-lookup"><span data-stu-id="c2b98-169">Which gives you:</span></span>

![Zrzut ekranu z uruchomioną aplikacją WPF.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="c2b98-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2b98-171">See also</span></span>

- [<span data-ttu-id="c2b98-172">WPF i Win32 — współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c2b98-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
