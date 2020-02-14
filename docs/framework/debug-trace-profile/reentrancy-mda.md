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
ms.openlocfilehash: 8f1621090079c030e3c055a417ed9bcad882bf78
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217232"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="b2539-102">wielobieżność MDA</span><span class="sxs-lookup"><span data-stu-id="b2539-102">reentrancy MDA</span></span>
<span data-ttu-id="b2539-103">Asystent debugowania zarządzanego `reentrancy` (MDA) jest uaktywniany, gdy podejmowana jest próba przejścia z macierzystego do kodu zarządzanego w przypadkach, gdy wcześniejsze przełączenie z kodu zarządzanego na kod natywny nie było wykonywane za pośrednictwem przejścia uporządkowanego.</span><span class="sxs-lookup"><span data-stu-id="b2539-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b2539-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="b2539-104">Symptoms</span></span>  
 <span data-ttu-id="b2539-105">Sterta obiektu jest uszkodzona lub występują inne poważne błędy podczas przechodzenia z kodu natywnego do zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b2539-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="b2539-106">Wątki przełączające się między kodem natywnym i zarządzanym w obu kierunkach muszą wykonywać uporządkowane przejścia.</span><span class="sxs-lookup"><span data-stu-id="b2539-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="b2539-107">Jednak niektóre punkty rozszerzenia niskiego poziomu w systemie operacyjnym, takie jak obsługa wyjątków wektorowych, zezwalają na przełączanie z kodu zarządzanego na natywny bez wykonywania uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="b2539-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="b2539-108">Te przełączniki są pod kontrolą systemu operacyjnego, a nie pod kontrolą środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b2539-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="b2539-109">Każdy kod natywny, który jest wykonywany w tych punktach rozszerzalności, musi unikać wywoływania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b2539-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b2539-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b2539-110">Cause</span></span>  
 <span data-ttu-id="b2539-111">Punkt rozszerzalności systemu operacyjnego niskiego poziomu, taki jak program obsługi wyjątków wektorowych, został aktywowany podczas wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b2539-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="b2539-112">Kod aplikacji, który jest wywoływany przez ten punkt rozszerzalności, próbuje wywołać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b2539-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="b2539-113">Ten problem jest zawsze spowodowany przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2539-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b2539-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b2539-114">Resolution</span></span>  
 <span data-ttu-id="b2539-115">Przejrzyj ślad stosu dla wątku, który uaktywnił to MDA.</span><span class="sxs-lookup"><span data-stu-id="b2539-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="b2539-116">Wątek próbuje niedozwolone wywołanie w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b2539-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="b2539-117">Ślad stosu powinien ujawnić kod aplikacji przy użyciu tego punktu rozszerzalności, kodu systemu operacyjnego, który zapewnia ten punkt rozszerzalności, oraz kodu zarządzanego, który został przerwany przez punkt rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="b2539-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="b2539-118">Na przykład zobaczysz, że element MDA został aktywowany w trakcie próby wywołania kodu zarządzanego z wewnątrz wektorowego programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b2539-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="b2539-119">Na stosie zobaczysz kod obsługi wyjątków systemu operacyjnego i jakiś kod zarządzany wyzwalający wyjątek, taki jak <xref:System.DivideByZeroException> lub <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="b2539-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="b2539-120">W tym przykładzie poprawne rozwiązanie polega na zaimplementowaniu w całości kodu niezarządzanego programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b2539-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b2539-121">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b2539-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="b2539-122">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="b2539-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b2539-123">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b2539-123">Output</span></span>  
 <span data-ttu-id="b2539-124">Podjęto próbę wykonania niedozwolonych współużytkowania wątkowości w raportach MDA.</span><span class="sxs-lookup"><span data-stu-id="b2539-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="b2539-125">Sprawdź stos wątku, aby określić, dlaczego dzieje się tak i jak rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="b2539-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="b2539-126">Poniżej przedstawiono przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b2539-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="b2539-127">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b2539-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="b2539-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2539-128">Example</span></span>  
 <span data-ttu-id="b2539-129">Poniższy przykład kodu powoduje zgłoszenie <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="b2539-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="b2539-130">W przypadku wersji systemu Windows, które obsługują obsługę wyjątków wektorowych, spowoduje to wywołanie zarządzanej procedury obsługi wyjątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="b2539-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="b2539-131">Jeśli `reentrancy` MDA jest włączona, zdarzenie MDA zostanie aktywowane podczas próby wywołania `MyHandler` z obsłudze wyjątków wektorowego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b2539-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2539-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2539-132">See also</span></span>

- [<span data-ttu-id="b2539-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b2539-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
