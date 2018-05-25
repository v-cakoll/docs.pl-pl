---
title: 'Porady: implementowanie funkcji wywołania zwrotnego'
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
ms.openlocfilehash: e081347129ce367cf6b46ca29c07a016bb64ab95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="4ac38-102">Porady: implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4ac38-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="4ac38-103">Poniższe procedury i przykładowe pokazują, jak wywołać przy użyciu platformy aplikacji zarządzanej, drukować wartość uchwytu dla każdego okna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4ac38-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="4ac38-104">W szczególności, użyj procedury i przykładowe **EnumWindows** funkcji kroków wykaz systemu windows oraz funkcja wywołania zwrotnego w zarządzanych (nazwane wywołania zwrotnego) do drukowania wartość uchwytu okna.</span><span class="sxs-lookup"><span data-stu-id="4ac38-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="4ac38-105">Aby wdrożyć funkcję wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4ac38-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="4ac38-106">Przyjrzyj się podpis dla **EnumWindows** funkcja przed przejściem dalej z implementacją.</span><span class="sxs-lookup"><span data-stu-id="4ac38-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="4ac38-107">**EnumWindows** ma następującą sygnaturą:</span><span class="sxs-lookup"><span data-stu-id="4ac38-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="4ac38-108">Jeden clue, że ta funkcja wymaga wywołania zwrotnego jest obecność **lpEnumFunc** argumentu.</span><span class="sxs-lookup"><span data-stu-id="4ac38-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="4ac38-109">Często, aby wyświetlić **lp** prefiks (wskaźnik długi) łączony z **Func** sufiks nazwy argumentów, które przyjmują wskaźnika do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4ac38-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="4ac38-110">Dokumentacja funkcji Win32 temacie zestawu SDK platformy firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4ac38-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="4ac38-111">Utwórz funkcję wywołania zwrotnego w zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4ac38-111">Create the managed callback function.</span></span> <span data-ttu-id="4ac38-112">Przykład deklaruje typ delegata o nazwie `CallBack`, który przyjmuje dwa argumenty (**hwnd** i **lparam**).</span><span class="sxs-lookup"><span data-stu-id="4ac38-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="4ac38-113">Pierwszy argument jest dojścia do okna; drugi argument jest zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4ac38-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="4ac38-114">W tej wersji oba argumenty muszą być liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="4ac38-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="4ac38-115">Funkcje wywołania zwrotnego zwracają zazwyczaj niezerowe wartości oznacza powodzenie i zera do wskazania błędu.</span><span class="sxs-lookup"><span data-stu-id="4ac38-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="4ac38-116">W tym przykładzie jawnie ustawia wartość zwrotną **true** kontynuowanie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4ac38-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="4ac38-117">Utworzenia delegata i przekaż go jako argument **EnumWindows** funkcji.</span><span class="sxs-lookup"><span data-stu-id="4ac38-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="4ac38-118">Wywołanie platformy automatycznie konwertuje delegata do formatu znanych wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4ac38-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="4ac38-119">Upewnij się, że moduł zbierający elementy bezużyteczne nie odzyskać delegat ukończenia pracy funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4ac38-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="4ac38-120">Przekazywanie obiektu delegate jako parametr lub przekazywanie obiektu delegate zawarte jako pola w strukturze pozostaje niepobranych na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="4ac38-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="4ac38-121">Tak jak w przypadku w poniższym przykładzie wyliczenie, funkcja wywołania zwrotnego nie ukończy pracy przed wywołanie zwraca i nie wymaga dodatkowych czynności przez obiekt wywołujący zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4ac38-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="4ac38-122">Jeśli jednak funkcja wywołania zwrotnego można wywołać po wywołaniu zwraca, wywołujący zarządzanych, należy wykonać kroki w celu zapewnienia delegat pozostaje niepobranych, dopóki nie zakończy się działanie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4ac38-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="4ac38-123">Aby uzyskać szczegółowe informacje dotyczące zapobiegania wyrzucanie elementów bezużytecznych, zobacz [organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md) z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="4ac38-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac38-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac38-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ac38-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ac38-125">See Also</span></span>  
 [<span data-ttu-id="4ac38-126">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4ac38-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 [<span data-ttu-id="4ac38-127">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="4ac38-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
