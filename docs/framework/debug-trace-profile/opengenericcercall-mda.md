---
title: openGenericCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181783"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="606a8-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="606a8-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="606a8-103">Zarządzany `openGenericCERCall` asystent debugowania jest aktywowany, aby ostrzec, że wykres regionu ograniczonego wykonywania (CER) z ogólnymi zmiennymi typu w metodzie głównej jest przetwarzany w czasie generowania kompilacji JIT lub obrazu natywnego, a co najmniej jedna ze zmiennych typu ogólnego jest typem odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="606a8-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="606a8-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="606a8-104">Symptoms</span></span>

<span data-ttu-id="606a8-105">Kod CER nie jest uruchamiany, gdy wątek zostanie przerwany lub gdy domena aplikacji zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="606a8-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="606a8-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="606a8-106">Cause</span></span>

<span data-ttu-id="606a8-107">W czasie kompilacji JIT wystąpienia zawierającego typ odwołania do obiektu jest tylko reprezentatywne, ponieważ wynikowy kod jest współużytkowany, a każda ze zmiennych typu odwołania do obiektu może być dowolnym typem odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="606a8-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="606a8-108">Może to uniemożliwić przygotowanie niektórych zasobów w czasie wykonywania z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="606a8-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="606a8-109">W szczególności metody ze zmiennymi typu ogólnego można leniwie przydzielać zasoby w tle.</span><span class="sxs-lookup"><span data-stu-id="606a8-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="606a8-110">Są one określane jako ogólne wpisy słownika.</span><span class="sxs-lookup"><span data-stu-id="606a8-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="606a8-111">Na przykład dla `List<T> list = new List<T>();` instrukcji, gdzie `T` jest zmienną typu ogólnego środowisko wykonawcze musi wyszukać i `List<Object>, List<String>`ewentualnie utworzyć dokładne wystąpienie w czasie wykonywania, na przykład i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="606a8-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="606a8-112">To może zakończyć się niepowodzeniem z różnych powodów poza kontrolą dewelopera, takich jak wyczerpanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="606a8-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="606a8-113">To MDA powinny być aktywowane tylko w czasie kompilacji JIT, a nie wtedy, gdy istnieje dokładne wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="606a8-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="606a8-114">Po aktywacji tego MDA, prawdopodobne objawy są, że CEPTR nie są funkcjonalne dla złych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="606a8-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="606a8-115">W rzeczywistości środowisko wykonawcze nie próbował zaimplementować CER w okolicznościach, które spowodowały MDA do aktywacji.</span><span class="sxs-lookup"><span data-stu-id="606a8-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="606a8-116">Więc jeśli deweloper używa udostępnionego wystąpienia CER, a następnie błędy kompilacji JIT, błędy ładowania typu generics lub przerywanie wątku w regionie zamierzonego CER nie są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="606a8-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="606a8-117">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="606a8-117">Resolution</span></span>

<span data-ttu-id="606a8-118">Nie należy używać zmiennych typu ogólnego, które są typu odwołania do obiektu dla metod, które mogą zawierać CER.</span><span class="sxs-lookup"><span data-stu-id="606a8-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="606a8-119">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="606a8-119">Effect on the Runtime</span></span>

<span data-ttu-id="606a8-120">To MDA nie ma wpływu na CLR.</span><span class="sxs-lookup"><span data-stu-id="606a8-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="606a8-121">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="606a8-121">Output</span></span>

<span data-ttu-id="606a8-122">Poniżej przedstawiono przykład danych wyjściowych z tego MDA:</span><span class="sxs-lookup"><span data-stu-id="606a8-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="606a8-123">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="606a8-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="606a8-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="606a8-124">Example</span></span>

<span data-ttu-id="606a8-125">Kod CER nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="606a8-125">The CER code is not executed.</span></span>

```csharp
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

## <a name="see-also"></a><span data-ttu-id="606a8-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="606a8-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="606a8-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="606a8-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
