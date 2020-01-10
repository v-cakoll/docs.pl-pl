---
title: modyfikator parametru- C# Reference
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715252"
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="65240-102">w modyfikatorze parametruC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="65240-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="65240-103">Słowo kluczowe `in` powoduje, że argumenty są przekazane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="65240-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="65240-104">Sprawia, że parametr formalny jest aliasem dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="65240-104">It makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="65240-105">Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie.</span><span class="sxs-lookup"><span data-stu-id="65240-105">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="65240-106">Przypomina słowa kluczowe [ref](ref.md) lub [out](out-parameter-modifier.md) , z tą różnicą, że `in` argumenty nie mogą być modyfikowane przez wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="65240-106">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="65240-107">`ref` argumenty mogą być modyfikowane, `out` argumenty muszą być modyfikowane przez wywołaną metodę, a te modyfikacje są zauważalne w kontekście wywołującym.</span><span class="sxs-lookup"><span data-stu-id="65240-107">Whereas `ref` arguments may be modified, `out` arguments must be modified by the called method, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="65240-108">W poprzednim przykładzie pokazano, że modyfikator `in` jest zwykle zbędny w odróżnieniu od lokacji wywołania.</span><span class="sxs-lookup"><span data-stu-id="65240-108">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="65240-109">Jest to wymagane tylko w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="65240-109">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="65240-110">Słowa kluczowego `in` można również użyć z parametrem typu ogólnego, aby określić, że parametr typu jest kontrawariantne, jako część instrukcji `foreach` lub jako część klauzuli `join` w zapytaniu LINQ.</span><span class="sxs-lookup"><span data-stu-id="65240-110">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="65240-111">Aby uzyskać więcej informacji na temat używania słowa kluczowego `in` w tych kontekstach, zobacz sekcję [w](in.md)temacie, która zawiera linki do wszystkich tych celów.</span><span class="sxs-lookup"><span data-stu-id="65240-111">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
<span data-ttu-id="65240-112">Zmienne przekazane jako argumenty `in` muszą być inicjowane przed przekazaniem w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="65240-112">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="65240-113">Jednak wywołana metoda nie może przypisywać wartości ani modyfikować argumentu.</span><span class="sxs-lookup"><span data-stu-id="65240-113">However, the called method may not assign a value or modify the argument.</span></span>  

<span data-ttu-id="65240-114">Modyfikator parametru `in` jest dostępny w C# 7,2 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="65240-114">The `in` parameter modifier is available in C# 7.2 and later.</span></span> <span data-ttu-id="65240-115">Poprzednie wersje generują błędy kompilatora `CS8107` ("funkcja" odwołania tylko do odczytu "jest C# niedostępna w 7,0.</span><span class="sxs-lookup"><span data-stu-id="65240-115">Previous versions generate compiler error `CS8107` ("Feature 'readonly references' is not available in C# 7.0.</span></span> <span data-ttu-id="65240-116">Użyj języka w wersji 7,2 lub nowszej. ") Aby skonfigurować wersję języka kompilatora, zobacz [Wybieranie wersji C# językowej](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="65240-116">Please use language version 7.2 or greater.") To configure the compiler language version, see [Select the C# language version](../configure-language-version.md).</span></span>

<span data-ttu-id="65240-117">Słowa kluczowe `in`, `ref`i `out` nie są uważane za część podpisu metody na potrzeby rozpoznawania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="65240-117">The `in`, `ref`, and `out` keywords are not considered part of the method signature for the purpose of overload resolution.</span></span> <span data-ttu-id="65240-118">W związku z tym metody nie mogą być przeciążone, jeśli jedyną różnicą jest to, że jedna metoda przyjmuje argument `ref` lub `in`, a drugi przyjmuje argument `out`.</span><span class="sxs-lookup"><span data-stu-id="65240-118">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="65240-119">Poniższy kod, na przykład, nie zostanie skompilowany:</span><span class="sxs-lookup"><span data-stu-id="65240-119">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="65240-120">Przeciążanie na podstawie obecności `in` jest dozwolone:</span><span class="sxs-lookup"><span data-stu-id="65240-120">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="65240-121">Reguły rozpoznawania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="65240-121">Overload resolution rules</span></span>

