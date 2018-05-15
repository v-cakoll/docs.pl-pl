---
title: w modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: aa6720430a1d93d7eacb098962c09efad09a179f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="17bdc-102">w modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="17bdc-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="17bdc-103">`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="17bdc-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="17bdc-104">Przypomina to [ref](ref.md) lub [limit](out-parameter-modifier.md) słów kluczowych, z wyjątkiem, że `in` argumentów nie można zmodyfikować przez metodę o nazwie, podczas gdy `ref` argumenty mogą zostać zmodyfikowane, `out` argumentów muszą zostać zmodyfikowane przez obiekt wywołujący, a te zmiany są według w kontekście wywołującego.</span><span class="sxs-lookup"><span data-stu-id="17bdc-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method, whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="17bdc-105">W poprzednim przykładzie pokazano `in` modyfikator zazwyczaj nie jest wykorzystywana w miejsce wywołania.</span><span class="sxs-lookup"><span data-stu-id="17bdc-105">The preceding example demonstrates the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="17bdc-106">Wymagane jest tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="17bdc-106">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="17bdc-107">`in` — Słowo kluczowe można również z parametrem typu ogólnego w celu wskazania, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="17bdc-107">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="17bdc-108">Aby uzyskać więcej informacji dotyczących korzystania z `in` — słowo kluczowe w tych kontekstach, zobacz [w](in.md), który zawiera łącza do tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="17bdc-108">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="17bdc-109">Zmienne przekazany jako `in` argumentów musi zostać zainicjowany przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="17bdc-109">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="17bdc-110">Wywołana metoda nie może jednak przypisać wartość lub zmodyfikuj argument.</span><span class="sxs-lookup"><span data-stu-id="17bdc-110">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="17bdc-111">Mimo że `in`, `ref`, i `out` słowa kluczowe przyczynę inaczej w czasie wykonywania, nie są wliczane część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="17bdc-111">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="17bdc-112">W związku z tym nie może zostać przeciążony metody Jeśli jedyną różnicą jest to, że jedna metoda przyjmuje `ref` lub `in` argument i innych przyjmuje `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="17bdc-112">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="17bdc-113">Następujący kod, na przykład nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="17bdc-113">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="17bdc-114">Przeciążanie na podstawie obecności z `in` jest dozwolone:</span><span class="sxs-lookup"><span data-stu-id="17bdc-114">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="17bdc-115">Zasady rozpoznawania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="17bdc-115">Overload resolution rules</span></span>

<span data-ttu-id="17bdc-116">Można zrozumieć zasady rozpoznawania przeciążenia metody z przez wartość a `in` argumenty za pośrednictwem opis motywacją `in` argumentów.</span><span class="sxs-lookup"><span data-stu-id="17bdc-116">You can understand the overload resolution rules for methods with by value vs. `in` arguments through understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="17bdc-117">Definiowanie przy użyciu metody `in` parametrów jest potencjalnych optymalizacji wydajności.</span><span class="sxs-lookup"><span data-stu-id="17bdc-117">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="17bdc-118">Niektóre `struct` argumentów typu mogą być duże i metody wywołanego w pętli ścisłej lub ścieżek kodu krytycznego koszt kopiowania tych konstrukcji jest krytyczne.</span><span class="sxs-lookup"><span data-stu-id="17bdc-118">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="17bdc-119">Metody deklarować `in` w celu określenia, że argumenty mogą być przekazywane przez odwołanie bezpiecznie ponieważ wywołana metoda nie modyfikuje stan tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="17bdc-119">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="17bdc-120">Przekazywanie tych argumentów przez odwołanie pozwala uniknąć kopiowania (potencjalnie) kosztowne.</span><span class="sxs-lookup"><span data-stu-id="17bdc-120">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="17bdc-121">Określanie `in` na argumentów w wywołaniu lokacji jest zwykle opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="17bdc-121">Specifying `in` on arguments at the call site is typically optional.</span></span> <span data-ttu-id="17bdc-122">Nie ma żadnej semantycznego różnicy między przekazywanie argumentów według wartości i przekazywanie ich przy użyciu odwołania `in` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="17bdc-122">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="17bdc-123">`in` Modyfikator w witrynie wywołanie jest opcjonalny, ponieważ nie ma potrzeby wskazywać, że wartość argumentu może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="17bdc-123">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="17bdc-124">Jawnie dodać `in` modyfikator w miejsce wywołania, aby upewnić się, argument jest przekazywana przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="17bdc-124">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="17bdc-125">Jawnie za pomocą `in` ma dwa efekty:</span><span class="sxs-lookup"><span data-stu-id="17bdc-125">Explicitly using `in` has two effects:</span></span>

