---
title: Automatyczna generalizacja (F#)
description: Dowiedz się, jak F# automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z wieloma typami, gdy jest to możliwe.
ms.date: 05/16/2016
ms.openlocfilehash: 84de9cbb2b9fcf2488393f7dbdfc3b610cdcffb0
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43855780"
---
# <a name="automatic-generalization"></a><span data-ttu-id="d8e26-103">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="d8e26-103">Automatic Generalization</span></span>

<span data-ttu-id="d8e26-104">F# używa wnioskowanie o typie, aby ocenić typy funkcje i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d8e26-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="d8e26-105">W tym temacie opisano, jak F# automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z wieloma typami, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d8e26-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="d8e26-106">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="d8e26-106">Automatic Generalization</span></span>

<span data-ttu-id="d8e26-107">Kompilator F#, gdy wykonuje wnioskowanie o typie dla funkcji określa, czy danego parametru może być ogólny.</span><span class="sxs-lookup"><span data-stu-id="d8e26-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="d8e26-108">Kompilator sprawdza każdy parametr i określa, czy funkcja zależny od określonego typu parametru.</span><span class="sxs-lookup"><span data-stu-id="d8e26-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="d8e26-109">Jeśli nie, typ jest wnioskowany jako ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d8e26-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="d8e26-110">Poniższy przykładowy kod przedstawia funkcję, która kompilator wnioskuje się ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d8e26-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="d8e26-111">Typ jest wnioskowany jako `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="d8e26-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="d8e26-112">Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty nieznanego tego samego typu i zwraca wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="d8e26-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="d8e26-113">Jedną z przyczyn, które mogą być poprzednim funkcji ogólnego jest to, że większa-than-operator (`>`) jest sam ogólny.</span><span class="sxs-lookup"><span data-stu-id="d8e26-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="d8e26-114">Większą-niż operator ma podpis `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="d8e26-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="d8e26-115">Nie wszystkie operatory są ogólne, a jeśli typ parametru funkcji nieogólnego lub operator korzysta z kodu w funkcji, nie mogą być uogólnione typu parametru.</span><span class="sxs-lookup"><span data-stu-id="d8e26-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="d8e26-116">Ponieważ `max` jest ogólny, może służyć z typami takich jak `int`, `float`i tak dalej, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="d8e26-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="d8e26-117">Jednak dwa argumenty muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="d8e26-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="d8e26-118">Podpis jest `'a -> 'a -> 'a`, a nie `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="d8e26-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="d8e26-119">W związku z tym poniższy kod powoduje błąd, ponieważ typy nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="d8e26-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="d8e26-120">`max` Funkcja działa także w przypadku dowolnego typu, który obsługuje większą-niż operator.</span><span class="sxs-lookup"><span data-stu-id="d8e26-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="d8e26-121">W związku z tym można również użyć tego na ciąg, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d8e26-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="d8e26-122">Ograniczenie dotyczące wartości</span><span class="sxs-lookup"><span data-stu-id="d8e26-122">Value Restriction</span></span>

<span data-ttu-id="d8e26-123">Kompilator wykonuje automatyczna Generalizacja tylko definicje pełne funkcji, które mają jawnych argumentów i prostych wartości niezmienne.</span><span class="sxs-lookup"><span data-stu-id="d8e26-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="d8e26-124">Oznacza to, że kompilator generuje błąd, Jeśli spróbujesz skompilować kod, który nie jest wystarczająco ograniczony do określonego typu, ale nie jest również generalizacji.</span><span class="sxs-lookup"><span data-stu-id="d8e26-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="d8e26-125">Komunikat o błędzie w przypadku tego problemu, który odwołuje się do tego ograniczenia na automatyczna Generalizacja wartości jako *wartość ograniczenia*.</span><span class="sxs-lookup"><span data-stu-id="d8e26-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="d8e26-126">Zazwyczaj błąd ograniczenia wartości występuje, gdy chcesz konstrukcję być rodzajowy, ale kompilator ma za mało informacji w celu uogólnienia go, lub przypadkowo pominąć wystarczających informacji o typie w konstrukcji nierodzajowych.</span><span class="sxs-lookup"><span data-stu-id="d8e26-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="d8e26-127">Rozwiązanie do błąd ograniczenia wartości jest zapewnienie dokładniejsze informacje, aby dokładniej ograniczyć problem wnioskowania typu, w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="d8e26-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="d8e26-128">Ograniczenie typ, który ma być nierodzajowych, dodając adnotację jawnego typu wartości lub parametr.</span><span class="sxs-lookup"><span data-stu-id="d8e26-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="d8e26-129">Jeśli ten problem za pomocą konstrukcji nongeneralizable do definiowania ogólnych funkcji, takich jak kompozycja funkcji lub nie w pełni zastosowane argumenty funkcji rozwinięte, próbę ponownego zapisywania pełnią definicji zwykłej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8e26-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="d8e26-130">Problem jest wyrażenie, które jest zbyt złożona, aby być uogólniony, aby ją do funkcji, dodając parametr dodatkowych, nieużywane.</span><span class="sxs-lookup"><span data-stu-id="d8e26-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="d8e26-131">Dodaj parametry jawnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d8e26-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="d8e26-132">Ta opcja jest rzadko używana.</span><span class="sxs-lookup"><span data-stu-id="d8e26-132">This option is rarely used.</span></span>

- <span data-ttu-id="d8e26-133">Poniższe przykłady kodu ilustrują każdego z tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d8e26-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="d8e26-134">Przypadek 1: Zbyt złożone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d8e26-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="d8e26-135">W tym przykładzie lista `counter` ma być `int option ref`, ale nie jest zdefiniowany jako wartość typu prostego niezmienne.</span><span class="sxs-lookup"><span data-stu-id="d8e26-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="d8e26-136">Przypadek 2: Za pomocą konstrukcji nongeneralizable, aby zdefiniować funkcję ogólną.</span><span class="sxs-lookup"><span data-stu-id="d8e26-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="d8e26-137">W tym przykładzie konstrukcja jest nongeneralizable, ponieważ spowodowałoby to częściowe stosowanie argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8e26-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="d8e26-138">Przypadek 3: Dodanie dodatkowych, nieużywane parametru.</span><span class="sxs-lookup"><span data-stu-id="d8e26-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="d8e26-139">To wyrażenie nie jest wystarczająco prosty Generalizacja, kompilator generuje błąd ograniczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="d8e26-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="d8e26-140">W przypadku 4: Dodawanie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="d8e26-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="d8e26-141">W ostatnim przypadku wartość staje się funkcji typu, który może służyć do tworzenia wartości wiele różnych typów, na przykład w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d8e26-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="d8e26-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8e26-142">See also</span></span>

- [<span data-ttu-id="d8e26-143">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="d8e26-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="d8e26-144">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d8e26-144">Generics</span></span>](index.md)
- [<span data-ttu-id="d8e26-145">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="d8e26-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="d8e26-146">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="d8e26-146">Constraints</span></span>](constraints.md)
