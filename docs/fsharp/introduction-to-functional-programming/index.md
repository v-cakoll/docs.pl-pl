---
title: Wprowadzenie do programowania funkcyjnego w F#
description: Poznaj podstawy programowania funkcyjnego w F#.
ms.date: 10/29/2018
ms.openlocfilehash: 84022e58c0f17b9e9875402c653c31e494e940da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772791"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="f321e-103">Wprowadzenie do programowania funkcyjnego w F\#</span><span class="sxs-lookup"><span data-stu-id="f321e-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="f321e-104">Programowanie funkcjonalne jest stylu programowania, która kładzie nacisk na korzystanie z funkcji i niezmienialnymi danymi.</span><span class="sxs-lookup"><span data-stu-id="f321e-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="f321e-105">Jest wpisane programowania funkcjonalnego, podczas programowania funkcjonalnego jest połączony z typów statycznych, takich jak za pomocą F#.</span><span class="sxs-lookup"><span data-stu-id="f321e-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="f321e-106">Ogólnie rzecz biorąc następujące pojęcia są wyróżniono w programowaniu funkcjonalności:</span><span class="sxs-lookup"><span data-stu-id="f321e-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="f321e-107">Funkcje jako głównymi konstrukcjami, których używasz</span><span class="sxs-lookup"><span data-stu-id="f321e-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="f321e-108">Wyrażeń, zamiast instrukcji</span><span class="sxs-lookup"><span data-stu-id="f321e-108">Expressions instead of statements</span></span>
* <span data-ttu-id="f321e-109">Niezmienne wartości zmiennych</span><span class="sxs-lookup"><span data-stu-id="f321e-109">Immutable values over variables</span></span>
* <span data-ttu-id="f321e-110">Programowanie deklaratywne za pośrednictwem programowanie imperatywne</span><span class="sxs-lookup"><span data-stu-id="f321e-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="f321e-111">W tej serii przedstawimy pojęcia i wzorce w funkcjonalności programowania przy użyciu F#.</span><span class="sxs-lookup"><span data-stu-id="f321e-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="f321e-112">Po drodze dowiesz się, niektóre F# zbyt.</span><span class="sxs-lookup"><span data-stu-id="f321e-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="f321e-113">Terminologia</span><span class="sxs-lookup"><span data-stu-id="f321e-113">Terminology</span></span>

<span data-ttu-id="f321e-114">Programowanie funkcjonalne, podobnie jak inne programowania paradygmatów jest powiązana z słownictwo, który ostatecznie trzeba będzie Dowiedz się więcej.</span><span class="sxs-lookup"><span data-stu-id="f321e-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="f321e-115">Poniżej przedstawiono niektóre typowe terminy, zobaczysz cały czas:</span><span class="sxs-lookup"><span data-stu-id="f321e-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="f321e-116">**Funkcja** — funkcja jest konstrukcja, która spowoduje wygenerowanie danych wyjściowych, gdy dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f321e-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="f321e-117">Więcej formalnie go _mapuje_ element z jednego zestawu do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f321e-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="f321e-118">Ta formalism zostało zniesione pod konkretny na wiele sposobów, zwłaszcza w przypadku korzystania z funkcji, które działają na zbiory danych.</span><span class="sxs-lookup"><span data-stu-id="f321e-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="f321e-119">To najbardziej podstawowy (i ważne) pojęciem programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="f321e-120">**Wyrażenie** -wyrażenie jest konstrukcja w kodzie, który generuje wartość.</span><span class="sxs-lookup"><span data-stu-id="f321e-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="f321e-121">W F#, ta wartość musi być powiązany lub jawnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f321e-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="f321e-122">Wyrażenie może być przypadku zastąpiony wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="f321e-123">**Czystość** -czystości to właściwość funkcji w taki sposób, że jego wartość zwracana jest zawsze taki sam, aby uzyskać te same argumenty i że jego oceny nie ma żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="f321e-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="f321e-124">Czystej funkcji zależy od całkowicie argumentów.</span><span class="sxs-lookup"><span data-stu-id="f321e-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="f321e-125">**Przezroczystość referencyjną** -referencyjną przezroczystości jest właściwość wyrażeń taki sposób, że ich, można zastąpić swoje dane wyjściowe bez wywierania wpływu na zachowanie programu.</span><span class="sxs-lookup"><span data-stu-id="f321e-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="f321e-126">**Niezmienność** -niezmienności oznacza wartość nie może być zmieniona w miejscu.</span><span class="sxs-lookup"><span data-stu-id="f321e-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="f321e-127">Jest to w przeciwieństwie do zmiennych, które można zmienić w miejscu.</span><span class="sxs-lookup"><span data-stu-id="f321e-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="f321e-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f321e-128">Examples</span></span>

