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
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181763"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="d46d1-102">wielobieżność MDA</span><span class="sxs-lookup"><span data-stu-id="d46d1-102">reentrancy MDA</span></span>
<span data-ttu-id="d46d1-103">Asystent `reentrancy` debugowania zarządzanego (MDA) jest aktywowany, gdy podejmowana jest próba przejścia z kodu macierzystego do zarządzanego w przypadkach, gdy wcześniejsze przejście z kodu natywnego nie zostało wykonane za pośrednictwem uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="d46d1-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d46d1-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="d46d1-104">Symptoms</span></span>  
 <span data-ttu-id="d46d1-105">Sterta obiektu jest uszkodzona lub inne poważne błędy występują podczas przechodzenia z kodu macierzystego do zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d46d1-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="d46d1-106">Wątki, które przełączają się między kodem macierzystym i zarządzanym w obu kierunkach, muszą wykonać uporządkowane przejście.</span><span class="sxs-lookup"><span data-stu-id="d46d1-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="d46d1-107">Jednak niektóre punkty rozszerzalności niskiego poziomu w systemie operacyjnym, takie jak program obsługi wyjątków wektorowych, umożliwiają przełączanie z kodu natywnego bez przeprowadzania uporządkowanego przejścia.</span><span class="sxs-lookup"><span data-stu-id="d46d1-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="d46d1-108">Te przełączniki są pod kontrolą systemu operacyjnego, a nie pod kontrolą wspólnego środowiska wykonawczego języka (CLR).</span><span class="sxs-lookup"><span data-stu-id="d46d1-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="d46d1-109">Każdy kod macierzysty, który wykonuje wewnątrz tych punktów rozszerzalności należy unikać wywoływania z powrotem do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d46d1-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d46d1-110">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d46d1-110">Cause</span></span>  
 <span data-ttu-id="d46d1-111">Niski poziom punktu rozszerzalności systemu operacyjnego, takich jak wektorowy program obsługi wyjątków, został aktywowany podczas wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d46d1-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="d46d1-112">Kod aplikacji, który jest wywoływany za pośrednictwem tego punktu rozszerzalności próbuje wywołać z powrotem do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d46d1-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="d46d1-113">Ten problem jest zawsze spowodowany przez kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d46d1-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d46d1-114">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d46d1-114">Resolution</span></span>  
 <span data-ttu-id="d46d1-115">Sprawdź ślad stosu dla wątku, który aktywował ten MDA.</span><span class="sxs-lookup"><span data-stu-id="d46d1-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="d46d1-116">Wątek próbuje nielegalnie wywołać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d46d1-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="d46d1-117">Ślad stosu powinien ujawnić kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zapewnia ten punkt rozszerzalności i kod zarządzany, który został przerwany przez punkt rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="d46d1-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="d46d1-118">Na przykład zostanie wyświetlony MDA aktywowany w próbie wywołania kodu zarządzanego z wewnątrz wektorowego programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d46d1-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="d46d1-119">Na stosie zobaczysz kod obsługi wyjątków systemu operacyjnego i niektóre <xref:System.DivideByZeroException> kody <xref:System.AccessViolationException>zarządzane wyzwalające wyjątek, taki jak a lub .</span><span class="sxs-lookup"><span data-stu-id="d46d1-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="d46d1-120">W tym przykładzie prawidłowe rozwiązanie jest do zaimplementowania wektorowego obsługi wyjątków całkowicie w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d46d1-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d46d1-121">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="d46d1-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="d46d1-122">To MDA nie ma wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="d46d1-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d46d1-123">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d46d1-123">Output</span></span>  
 <span data-ttu-id="d46d1-124">MDA informuje, że podejmowane są próby nielegalnego ponownego wejścia na boja.</span><span class="sxs-lookup"><span data-stu-id="d46d1-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="d46d1-125">Sprawdź stos wątku, aby ustalić, dlaczego tak się dzieje i jak rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="d46d1-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="d46d1-126">Poniżej przedstawiono dane wyjściowe próbki.</span><span class="sxs-lookup"><span data-stu-id="d46d1-126">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="d46d1-127">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="d46d1-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="d46d1-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d46d1-128">Example</span></span>  
 <span data-ttu-id="d46d1-129">Poniższy przykład kodu <xref:System.AccessViolationException> powoduje, że mają być generowane.</span><span class="sxs-lookup"><span data-stu-id="d46d1-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="d46d1-130">W wersjach systemu Windows, które obsługują wektorowe obsługi wyjątków, spowoduje to, że zarządzany program obsługi wyjątków wektorowych do wywołania.</span><span class="sxs-lookup"><span data-stu-id="d46d1-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="d46d1-131">Jeśli `reentrancy` MDA jest włączona, MDA aktywuje się `MyHandler` podczas próby wywołania z systemu operacyjnego wektorowe kod obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d46d1-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d46d1-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d46d1-132">See also</span></span>

- [<span data-ttu-id="d46d1-133">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d46d1-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
