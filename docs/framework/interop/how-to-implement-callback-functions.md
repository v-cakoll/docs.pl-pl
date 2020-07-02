---
title: 'Instrukcje: Implementowanie funkcji wywołania zwrotnego'
description: Zobacz, jak zaimplementować funkcje wywołania zwrotnego. W tym przykładzie zarządzana aplikacja używa wywołania platformy, drukuje wartość dojścia dla każdego okna na komputerze.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: 31c657372e760c8d57f9714b20178967ad85fcd3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619120"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="4df1a-104">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4df1a-104">How to: Implement Callback Functions</span></span>
<span data-ttu-id="4df1a-105">Poniższa procedura i przykład przedstawiają sposób, w jaki aplikacja zarządzana używająca funkcji wywołania platformy może drukować wartość dojścia dla każdego okna na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4df1a-105">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="4df1a-106">W ramach procedury i przykładu Użyj funkcji **EnumWindows** , aby przejść przez listę systemu Windows i zarządzaną funkcję wywołania zwrotnego (nazwanego wywołania zwrotnego) w celu wydrukowania wartości uchwytu okna.</span><span class="sxs-lookup"><span data-stu-id="4df1a-106">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="4df1a-107">Aby zaimplementować funkcję wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4df1a-107">To implement a callback function</span></span>  
  
1. <span data-ttu-id="4df1a-108">Przed przejściem do implementacji zapoznaj się z podpisem funkcji **EnumWindows** .</span><span class="sxs-lookup"><span data-stu-id="4df1a-108">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="4df1a-109">**EnumWindows** ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="4df1a-109">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="4df1a-110">Jedną z wskazówek, że ta funkcja wymaga wywołania zwrotnego, jest obecność argumentu **lpEnumFunc** .</span><span class="sxs-lookup"><span data-stu-id="4df1a-110">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="4df1a-111">Często widzisz prefiks **LP** (długi wskaźnik) połączony z sufiksem **Func** w nazwie argumentów, które przyjmują wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4df1a-111">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="4df1a-112">Aby uzyskać dokumentację dotyczącą funkcji Win32, zobacz zestaw SDK platformy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4df1a-112">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="4df1a-113">Utwórz zarządzaną funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4df1a-113">Create the managed callback function.</span></span> <span data-ttu-id="4df1a-114">Przykład deklaruje typ delegata o nazwie `CallBack` , który przyjmuje dwa argumenty (**HWND** i **lParam**).</span><span class="sxs-lookup"><span data-stu-id="4df1a-114">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="4df1a-115">Pierwszy argument jest dojściem do okna; drugi argument jest zdefiniowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4df1a-115">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="4df1a-116">W tej wersji oba argumenty muszą być liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="4df1a-116">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="4df1a-117">Funkcje wywołania zwrotnego zwykle zwracają wartości niezerowe, aby wskazać sukces i zero, aby wskazać błąd.</span><span class="sxs-lookup"><span data-stu-id="4df1a-117">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="4df1a-118">Ten przykład jawnie ustawia wartość zwracaną na **true** , aby kontynuować wyliczanie.</span><span class="sxs-lookup"><span data-stu-id="4df1a-118">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="4df1a-119">Utwórz delegata i przekaż go jako argument do funkcji **EnumWindows** .</span><span class="sxs-lookup"><span data-stu-id="4df1a-119">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="4df1a-120">Wywołanie platformy konwertuje delegata na automatycznie znany Format wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4df1a-120">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="4df1a-121">Upewnij się, że moduł zbierający elementy bezużyteczne nie odzyska delegata, zanim funkcja wywołania zwrotnego zakończy pracę.</span><span class="sxs-lookup"><span data-stu-id="4df1a-121">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="4df1a-122">Gdy przekazujesz delegata jako parametr lub Przekaż delegata zawarty jako pole w strukturze, pozostanie ono niezebrane na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="4df1a-122">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="4df1a-123">Tak więc, podobnie jak w poniższym przykładzie wyliczenia, funkcja wywołania zwrotnego uzupełnia swoją pracę przed wywołaniem zwrotnym i nie wymaga żadnych dodatkowych akcji przez zarządzany obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="4df1a-123">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="4df1a-124">Jeśli jednak funkcja wywołania zwrotnego może być wywoływana po wywołaniu zwrotnym, zarządzany obiekt wywołujący musi wykonać kroki, aby upewnić się, że delegat pozostanie niepobrany do momentu zakończenia funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4df1a-124">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="4df1a-125">Aby uzyskać szczegółowe informacje na temat zapobiegania wyrzucaniu elementów bezużytecznych, zobacz [Marshaling Interop](interop-marshaling.md) with platform Invoke.</span><span class="sxs-lookup"><span data-stu-id="4df1a-125">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df1a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="4df1a-126">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4df1a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4df1a-127">See also</span></span>

- [<span data-ttu-id="4df1a-128">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="4df1a-128">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="4df1a-129">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="4df1a-129">Calling a DLL Function</span></span>](calling-a-dll-function.md)
