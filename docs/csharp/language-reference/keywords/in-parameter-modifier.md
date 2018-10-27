---
title: w modyfikator parametrów (odwołanie w C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 199d2d54a1937b9982131b8cc7f1c777f656d7a9
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50049454"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="463d7-102">w modyfikator parametrów (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="463d7-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="463d7-103">`in` — Słowo kluczowe powoduje, że argumenty przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="463d7-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="463d7-104">Jest on podobny do [ref](ref.md) lub [się](out-parameter-modifier.md) słów kluczowych, poza tym, że `in` argumentów nie można zmodyfikować przez metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="463d7-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="463d7-105">Natomiast `ref` argumentów może być modyfikowany, `out` argumenty muszą zostać zmodyfikowane przez metodę o nazwie, a te zmiany są obserwowalnymi w kontekst wywołania.</span><span class="sxs-lookup"><span data-stu-id="463d7-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="463d7-106">Poprzedni przykład pokazuje, że `in` modyfikator jest zazwyczaj zbędna w witrynie wywołania.</span><span class="sxs-lookup"><span data-stu-id="463d7-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="463d7-107">Jest wymagany tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="463d7-107">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="463d7-108">`in` — Słowo kluczowe można również za pomocą parametru typu ogólnego do określenia, czy parametr typu jest kontrawariantny, jako część `foreach` instrukcji, lub jako część `join` klauzuli w zapytaniu LINQ.</span><span class="sxs-lookup"><span data-stu-id="463d7-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="463d7-109">Aby uzyskać więcej informacji na temat użytkowania `in` Zobacz — słowo kluczowe w tych kontekstach [w](in.md), który zawiera łącza do wszystkich tych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="463d7-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="463d7-110">Zmienne są przekazywane jako `in` argumentów musi zostać zainicjowany przed przesłaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="463d7-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="463d7-111">Jednak wywoływanej metody nie może przypisać wartość lub zmodyfikuj argumentu.</span><span class="sxs-lookup"><span data-stu-id="463d7-111">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="463d7-112">Mimo że `in`, `ref`, i `out` słowa kluczowe powodować różne zachowanie w czasie wykonywania, ich nie są uważane za część podpisu metody w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="463d7-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="463d7-113">W związku z tym, nie mogą być przeciążone metody, jeśli jedyna różnica polega na to, że jedna metoda przyjmuje strukturę `ref` lub `in` argument i drugie `out` argumentu.</span><span class="sxs-lookup"><span data-stu-id="463d7-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="463d7-114">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="463d7-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="463d7-115">Przeciążenie oparte na obecność `in` jest dozwolony:</span><span class="sxs-lookup"><span data-stu-id="463d7-115">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="463d7-116">Zasad rozpoznawania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="463d7-116">Overload resolution rules</span></span>

<span data-ttu-id="463d7-117">Rozumiesz reguły rozdzielczość przeciążenia dla metod z według wartości a `in` argumenty dzięki zrozumieniu motywacją `in` argumentów.</span><span class="sxs-lookup"><span data-stu-id="463d7-117">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="463d7-118">Definiowanie metody przy użyciu `in` parametry są potencjalnymi optymalizacji wydajności.</span><span class="sxs-lookup"><span data-stu-id="463d7-118">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="463d7-119">Niektóre `struct` argumentów typu może być duży, rozmiar i metody wywołanego w ścisłej pętli lub ścieżek kodu krytycznego koszt kopiowania tych konstrukcji jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="463d7-119">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="463d7-120">Zadeklaruj metody `in` parametry, aby określić, że argumenty mogą być przekazywane przez odwołanie bezpiecznie ponieważ wywoływanej metody nie powoduje modyfikacji stanu tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="463d7-120">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="463d7-121">Przekazywanie tych argumentów poprzez odwołanie pozwala uniknąć kopiowania (potencjalnie).</span><span class="sxs-lookup"><span data-stu-id="463d7-121">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="463d7-122">Określanie `in` dla argumentów w wywołaniu witryny jest zazwyczaj opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="463d7-122">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="463d7-123">Nie ma żadnej różnicy semantycznego między przekazywanie argumentów według wartości i przekazywania ich za pomocą odwołania `in` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="463d7-123">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="463d7-124">`in` Modyfikator lokacji wywołanie jest opcjonalny, ponieważ nie wymaga wskazać, że wartość argumentu może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="463d7-124">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="463d7-125">Jawnie dodać `in` modyfikator w witrynie wywołania, aby upewnić się, argument jest przekazywany przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="463d7-125">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="463d7-126">Lepiej nie używać `in` ma następujące dwa skutki:</span><span class="sxs-lookup"><span data-stu-id="463d7-126">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="463d7-127">Po pierwsze, określając `in` w wywołaniu witryny wymusza na kompilatorze o wybranie metody zdefiniowane przy użyciu zgodnego `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="463d7-127">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="463d7-128">W przeciwnym razie, gdy dwie metody różnią się tylko w obecności właściwości `in`, według wartości przeciążenia ma lepsze dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="463d7-128">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="463d7-129">Po drugie, określając `in` deklaruje zgodne z zamiarami użytkownika do przekazywania argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="463d7-129">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="463d7-130">Argument używane z `in` musi reprezentować lokalizacji, która może być bezpośrednio określonych.</span><span class="sxs-lookup"><span data-stu-id="463d7-130">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="463d7-131">Ten sam ogólne reguły `out` i `ref` stosowanie argumentów: nie można używać stałych, właściwości zwykłych lub innych wyrażeń, które generują wartości.</span><span class="sxs-lookup"><span data-stu-id="463d7-131">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="463d7-132">W przeciwnym razie pominięcie `in` w wywołaniu witryny informuje kompilator, będą mogli go, aby utworzyć zmiennej tymczasowej, aby przekazać tylko do odczytu odwołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="463d7-132">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="463d7-133">Kompilator tworzy zmienną tymczasową celu wyeliminowanie kilku ograniczeń za pomocą `in` argumenty:</span><span class="sxs-lookup"><span data-stu-id="463d7-133">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="463d7-134">Zmienna tymczasowa umożliwia stałe kompilacji jako `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="463d7-134">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="463d7-135">Zmienna tymczasowa umożliwia właściwości lub innych wyrażeń dla `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="463d7-135">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="463d7-136">Zmienna tymczasowa zezwala argumenty w przypadku, gdy istnieje niejawna konwersja z typu argumentu z typem parametru.</span><span class="sxs-lookup"><span data-stu-id="463d7-136">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="463d7-137">We wszystkich wystąpieniach poprzedniej kompilator tworzy zmiennej tymczasowej, która przechowuje wartość stałą, właściwość lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="463d7-137">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="463d7-138">Poniższy kod ilustruje te reguły:</span><span class="sxs-lookup"><span data-stu-id="463d7-138">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="463d7-139">Teraz załóżmy, że innej metody, używając wartości argumentów była dostępna.</span><span class="sxs-lookup"><span data-stu-id="463d7-139">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="463d7-140">Wyniki zmiany, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="463d7-140">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="463d7-141">Wywołanie metody tylko wtedy, gdy argument jest przekazywany przez odwołanie jest ostatecznej.</span><span class="sxs-lookup"><span data-stu-id="463d7-141">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="463d7-142">W poprzednim kodzie użyto `int` jako typ argumentu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="463d7-142">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="463d7-143">Ponieważ `int` jest nie większy niż odwołanie w większości współczesnych komputerów jest przekazanie pojedynczej żadnych korzyści `int` jako odwołanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="463d7-143">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="463d7-144">Ograniczenia dotyczące `in` parametrów</span><span class="sxs-lookup"><span data-stu-id="463d7-144">Limitations on `in` parameters</span></span>

<span data-ttu-id="463d7-145">Nie można użyć `in`, `ref`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="463d7-145">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="463d7-146">Metody asynchroniczne, które można zdefiniować przy użyciu [async](async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="463d7-146">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="463d7-147">Metody iteratora, które obejmują [yield return](yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="463d7-147">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="463d7-148">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="463d7-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="463d7-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="463d7-149">See Also</span></span>

- [<span data-ttu-id="463d7-150">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="463d7-150">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="463d7-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="463d7-151">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="463d7-152">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="463d7-152">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="463d7-153">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="463d7-153">Method Parameters</span></span>](method-parameters.md)  
- [<span data-ttu-id="463d7-154">Pisanie kodu efektywne bezpieczne</span><span class="sxs-lookup"><span data-stu-id="463d7-154">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)  