<span data-ttu-id="f321e-129">W poniższych przykładach pokazano tych podstawowych założeń.</span><span class="sxs-lookup"><span data-stu-id="f321e-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="f321e-130">Funkcje</span><span class="sxs-lookup"><span data-stu-id="f321e-130">Functions</span></span>

<span data-ttu-id="f321e-131">Najbardziej typowe i podstawowe konstrukcję w programowania funkcjonalnego jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="f321e-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="f321e-132">Poniżej przedstawiono prosty funkcja, która dodaje 1 na liczbę całkowitą:</span><span class="sxs-lookup"><span data-stu-id="f321e-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="f321e-133">Podpis jego typ jest następująca:</span><span class="sxs-lookup"><span data-stu-id="f321e-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="f321e-134">Podpis mogą być odczytywane jako "`addOne` akceptuje `int` o nazwie `x` i będzie generować `int`".</span><span class="sxs-lookup"><span data-stu-id="f321e-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="f321e-135">Więcej formalnie `addOne` jest _mapowania_ wartość z liczby całkowite na liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="f321e-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="f321e-136">`->` Token, oznacza to mapowanie.</span><span class="sxs-lookup"><span data-stu-id="f321e-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="f321e-137">W F#, zwykle przyjrzymy się sygnatura funkcji, aby poznać jego przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="f321e-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="f321e-138">Dlatego jest podpis ważna</span><span class="sxs-lookup"><span data-stu-id="f321e-138">So, why is the signature important?</span></span> <span data-ttu-id="f321e-139">W typizowanych programowania funkcjonalnego, implementacja funkcji jest często mniej istotne niż rzeczywisty typ podpisu!</span><span class="sxs-lookup"><span data-stu-id="f321e-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="f321e-140">Fakt, `addOne` dodaje wartość od 1 do liczby całkowitej jest interesująca w czasie wykonywania, ale gdy są konstruowanie programu fakt, że akceptuje i zwraca `int` to, co informuje, jak faktycznie użyjesz tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="f321e-141">Ponadto, gdy funkcja poprawnie (względem jeho signatura typu), diagnozowanie problemów może odbywać się tylko w treści `addOne` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="f321e-142">Jest to tempa za wpisane programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="f321e-143">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f321e-143">Expressions</span></span>

<span data-ttu-id="f321e-144">Wyrażenia są konstrukcji, które obliczają do wartości.</span><span class="sxs-lookup"><span data-stu-id="f321e-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="f321e-145">W przeciwieństwie do instrukcji, które wykonują akcję, można traktować wyrażeń wykonywanie akcji, która zapewnia ponownie wartość.</span><span class="sxs-lookup"><span data-stu-id="f321e-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="f321e-146">Wyrażenia prawie zawsze są używane na rzecz instrukcji programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="f321e-147">Należy wziąć pod uwagę poprzednie funkcji `addOne`.</span><span class="sxs-lookup"><span data-stu-id="f321e-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="f321e-148">Treść `addOne` to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="f321e-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="f321e-149">Jest to wynik tego wyrażenia, który definiuje typ wyniku `addOne` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="f321e-150">Na przykład, wyrażenie, które tworzą tej funkcji można ją zmienić w taki sposób, na być innego typu, taką jak `string`:</span><span class="sxs-lookup"><span data-stu-id="f321e-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="f321e-151">Podpis funkcji jest teraz:</span><span class="sxs-lookup"><span data-stu-id="f321e-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="f321e-152">Od dowolnego typu w F# może mieć `ToString()` wywoływać w nim typ `x` wprowadzono ogólnego (o nazwie [automatyczna Generalizacja](../language-reference/generics/automatic-generalization.md)), a wynikowy typ to `string`.</span><span class="sxs-lookup"><span data-stu-id="f321e-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="f321e-153">Wyrażenia nie są po prostu treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="f321e-154">Może mieć wyrażenia, które generują wartość, których używasz w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="f321e-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="f321e-155">Często jest `if`:</span><span class="sxs-lookup"><span data-stu-id="f321e-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="f321e-156">`if` Wyrażenia generują wartość o nazwie `result`.</span><span class="sxs-lookup"><span data-stu-id="f321e-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="f321e-157">Należy zauważyć, że można pominąć `result` całości, dzięki czemu `if` wyrażenia treści z `addOneIfOdd` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="f321e-158">Kluczową kwestią do zapamiętania informacji na temat wyrażeń jest, aby spowodować wartość.</span><span class="sxs-lookup"><span data-stu-id="f321e-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="f321e-159">Jest specjalnym typem `unit`, który jest używany, gdy nie ma nic do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="f321e-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="f321e-160">Na przykład należy wziąć pod uwagę tej prostej funkcji:</span><span class="sxs-lookup"><span data-stu-id="f321e-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="f321e-161">Podpis wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="f321e-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="f321e-162">`unit` Typu wskazuje, że nie ma rzeczywiste wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="f321e-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="f321e-163">Jest to przydatne, gdy masz procedurę, która musi "work" pomimo posiadanie żadnej wartości do zwrócenia w wyniku tej pracy.</span><span class="sxs-lookup"><span data-stu-id="f321e-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="f321e-164">To sharp natomiast do programowania imperatywnego, gdzie odpowiednik `if` konstrukcja jest instrukcją i produkcji wartości często odbywa się za pomocą mutacja zmiennych.</span><span class="sxs-lookup"><span data-stu-id="f321e-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="f321e-165">Na przykład w C#, kod może być zapisany jako:</span><span class="sxs-lookup"><span data-stu-id="f321e-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="f321e-166">Warto zauważyć, że C# i innych językach w stylu języka C obsługuje [trójargumentowy wyrażenie](../../csharp/language-reference/operators/conditional-operator.md), co umożliwia oparte na wyrażeniach warunkowych programowania.</span><span class="sxs-lookup"><span data-stu-id="f321e-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="f321e-167">W programowaniu funkcjonalności, to rzadkość, aby mutować wartości za pomocą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="f321e-168">Mimo że w przypadku niektórych języków funkcjonalnych obsługuje oświadczenia i mutacji, nie jest często używa tych pojęć w programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="f321e-169">Czystych funkcji</span><span class="sxs-lookup"><span data-stu-id="f321e-169">Pure functions</span></span>

