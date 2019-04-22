---
title: wielobieżność MDA
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094219"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="dd1d9-102">wielobieżność MDA</span><span class="sxs-lookup"><span data-stu-id="dd1d9-102">reentrancy MDA</span></span>
<span data-ttu-id="dd1d9-103">`reentrancy` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy podejmowana jest próba przejścia z natywnego do zarządzanego kodu w przypadkach, gdzie wcześniejsze przełącznika z kodu zarządzanego do natywnego nie było wykonywane za pośrednictwem przejścia.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="dd1d9-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="dd1d9-104">Symptoms</span></span>  
 <span data-ttu-id="dd1d9-105">Sterty obiektów jest uszkodzony lub inne poważne błędy występują w przypadku przechodzenia z natywnego do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="dd1d9-106">Wątki, przełączać się między kodu natywnego i zarządzanego w dowolnym kierunku, które należy wykonać przejścia.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="dd1d9-107">Jednak niektóre punkty rozszerzeń niskiego poziomu, w systemie operacyjnym, takich jak wektorowa obsługa wyjątków, umożliwia przełączników z kodu zarządzanego do natywnego kodu bez przeprowadzania przejścia.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="dd1d9-108">Te przełączniki są pod kontrolą systemu operacyjnego, a nie kontrolowanymi języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="dd1d9-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="dd1d9-109">Kodu macierzystego, który jest wykonywany wewnątrz te punkty rozszerzeń należy unikać wywołań zwrotnych do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="dd1d9-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="dd1d9-110">Cause</span></span>  
 <span data-ttu-id="dd1d9-111">Punkt rozszerzeń niskiego poziomu systemu operacyjnego, takie jak wektorowa obsługa wyjątków, zostało uaktywnione podczas wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="dd1d9-112">Kod aplikacji, która jest wywoływana za pomocą tego punktu rozszerzalności podejmuje próbę wywołania zwrotnego w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="dd1d9-113">Ten problem, zawsze jest spowodowane przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="dd1d9-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="dd1d9-114">Resolution</span></span>  
 <span data-ttu-id="dd1d9-115">Sprawdź ślad stosu dla wątku, który uaktywnił to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="dd1d9-116">Wątek podejmuje próbę nielegalnego mogą wywoływać kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="dd1d9-117">Ślad stosu powinno ujawnić, kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zawiera ten punkt rozszerzeń i kodu zarządzanego, który został przerwany przez punkt rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="dd1d9-118">Na przykład zobaczysz MDA aktywacji w celu wywołania kodu zarządzanego z wewnątrz wektorowa obsługa wyjątków.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="dd1d9-119">Na stosie zobaczysz obsługi kodu i niektórych kodu zarządzanego, takie jak wyzwolenie wyjątek wyjątków systemu operacyjnego <xref:System.DivideByZeroException> lub <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="dd1d9-120">W tym przykładzie poprawnego rozpoznawania jest całkowicie zaimplementować wektorowa obsługa wyjątków w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="dd1d9-121">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="dd1d9-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="dd1d9-122">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="dd1d9-123">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="dd1d9-123">Output</span></span>  
 <span data-ttu-id="dd1d9-124">MDA zgłasza, że niedozwolona wielobieżność zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="dd1d9-125">Sprawdź stosu wątku w celu ustalenia, dlaczego to się dzieje i jak rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="dd1d9-126">Poniżej przedstawiono przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="dd1d9-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="dd1d9-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="dd1d9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd1d9-128">Example</span></span>  
 <span data-ttu-id="dd1d9-129">Poniższy kod powoduje, że przykład <xref:System.AccessViolationException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="dd1d9-130">W wersjach systemu Windows, który obsługuje wektorowa wyjątków spowoduje to zarządzane wektorowa obsługa wyjątków do wywołania.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="dd1d9-131">Jeśli `reentrancy` MDA jest włączona, MDA uaktywni się podczas próby wywołania `MyHandler` z systemu operacyjnego wyjątek wektorowa obsługi kod pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd1d9-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd1d9-132">See also</span></span>

- [<span data-ttu-id="dd1d9-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="dd1d9-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