<span data-ttu-id="65240-122">Można zrozumieć reguły rozpoznawania przeciążeń dla metod za pomocą wartości przez wartość i `in` argumenty przez zrozumienie motywacji argumentów `in`.</span><span class="sxs-lookup"><span data-stu-id="65240-122">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="65240-123">Definiowanie metod przy użyciu parametrów `in` jest potencjalną optymalizacją wydajności.</span><span class="sxs-lookup"><span data-stu-id="65240-123">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="65240-124">Niektóre argumenty typu `struct` mogą być duże, a gdy metody są wywoływane przy użyciu ścisłych pętli lub ścieżek kodu krytycznego, koszt kopiowania tych struktur jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="65240-124">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="65240-125">Metody deklarują `in` parametry, aby określić, że argumenty mogą być przekazane przez odwołanie bezpiecznie, ponieważ wywołana metoda nie modyfikuje stanu tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="65240-125">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="65240-126">Przekazanie tych argumentów przez odwołanie pozwala uniknąć (potencjalnie) kosztownego kopiowania.</span><span class="sxs-lookup"><span data-stu-id="65240-126">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="65240-127">Określanie `in` dla argumentów w miejscu wywołania jest zwykle opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="65240-127">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="65240-128">Między przekazywaniem argumentów przez wartość i przekazaniem ich przez odwołanie przy użyciu modyfikatora `in` nie ma różnicy semantycznej.</span><span class="sxs-lookup"><span data-stu-id="65240-128">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="65240-129">Modyfikator `in` w miejscu wywołania jest opcjonalny, ponieważ nie trzeba wskazywać, że wartość argumentu może zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="65240-129">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="65240-130">Należy jawnie dodać modyfikator `in` w miejscu wywołania, aby upewnić się, że argument jest przenoszona przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="65240-130">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="65240-131">Jawnie używanie `in` ma dwa następujące efekty:</span><span class="sxs-lookup"><span data-stu-id="65240-131">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="65240-132">Najpierw Określanie `in` w witrynie wywołania wymusza, aby kompilator wybierał metodę zdefiniowaną za pomocą pasującego parametru `in`.</span><span class="sxs-lookup"><span data-stu-id="65240-132">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="65240-133">W przeciwnym razie, gdy dwie metody różnią się tylko w obecności `in`, Przeciążenie przez wartość jest lepszym dopasowaniem.</span><span class="sxs-lookup"><span data-stu-id="65240-133">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="65240-134">Po drugie, określenie `in` deklaruje intencję przekazania argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="65240-134">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="65240-135">Argument używany z `in` musi reprezentować lokalizację, do której może odwoływać się bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="65240-135">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="65240-136">Te same reguły ogólne dla argumentów `out` i `ref` mają zastosowanie: nie można użyć stałych, zwykłych właściwości ani innych wyrażeń, które tworzą wartości.</span><span class="sxs-lookup"><span data-stu-id="65240-136">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="65240-137">W przeciwnym razie pominięcie `in` w witrynie wywołania informuje kompilator, że umożliwi to utworzenie zmiennej tymczasowej do przekazania przez odwołanie tylko do odczytu do metody.</span><span class="sxs-lookup"><span data-stu-id="65240-137">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="65240-138">Kompilator tworzy zmienną tymczasową, aby przezwyciężyć kilka ograniczeń z `in` argumentami:</span><span class="sxs-lookup"><span data-stu-id="65240-138">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="65240-139">Zmienna tymczasowa dopuszcza stałe w czasie kompilacji jako parametry `in`.</span><span class="sxs-lookup"><span data-stu-id="65240-139">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="65240-140">Zmienna tymczasowa zezwala na właściwości lub inne wyrażenia dla `in` parametrów.</span><span class="sxs-lookup"><span data-stu-id="65240-140">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="65240-141">Zmienna tymczasowa zezwala na argumenty, w których istnieje niejawna konwersja z typu argumentu na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="65240-141">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="65240-142">We wszystkich poprzednich wystąpieniach kompilator tworzy zmienną tymczasową, która przechowuje wartość stałej, właściwości lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="65240-142">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="65240-143">Poniższy kod ilustruje następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="65240-143">The following code illustrates these rules:</span></span>

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

<span data-ttu-id="65240-144">Teraz Załóżmy, że jest dostępna inna metoda używająca argumentów wartości.</span><span class="sxs-lookup"><span data-stu-id="65240-144">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="65240-145">Wyniki są zmieniane, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="65240-145">The results change as shown in the following code:</span></span>

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

<span data-ttu-id="65240-146">Jedyne wywołanie metody, do którego argument jest przenoszona przez odwołanie jest ostatnim z nich.</span><span class="sxs-lookup"><span data-stu-id="65240-146">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="65240-147">Poprzedni kod używa `int` jako typ argumentu dla uproszczenia.</span><span class="sxs-lookup"><span data-stu-id="65240-147">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="65240-148">Ponieważ `int` nie jest większy niż odwołanie w większości nowoczesnych maszyn, nie ma korzyści, aby przekazywać pojedynczy `int` jako odwołanie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="65240-148">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="65240-149">Ograniczenia dotyczące parametrów `in`</span><span class="sxs-lookup"><span data-stu-id="65240-149">Limitations on `in` parameters</span></span>

<span data-ttu-id="65240-150">Nie można użyć słów kluczowych `in`, `ref`i `out` dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="65240-150">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="65240-151">Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="65240-151">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="65240-152">Metody iteratorów, które zawierają instrukcję [yield return](yield.md) lub `yield break`.</span><span class="sxs-lookup"><span data-stu-id="65240-152">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="65240-153">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="65240-153">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65240-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65240-154">See also</span></span>

- [<span data-ttu-id="65240-155">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="65240-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="65240-156">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="65240-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="65240-157">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="65240-157">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="65240-158">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="65240-158">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="65240-159">Zapisz bezpieczny wydajny kod</span><span class="sxs-lookup"><span data-stu-id="65240-159">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
