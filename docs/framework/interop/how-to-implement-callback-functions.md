---
title: 'Instrukcje: Implementowanie funkcji wywołania zwrotnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0a033e6881f9c0c8741fda26211b0f565762de4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331328"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="4f446-102">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4f446-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="4f446-103">Poniższy przykład i procedury pokazują, jak wywołać przy użyciu platformy zarządzanej aplikacji, można wydrukować wartość dojścia dla każdego przedziału na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4f446-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="4f446-104">W szczególności procedury i przykładowego użycia **EnumWindows** funkcji przechodzić przez wykaz systemu windows i funkcji wywołania zwrotnego zarządzanych (o nazwie wywołanie zwrotne) aby wyświetlić wartość uchwyt okna.</span><span class="sxs-lookup"><span data-stu-id="4f446-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="4f446-105">Aby zaimplementować funkcję wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4f446-105">To implement a callback function</span></span>  
  
1. <span data-ttu-id="4f446-106">Przyjrzyj się podpis dla **EnumWindows** funkcji przed przejściem dalej z implementacją.</span><span class="sxs-lookup"><span data-stu-id="4f446-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="4f446-107">**EnumWindows** ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="4f446-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="4f446-108">Co sugeruje, że ta funkcja wymaga wywołania zwrotnego jest obecność **lpEnumFunc** argumentu.</span><span class="sxs-lookup"><span data-stu-id="4f446-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="4f446-109">Bardzo często, aby zobaczyć **lp** prefiksu (wskaźnik długi) w połączeniu z **Func** sufiks nazwy argumentów, które przyjmują wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4f446-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="4f446-110">Dokumentację informacji na temat funkcji Win32 na ten temat można znaleźć w zestawie SDK platformy firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4f446-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="4f446-111">Tworzenie funkcji wywołania zwrotnego zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4f446-111">Create the managed callback function.</span></span> <span data-ttu-id="4f446-112">Przykład deklaruje typu delegata, o nazwie `CallBack`, który przyjmuje dwa argumenty (**hwnd** i **lparam**).</span><span class="sxs-lookup"><span data-stu-id="4f446-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="4f446-113">Pierwszy argument jest uchwytem do okna; drugi argument funkcji jest zdefiniowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4f446-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="4f446-114">W tej wersji oba argumenty muszą być liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="4f446-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="4f446-115">Funkcje wywołania zwrotnego zazwyczaj zwraca wartość różną od zera wartości do wskazania sukcesu oraz zero, aby wskazać błąd.</span><span class="sxs-lookup"><span data-stu-id="4f446-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="4f446-116">W tym przykładzie jawnie ustawia wartość zwracaną **true** kontynuować wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4f446-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="4f446-117">Utwórz delegata i przekazać go jako argument do **EnumWindows** funkcji.</span><span class="sxs-lookup"><span data-stu-id="4f446-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="4f446-118">Wywołanie platformy automatycznie konwertuje delegata do formatu znanych wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4f446-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="4f446-119">Upewnij się, że moduł odśmiecania pamięci nie spowoduje odzyskania delegata przed funkcji wywołania zwrotnego nie ukończy pracy.</span><span class="sxs-lookup"><span data-stu-id="4f446-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="4f446-120">Przekazywanie obiektu delegate jako parametr lub przekazywanie obiektu delegate zawarte jako pole w strukturze, pozostaje niepobranych na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="4f446-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="4f446-121">Tak jak w przypadku, w poniższym przykładzie wyliczenie, funkcja wywołania zwrotnego nie ukończy pracy przed wywołanie zwraca i nie wymaga dodatkowych czynności przez zarządzany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4f446-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="4f446-122">Jeśli jednak po wywołaniu zwraca można wywołać funkcję wywołania zwrotnego, zarządzanego obiektu wywołującego, należy wykonać czynności, aby upewnić się, delegat pozostaje niepobranych, dopóki nie zakończy się działanie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4f446-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="4f446-123">Aby uzyskać szczegółowe informacje dotyczące zapobiegania wyrzucania elementów bezużytecznych, zobacz [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) za pomocą wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="4f446-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f446-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f446-124">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f446-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f446-125">See also</span></span>

- [<span data-ttu-id="4f446-126">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4f446-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)
- [<span data-ttu-id="4f446-127">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="4f446-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
