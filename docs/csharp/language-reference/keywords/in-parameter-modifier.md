---
title: "w modyfikator parametrów (odwołanie w C#)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="dcb88-102">w modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dcb88-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="dcb88-103">`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="dcb88-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="dcb88-104">Przypomina to [ref](ref.md) lub [limit](out-parameter-modifier.md) słów kluczowych, z wyjątkiem, że `in` argumentów nie można zmodyfikować przez metodę o nazwie, podczas gdy `ref` argumenty mogą zostać zmodyfikowane, `out` argumentów muszą zostać zmodyfikowane przez obiekt wywołujący, a te zmiany są według w kontekście wywołującego.</span><span class="sxs-lookup"><span data-stu-id="dcb88-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="dcb88-105">W poprzednim przykładzie pokazano, które `in` modyfikator nie jest konieczne, w miejsce wywołania.</span><span class="sxs-lookup"><span data-stu-id="dcb88-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="dcb88-106">Wymagane jest tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="dcb88-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="dcb88-107">`in` — Słowo kluczowe można również z parametrem typu ogólnego w celu wskazania, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="dcb88-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="dcb88-108">Aby uzyskać więcej informacji dotyczących korzystania z `in` — słowo kluczowe w tych kontekstach, zobacz [w](in.md) zapewniające łącza do tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="dcb88-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="dcb88-109">Zmienne przekazany jako `in` argumentów musi zostać zainicjowany przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="dcb88-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="dcb88-110">Wywołana metoda nie może jednak przypisać wartość lub zmodyfikuj argument.</span><span class="sxs-lookup"><span data-stu-id="dcb88-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="dcb88-111">Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dcb88-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="dcb88-112">W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="dcb88-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="dcb88-113">Następujący kod, na przykład nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="dcb88-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="dcb88-114">Przeciążanie na podstawie obecności z `in` jest dozwolone, ale generuje ostrzeżenie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="dcb88-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="dcb88-115">Właściwości lub stałe mogą być przekazywane jako `in` parametrów, ponieważ wywołanie metody nie mogą modyfikować wartości.</span><span class="sxs-lookup"><span data-stu-id="dcb88-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="dcb88-116">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="dcb88-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="dcb88-117">Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="dcb88-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="dcb88-118">Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dcb88-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="dcb88-119">Zwykle zadeklarować `in` argumentów, aby uniknąć wymaganych przez przekazywanie argumentów poprzez wartość operacje kopiowania.</span><span class="sxs-lookup"><span data-stu-id="dcb88-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="dcb88-120">Jest to najbardziej przydatne w przypadku argumentów struktury lub tablice struktur.</span><span class="sxs-lookup"><span data-stu-id="dcb88-120">This is most useful when arguments are structures or arrays of structures.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dcb88-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dcb88-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dcb88-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcb88-122">See Also</span></span>  
 [<span data-ttu-id="dcb88-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="dcb88-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dcb88-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dcb88-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dcb88-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dcb88-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="dcb88-126">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="dcb88-126">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
