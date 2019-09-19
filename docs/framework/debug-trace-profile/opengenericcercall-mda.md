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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6ad656a5f762bf86d277d986bb087c97d7a78f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052414"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="0c4f0-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="0c4f0-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="0c4f0-103">Asystent `openGenericCERCall` debugowania zarządzanego został aktywowany, aby ostrzec, że wykres ograniczonego regionu wykonania (CER) z zmiennymi typu ogólnego w metodzie głównej jest przetwarzany podczas kompilacji JIT lub czasu generowania obrazu natywnego, a co najmniej jeden z ogólnych zmienne typu są typu odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0c4f0-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="0c4f0-104">Symptoms</span></span>  
 <span data-ttu-id="0c4f0-105">Kod CER nie jest uruchamiany, gdy wątek zostanie przerwany lub gdy domena aplikacji zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0c4f0-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="0c4f0-106">Cause</span></span>  
 <span data-ttu-id="0c4f0-107">W czasie kompilacji JIT proces tworzenia wystąpienia zawierającego typ odwołania do obiektu jest tylko reprezentatywny, ponieważ wynikowy kod jest współużytkowany, a Każda zmienna typu odwołania do obiektu może być dowolnym typem odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="0c4f0-108">Może to uniemożliwić przygotowanie niektórych zasobów czasu wykonywania przed czasem.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="0c4f0-109">W szczególności metody z zmiennymi typów ogólnych mogą opóźnieniem przydzielać zasoby w tle.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="0c4f0-110">Są one określane mianem zwykłych wpisów słownika.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="0c4f0-111">Na przykład dla instrukcji `List<T> list = new List<T>();` Where `T` jest zmienną typu ogólnego środowisko uruchomieniowe musi wyszukać i ewentualnie utworzyć dokładne wystąpienie w `List<Object>, List<String>`czasie wykonywania, na przykład, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="0c4f0-112">Może to się nie powieść z różnych powodów wykraczających poza kontrolę dewelopera, na przykład za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="0c4f0-113">To zdarzenie MDA powinno być aktywowane tylko w czasie kompilacji JIT, a nie w przypadku wystąpienia dokładnego.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="0c4f0-114">Po aktywowaniu tego elementu MDA prawdopodobnie CERs nie działają w przypadku nieprawidłowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="0c4f0-115">W rzeczywistości środowisko uruchomieniowe nie podjęło próby wdrożenia CER w warunkach, które spowodowały aktywowanie MDA.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="0c4f0-116">Tak więc jeśli deweloper korzysta z udostępnionego wystąpienia programu CER, błędy kompilacji JIT, błędy ładowania typów lub przerwania wątku w regionie zamierzonego CER nie są przechwytywane.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0c4f0-117">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="0c4f0-117">Resolution</span></span>  
 <span data-ttu-id="0c4f0-118">Nie używaj typów ogólnych zmiennych, które są typu odwołania do obiektu dla metod, które mogą zawierać CER.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0c4f0-119">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0c4f0-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="0c4f0-120">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0c4f0-121">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="0c4f0-121">Output</span></span>  
 <span data-ttu-id="0c4f0-122">Poniżej znajduje się przykład danych wyjściowych z tego MDA.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="0c4f0-123">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="0c4f0-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0c4f0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c4f0-124">Example</span></span>  
 <span data-ttu-id="0c4f0-125">Kod CER nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="0c4f0-125">The CER code is not executed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c4f0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c4f0-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="0c4f0-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="0c4f0-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
