---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: eb14e0df5396d92eb223dde2e562684c4c318295
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217568"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="efff2-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="efff2-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="efff2-103">Asystent debugowania zarządzanego `callbackOnCollectedDelegate` (MDA) jest aktywowany, jeśli delegat jest zorganizowany z zarządzanego do niezarządzanego kodu jako wskaźnik funkcji, a wywołanie zwrotne jest umieszczane na tym wskaźniku funkcji po usunięciu elementu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="efff2-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="efff2-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="efff2-104">Symptoms</span></span>  
 <span data-ttu-id="efff2-105">Podczas próby wywołania kodu zarządzanego za pomocą wskaźników funkcji uzyskanych z zarządzanych delegatów nastąpiły naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="efff2-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="efff2-106">Te błędy, podczas gdy nie występują usterki środowiska uruchomieniowego języka wspólnego (CLR), mogą wydawać się tak, ponieważ w kodzie CLR występuje naruszenie zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="efff2-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="efff2-107">Błąd nie jest spójny; Czasami wywołanie funkcji powiedzie się i czasami kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="efff2-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="efff2-108">Awaria może wystąpić tylko przy dużym obciążeniu lub losowej liczbie prób.</span><span class="sxs-lookup"><span data-stu-id="efff2-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="efff2-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="efff2-109">Cause</span></span>  
 <span data-ttu-id="efff2-110">Delegat, z którego został utworzony wskaźnik funkcji i ujawniony w kodzie niezarządzanym, został odrzucony.</span><span class="sxs-lookup"><span data-stu-id="efff2-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="efff2-111">Gdy składnik niezarządzany próbuje wywołać wskaźnik funkcji, generuje naruszenie zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="efff2-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="efff2-112">Błąd pojawia się losowo, ponieważ zależy od momentu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="efff2-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="efff2-113">Jeśli delegat kwalifikuje się do kolekcji, wyrzucanie elementów bezużytecznych może wystąpić po wywołaniu wywołania zwrotnego i wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="efff2-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="efff2-114">W innych przypadkach wyrzucanie elementów bezużytecznych występuje przed wywołaniem zwrotnym, wywołanie zwrotne generuje naruszenie zasad dostępu, a program zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="efff2-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="efff2-115">Prawdopodobieństwo wystąpienia błędu zależy od czasu między kierowaniem delegata i wywołaniem zwrotnym na wskaźniku funkcji, a także częstotliwością wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="efff2-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="efff2-116">Awaria jest sporadyczna, jeśli czas między kierowaniem delegata i wynikający z wywołania zwrotnego jest krótki.</span><span class="sxs-lookup"><span data-stu-id="efff2-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="efff2-117">Zwykle jest to przypadek, jeśli niezarządzana Metoda otrzymująca wskaźnik funkcji nie zapisuje wskaźnika funkcji do późniejszego użycia, ale zamiast tego ponownie wywołuje wskaźnik funkcji, aby zakończyć operację przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="efff2-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="efff2-118">Podobnie więcej wyrzucania elementów bezużytecznych występuje, gdy system jest mocno obciążony, co sprawia, że wyrzucanie elementów bezużytecznych zostanie przeprowadzone przed wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="efff2-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="efff2-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="efff2-119">Resolution</span></span>  
 <span data-ttu-id="efff2-120">Gdy delegat został zorganizowany jako wskaźnik funkcji niezarządzanej, Moduł wyrzucania elementów bezużytecznych nie może śledzić swojego okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="efff2-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="efff2-121">Zamiast tego kod musi przechowywać odwołanie do delegata dla okresu istnienia wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="efff2-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="efff2-122">Jednak przed wykonaniem tej czynności należy najpierw określić, który delegat został zebrany.</span><span class="sxs-lookup"><span data-stu-id="efff2-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="efff2-123">Gdy zdarzenie MDA zostanie aktywowane, zawiera nazwę typu delegata.</span><span class="sxs-lookup"><span data-stu-id="efff2-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="efff2-124">Użyj tej nazwy, aby przeszukać swój kod dla wywołania platformy lub sygnatur COM, które są przekazywane przez delegata do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="efff2-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="efff2-125">Nieprawidłowy delegat jest przepuszczany przez jedną z tych lokacji wywołań.</span><span class="sxs-lookup"><span data-stu-id="efff2-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="efff2-126">Możesz również włączyć `gcUnmanagedToManaged` MDA, aby wymusić wyrzucanie elementów bezużytecznych przed każdym wywołaniem zwrotnym do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="efff2-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="efff2-127">Spowoduje to usunięcie niepewności wprowadzonej przez wyrzucanie elementów bezużytecznych przez zapewnienie, że wyrzucanie elementów bezużytecznych zawsze występuje przed wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="efff2-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="efff2-128">Po uzyskaniu informacji o tym, który delegat został zebrany, Zmień kod, aby zachować odwołanie do tego delegata po stronie zarządzanej na potrzeby okresu istnienia organizowanego wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="efff2-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="efff2-129">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="efff2-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="efff2-130">Gdy Delegaty są organizowane jako wskaźniki funkcji, środowisko uruchomieniowe przydziela element thunk, który powoduje, że przejście z niezarządzanego do zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="efff2-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="efff2-131">Thunk jest to, co faktycznie wywołuje kod niezarządzany, zanim zarządzany delegat jest ostatecznie wywoływany.</span><span class="sxs-lookup"><span data-stu-id="efff2-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="efff2-132">Bez włączonej `callbackOnCollectedDelegate` MDA, niezarządzany kod kierujący jest usuwany podczas zbierania delegata.</span><span class="sxs-lookup"><span data-stu-id="efff2-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="efff2-133">Po włączeniu `callbackOnCollectedDelegate` MDA, niezarządzany kod kierujący nie zostanie natychmiast usunięty po zebraniu delegata.</span><span class="sxs-lookup"><span data-stu-id="efff2-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="efff2-134">Zamiast tego ostatnie wystąpienia 1 000 są utrzymywane domyślnie i zmieniane w celu aktywowania MDA po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="efff2-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="efff2-135">Thunk jest ostatecznie usuwana po 1 001 większej liczby delegatów zorganizowanych.</span><span class="sxs-lookup"><span data-stu-id="efff2-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="efff2-136">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="efff2-136">Output</span></span>  
 <span data-ttu-id="efff2-137">Zdarzenie MDA raportuje nazwę typu delegata, który został zebrany przed podjęciem próby wywołania zwrotnego na niezarządzanym wskaźniku funkcji.</span><span class="sxs-lookup"><span data-stu-id="efff2-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="efff2-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="efff2-138">Configuration</span></span>  
 <span data-ttu-id="efff2-139">W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efff2-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="efff2-140">Ustawia liczbę sekcje thunk, że zdarzenie MDA utrzymuje aktywność do 1 500.</span><span class="sxs-lookup"><span data-stu-id="efff2-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="efff2-141">Wartość domyślna `listSize` to 1 000, minimum to 50, a maksymalna to 2 000.</span><span class="sxs-lookup"><span data-stu-id="efff2-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="efff2-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="efff2-142">Example</span></span>  
 <span data-ttu-id="efff2-143">Poniższy przykład ilustruje sytuację, w której można aktywować to MDA:</span><span class="sxs-lookup"><span data-stu-id="efff2-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="efff2-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efff2-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="efff2-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="efff2-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="efff2-146">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="efff2-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="efff2-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="efff2-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
