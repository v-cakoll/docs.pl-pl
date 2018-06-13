---
title: Hosting zawartości Win32 w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: beb7d5e6e1f934b89bb7516eb7e9bbbaad696238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547358"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="6deaa-102">Hosting zawartości Win32 w WPF</span><span class="sxs-lookup"><span data-stu-id="6deaa-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="6deaa-103">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6deaa-103">Prerequisites</span></span>  
 <span data-ttu-id="6deaa-104">Zobacz [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="6deaa-104">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="6deaa-105">Przewodnik Win32 wewnątrz Windows Presentation Framework (element HwndHost)</span><span class="sxs-lookup"><span data-stu-id="6deaa-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="6deaa-106">Ponowne użycie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zawartości wewnątrz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, użyj <xref:System.Windows.Interop.HwndHost>, która jest formant, który sprawia, że parametrów hWnd wyglądać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="6deaa-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="6deaa-107">Podobnie jak <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> jest prosty do użycia: pochodzi od <xref:System.Windows.Interop.HwndHost> i wdrożenie `BuildWindowCore` i `DestroyWindowCore` metod, następnie wystąpienia z <xref:System.Windows.Interop.HwndHost> klasy i umieszczenie go w programie z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja.</span><span class="sxs-lookup"><span data-stu-id="6deaa-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="6deaa-108">Jeśli Twoje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiki już jest dostarczana jako metoda kontrolowania, prawdopodobnie `BuildWindowCore` implementacja jest więcej niż wywołania `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="6deaa-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="6deaa-109">Na przykład, aby utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kontrolki LISTBOX [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="6deaa-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-110">Załóżmy, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kod nie jest dość tak niezależne?</span><span class="sxs-lookup"><span data-stu-id="6deaa-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="6deaa-111">Jeśli tak, możesz utworzyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego pole i osadzanie jego zawartość w większych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6deaa-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="6deaa-112">Pokazano to w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], chociaż jest również można to zrobić w innym języku lub w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6deaa-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="6deaa-113">Rozpoczynać się od prostego okno dialogowe, które ma zostać skompilowany w [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="6deaa-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="6deaa-114">Następnie wprowadzić okna dialogowego do większy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6deaa-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="6deaa-115">Kompiluj [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako zarządzany (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="6deaa-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="6deaa-116">Włącz okna dialogowego w formancie</span><span class="sxs-lookup"><span data-stu-id="6deaa-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="6deaa-117">Zdefiniuj klasy pochodnej z <xref:System.Windows.Interop.HwndHost> z `BuildWindowCore` i `DestroyWindowCore` metody</span><span class="sxs-lookup"><span data-stu-id="6deaa-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="6deaa-118">Zastąpienie `TranslateAccelerator` można obsłużyć klucze okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="6deaa-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="6deaa-119">Zastąpienie `TabInto` metody do obsługi klawisza TAB</span><span class="sxs-lookup"><span data-stu-id="6deaa-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="6deaa-120">Zastąpienie `OnMnemonic` metody do obsługi klawiszy skrótu</span><span class="sxs-lookup"><span data-stu-id="6deaa-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="6deaa-121">Utwórz wystąpienie <xref:System.Windows.Interop.HwndHost> podklasy i umieszcza je w ramach prawa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu</span><span class="sxs-lookup"><span data-stu-id="6deaa-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="6deaa-122">Włącz okna dialogowego w formancie</span><span class="sxs-lookup"><span data-stu-id="6deaa-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="6deaa-123">Okno dialogowe można przekształcić w podrzędny HWND przy użyciu stylów ws_child — i DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="6deaa-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="6deaa-124">Przejdź do pliku zasobów (.rc), gdzie są zdefiniowane okna dialogowego i Znajdź początek definicji okna dialogowego:</span><span class="sxs-lookup"><span data-stu-id="6deaa-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="6deaa-125">Zmień drugi wiersz do:</span><span class="sxs-lookup"><span data-stu-id="6deaa-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="6deaa-126">Ta akcja nie pełni pakietów go w autonomiczną kontroli. nadal trzeba wywołać `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] może przetwarzać komunikatów, ale zmiana sterowania zapewnia łatwe umieszczanie tych kontrolek wewnątrz innego HWND.</span><span class="sxs-lookup"><span data-stu-id="6deaa-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="6deaa-127">Element HwndHost podklasy</span><span class="sxs-lookup"><span data-stu-id="6deaa-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="6deaa-128">Zaimportuj następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="6deaa-128">Import the following namespaces:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-129">Następnie utwórz klasy pochodnej z <xref:System.Windows.Interop.HwndHost> i zastąpić `BuildWindowCore` i `DestroyWindowCore` metod:</span><span class="sxs-lookup"><span data-stu-id="6deaa-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-130">W tym miejscu użyć `CreateDialog` można utworzyć okna dialogowego, że to naprawdę formantu.</span><span class="sxs-lookup"><span data-stu-id="6deaa-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="6deaa-131">Ponieważ to jest pierwszy metody wywołane wewnątrz [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], należy również wykonać niektóre standardowe [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicjowania przez wywołanie funkcji, należy zdefiniować zostanie później, o nazwie `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="6deaa-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="6deaa-132">Zastępuje metodę TranslateAccelerator w celu obsługi kluczy okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="6deaa-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="6deaa-133">W przypadku uruchomienia tego przykładu teraz, jak okna dialogowego kontrolkę wyświetlającą, ale go spowoduje zignorowanie wszystkich klawiatury przetwarzania tego sprawia, że okno dialogowe funkcjonalności okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6deaa-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="6deaa-134">Powinny teraz zastępować `TranslateAccelerator` implementacji (która pochodzi z `IKeyboardInputSink`, interfejs który <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="6deaa-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="6deaa-135">Ta metoda jest wywoływana, gdy aplikacja odbiera WM_KEYDOWN i WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="6deaa-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
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
  
 <span data-ttu-id="6deaa-136">To jest dużo kodu w jeden element, aby można było używać niektórych bardziej szczegółowych wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="6deaa-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="6deaa-137">Najpierw kodu za pomocą [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] i [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; należy mieć świadomość, że jest już makrem o nazwie `TranslateAccelerator`, która jest zdefiniowana w winuser.h:</span><span class="sxs-lookup"><span data-stu-id="6deaa-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="6deaa-138">Dlatego upewnij się zdefiniować `TranslateAccelerator` metody i nie `TranslateAcceleratorW` metody.</span><span class="sxs-lookup"><span data-stu-id="6deaa-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="6deaa-139">Podobnie jest niezarządzany winuser.h MSG i zarządzanej `Microsoft::Win32::MSG` struktury.</span><span class="sxs-lookup"><span data-stu-id="6deaa-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="6deaa-140">Można odróżnić między nimi przy użyciu [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operatora.</span><span class="sxs-lookup"><span data-stu-id="6deaa-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="6deaa-141">Zarówno wiad mieć tych samych danych, ale czasami jest łatwiejsze do pracy z niezarządzanym definicję, tak w tym przykładzie można zdefiniować procedury konwersji oczywiste:</span><span class="sxs-lookup"><span data-stu-id="6deaa-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-142">Powrót do `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="6deaa-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="6deaa-143">Podstawową zasadą jest wywołanie [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkcja `IsDialogMessage` jak dużo pracy, jak to możliwe, ale `IsDialogMessage` nie ma dostępu do żadnej poza okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="6deaa-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="6deaa-144">Jak działa na karcie użytkownika wokół okna dialogowego, gdy klawisza TAB poza ostatni formant w naszym okna dialogowego, musisz ustawić fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części przez wywołanie metody `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="6deaa-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
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
  
 <span data-ttu-id="6deaa-145">Na koniec wywołania `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="6deaa-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="6deaa-146">Oprócz jednego obowiązków `TranslateAccelerator` informuje metody [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] czy naciśnięcie klawisza obsługiwany lub nie.</span><span class="sxs-lookup"><span data-stu-id="6deaa-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="6deaa-147">Jeśli nie obsłużyć, zdarzenie wejściowe może służyć do tunelowania i bąbelków do pozostałej części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6deaa-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="6deaa-148">W tym miejscu będą ujawnia niedoskonałość Obsługa messange klawiatury i rodzaj wejściowych architektury w [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6deaa-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="6deaa-149">Niestety `IsDialogMessage` nie może zwracać w żaden sposób czy obsługi określonego klawisza.</span><span class="sxs-lookup"><span data-stu-id="6deaa-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="6deaa-150">Nawet gorsza wywoła `DispatchMessage()` na naciśnięcia klawiszy nie powinna obsługiwać!</span><span class="sxs-lookup"><span data-stu-id="6deaa-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="6deaa-151">Dlatego trzeba odtwarzanie `IsDialogMessage`i tylko wywołania dla kluczy ją znasz będzie obsługiwać:</span><span class="sxs-lookup"><span data-stu-id="6deaa-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="6deaa-152">Metoda musi zostać zastąpiona TabInto do obsługi klawisza TAB</span><span class="sxs-lookup"><span data-stu-id="6deaa-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="6deaa-153">Teraz, gdy zostały zaimplementowane `TranslateAccelerator`, tab wokół, w oknie dialogowym karta poza go do większa i pole [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6deaa-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="6deaa-154">Jednak użytkownik karcie nie można wrócić do okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="6deaa-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="6deaa-155">Do rozwiązania, które, Zastąp `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="6deaa-155">To solve that, you override `TabInto`:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-156">`TraversalRequest` Parametr informuje, czy akcja karta jest karty lub shift.</span><span class="sxs-lookup"><span data-stu-id="6deaa-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="6deaa-157">Zastąp metodę OnMnemonic do obsługi klawiszy skrótu</span><span class="sxs-lookup"><span data-stu-id="6deaa-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="6deaa-158">Obsługa klawiatury jest niemal ukończone, ale jest jeden element Brak — klawiszy skrótu nie działają.</span><span class="sxs-lookup"><span data-stu-id="6deaa-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="6deaa-159">Jeśli użytkownik naciśnie klawisz alt-F, Nowak fokus nie przeskoczyć do "imię:" polu edycji.</span><span class="sxs-lookup"><span data-stu-id="6deaa-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="6deaa-160">Tak, można zastąpić `OnMnemonic` metody:</span><span class="sxs-lookup"><span data-stu-id="6deaa-160">So, you override the `OnMnemonic` method:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-161">Dlaczego nie mogą wywoływać `IsDialogMessage` w tym miejscu?</span><span class="sxs-lookup"><span data-stu-id="6deaa-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="6deaa-162">Mają ten sam problem, jak przed — muszą mieć możliwość informuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu czy swój kod obsługi naciśnięcie klawisza lub nie, i `IsDialogMessage` nie.</span><span class="sxs-lookup"><span data-stu-id="6deaa-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="6deaa-163">Istnieje również drugi problem, ponieważ `IsDialogMessage` odmówił przetworzenia mnemonik, jeśli ukierunkowanych HWND nie znajduje się w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="6deaa-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="6deaa-164">Utwórz wystąpienie klasy pochodnej element HwndHost</span><span class="sxs-lookup"><span data-stu-id="6deaa-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="6deaa-165">Ponadto skoro wszystkie obsługują klucza i kartę znajduje się w miejscu, można umieścić Twojej <xref:System.Windows.Interop.HwndHost> na większy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6deaa-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="6deaa-166">Jeśli głównej aplikacji jest zapisywany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najprostszym sposobem, aby umieścić go w odpowiednim miejscu jest pozostaw pustą <xref:System.Windows.Controls.Border> elementu, gdzie chcesz umieścić <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="6deaa-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="6deaa-167">W tym miejscu Utwórz <xref:System.Windows.Controls.Border> o nazwie `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="6deaa-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-168">Wszystkie opcje, które pozostaje jest znalezienie dobrym miejscem w sekwencji kodu można utworzyć wystąpienia, a następnie <xref:System.Windows.Interop.HwndHost> i połącz go z <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="6deaa-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="6deaa-169">W tym przykładzie zostanie umieszcza je w Konstruktorze <xref:System.Windows.Window> klasy:</span><span class="sxs-lookup"><span data-stu-id="6deaa-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
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
  
 <span data-ttu-id="6deaa-170">Które zapewnia:</span><span class="sxs-lookup"><span data-stu-id="6deaa-170">Which gives you:</span></span>  
  
 <span data-ttu-id="6deaa-171">![Zrzut ekranu aplikacji WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="6deaa-171">![WPF application screen shot](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6deaa-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6deaa-172">See Also</span></span>  
 [<span data-ttu-id="6deaa-173">WPF i Win32 — współdziałanie</span><span class="sxs-lookup"><span data-stu-id="6deaa-173">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
