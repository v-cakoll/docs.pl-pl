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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31aa9f18729bf5d85e28d484f5fd1f5aac762470
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593540"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="75e5c-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="75e5c-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="75e5c-103">`callbackOnCollectedDelegate` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli obiekt delegowany jest przekazywane z kodu zarządzanego do kodu niezarządzanego jako wskaźnik funkcji i wywołanie zwrotne jest umieszczany na ten wskaźnik funkcji bezużyteczne po delegata.</span><span class="sxs-lookup"><span data-stu-id="75e5c-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="75e5c-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="75e5c-104">Symptoms</span></span>  
 <span data-ttu-id="75e5c-105">Naruszenia zasad dostępu wystąpić, gdy próba wywołania kodu zarządzanego za pomocą wskaźników funkcji, które zostały uzyskane z zarządzanych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="75e5c-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="75e5c-106">Te błędy, podczas nie typowych błędów języka środowiska uruchomieniowego (języka wspólnego CLR), może wydawać się być tak, ponieważ naruszenie zasad dostępu odbywa się w kodzie CLR.</span><span class="sxs-lookup"><span data-stu-id="75e5c-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="75e5c-107">Błąd nie jest zgodne ze sobą. Czasami połączenie na wskaźnik funkcji zakończy się powodzeniem, a czasami kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="75e5c-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="75e5c-108">Błąd może wystąpić tylko pod dużym obciążeniem, lub na liczbę losową liczbę prób.</span><span class="sxs-lookup"><span data-stu-id="75e5c-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="75e5c-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="75e5c-109">Cause</span></span>  
 <span data-ttu-id="75e5c-110">Delegat, z którego została utworzona i udostępniana dla kodu niezarządzanego wskaźnik funkcji było bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="75e5c-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="75e5c-111">Gdy składnik niezarządzanych próbuje wywołać na wskaźnik funkcji, generuje naruszenie zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="75e5c-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="75e5c-112">Błąd pojawia się losowych, ponieważ zależy podczas wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75e5c-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="75e5c-113">Jeśli obiekt delegowany kwalifikuje się do kolekcji wyrzucania elementów bezużytecznych może wystąpić po wywołania zwrotnego i wywołanie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="75e5c-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="75e5c-114">W pozostałym czasie wyrzucania elementów bezużytecznych występuje przed wywołania zwrotnego, wywołanie zwrotne generuje naruszenie zasad dostępu i zatrzymuje program.</span><span class="sxs-lookup"><span data-stu-id="75e5c-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="75e5c-115">Prawdopodobieństwo awarii zależy od czasu między marshaling delegata i wywołania zwrotnego na wskaźnik funkcji, jak i częstotliwość wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="75e5c-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="75e5c-116">Błąd jest sporadyczne, jeśli czas między marshaling delegata i wynikający z tego wywołania zwrotnego jest krótki.</span><span class="sxs-lookup"><span data-stu-id="75e5c-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="75e5c-117">Jest to zazwyczaj tak, jeśli metoda niezarządzanego odbieranie wskaźnik funkcji nie jest zapisywany wskaźnik funkcji do późniejszego użycia, ale zamiast tego ponownie wywołuje na wskaźnik funkcji, aby ukończyć jej działania przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="75e5c-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="75e5c-118">Podobnie więcej wyrzucania elementów bezużytecznych wystąpić, gdy system jest mocno obciążony, co pozwala na bardziej prawdopodobne, że wyrzucania elementów bezużytecznych nastąpi przed wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="75e5c-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="75e5c-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="75e5c-119">Resolution</span></span>  
 <span data-ttu-id="75e5c-120">Gdy obiekt delegowany został przekazany się jak wskaźnik funkcji niezarządzanej, moduł odśmiecania pamięci nie można śledzić jego okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="75e5c-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="75e5c-121">Zamiast tego kod musi przechowywać odwołanie do obiektu delegowanego okres istnienia wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="75e5c-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="75e5c-122">Jednak zanim to zrobić, należy najpierw zidentyfikować delegata, który został zebrany.</span><span class="sxs-lookup"><span data-stu-id="75e5c-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="75e5c-123">Gdy zdarzenie MDA jest aktywowane, zawiera nazwę typu delegata.</span><span class="sxs-lookup"><span data-stu-id="75e5c-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="75e5c-124">Należy użyć tej nazwy do wyszukiwania wywołania kodu platformy lub podpisy COM, które przekazać delegata do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="75e5c-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="75e5c-125">Naruszającym delegata jest przekazywana jeden z nich wywołania.</span><span class="sxs-lookup"><span data-stu-id="75e5c-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="75e5c-126">Można również włączyć `gcUnmanagedToManaged` MDA do wymuszenia wyrzucania elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="75e5c-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="75e5c-127">Spowoduje to usunięcie niepewności wprowadzone przez wyrzucanie elementów bezużytecznych poprzez zapewnienie, że zawsze wyrzucania elementów bezużytecznych występuje przed wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="75e5c-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="75e5c-128">Wiesz, jakie delegata został zebrany, zmień swój kod, aby zachować odwołanie do delegata stronie zarządzanej okres istnienia wskaźnika zorganizowanej niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="75e5c-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="75e5c-129">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="75e5c-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="75e5c-130">Gdy obiekty delegowane są przekazywane jako wskaźniki funkcji, środowisko uruchomieniowe przydziela thunk, który wykonuje przejścia z niezarządzanych w zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="75e5c-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="75e5c-131">To wywołanie jest co kod niezarządzany wywołuje przed zarządzany obiekt delegowany na koniec jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="75e5c-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="75e5c-132">Bez `callbackOnCollectedDelegate` MDA włączona, organizowanie kodu niezarządzanego jest usuwany po delegata są zbierane.</span><span class="sxs-lookup"><span data-stu-id="75e5c-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="75e5c-133">Za pomocą `callbackOnCollectedDelegate` MDA włączona, niezarządzanych organizowanie kodu nie są natychmiast usuwane w przypadku delegata są zbierane.</span><span class="sxs-lookup"><span data-stu-id="75e5c-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="75e5c-134">Zamiast tego ostatniego 1000 wystąpień są życiu domyślnie i zmienione w celu aktywowania MDA, gdy zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="75e5c-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="75e5c-135">Thunk został usunięty po pewnym czasie, gdy 1,001 bardziej zorganizowanej obiekty delegowane są zbierane.</span><span class="sxs-lookup"><span data-stu-id="75e5c-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="75e5c-136">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="75e5c-136">Output</span></span>  
 <span data-ttu-id="75e5c-137">MDA raporty nazwę typu delegata, który został zebrany przed podjęto próbę wywołania zwrotnego na swojego wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="75e5c-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="75e5c-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="75e5c-138">Configuration</span></span>  
 <span data-ttu-id="75e5c-139">Poniższy przykład przedstawia opcje konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75e5c-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="75e5c-140">Ustawia liczbę sekcje Thunk, który MDA utrzymuje aktywność do 1500.</span><span class="sxs-lookup"><span data-stu-id="75e5c-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="75e5c-141">Wartość domyślna `listSize` wartość wynosi 1000, minimum to 50, a wartość maksymalna to 2000.</span><span class="sxs-lookup"><span data-stu-id="75e5c-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="75e5c-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="75e5c-142">Example</span></span>  
 <span data-ttu-id="75e5c-143">W poniższym przykładzie pokazano sytuację, która może aktywować to zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="75e5c-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75e5c-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75e5c-144">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="75e5c-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="75e5c-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="75e5c-146">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="75e5c-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
- [<span data-ttu-id="75e5c-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="75e5c-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
