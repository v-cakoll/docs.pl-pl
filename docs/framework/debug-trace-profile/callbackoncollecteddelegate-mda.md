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
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174228"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="4753a-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="4753a-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="4753a-103">Zarządzany `callbackOnCollectedDelegate` asystent debugowania (MDA) jest aktywowany, jeśli pełnomocnik jest organizowany z zarządzanego kodu jako wskaźnik funkcji i wywołania zwrotnego jest umieszczana na tym wskaźniku funkcji po delegat został zebranych śmieci.</span><span class="sxs-lookup"><span data-stu-id="4753a-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4753a-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="4753a-104">Symptoms</span></span>  
 <span data-ttu-id="4753a-105">Naruszenia dostępu występują podczas próby wywołania kodu zarządzanego za pomocą wskaźników funkcji, które zostały uzyskane od zarządzanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="4753a-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="4753a-106">Te błędy, podczas gdy nie ma błędów wspólnego środowiska wykonawczego języka (CLR), może wydawać się tak, ponieważ naruszenie zasad dostępu występuje w kodzie CLR.</span><span class="sxs-lookup"><span data-stu-id="4753a-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="4753a-107">Błąd nie jest spójny; czasami wywołanie wskaźnika funkcji powiedzie się, a czasami kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="4753a-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="4753a-108">Awaria może wystąpić tylko przy dużym obciążeniu lub przy losowej liczbie prób.</span><span class="sxs-lookup"><span data-stu-id="4753a-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4753a-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="4753a-109">Cause</span></span>  
 <span data-ttu-id="4753a-110">Delegat, z którego został utworzony wskaźnik funkcji i narażone na kod niezarządzane został zebranych śmieci.</span><span class="sxs-lookup"><span data-stu-id="4753a-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="4753a-111">Gdy składnik niezarządzane próbuje wywołać wskaźnik funkcji, generuje naruszenie zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="4753a-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="4753a-112">Błąd pojawia się losowo, ponieważ zależy od tego, kiedy występuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4753a-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="4753a-113">Jeśli pełnomocnik kwalifikuje się do odbioru, wyrzucania elementów bezużytecznych może wystąpić po wywołaniu zwrotnym i wywołanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4753a-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="4753a-114">W innych przypadkach wyrzucania elementów bezużytecznych występuje przed wywołaniem zwrotnym, wywołanie zwrotne generuje naruszenie zasad dostępu, a program zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="4753a-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="4753a-115">Prawdopodobieństwo awarii zależy od czasu między kierowanie delegata i wywołania zwrotnego na wskaźnik funkcji, a także częstotliwość wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4753a-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="4753a-116">Błąd jest sporadyczne, jeśli czas między kierowanie delegata i wywołanie zwrotne wynika jest krótki.</span><span class="sxs-lookup"><span data-stu-id="4753a-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="4753a-117">Zazwyczaj jest tak, jeśli metoda niezarządzana odbierająca wskaźnik funkcji nie zapisuje wskaźnika funkcji do późniejszego użycia, ale zamiast tego natychmiast wywołuje wskaźnik funkcji, aby zakończyć jego działanie przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="4753a-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="4753a-118">Podobnie więcej wyrzucania elementów bezużytecznych występuje, gdy system jest pod dużym obciążeniem, co sprawia, że bardziej prawdopodobne, że wyrzucanie elementów bezużytecznych wystąpi przed wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="4753a-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4753a-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4753a-119">Resolution</span></span>  
 <span data-ttu-id="4753a-120">Gdy delegat został zorganizowany jako wskaźnik funkcji niezarządzane, moduł zbierający elementy bezużyteczne nie może śledzić jego istnienia.</span><span class="sxs-lookup"><span data-stu-id="4753a-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="4753a-121">Zamiast tego kod musi zachować odwołanie do pełnomocnika przez cały okres istnienia wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4753a-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="4753a-122">Ale zanim będzie można to zrobić, należy najpierw określić, który delegat został zebrany.</span><span class="sxs-lookup"><span data-stu-id="4753a-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="4753a-123">Po aktywowaniu mda, zawiera nazwę typu delegata.</span><span class="sxs-lookup"><span data-stu-id="4753a-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="4753a-124">Ta nazwa służy do wyszukiwania kodu dla platformy wywołać lub sygnatury COM, które przekazują, że delegata do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4753a-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="4753a-125">Pełnomocnik naruszający jest przekazywane za pośrednictwem jednej z tych witryn wywołania.</span><span class="sxs-lookup"><span data-stu-id="4753a-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="4753a-126">Można również włączyć `gcUnmanagedToManaged` MDA wymusić wyrzucania elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4753a-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="4753a-127">Spowoduje to usunięcie niepewności wprowadzone przez wyrzucania elementów bezużytecznych, zapewniając, że wyrzucanie elementów bezużytecznych zawsze występuje przed wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="4753a-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="4753a-128">Gdy wiesz, co delegat został zebrany, należy zmienić kod, aby zachować odwołanie do tego delegata po stronie zarządzanej przez cały okres istnienia wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="4753a-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4753a-129">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="4753a-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="4753a-130">Gdy delegaci są organizowane jako wskaźniki funkcji, środowisko wykonawcze przydziela thunk, który wykonuje przejście z niezarządzane do zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4753a-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="4753a-131">To thunk jest to, co kod niezarządzany faktycznie wywołuje przed zarządzanym delegatem jest ostatecznie wywoływane.</span><span class="sxs-lookup"><span data-stu-id="4753a-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="4753a-132">Bez `callbackOnCollectedDelegate` włączone MDA niezarządzanego kodu kierowania jest usuwany, gdy pełnomocnik jest zbierany.</span><span class="sxs-lookup"><span data-stu-id="4753a-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="4753a-133">Z `callbackOnCollectedDelegate` mda włączone, niezarządzany kod kierowanie nie jest natychmiast usuwany podczas pobierania pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="4753a-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="4753a-134">Zamiast tego ostatnie 1000 wystąpień są domyślnie utrzymywane przy życiu i zmieniane, aby aktywować MDA po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="4753a-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="4753a-135">Thunk jest ostatecznie usuwany po 1001 więcej marshaled delegatów są zbierane.</span><span class="sxs-lookup"><span data-stu-id="4753a-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4753a-136">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4753a-136">Output</span></span>  
 <span data-ttu-id="4753a-137">MDA raportuje nazwę typu delegata, który został zebrany przed wywołaniem zwrotnym próbowano na jego wskaźnik funkcji niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="4753a-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4753a-138">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="4753a-138">Configuration</span></span>  
 <span data-ttu-id="4753a-139">W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4753a-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="4753a-140">Ustawia liczbę thunks MDA utrzymuje przy życiu do 1500.</span><span class="sxs-lookup"><span data-stu-id="4753a-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="4753a-141">Wartość `listSize` domyślna to 1000, minimalna 50, a maksymalna 2000.</span><span class="sxs-lookup"><span data-stu-id="4753a-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4753a-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="4753a-142">Example</span></span>  
 <span data-ttu-id="4753a-143">Poniższy przykład pokazuje sytuację, która może aktywować ten MDA:</span><span class="sxs-lookup"><span data-stu-id="4753a-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4753a-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4753a-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4753a-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="4753a-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4753a-146">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="4753a-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="4753a-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="4753a-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
