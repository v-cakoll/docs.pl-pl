---
title: Automatyczna generalizacja
description: Dowiedz F# się, jak automatycznie uogólniać argumenty i typy funkcji, tak aby współpracowały z wieloma typami, gdy jest to możliwe.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630624"
---
# <a name="automatic-generalization"></a><span data-ttu-id="06425-103">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="06425-103">Automatic Generalization</span></span>

<span data-ttu-id="06425-104">F#używa wnioskowania o typie do obliczenia typów funkcji i wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="06425-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="06425-105">W tym temacie opisano F# , jak program automatycznie uogólniuje argumenty i typy funkcji, tak aby współpracowały z wieloma typami, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="06425-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="06425-106">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="06425-106">Automatic Generalization</span></span>

<span data-ttu-id="06425-107">F# Kompilator, gdy wykonuje wnioskowanie o typie dla funkcji, określa, czy dany parametr może być ogólny.</span><span class="sxs-lookup"><span data-stu-id="06425-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="06425-108">Kompilator sprawdza każdy parametr i określa, czy funkcja ma zależność od określonego typu parametru.</span><span class="sxs-lookup"><span data-stu-id="06425-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="06425-109">Jeśli tak nie jest, typ jest wywnioskowany jako ogólny.</span><span class="sxs-lookup"><span data-stu-id="06425-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="06425-110">Poniższy przykład kodu ilustruje funkcję, którą kompilator wnioskuje za ogólny.</span><span class="sxs-lookup"><span data-stu-id="06425-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="06425-111">Typ jest wywnioskowany `'a -> 'a -> 'a`jako.</span><span class="sxs-lookup"><span data-stu-id="06425-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="06425-112">Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty tego samego nieznanego typu i zwraca wartość tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="06425-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="06425-113">Jedną z powodów, w których można użyć poprzedniej funkcji, jest to, że operator większości (`>`) jest sama jako ogólny.</span><span class="sxs-lookup"><span data-stu-id="06425-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="06425-114">Operator większa niż jest sygnaturą `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="06425-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="06425-115">Nie wszystkie operatory są ogólne i jeśli kod w funkcji używa typu parametru wraz z nieogólną funkcją lub operatorem, ten typ parametru nie może być uogólniony.</span><span class="sxs-lookup"><span data-stu-id="06425-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="06425-116">Ponieważ `max` jest ogólny, można go używać z typami takimi jak `int`, `float`, i tak dalej, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="06425-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="06425-117">Jednak te dwa argumenty muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="06425-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="06425-118">Sygnatura to `'a -> 'a -> 'a`, nie `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="06425-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="06425-119">W związku z tym Poniższy kod generuje błąd, ponieważ typy nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="06425-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="06425-120">`max` Funkcja działa również z dowolnym typem, który obsługuje operator większości.</span><span class="sxs-lookup"><span data-stu-id="06425-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="06425-121">Z tego względu można również użyć go w ciągu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="06425-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="06425-122">Ograniczenie wartości</span><span class="sxs-lookup"><span data-stu-id="06425-122">Value Restriction</span></span>

<span data-ttu-id="06425-123">Kompilator wykonuje automatyczne uogólnianie tylko w przypadku kompletnych definicji funkcji, które mają jawne argumenty i w przypadku prostych niezmiennych wartości.</span><span class="sxs-lookup"><span data-stu-id="06425-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="06425-124">Oznacza to, że kompilator wystawia błąd w przypadku próby skompilowania kodu, który nie jest wystarczająco ograniczony do określonego typu, ale również nie jest możliwe jego uogólnienie.</span><span class="sxs-lookup"><span data-stu-id="06425-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="06425-125">Komunikat o błędzie dotyczący tego problemu dotyczy tego ograniczenia dotyczącego automatycznego uogólniania wartości jako *ograniczenia wartości*.</span><span class="sxs-lookup"><span data-stu-id="06425-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="06425-126">Zazwyczaj błąd ograniczenia wartości występuje, gdy konstrukcja ma być ogólna, ale kompilator nie ma wystarczających informacji do jego uogólnienia lub gdy przypadkowo pominięto wystarczające informacje o typie w nieogólnej konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="06425-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="06425-127">Rozwiązaniem związanym z błędem ograniczenia wartości jest dostarczenie bardziej jawnych informacji w celu bardziej pełnego ograniczenia problemu wnioskowania o typie w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="06425-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="06425-128">Ogranicz typ jako nieogólny przez dodanie jawnej adnotacji typu do wartości lub parametru.</span><span class="sxs-lookup"><span data-stu-id="06425-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="06425-129">Jeśli problem używa konstrukcji niemożliwej do uogólnienia w celu zdefiniowania funkcji ogólnej, takiej jak kompozycja funkcji lub nieukończone zastosowane argumenty funkcji rozwinięte, spróbuj ponownie napisać funkcję jako definicję zwykłej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06425-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="06425-130">Jeśli problem jest wyrażeniem, które jest zbyt złożone, aby było uogólnione, ustaw go w funkcji przez dodanie dodatkowego, nieużywanego parametru.</span><span class="sxs-lookup"><span data-stu-id="06425-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="06425-131">Dodawanie jawnych parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06425-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="06425-132">Ta opcja jest rzadko używana.</span><span class="sxs-lookup"><span data-stu-id="06425-132">This option is rarely used.</span></span>

- <span data-ttu-id="06425-133">Poniższe przykłady kodu ilustrują poszczególne z tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="06425-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="06425-134">Przypadek 1: Wyrażenie jest zbyt złożone.</span><span class="sxs-lookup"><span data-stu-id="06425-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="06425-135">W tym przykładzie lista `counter` jest przeznaczona `int option ref`do, ale nie jest zdefiniowana jako prosta niezmienna wartość.</span><span class="sxs-lookup"><span data-stu-id="06425-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="06425-136">Przypadek 2: Definiowanie funkcji ogólnej przy użyciu konstrukcji nieuogólnieniowej.</span><span class="sxs-lookup"><span data-stu-id="06425-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="06425-137">W tym przykładzie konstrukcja jest nieuogólnienia, ponieważ obejmuje częściowe stosowanie argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="06425-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="06425-138">Przypadek 3: Dodawanie dodatkowego, nieużywanego parametru.</span><span class="sxs-lookup"><span data-stu-id="06425-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="06425-139">Ponieważ to wyrażenie nie jest wystarczająco proste dla generalizacji, kompilator wystawia błąd ograniczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="06425-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="06425-140">Przypadek 4: Dodawanie parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="06425-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="06425-141">W ostatnim przypadku wartość jest funkcją typu, która może służyć do tworzenia wartości wielu różnych typów, na przykład w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="06425-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="06425-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06425-142">See also</span></span>

- [<span data-ttu-id="06425-143">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="06425-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="06425-144">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="06425-144">Generics</span></span>](index.md)
- [<span data-ttu-id="06425-145">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="06425-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="06425-146">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06425-146">Constraints</span></span>](constraints.md)