<span data-ttu-id="17bdc-126">Po pierwsze, określając `in` w wywołaniu lokacji wymusza kompilator, aby wybrać metodę zdefiniowane z odpowiadającego mu `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="17bdc-126">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="17bdc-127">W przeciwnym razie, gdy dwie metody różnią się jedynie w związku z występowaniem `in`, przez wartość przeciążenia jest lepszym dopasowaniem.</span><span class="sxs-lookup"><span data-stu-id="17bdc-127">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="17bdc-128">Po drugie, określając `in` deklaruje zamiaru przekazywania argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="17bdc-128">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="17bdc-129">Argument używany z `in` musi reprezentować lokalizacji, która może być bezpośrednio określonych.</span><span class="sxs-lookup"><span data-stu-id="17bdc-129">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="17bdc-130">Zasady ogólne tej samej `out` i `ref` mają zastosowanie argumenty: nie można użyć stałe, właściwości zwykłych lub inne wyrażenia, które powodują powstanie wartości.</span><span class="sxs-lookup"><span data-stu-id="17bdc-130">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="17bdc-131">W przeciwnym razie pominięcie `in` w wywołaniu lokacji informuje kompilator, że będą mogli go w celu utworzenia zmiennej tymczasowej przekazywane przez odwołanie tylko do odczytu do metody.</span><span class="sxs-lookup"><span data-stu-id="17bdc-131">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="17bdc-132">Kompilator tworzy zmiennej tymczasowej, aby wyeliminować kilka ograniczeń z `in` argumentów:</span><span class="sxs-lookup"><span data-stu-id="17bdc-132">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="17bdc-133">Stałe kompilacji jako umożliwia zmiennej tymczasowej `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="17bdc-133">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="17bdc-134">Umożliwia zmiennej tymczasowej, właściwości lub inne wyrażenia `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="17bdc-134">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="17bdc-135">Zmiennej tymczasowej umożliwia argumentów w przypadku, gdy istnieje niejawna konwersja z typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="17bdc-135">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="17bdc-136">We wszystkich powyższych przypadkach kompilator tworzy zmiennej tymczasowej, która zawiera wartość stałą, właściwości lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="17bdc-136">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="17bdc-137">Poniższy kod ilustruje te reguły:</span><span class="sxs-lookup"><span data-stu-id="17bdc-137">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="17bdc-138">Załóżmy, że innej metody, używając argumentów była dostępna.</span><span class="sxs-lookup"><span data-stu-id="17bdc-138">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="17bdc-139">Wyniki zmiany, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="17bdc-139">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="17bdc-140">Tylko wywołania metody, gdy argument jest przekazywana przez odwołanie, jest to końcowy.</span><span class="sxs-lookup"><span data-stu-id="17bdc-140">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="17bdc-141">W poprzednim kodzie użyto `int` jako typ argumentu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="17bdc-141">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="17bdc-142">Ponieważ `int` jest nie większy niż odwołanie w najbardziej nowoczesne urządzenia jest żadnych korzyści przekazywanie pojedynczy `int` jako odwołanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="17bdc-142">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="17bdc-143">Ograniczenia dotyczące `in` parametrów</span><span class="sxs-lookup"><span data-stu-id="17bdc-143">Limitations on `in` parameters</span></span>

<span data-ttu-id="17bdc-144">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="17bdc-144">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="17bdc-145">Metody asynchroniczne, które definiują przy użyciu [async](async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="17bdc-145">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="17bdc-146">Metody iteracyjne, które obejmują [yield return](yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="17bdc-146">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="17bdc-147">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="17bdc-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17bdc-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17bdc-148">See Also</span></span>  
 [<span data-ttu-id="17bdc-149">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="17bdc-149">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="17bdc-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="17bdc-150">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="17bdc-151">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="17bdc-151">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="17bdc-152">[Parametry metody](method-parameters.md) [odwołania semantyka typów wartości](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="17bdc-152">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
