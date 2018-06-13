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
ms.openlocfilehash: 0aa9ecd357a192eba64cc14f8940b264461b5e74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356359"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="27dcf-102">callbackOnCollectedDelegate MDA</span><span class="sxs-lookup"><span data-stu-id="27dcf-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="27dcf-103">`callbackOnCollectedDelegate` Zarządzany Asystent debugowania (MDA) jest włączone, jeśli delegat jest przekazywane z kodu zarządzanego do kodu niezarządzanego jako wskaźnik funkcji i wywołanie zwrotne jest umieszczona na wskaźnik tej funkcji po bezużytecznych delegata.</span><span class="sxs-lookup"><span data-stu-id="27dcf-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="27dcf-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="27dcf-104">Symptoms</span></span>  
 <span data-ttu-id="27dcf-105">Naruszenia zasad dostępu występują, jeśli próba wywołania wewnątrz kodu zarządzanego za pośrednictwem wskaźników funkcji, które zostały uzyskane z zarządzanych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="27dcf-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="27dcf-106">Te błędy podczas nie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) usterki, mogą sprawiać, ponieważ naruszenie zasad dostępu występuje w kodzie CLR.</span><span class="sxs-lookup"><span data-stu-id="27dcf-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="27dcf-107">Błąd nie jest zgodne ze sobą. Czasami wywołania na wskaźnik funkcji zakończy się powodzeniem i czasami kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="27dcf-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="27dcf-108">Błąd może wystąpić tylko obciążona lub losową liczbę prób.</span><span class="sxs-lookup"><span data-stu-id="27dcf-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="27dcf-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="27dcf-109">Cause</span></span>  
 <span data-ttu-id="27dcf-110">Delegat, z którego została utworzona i ujawniony dla kodu niezarządzanego wskaźnika funkcji została wyrzucona jako element bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="27dcf-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="27dcf-111">Próba wywołania na wskaźnik funkcji przez składnik niezarządzane generuje naruszenia zasad dostępu.</span><span class="sxs-lookup"><span data-stu-id="27dcf-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="27dcf-112">Błąd pojawia się losowych, ponieważ zależy po wystąpieniu wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="27dcf-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="27dcf-113">Jeśli delegat jest uprawniona do kolekcji, wyrzucanie elementów bezużytecznych może wystąpić po wywołania zwrotnego i wywołanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="27dcf-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="27dcf-114">W pozostałych godzinach wyrzucanie elementów bezużytecznych występuje przed wywołania zwrotnego, wywołania zwrotnego generuje naruszenia zasad dostępu i zatrzymuje program.</span><span class="sxs-lookup"><span data-stu-id="27dcf-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="27dcf-115">Prawdopodobieństwo wystąpienia błędu zależy od czasu między marshaling delegata i wywołania zwrotnego na wskaźnik funkcji, jak i częstotliwość odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="27dcf-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="27dcf-116">Błąd jest sporadyczne, jeśli jest krótki czas między marshaling delegata i następujących wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27dcf-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="27dcf-117">Jest to zwykle wielkość liter, jeśli metoda niezarządzanego odbieranie wskaźnik funkcji nie powoduje zapisania wskaźnik funkcji do późniejszego użycia, ale zamiast tego wywołuje na wskaźnik funkcji natychmiast, aby ukończyć jej działania przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="27dcf-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="27dcf-118">Podobnie więcej wyrzucania wystąpić, gdy system jest mocno obciążony, co pozwala na bardziej prawdopodobne, że przed wywołania zwrotnego nastąpi wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="27dcf-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="27dcf-119">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="27dcf-119">Resolution</span></span>  
 <span data-ttu-id="27dcf-120">Po delegata organizowanego się jako wskaźnik funkcji niezarządzanej, moduł zbierający elementy bezużyteczne nie może śledzić jego okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="27dcf-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="27dcf-121">Zamiast tego kodu przez czas ich istnienia wskaźnika funkcji niezarządzanej przechowuje odwołanie do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="27dcf-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="27dcf-122">Jednak zanim można to zrobić, należy najpierw określić delegata, które zostały zebrane.</span><span class="sxs-lookup"><span data-stu-id="27dcf-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="27dcf-123">Po aktywowaniu MDA zawiera nazwę typu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="27dcf-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="27dcf-124">Użyj tej nazwy do wyszukiwania wywołanie kodu platformy lub podpisy COM, które przekazać ten delegat do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="27dcf-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="27dcf-125">Delegat ataku jest przekazywany za pomocą jednego z tych wywołań witryny.</span><span class="sxs-lookup"><span data-stu-id="27dcf-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="27dcf-126">Można również włączyć `gcUnmanagedToManaged` MDA, aby wymusić wyrzucanie elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="27dcf-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="27dcf-127">Spowoduje to usunięcie niedokładność wprowadzone przez pamięci przez zapewnienie im występujący wyrzucania elementów bezużytecznych zawsze przed wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27dcf-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="27dcf-128">Po sprawdzeniu, jakie delegata zostały zebrane, zmień swój kod, aby zachować odwołania do tego obiektu delegowanego po stronie zarządzanej przez czas ich istnienia wskaźnika funkcji niezarządzanej organizowane.</span><span class="sxs-lookup"><span data-stu-id="27dcf-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="27dcf-129">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="27dcf-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="27dcf-130">Jeśli obiekty delegowane są przekazywane jako wskaźników funkcji, środowisko uruchomieniowe przydziela thunk, który wykonuje przejścia z niezarządzanych w zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="27dcf-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="27dcf-131">Ta konwersja jest co niezarządzany kod wywołuje przed zarządzanej delegata na koniec jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="27dcf-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="27dcf-132">Bez `callbackOnCollectedDelegate` MDA włączone, niezarządzany kod kierowania zostanie usunięta po są zbierane z obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="27dcf-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="27dcf-133">Z `callbackOnCollectedDelegate` MDA włączone, niezarządzany kod kierowania nie są natychmiast usuwane podczas delegata są zbierane.</span><span class="sxs-lookup"><span data-stu-id="27dcf-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="27dcf-134">Zamiast tego ostatniego 1000 wystąpień są utrzymywane domyślnie i zmienić aktywować MDA po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="27dcf-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="27dcf-135">Thunk, zostanie ostatecznie usunięta po 1,001 więcej organizowane delegatów są zbierane.</span><span class="sxs-lookup"><span data-stu-id="27dcf-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="27dcf-136">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="27dcf-136">Output</span></span>  
 <span data-ttu-id="27dcf-137">MDA raporty nazwę typu delegata, który został zebrany zanim podjęto próbę wywołania zwrotnego na jego wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="27dcf-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="27dcf-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="27dcf-138">Configuration</span></span>  
 <span data-ttu-id="27dcf-139">W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27dcf-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="27dcf-140">Ustawia liczbę osadzeń, który MDA śledzi aktywności do 1500.</span><span class="sxs-lookup"><span data-stu-id="27dcf-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="27dcf-141">Wartość domyślna `listSize` wynosi 1000, wartość minimalna to 50 i maksymalna to 2000.</span><span class="sxs-lookup"><span data-stu-id="27dcf-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="27dcf-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="27dcf-142">Example</span></span>  
 <span data-ttu-id="27dcf-143">W poniższym przykładzie pokazano sytuację, której można uaktywnić to zdarzenie MDA:</span><span class="sxs-lookup"><span data-stu-id="27dcf-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
// ---------------------------------------------------  
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
  
## <a name="see-also"></a><span data-ttu-id="27dcf-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27dcf-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="27dcf-145">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="27dcf-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="27dcf-146">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="27dcf-146">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="27dcf-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="27dcf-147">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