<span data-ttu-id="f321e-170">Jak wspomniano wcześniej, czystej funkcji funkcji:</span><span class="sxs-lookup"><span data-stu-id="f321e-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="f321e-171">Zawsze należy przeprowadzić ocenę na tę samą wartość dla tych samych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f321e-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="f321e-172">Mieć żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="f321e-172">Have no side effects.</span></span>

<span data-ttu-id="f321e-173">Warto traktować funkcji matematycznych, w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="f321e-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="f321e-174">W matematyce funkcje być zależne tylko od ich argumentów i nie ma żadnych efektów ubocznych.</span><span class="sxs-lookup"><span data-stu-id="f321e-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="f321e-175">W funkcji matematycznych `f(x) = x + 1`, wartość `f(x)` zależy tylko od wartości `x`.</span><span class="sxs-lookup"><span data-stu-id="f321e-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="f321e-176">Czystej funkcji w programowania funkcjonalnego jest taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f321e-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="f321e-177">Podczas pisania czystą funkcję, funkcja musi być zależne tylko od argumentów i wykonuje żadnych działań, które powoduje efekt uboczny.</span><span class="sxs-lookup"><span data-stu-id="f321e-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="f321e-178">Oto przykład-czystej funkcji, ponieważ zależy od globalnej, modyfikowalnego stanu:</span><span class="sxs-lookup"><span data-stu-id="f321e-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="f321e-179">`addOneToValue` Funkcja jest wyraźnie oczyścić zanieczyszczony, ponieważ `value` można zmienić w dowolnym momencie, będzie mieć wartość inną niż 1.</span><span class="sxs-lookup"><span data-stu-id="f321e-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="f321e-180">Tego wzorca w zależności od wartości globalnej jest unikać w programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="f321e-181">Oto inny przykład-czystą funkcję, bo efekt uboczny:</span><span class="sxs-lookup"><span data-stu-id="f321e-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="f321e-182">Chociaż ta funkcja nie zależy od wartości globalnej, zapisuje wartość `x` danych wyjściowych programu.</span><span class="sxs-lookup"><span data-stu-id="f321e-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="f321e-183">Mimo że nie ma natury błąd w ten sposób, to oznacza, że funkcja nie jest czysty.</span><span class="sxs-lookup"><span data-stu-id="f321e-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="f321e-184">Jeśli innej części programu, który jest zależna od coś zewnętrznego do programu, takie jak bufor wyjściowy następnie wywołaniu tej funkcji może mieć wpływ na tę część programu.</span><span class="sxs-lookup"><span data-stu-id="f321e-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="f321e-185">Usuwanie `printfn` instrukcji sprawia, że funkcja jest czysty:</span><span class="sxs-lookup"><span data-stu-id="f321e-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="f321e-186">Chociaż ta funkcja nie jest z natury _lepsze_ niż poprzednia wersja z `printfn` instrukcji zagwarantować wszystkie ta funkcja nie jest zwrócona wartość.</span><span class="sxs-lookup"><span data-stu-id="f321e-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="f321e-187">Wywołanie tej funkcji dowolną liczbę razy daje ten sam wynik: po prostu tworzy wartość.</span><span class="sxs-lookup"><span data-stu-id="f321e-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="f321e-188">Przewidywalność podane przez czystości sytuacji niełatwo jest wielu programistów funkcjonalności Dokładamy wszelkich starań, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="f321e-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="f321e-189">Niezmienność</span><span class="sxs-lookup"><span data-stu-id="f321e-189">Immutability</span></span>

