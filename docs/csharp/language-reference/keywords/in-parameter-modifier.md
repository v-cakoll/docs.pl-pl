---
title: w modyfikator parametrów (odwołanie w C#)
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
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="3a6e1-102">w modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3a6e1-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="3a6e1-103">`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="3a6e1-104">Przypomina to [ref](ref.md) lub [limit](out-parameter-modifier.md) słów kluczowych, z wyjątkiem, że `in` argumentów nie można zmodyfikować przez metodę o nazwie, podczas gdy `ref` argumenty mogą zostać zmodyfikowane, `out` argumentów muszą zostać zmodyfikowane przez obiekt wywołujący, a te zmiany są według w kontekście wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="3a6e1-105">W poprzednim przykładzie pokazano, które `in` modyfikator nie jest konieczne, w miejsce wywołania.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-105">The preceding example demonstrates that the `in` modifier is unnecessary at the call site.</span></span> <span data-ttu-id="3a6e1-106">Wymagane jest tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="3a6e1-107">`in` — Słowo kluczowe można również z parametrem typu ogólnego w celu wskazania, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="3a6e1-108">Aby uzyskać więcej informacji dotyczących korzystania z `in` — słowo kluczowe w tych kontekstach, zobacz [w](in.md) zapewniające łącza do tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md) which provides links to all those uses.</span></span>
  
 <span data-ttu-id="3a6e1-109">Zmienne przekazany jako `in` argumentów musi zostać zainicjowany przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="3a6e1-110">Wywołana metoda nie może jednak przypisać wartość lub zmodyfikuj argument.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="3a6e1-111">Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="3a6e1-112">W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="3a6e1-113">Następujący kod, na przykład nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="3a6e1-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="3a6e1-114">Przeciążanie na podstawie obecności z `in` jest dozwolone, ale generuje ostrzeżenie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="3a6e1-114">Overloading based on the presence of `in` is allowed, but generates a compiler warning:</span></span>  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

<span data-ttu-id="3a6e1-115">Właściwości lub stałe mogą być przekazywane jako `in` parametrów, ponieważ wywołanie metody nie mogą modyfikować wartości.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-115">Properties or constants may be passed as `in` parameters, because the calling method may not modify their values.</span></span>
  
<span data-ttu-id="3a6e1-116">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="3a6e1-116">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="3a6e1-117">Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-117">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
- <span data-ttu-id="3a6e1-118">Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-118">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

<span data-ttu-id="3a6e1-119">Zwykle zadeklarować `in` argumentów, aby uniknąć wymaganych przez przekazywanie argumentów poprzez wartość operacje kopiowania.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-119">You typically declare `in` arguments to avoid the copy operations necessary for passing arguments by value.</span></span> <span data-ttu-id="3a6e1-120">Jest to najbardziej przydatny w przypadku argumenty typów wartości, takich jak struktury gdzie operacje kopiowania są droższe niż przekazywanie poprzez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-120">This is most useful when arguments are value types such as structures where copy operations are more expensive than passing by reference.</span></span>

> [!WARNING]
>  <span data-ttu-id="3a6e1-121">`in` Parametry mogą być bardziej kosztowne niewłaściwego użycia.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-121">`in` parameters can be even more expensive if misused.</span></span> <span data-ttu-id="3a6e1-122">Kompilator może nie wiedzieć, jeśli element członkowski metod modyfikowania stanu struktury.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-122">The compiler may not know if member methods modify the state of the struct.</span></span> <span data-ttu-id="3a6e1-123">Zawsze, gdy kompilator nie powiodło się, że obiekt nie jest modyfikowany, pamiętać o tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-123">Whenever the compiler cannot ensure that the object is not modified, it defensively creates a copy and calls member references using that copy.</span></span> <span data-ttu-id="3a6e1-124">Wszystkie możliwe modyfikacje zostaną obrony ją.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-124">Any possible modifications are to that defensive copy.</span></span> <span data-ttu-id="3a6e1-125">Są dwa sposoby, aby uniknąć tych kopii do przekazania `in` parametrów jako `in` argumentów lub definiowania struktury jako `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="3a6e1-125">The two ways to avoid these copies are to pass `in` parameters as `in` arguments or to define structures as `readonly struct`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3a6e1-126">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3a6e1-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a6e1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a6e1-127">See Also</span></span>  
 [<span data-ttu-id="3a6e1-128">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3a6e1-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3a6e1-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3a6e1-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3a6e1-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3a6e1-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3a6e1-131">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="3a6e1-131">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="3a6e1-132">Semantykę odwołania z typami wartości</span><span class="sxs-lookup"><span data-stu-id="3a6e1-132">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
