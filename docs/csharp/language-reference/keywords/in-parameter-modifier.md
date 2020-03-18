---
title: w modyfikatorze parametrów - Odwołanie do języka C#
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: cbde7a571fb71ed7577077c77a5c61db553ec859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173617"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="6dd6e-102">w modyfikatorze parametrów (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="6dd6e-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="6dd6e-103">Słowo `in` kluczowe powoduje, że argumenty mają być przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="6dd6e-104">To sprawia, że formalny parametr alias dla argumentu, który musi być zmienna.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="6dd6e-105">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="6dd6e-106">Jest jak [ref](ref.md) lub [out](out-parameter-modifier.md) słów `in` kluczowych, z tą różnicą, że argumenty nie mogą być modyfikowane przez wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="6dd6e-107">`ref` Argumenty mogą być `out` modyfikowane, argumenty muszą być modyfikowane przez wywoływaną metodę, a te modyfikacje są obserwowalne w kontekście wywołującym.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="6dd6e-108">W poprzednim przykładzie pokazano, że `in` modyfikator jest zwykle niepotrzebne w witrynie wywołania.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="6dd6e-109">Jest to wymagane tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-109">It is only required in the method declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="6dd6e-110">Słowo `in` kluczowe może być również używany z parametrem typu ogólnego, aby określić, że parametr typu jest kontrawariantny, jako część `foreach` instrukcji lub jako część `join` klauzuli w kwerendzie LINQ.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="6dd6e-111">Aby uzyskać więcej informacji `in` na temat używania słowa kluczowego w tych kontekstach, zobacz [w](in.md), który zawiera łącza do wszystkich tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="6dd6e-112">Zmienne przekazywane `in` jako argumenty muszą zostać zainicjowane przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="6dd6e-113">Jednak wywoływana metoda nie może przypisać wartość lub zmodyfikować argument.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="6dd6e-114">Modyfikator `in` parametrów jest dostępny w języku C# 7.2 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="6dd6e-115">Poprzednie wersje generują `CS8107` błąd kompilatora ("Funkcja "odwołania tylko do odczytu" nie jest dostępna w języku C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="6dd6e-116">Proszę użyć wersji językowej 7.2 lub większej.") Aby skonfigurować wersję językową kompilatora, zobacz [Wybieranie wersji języka Języka C#.](../configure-language-version.md)</span><span class="sxs-lookup"><span data-stu-id="6dd6e-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="6dd6e-117">Słowa `in` `ref`kluczowe `out` , i słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="6dd6e-118">W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda ma `ref` lub `in` argument, a druga przyjmuje argument. `out`</span><span class="sxs-lookup"><span data-stu-id="6dd6e-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="6dd6e-119">Poniższy kod, na przykład, nie skompiluje:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="6dd6e-120">Przeciążenie w oparciu `in` o obecność jest dozwolone:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="6dd6e-121">Reguły rozpoznawania przeciążeń</span><span class="sxs-lookup"><span data-stu-id="6dd6e-121">Overload resolution rules</span></span>

<span data-ttu-id="6dd6e-122">Można zrozumieć reguły rozpoznawania przeciążenia dla metod `in` z argumentami `in` według wartości i przez zrozumienie motywacji argumentów.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="6dd6e-123">Definiowanie metod `in` przy użyciu parametrów jest potencjalną optymalizacją wydajności.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="6dd6e-124">Niektóre `struct` argumenty typu mogą mieć duży rozmiar, a gdy metody są wywoływane w ciasnych pętlach lub krytycznych ścieżkach kodu, koszt kopiowania tych struktur jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="6dd6e-125">Metody deklarują `in` parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie, ponieważ wywoływana metoda nie modyfikuje stanu tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="6dd6e-126">Przekazywanie tych argumentów przez odwołanie pozwala uniknąć (potencjalnie) drogiej kopii.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span>

<span data-ttu-id="6dd6e-127">Określanie `in` argumentów w witrynie wywołania jest zazwyczaj opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="6dd6e-128">Nie ma żadnej różnicy semantyczne między przekazywanie argumentów `in` przez wartość i przekazywanie ich przez odwołanie za pomocą modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="6dd6e-129">Modyfikator `in` w witrynie wywołania jest opcjonalny, ponieważ nie trzeba wskazywać, że wartość argumentu może zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="6dd6e-130">Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, że argument jest przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="6dd6e-131">Jawnie `in` przy użyciu ma następujące dwa efekty:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="6dd6e-132">Najpierw określenie `in` w witrynie wywołania wymusza kompilator, aby `in` wybrać metodę zdefiniowaną z parametrem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="6dd6e-133">W przeciwnym razie, gdy dwie metody `in`różnią się tylko w obecności , przeciążenie przez wartość jest lepsze dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="6dd6e-134">Po drugie, `in` określenie deklaruje zamiar przekazania argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="6dd6e-135">Argument używany `in` z musi reprezentować lokalizację, która może być bezpośrednio odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="6dd6e-136">Te same ogólne `out` `ref` reguły i argumenty mają zastosowanie: Nie można używać stałych, zwykłych właściwości lub innych wyrażeń, które generują wartości.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="6dd6e-137">W przeciwnym razie `in` pominięcie w witrynie wywołania informuje kompilator, że pozwolisz mu utworzyć zmienną tymczasową do przekazywania przez odwołanie tylko do odczytu do metody.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="6dd6e-138">Kompilator tworzy zmienną tymczasową, aby pokonać kilka ograniczeń za pomocą `in` argumentów:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="6dd6e-139">Zmienna tymczasowa umożliwia skompilowanie `in` w czasie jako parametry.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="6dd6e-140">Zmienna tymczasowa umożliwia właściwości lub `in` inne wyrażenia dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="6dd6e-141">Zmienna tymczasowa zezwala na argumenty, w których istnieje niejawna konwersja z typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="6dd6e-142">We wszystkich poprzednich wystąpieniach kompilator tworzy zmienną tymczasową, która przechowuje wartość wyrażenia stała, właściwość lub inne.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="6dd6e-143">Poniższy kod ilustruje następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="6dd6e-144">Teraz załóżmy, że dostępna była inna metoda używająca argumentów wartości.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="6dd6e-145">Wyniki zmieniają się, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="6dd6e-146">Jedyną metodą wywołania, gdzie argument jest przekazywany przez odwołanie jest ostateczna.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="6dd6e-147">Poprzedni kod używa `int` jako typ argumentu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="6dd6e-148">Ponieważ `int` nie jest większy niż odwołanie w większości nowoczesnych maszyn, `int` nie ma żadnych korzyści z przekazywania jednego jako odwołanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span>

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="6dd6e-149">Ograniczenia `in` parametrów</span><span class="sxs-lookup"><span data-stu-id="6dd6e-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="6dd6e-150">Nie można używać `in`słów `ref` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="6dd6e-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="6dd6e-151">Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)</span><span class="sxs-lookup"><span data-stu-id="6dd6e-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="6dd6e-152">Metody iterator, które obejmują zwrot `yield break` [uchylić](yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6dd6e-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="6dd6e-153">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6dd6e-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6dd6e-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dd6e-154">See also</span></span>

- [<span data-ttu-id="6dd6e-155">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="6dd6e-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6dd6e-156">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="6dd6e-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6dd6e-157">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6dd6e-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6dd6e-158">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="6dd6e-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="6dd6e-159">Napisz bezpieczny, wydajny kod</span><span class="sxs-lookup"><span data-stu-id="6dd6e-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
