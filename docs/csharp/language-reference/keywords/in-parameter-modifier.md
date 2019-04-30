---
title: w modyfikator parametru - C# odwołania
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: e39d470308ed5a2b2ed82ade0faf8ba925228c2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661441"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="eefcc-102">w modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eefcc-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="eefcc-103">`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="eefcc-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="eefcc-104">To sprawia, że parametr formalny alias dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="eefcc-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="eefcc-105">Innymi słowy żadnych operacji na parametr składa się od argumentu.</span><span class="sxs-lookup"><span data-stu-id="eefcc-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="eefcc-106">Jest on podobny do [ref](ref.md) lub [się](out-parameter-modifier.md) słów kluczowych, poza tym, że `in` argumentów nie można zmodyfikować przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="eefcc-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="eefcc-107">Natomiast `ref` argumentów może być modyfikowany, `out` argumenty muszą zostać zmodyfikowane przez metodę o nazwie, a te zmiany są obserwowalnymi w kontekst wywołania.</span><span class="sxs-lookup"><span data-stu-id="eefcc-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="eefcc-108">Poprzedni przykład pokazuje, że `in` modyfikator jest zazwyczaj zbędna w witrynie wywołania.</span><span class="sxs-lookup"><span data-stu-id="eefcc-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="eefcc-109">Jest wymagany tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="eefcc-109">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="eefcc-110">`in` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu LINQ.</span><span class="sxs-lookup"><span data-stu-id="eefcc-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="eefcc-111">Aby uzyskać więcej informacji na temat użytkowania `in` Zobacz — słowo kluczowe w tych kontekstach [w](in.md), który zawiera łącza do wszystkich tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="eefcc-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="eefcc-112">Zmienne są przekazywane jako `in` argumentów musi zostać zainicjowany przed przesłaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="eefcc-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="eefcc-113">Jednak wywoływanej metody nie może przypisać wartość lub zmodyfikuj argumentu.</span><span class="sxs-lookup"><span data-stu-id="eefcc-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="eefcc-114">`in` Modyfikator parametru jest dostępna w C# wersji 7.2 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="eefcc-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="eefcc-115">Poprzednie wersje wygenerować błąd kompilatora `CS8107` ("Funkcja"odwołań tylko do odczytu"nie jest dostępna w C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="eefcc-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="eefcc-116">Użyj języka w wersji 7.2 lub większą.") Aby skonfigurować wersji kompilatora języka, zobacz [wybierz C# wersji językowej](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="eefcc-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="eefcc-117">`in`, `ref`, I `out` słowa kluczowe nie są uważane za część podpisu metody na potrzeby rozwiązania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="eefcc-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="eefcc-118">W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="eefcc-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="eefcc-119">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="eefcc-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="eefcc-120">Przeciążenie oparte na obecność `in` jest dozwolony:</span><span class="sxs-lookup"><span data-stu-id="eefcc-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="eefcc-121">Zasad rozpoznawania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="eefcc-121">Overload resolution rules</span></span>

<span data-ttu-id="eefcc-122">Rozumiesz reguły rozdzielczość przeciążenia dla metod z według wartości a `in` argumenty dzięki zrozumieniu motywacją `in` argumentów.</span><span class="sxs-lookup"><span data-stu-id="eefcc-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="eefcc-123">Definiowanie metody przy użyciu `in` parametry są potencjalnymi optymalizacji wydajności.</span><span class="sxs-lookup"><span data-stu-id="eefcc-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="eefcc-124">Niektóre `struct` argumentów typu może być duży, rozmiar i metody wywołanego w ścisłej pętli lub ścieżek kodu krytycznego koszt kopiowania tych konstrukcji jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="eefcc-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="eefcc-125">Zadeklaruj metody `in` parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie ponieważ wywoływanej metody nie powoduje modyfikacji stanu tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="eefcc-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="eefcc-126">Przekazywanie tych argumentów poprzez odwołanie pozwala uniknąć kopiowania (potencjalnie).</span><span class="sxs-lookup"><span data-stu-id="eefcc-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="eefcc-127">Określanie `in` dla argumentów w wywołaniu witryny jest zazwyczaj opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="eefcc-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="eefcc-128">Nie ma żadnej różnicy semantycznego między przekazywanie argumentów według wartości i przekazywania ich za pomocą odwołania `in` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="eefcc-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="eefcc-129">`in` Modyfikator lokacji wywołanie jest opcjonalny, ponieważ nie wymaga wskazać, że wartość argumentu może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="eefcc-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="eefcc-130">Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, argument jest przekazywany przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="eefcc-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="eefcc-131">Lepiej nie używać `in` ma następujące dwa skutki:</span><span class="sxs-lookup"><span data-stu-id="eefcc-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="eefcc-132">Po pierwsze, określając `in` w wywołaniu witryny wymusza na kompilatorze o wybranie metody zdefiniowane przy użyciu zgodnego `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="eefcc-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="eefcc-133">W przeciwnym razie, gdy dwie metody różnią się tylko w obecności właściwości `in`, według wartości przeciążenia ma lepsze dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="eefcc-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="eefcc-134">Po drugie, określając `in` deklaruje zgodne z zamiarami użytkownika do przekazywania argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="eefcc-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="eefcc-135">Argument używane z `in` musi reprezentować lokalizacji, która może być bezpośrednio określonych.</span><span class="sxs-lookup"><span data-stu-id="eefcc-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="eefcc-136">Ten sam ogólne reguły `out` i `ref` stosowanie argumentów: Nie można używać stałych, właściwości zwykłych lub innych wyrażeń, które generują wartości.</span><span class="sxs-lookup"><span data-stu-id="eefcc-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="eefcc-137">W przeciwnym razie pominięcie `in` w wywołaniu witryny informuje kompilator, będą mogli go, aby utworzyć zmiennej tymczasowej, aby przekazać tylko do odczytu odwołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="eefcc-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="eefcc-138">Kompilator tworzy zmienną tymczasową celu wyeliminowanie kilku ograniczeń za pomocą `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="eefcc-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="eefcc-139">Zmienna tymczasowa umożliwia stałe kompilacji jako `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="eefcc-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="eefcc-140">Zmienna tymczasowa umożliwia właściwości lub innych wyrażeń dla `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="eefcc-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="eefcc-141">Zmienna tymczasowa zezwala argumenty w przypadku, gdy istnieje niejawna konwersja z typu argumentu z typem parametru.</span><span class="sxs-lookup"><span data-stu-id="eefcc-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="eefcc-142">We wszystkich wystąpieniach poprzedniej kompilator tworzy zmiennej tymczasowej, która przechowuje wartość stałą, właściwość lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="eefcc-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="eefcc-143">Poniższy kod ilustruje te reguły:</span><span class="sxs-lookup"><span data-stu-id="eefcc-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="eefcc-144">Teraz załóżmy, że innej metody, używając wartości argumentów była dostępna.</span><span class="sxs-lookup"><span data-stu-id="eefcc-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="eefcc-145">Wyniki zmiany, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="eefcc-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="eefcc-146">Wywołanie metody tylko wtedy, gdy argument jest przekazywany przez odwołanie jest ostatecznej.</span><span class="sxs-lookup"><span data-stu-id="eefcc-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="eefcc-147">W poprzednim kodzie użyto `int` jako typ argumentu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="eefcc-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="eefcc-148">Ponieważ `int` jest nie większy niż odwołanie w większości współczesnych komputerów jest przekazanie pojedynczej żadnych korzyści `int` jako odwołanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="eefcc-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="eefcc-149">Ograniczenia dotyczące `in` parametrów</span><span class="sxs-lookup"><span data-stu-id="eefcc-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="eefcc-150">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="eefcc-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="eefcc-151">Metody asynchroniczne, które można zdefiniować przy użyciu [async](async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="eefcc-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="eefcc-152">Metody iteratora, które obejmują [yield return](yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="eefcc-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="eefcc-153">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eefcc-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eefcc-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eefcc-154">See also</span></span>

- [<span data-ttu-id="eefcc-155">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eefcc-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eefcc-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eefcc-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eefcc-157">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="eefcc-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eefcc-158">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="eefcc-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="eefcc-159">Pisanie kodu efektywne bezpieczne</span><span class="sxs-lookup"><span data-stu-id="eefcc-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
