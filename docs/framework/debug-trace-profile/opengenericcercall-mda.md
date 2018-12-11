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
ms.openlocfilehash: c2cb99a1bda8223ddece4b4aff4a87d95357d90e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153699"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="d29af-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="d29af-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="d29af-103">`openGenericCERCall` Zarządzany Asystent debugowania jest aktywowana Aby ostrzeżenie, że wykres ograniczonego wykonania region (CER) za pomocą zmiennych typu rodzajowego w metodzie głównej jest przetwarzany na kompilację JIT lub obrazu macierzystego czas generowania i co najmniej jeden z ogólnych zmienne typu jest typu odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="d29af-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d29af-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="d29af-104">Symptoms</span></span>  
 <span data-ttu-id="d29af-105">CER kodu nie jest uruchamiany, gdy wątek został przerwany lub domena aplikacji jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="d29af-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d29af-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="d29af-106">Cause</span></span>  
 <span data-ttu-id="d29af-107">W czasie kompilacji JIT podczas tworzenia wystąpienia typu odwołanie do obiektu zawierającego to tylko ponieważ wynikowy kod jest współużytkowany, a każda z tych zmiennych typu odwołania może być dowolnego typu odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="d29af-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="d29af-108">Może to spowodować przygotowania niektóre zasoby środowiska wykonawczego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d29af-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="d29af-109">W szczególności metody ze zmiennymi typu ogólnego, opóźnieniem można przydzielić zasoby w tle.</span><span class="sxs-lookup"><span data-stu-id="d29af-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="d29af-110">Są one określane jako wpisy generyczny słownik.</span><span class="sxs-lookup"><span data-stu-id="d29af-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="d29af-111">Na przykład dla instrukcji `List<T> list = new List<T>();` gdzie `T` jest zmienną typu rodzajowego, środowisko wykonawcze musi strzałki w górę i ewentualnie utworzyć związanej dokładna w czasie wykonywania, na przykład `List<Object>, List<String>`, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d29af-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="d29af-112">To może się nie powieść z różnych powodów będące poza kontrolą dewelopera, takie jak uruchamianie za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="d29af-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="d29af-113">To zdarzenie MDA można uaktywniać tylko w czasie kompilacji JIT, nie po dokładnie egzemplarz.</span><span class="sxs-lookup"><span data-stu-id="d29af-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="d29af-114">To zdarzenie MDA jest aktywowane, prawdopodobnie objawów są czy CERs nie działają dla zły wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d29af-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="d29af-115">W rzeczywistości środowisko wykonawcze nie próbował zaimplementować CER w sytuacjach, które spowodowały MDA zostanie uaktywniony.</span><span class="sxs-lookup"><span data-stu-id="d29af-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="d29af-116">Dlatego jeśli programistka używa udostępnionego podczas tworzenia wystąpienia CER, a następnie błędy kompilacji JIT, ogólne typu błędy ładowania lub Wątek przerywa w obrębie regionu zamierzony CER nie zostały wyłapane.</span><span class="sxs-lookup"><span data-stu-id="d29af-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d29af-117">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="d29af-117">Resolution</span></span>  
 <span data-ttu-id="d29af-118">Nie należy używać zmiennych typu ogólnego, które są typu odwołanie do obiektu dla metod, które mogą zawierać CER.</span><span class="sxs-lookup"><span data-stu-id="d29af-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d29af-119">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d29af-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="d29af-120">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="d29af-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d29af-121">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d29af-121">Output</span></span>  
 <span data-ttu-id="d29af-122">Poniżej przedstawiono przykładowe dane wyjściowe z tego MDA.</span><span class="sxs-lookup"><span data-stu-id="d29af-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="d29af-123">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d29af-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="d29af-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d29af-124">Example</span></span>  
 <span data-ttu-id="d29af-125">Kod CER nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d29af-125">The CER code is not executed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d29af-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d29af-126">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="d29af-127">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d29af-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