<span data-ttu-id="f321e-190">Na koniec jest jedną z najbardziej podstawowe pojęcia programowania funkcjonalnego wpisane niezmienności.</span><span class="sxs-lookup"><span data-stu-id="f321e-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="f321e-191">W F#, wszystkie wartości są niezmienne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f321e-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="f321e-192">Oznacza to, że nie może być zmutowania na miejscu, chyba że wyraźnie oznaczyć je jako modyfikowalna.</span><span class="sxs-lookup"><span data-stu-id="f321e-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="f321e-193">W praktyce Praca z wartościami niezmiennymi oznacza, że zmienić swoje podejście do programowania z "Muszę coś zmienić", aby "należy utworzyć nową wartość".</span><span class="sxs-lookup"><span data-stu-id="f321e-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="f321e-194">Na przykład dodawanie 1 na wartość oznacza produkujących nową wartość, nie mutacja istniejącą grupę:</span><span class="sxs-lookup"><span data-stu-id="f321e-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="f321e-195">W F#, poniższy kod wykonuje **nie** mutować `value` funkcji; zamiast tego wykonuje sprawdzanie równości:</span><span class="sxs-lookup"><span data-stu-id="f321e-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="f321e-196">Niektóre funkcjonalności języki programowania nie obsługują na wszystkich mutacji.</span><span class="sxs-lookup"><span data-stu-id="f321e-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="f321e-197">W F#, jest obsługiwane, ale nie jest to domyślne zachowanie dla wartości.</span><span class="sxs-lookup"><span data-stu-id="f321e-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="f321e-198">Rozszerza tę koncepcję nawet bardziej struktur danych.</span><span class="sxs-lookup"><span data-stu-id="f321e-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="f321e-199">W programowania funkcjonalnego, danymi niezmiennymi struktury, takich jak zestawy (i wielu innych) mają różne implementacje niż może być początkowo się spodziewać.</span><span class="sxs-lookup"><span data-stu-id="f321e-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="f321e-200">Model coś, takie jak dodanie elementu do zestawu nie zmienia się zestaw, generuje _nowe_ zestawu przy użyciu wartości dodanej.</span><span class="sxs-lookup"><span data-stu-id="f321e-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="f321e-201">Dzieje się w tle to często odbywa się przez to struktura różnych danych, która pozwala na efektywne śledzenia wartość tak, aby w efekcie można podać odpowiednie reprezentacja danych.</span><span class="sxs-lookup"><span data-stu-id="f321e-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="f321e-202">Ten styl pracy z wartościami i struktur danych ma krytyczne znaczenie, ponieważ wymusza można traktować każdej operacji, która modyfikuje coś tak, jakby tworzy nową wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f321e-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="f321e-203">Umożliwi to np. równości i porównywalności zachować spójność w swoich programach.</span><span class="sxs-lookup"><span data-stu-id="f321e-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f321e-204">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f321e-204">Next steps</span></span>

<span data-ttu-id="f321e-205">Następna sekcja dokładnie obejmuje funkcje, eksplorowanie różne sposoby, można ich używać w programowania funkcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="f321e-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="f321e-206">[Funkcje pierwszej klasy](first-class-functions.md) Eksploruje funkcje głęboko, przedstawiający sposób ich użycia w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="f321e-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="f321e-207">Dalsze informacje</span><span class="sxs-lookup"><span data-stu-id="f321e-207">Further reading</span></span>

<span data-ttu-id="f321e-208">[Myśl funkcjonalnie](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) seria jest innym świetnym zasobem, aby dowiedzieć się więcej o programowania funkcjonalnego, za pomocą F#.</span><span class="sxs-lookup"><span data-stu-id="f321e-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="f321e-209">Poruszono w nim podstawowe informacje na temat programowania funkcjonalnego w sposób pragmatyczne i łatwe do odczytania przy użyciu F# funkcji w celu zilustrowania koncepcji.</span><span class="sxs-lookup"><span data-stu-id="f321e-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
