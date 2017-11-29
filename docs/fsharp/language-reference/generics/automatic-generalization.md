---
title: Automatyczna generalizacja (F#)
description: "Dowiedz się, jak F # automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z różnymi typami, gdy jest to możliwe."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 14a3554c-3fad-4eba-a93d-8ba07d1245b4
ms.openlocfilehash: d60831084cef76ce29f64322362b4920520f71d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-generalization"></a><span data-ttu-id="8fdf1-104">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="8fdf1-104">Automatic Generalization</span></span>

<span data-ttu-id="8fdf1-105">F # używa wnioskowanie o typie w celu oceny typów wyrażeń i funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-105">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="8fdf1-106">W tym temacie opisano, jak F # automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z różnymi typami, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-106">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="8fdf1-107">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="8fdf1-107">Automatic Generalization</span></span>
<span data-ttu-id="8fdf1-108">Kompilator języka F # podczas wykonywania wnioskowanie o typie dla funkcji, określa, czy dany parametr może być rodzajowy.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-108">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="8fdf1-109">Kompilator sprawdza każdego parametru i określa, czy funkcja ma zależność na określony typ parametru.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-109">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="8fdf1-110">Jeśli nie, typu jest wywnioskowany, aby wartość była ogólna.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-110">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="8fdf1-111">Poniższy przykładowy kod przedstawia funkcję, która wnioskuje kompilator, aby wartość była ogólna.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-111">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="8fdf1-112">Typ jest wywnioskowany jako `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-112">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="8fdf1-113">Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty nieznanego typu tego samego i zwraca wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-113">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="8fdf1-114">Jedną z przyczyn, które mogą być poprzedniej funkcji ogólnego jest to, że większa — niż — operator (`>`) jest rodzajowy.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-114">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="8fdf1-115">Większa-niż operator ma podpis `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-115">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="8fdf1-116">Nie wszystkie operatory są ogólne, a jeśli kod w funkcji korzysta z typem parametru razem z funkcji nierodzajową lub operator, nie można uogólnić typu parametru.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-116">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="8fdf1-117">Ponieważ `max` jest ogólny, można z typami takich jak `int`, `float`i tak dalej, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-117">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="8fdf1-118">Jednak dwa argumenty muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-118">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="8fdf1-119">Podpis jest `'a -> 'a -> 'a`, a nie `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-119">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="8fdf1-120">W związku z tym poniższy kod tworzy błąd, ponieważ typy są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-120">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="8fdf1-121">`max` Funkcja działa także w przypadku dowolnego typu, który obsługuje większą-niż operator.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-121">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="8fdf1-122">W związku z tym można również użyć tego na ciąg, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-122">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="8fdf1-123">Wartość ograniczenia</span><span class="sxs-lookup"><span data-stu-id="8fdf1-123">Value Restriction</span></span>
<span data-ttu-id="8fdf1-124">Kompilator wykonuje automatyczna Generalizacja tylko w definicji funkcji pełną, które mają jawne argumenty i proste modyfikować wartości.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-124">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="8fdf1-125">Oznacza to, że kompilator generuje błąd, Jeśli spróbujesz skompilować kod, który nie jest wystarczająco ograniczone do określonego typu, ale nie jest również generalizacji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-125">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="8fdf1-126">Komunikat o błędzie w przypadku tego problemu, który odwołuje się do tego ograniczenia automatyczna Generalizacja wartości jako *wartość ograniczenia*.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-126">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="8fdf1-127">Zazwyczaj błąd ograniczenie wartości występuje, gdy konstrukcji, aby wartość była ogólna a kompilator ma za mało informacji do uogólnienia go lub jeśli pominięto przypadkowo wystarczających informacji o typie w nierodzajowe konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-127">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="8fdf1-128">Rozwiązania pod kątem błędów ograniczeń wartość ma na celu dostarczenie dokładniejsze informacje do dokładniejszego ograniczyć problem wnioskowania typu, w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="8fdf1-128">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="8fdf1-129">Ograniczenie typu jako nierodzajowe przez dodanie jawną adnotację typu wartości lub parametr.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-129">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="8fdf1-130">Jeśli ten problem przy użyciu konstrukcji nongeneralizable do definiowania ogólnych funkcji, takich jak kompozycja funkcji lub nie w pełni stosowane argumenty curried funkcji, spróbuj przepisywania funkcji jako definicji zwykłej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-130">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="8fdf1-131">Problem jest wyrażenie jest zbyt złożone, aby być uogólniony, aby go do funkcji przez dodanie parametru dodatkowe, nieużywane.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-131">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="8fdf1-132">Dodaj parametry jawnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-132">Add explicit generic type parameters.</span></span> <span data-ttu-id="8fdf1-133">Ta opcja jest rzadko używana.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-133">This option is rarely used.</span></span>

- <span data-ttu-id="8fdf1-134">Poniższe przykłady kodu przedstawiają każdego z tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-134">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="8fdf1-135">Przypadek 1: Zbyt złożone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-135">Case 1: Too complex an expression.</span></span> <span data-ttu-id="8fdf1-136">W tym przykładzie listy `counter` ma być `int option ref`, ale nie jest zdefiniowany jako niezmienialny wartość prostą.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-136">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="8fdf1-137">Przypadek 2: Przy użyciu konstrukcji nongeneralizable do definiowania ogólnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-137">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="8fdf1-138">W tym przykładzie konstrukcja jest nongeneralizable, ponieważ spowodowałoby to aplikacja częściowa argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-138">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="8fdf1-139">Przypadek 3: Dodanie dodatkowych, nieużywane parametru.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-139">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="8fdf1-140">To wyrażenie nie jest wystarczająco prosty generalizacji, kompilator generuje błąd ograniczenie wartości.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-140">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="8fdf1-141">W przypadku 4: Dodawanie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="8fdf1-141">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="8fdf1-142">W ostatnim przypadku wartość staje się typ funkcji, które mogą służyć do tworzenia wartości wielu różnych typów, na przykład w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8fdf1-142">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="8fdf1-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fdf1-143">See Also</span></span>
[<span data-ttu-id="8fdf1-144">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="8fdf1-144">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="8fdf1-145">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="8fdf1-145">Generics</span></span>](index.md)

[<span data-ttu-id="8fdf1-146">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="8fdf1-146">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="8fdf1-147">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="8fdf1-147">Constraints</span></span>](constraints.md)

