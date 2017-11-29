---
title: openGenericCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f82760eaeb051f2006a8baf11ac77c485d007758
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="f46ba-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="f46ba-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="f46ba-103">`openGenericCERCall` Asystent debugowania zarządzanego został aktywowany do ostrzeżenie, że wykres region (CER) ograniczonego wykonania ze zmiennymi typu ogólnego w metodzie głównego jest przetwarzany w kompilacji JIT lub obrazu macierzystego czas generowania i co najmniej jeden z ogólnych zmienne typu jest typu odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f46ba-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f46ba-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="f46ba-104">Symptoms</span></span>  
 <span data-ttu-id="f46ba-105">CER kod nie zostanie uruchomiony, gdy wątek został przerwany lub domeny aplikacji jest zwolniony.</span><span class="sxs-lookup"><span data-stu-id="f46ba-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f46ba-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="f46ba-106">Cause</span></span>  
 <span data-ttu-id="f46ba-107">W czasie kompilacji JIT podczas tworzenia wystąpienia typu odwołanie do obiektu zawierającego jest tylko przedstawiciel, ponieważ wynikowy kod jest udostępniony, a każdy z tych zmiennych typu odwołania mogą być dowolnego typu odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f46ba-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="f46ba-108">Może to spowodować przygotowanie niektórych zasobów środowiska wykonawczego wcześniejsze.</span><span class="sxs-lookup"><span data-stu-id="f46ba-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="f46ba-109">W szczególności metody ze zmiennymi typu ogólnego opóźnieniem można przydzielić zasoby w tle.</span><span class="sxs-lookup"><span data-stu-id="f46ba-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="f46ba-110">Te są określane jako wpisy słownika ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f46ba-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="f46ba-111">Na przykład dla instrukcji `List<T> list = new List<T>();` gdzie `T` jest zmienną typu ogólnego środowiska uruchomieniowego musi strzałki w górę i prawdopodobnie utworzyć wystąpienia dokładnie w czasie wykonywania, na przykład `List<Object>, List<String>`, itd.</span><span class="sxs-lookup"><span data-stu-id="f46ba-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="f46ba-112">To może się nie powieść z różnych powodów pozostających poza kontrolą dewelopera, takich jak wyczerpaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="f46ba-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="f46ba-113">To zdarzenie MDA należy aktywować tylko w czasie kompilacji JIT nie po wystąpieniu dokładne.</span><span class="sxs-lookup"><span data-stu-id="f46ba-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="f46ba-114">Po uaktywnieniu to zdarzenie MDA objawy prawdopodobnie są CERs nie są funkcjonalności dla zły wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f46ba-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="f46ba-115">W rzeczywistości środowiska uruchomieniowego nie podjął próbę wykonania CER czynników, które spowodowały MDA do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f46ba-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="f46ba-116">Dlatego projektanta używa udostępnionego podczas tworzenia wystąpienia CER, a następnie błędy kompilacji JIT, Ogólne wpisz błędy ładowania lub przerwanie wątku w regionie zamierzone CER nie są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="f46ba-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f46ba-117">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="f46ba-117">Resolution</span></span>  
 <span data-ttu-id="f46ba-118">Nie należy używać zmiennych typu ogólnego typu odwołanie do obiektu dla metod, które mogą zawierać CER.</span><span class="sxs-lookup"><span data-stu-id="f46ba-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f46ba-119">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f46ba-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="f46ba-120">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f46ba-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f46ba-121">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f46ba-121">Output</span></span>  
 <span data-ttu-id="f46ba-122">Poniżej przedstawiono przykładowe dane wyjściowe to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="f46ba-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="f46ba-123">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f46ba-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f46ba-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="f46ba-124">Example</span></span>  
 <span data-ttu-id="f46ba-125">Kod CER nie została wykonana.</span><span class="sxs-lookup"><span data-stu-id="f46ba-125">The CER code is not executed.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f46ba-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f46ba-126">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="f46ba-127">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="f46ba-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
