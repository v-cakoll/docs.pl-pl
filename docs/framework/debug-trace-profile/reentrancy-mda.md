---
title: "wielobieżność MDA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a54a985abbc59aea0eeb46cc74560485e86b897d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reentrancy-mda"></a><span data-ttu-id="f9640-102">wielobieżność MDA</span><span class="sxs-lookup"><span data-stu-id="f9640-102">reentrancy MDA</span></span>
<span data-ttu-id="f9640-103">`reentrancy` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy podejmowana jest próba przejście z kodu natywnego do zarządzanego kodu w przypadkach, gdy wcześniejsze przełącznika z kodu zarządzanego do natywnego nie została wykonana za pomocą uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="f9640-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f9640-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f9640-104">Symptoms</span></span>  
 <span data-ttu-id="f9640-105">Sterty obiektów jest uszkodzony lub innych błędów występujących podczas przejścia z kodu natywnego do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f9640-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="f9640-106">Wątki przełączania się między kodu natywnego i zarządzanego w żadnym kierunku, należy wykonać uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="f9640-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="f9640-107">Jednak niektórych punktów rozszerzalności niskiego poziomu systemu operacyjnego, takich jak wektorowa obsługa wyjątków, Zezwalaj przełączników z zarządzanego do kodu macierzystego bez uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="f9640-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="f9640-108">Te przełączniki są pod kontrolą systemu operacyjnego, a nie pod kontrolą języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f9640-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="f9640-109">Kod natywny, wykonujący wewnątrz tych punktów rozszerzalności należy unikać wywołań zwrotnych do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f9640-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f9640-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f9640-110">Cause</span></span>  
 <span data-ttu-id="f9640-111">Punktów rozszerzalności niskiego poziomu systemu operacyjnego, takich jak wektorowa obsługa wyjątków, zostało uaktywnione podczas wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f9640-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="f9640-112">Kod aplikacji, które jest wywoływane przez ten punkt rozszerzalności próbuje wywołanie zwrotne do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f9640-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="f9640-113">Przyczyną tego problemu jest zawsze kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9640-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f9640-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f9640-114">Resolution</span></span>  
 <span data-ttu-id="f9640-115">Sprawdź, czy śledzenia stosu dla wątku, który został aktywowany to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="f9640-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="f9640-116">Wątek próbuje nielegalnego wywołania wewnątrz kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f9640-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="f9640-117">Ślad stosu powinno ujawnić kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zawiera ten punkt rozszerzeń i kod zarządzany, który został przerwany przez punkt rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="f9640-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="f9640-118">Na przykład zobaczysz MDA aktywować próba wywołania kodu zarządzanego z wewnątrz wektorowa obsługa wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f9640-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="f9640-119">Na stosie zobaczysz obsługi kodu i niektóre kod zarządzany, takich jak wyzwalają wyjątek wyjątków systemu operacyjnego <xref:System.DivideByZeroException> lub <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="f9640-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="f9640-120">W tym przykładzie poprawnego rozpoznawania jest całkowicie implementacja wektorowa obsługa wyjątków za pomocą kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f9640-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f9640-121">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f9640-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="f9640-122">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f9640-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f9640-123">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f9640-123">Output</span></span>  
 <span data-ttu-id="f9640-124">MDA zgłasza, że niedozwolona wielobieżność podjęto próbę.</span><span class="sxs-lookup"><span data-stu-id="f9640-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="f9640-125">Sprawdź, czy stosu wątku w celu ustalenia, dlaczego zdarza się to i sposobu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="f9640-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="f9640-126">Oto przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="f9640-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="f9640-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f9640-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f9640-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9640-128">Example</span></span>  
 <span data-ttu-id="f9640-129">Poniższy kod przyczyny przykład <xref:System.AccessViolationException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="f9640-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="f9640-130">W wersjach systemu Windows, który obsługi wyjątków wektorowa spowoduje to zarządzany wektorowa obsługa wyjątków do wywołania.</span><span class="sxs-lookup"><span data-stu-id="f9640-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="f9640-131">Jeśli `reentrancy` MDA jest włączona, MDA uaktywni się podczas próby wywołania `MyHandler` z systemu operacyjnego wyjątek wektorowa obsługa kodu pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="f9640-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="f9640-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9640-132">See Also</span></span>  
 [<span data-ttu-id="f9640-133">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f9640-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
