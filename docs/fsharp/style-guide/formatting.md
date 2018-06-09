---
title: 'Wskazówki dotyczące formatowania kodu języka F #'
description: 'Dowiedz się wskazówki dotyczące formatowania kodu F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6c8e4059fd4bf1e7450118a6df02609217c4f4db
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231513"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="85e40-103">Wskazówki dotyczące formatowania kodu języka F #</span><span class="sxs-lookup"><span data-stu-id="85e40-103">F# code formatting guidelines</span></span>

<span data-ttu-id="85e40-104">Ten artykuł zawiera wskazówki dotyczące formatowania kodu tak, aby w kodzie języka F # jest:</span><span class="sxs-lookup"><span data-stu-id="85e40-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="85e40-105">Zazwyczaj są wyświetlane jako bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="85e40-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="85e40-106">Jest zgodnie z konwencjami stosowane przez formatowania narzędzia w programie Visual Studio i innych edytorów</span><span class="sxs-lookup"><span data-stu-id="85e40-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="85e40-107">Podobnie jak inne kodem online</span><span class="sxs-lookup"><span data-stu-id="85e40-107">Similar to other code online</span></span>

<span data-ttu-id="85e40-108">Niniejsze wytyczne dotyczą [kompletny przewodnik F # formatowania konwencje](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) przez [Phan Anh obornik](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="85e40-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="85e40-109">Ogólne zasady wcięcie</span><span class="sxs-lookup"><span data-stu-id="85e40-109">General rules for indentation</span></span>

<span data-ttu-id="85e40-110">F # domyślnie używa znaczącym odstępem.</span><span class="sxs-lookup"><span data-stu-id="85e40-110">F# uses significant whitespace by default.</span></span> <span data-ttu-id="85e40-111">Poniższe wskazówki są przeznaczone do zawierają wskazówki dotyczące sposobu łatwiejszą obsługę niektóre wyzwania, które to skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="85e40-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="85e40-112">Przy użyciu spacji</span><span class="sxs-lookup"><span data-stu-id="85e40-112">Using spaces</span></span>

<span data-ttu-id="85e40-113">Gdy wymagana jest wcięcie, należy użyć spacje, tabulatory nie.</span><span class="sxs-lookup"><span data-stu-id="85e40-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="85e40-114">Wymagana jest co najmniej jedną przestrzeń.</span><span class="sxs-lookup"><span data-stu-id="85e40-114">At least one space is required.</span></span> <span data-ttu-id="85e40-115">Organizacja może utworzyć standardów kodowania, aby określić liczbę spacji dla wcięć; Typowy jest dwóch, trzech lub czterech spacji wcięcia na każdym poziomie, gdzie występuje wcięcia.</span><span class="sxs-lookup"><span data-stu-id="85e40-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="85e40-116">**Zalecamy 4 spacje na wcięcia.**</span><span class="sxs-lookup"><span data-stu-id="85e40-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="85e40-117">Inaczej mówiąc, wcięcia programów polega na subiektywne.</span><span class="sxs-lookup"><span data-stu-id="85e40-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="85e40-118">Zmiany są dozwolone, ale jest pierwszą regułę, należy wykonać *spójności wcięcia*.</span><span class="sxs-lookup"><span data-stu-id="85e40-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="85e40-119">Wybierz styl ogólnie akceptowanych wcięcia i korzystać z niego systematycznie w całym baza kodu.</span><span class="sxs-lookup"><span data-stu-id="85e40-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="85e40-120">Formatowanie puste wiersze</span><span class="sxs-lookup"><span data-stu-id="85e40-120">Formatting blank lines</span></span>

* <span data-ttu-id="85e40-121">Oddzielne najwyższego poziomu funkcji i klasy definicji dwa puste wiersze.</span><span class="sxs-lookup"><span data-stu-id="85e40-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="85e40-122">Definicje metody w klasie są rozdzielone przez pojedynczy pusty wiersz.</span><span class="sxs-lookup"><span data-stu-id="85e40-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="85e40-123">Dodatkowe puste wiersze może służyć (oszczędnie) do oddzielania grup powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="85e40-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="85e40-124">Puste wiersze można pominąć między licznych one-liners powiązane (na przykład zestawu zastępczego implementacji).</span><span class="sxs-lookup"><span data-stu-id="85e40-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="85e40-125">Użyj oszczędnie, pustych wierszy w funkcjach, aby wskazać logiczne sekcje.</span><span class="sxs-lookup"><span data-stu-id="85e40-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="85e40-126">Formatowanie komentarzy</span><span class="sxs-lookup"><span data-stu-id="85e40-126">Formatting comments</span></span>

<span data-ttu-id="85e40-127">Ogólnie rzecz biorąc Preferuj wielu komentarzy o podwójnej precyzji ukośnika przed komentarze bloku stylu uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="85e40-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="85e40-128">Komentarzy wewnętrznych powinien wielką literą.</span><span class="sxs-lookup"><span data-stu-id="85e40-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="85e40-129">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="85e40-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="85e40-130">Użyj wartości powiązane z klasy, powiązane z wyrażenia i powiązane z wzorca i funkcji (camelcase)</span><span class="sxs-lookup"><span data-stu-id="85e40-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="85e40-131">Często i zaakceptowane styl F # (camelcase) na potrzeby wszystkich nazw powiązana jako zmienne lokalne lub w dopasowaniach wzorców i definicje funkcji.</span><span class="sxs-lookup"><span data-stu-id="85e40-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="85e40-132">Funkcje wiązaniem lokalnie w klasach też używać (camelcase).</span><span class="sxs-lookup"><span data-stu-id="85e40-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="85e40-133">Użyj (camelcase) dla funkcji publicznych powiązanych z modułu</span><span class="sxs-lookup"><span data-stu-id="85e40-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="85e40-134">Jeśli funkcja powiązane z modułu jest częścią publiczny interfejs API, korzystała (camelcase):</span><span class="sxs-lookup"><span data-stu-id="85e40-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="85e40-135">Użyj wartości powiązane z modułu wewnętrzne i prywatne i funkcji (camelcase)</span><span class="sxs-lookup"><span data-stu-id="85e40-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="85e40-136">Użyj (camelcase) dla wartości powiązane z modułu prywatne, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="85e40-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="85e40-137">Funkcje ad hoc w skryptach</span><span class="sxs-lookup"><span data-stu-id="85e40-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="85e40-138">Wartości tworzących wewnętrznej implementacji modułu lub typu</span><span class="sxs-lookup"><span data-stu-id="85e40-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="85e40-139">Użyj parametrów (camelcase)</span><span class="sxs-lookup"><span data-stu-id="85e40-139">Use camelCase for parameters</span></span>

<span data-ttu-id="85e40-140">Wszystkie parametry powinien używać (camelcase) zgodnie z konwencją nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="85e40-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="85e40-141">Użyj PascalCase dla modułów</span><span class="sxs-lookup"><span data-stu-id="85e40-141">Use PascalCase for modules</span></span>

<span data-ttu-id="85e40-142">Wszystkie moduły (najwyższego poziomu, wewnętrzne, prywatne, zagnieżdżonych) należy używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="85e40-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="85e40-143">Użyj PascalCase dla deklaracji typu, członków i etykiety</span><span class="sxs-lookup"><span data-stu-id="85e40-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="85e40-144">Klasy, interfejsy, struktury, wyliczenia, delegatów, rekordów i rozłączne powinny być wszystkie nazwę z PascalCase.</span><span class="sxs-lookup"><span data-stu-id="85e40-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="85e40-145">Elementy członkowskie w ramach typy oraz etykiety dla rekordów i rozłączne też używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="85e40-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="85e40-146">Użyj PascalCase dla konstrukcji wewnętrznej do .NET</span><span class="sxs-lookup"><span data-stu-id="85e40-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="85e40-147">Przestrzenie nazw, wyjątki, zdarzeń i projektu /`.dll` nazwy też używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="85e40-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="85e40-148">Nie tylko jest to, że zużycie z innymi językami .NET możesz bardziej naturalne dla konsumentów, również jest spójna z konwencji nazewnictwa platformy .NET, które mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="85e40-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="85e40-149">Unikaj podkreślenia w nazwach</span><span class="sxs-lookup"><span data-stu-id="85e40-149">Avoid underscores in names</span></span>

<span data-ttu-id="85e40-150">W przeszłości niektórych bibliotek języka F # użyto podkreślenia w nazwach.</span><span class="sxs-lookup"><span data-stu-id="85e40-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="85e40-151">Jednak nie jest już powszechnie zaakceptowaniu częściowo, ponieważ jest ona konflikt z konwencji nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="85e40-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="85e40-152">Inaczej mówiąc, niektóre programistów F # przy użyciu podkreślenia znacznie, częściowo przyczyn historycznych, a na uszkodzenia i zakresie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="85e40-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="85e40-153">Należy jednak pamiętać, że styl jest często disliked przez innych użytkowników, którzy mają wybór o tym, czy z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="85e40-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="85e40-154">Niektóre wyjątki obejmuje współpracy z natywnego składniki, których podkreślenia są bardziej powszechne.</span><span class="sxs-lookup"><span data-stu-id="85e40-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="85e40-155">Użyj standardowych operatorów F #</span><span class="sxs-lookup"><span data-stu-id="85e40-155">Use standard F# operators</span></span>

<span data-ttu-id="85e40-156">Następujące operatory są zdefiniowane w standardowej biblioteki języka F # i powinna być używana zamiast funkcji definiujący odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="85e40-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="85e40-157">Za pomocą tych operatorów jest zalecane, ponieważ sprawia kodu bardziej czytelny i idiomatyczne.</span><span class="sxs-lookup"><span data-stu-id="85e40-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="85e40-158">Może być przystosowane do różnych idioms deweloperom tła w OCaml lub innych funkcjonalny język programowania.</span><span class="sxs-lookup"><span data-stu-id="85e40-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="85e40-159">Poniższa lista zawiera podsumowanie zalecane operatory F #.</span><span class="sxs-lookup"><span data-stu-id="85e40-159">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="85e40-160">Należy użyć składni prefiks dla typów ogólnych (`Foo<T>`) zamiast składni przyrostek (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="85e40-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="85e40-161">F # dziedziczy zarówno przyrostek ML styl nazewnictwa typów ogólnych (na przykład `int list`) oraz prefiks styl .NET (na przykład `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="85e40-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="85e40-162">Preferowane jest styl .NET, z wyjątkiem cztery określonych typów:</span><span class="sxs-lookup"><span data-stu-id="85e40-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="85e40-163">F # list, użyj przyrostkowej formy: `int list` zamiast `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="85e40-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="85e40-164">F # opcji, należy użyć przyrostkowej formy: `int option` zamiast `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="85e40-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="85e40-165">Dla języka F # tablic, użyj składni nazwy `int[]` zamiast `int array` lub `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="85e40-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="85e40-166">Komórki odwołań, można użyć `int ref` zamiast `ref<int>` lub `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="85e40-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="85e40-167">Dla wszystkich innych typów formularz prefiks.</span><span class="sxs-lookup"><span data-stu-id="85e40-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="85e40-168">Formatowanie Suma rozłączna — deklaracje złożeń</span><span class="sxs-lookup"><span data-stu-id="85e40-168">Formatting discriminated union declarations</span></span>

<span data-ttu-id="85e40-169">Wcięcie `|` w definicji typu przy użyciu spacji 4:</span><span class="sxs-lookup"><span data-stu-id="85e40-169">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

<span data-ttu-id="85e40-170">Skonkretyzowanym Suma rozłączna Unii, które podzielić na wiele wierszy powinny zawierać danych zawartych w niej nowego zakresu z wcięcia:</span><span class="sxs-lookup"><span data-stu-id="85e40-170">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="85e40-171">Zamykający nawias okrągły można też w nowym wierszu:</span><span class="sxs-lookup"><span data-stu-id="85e40-171">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a><span data-ttu-id="85e40-172">Formatowanie krotek</span><span class="sxs-lookup"><span data-stu-id="85e40-172">Formatting tuples</span></span>

<span data-ttu-id="85e40-173">Wystąpienia spójnej kolekcji powinna być umieszczona w nawiasach i rozdzielające przecinków wewnątrz powinno następować jednego miejsca, na przykład: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="85e40-173">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="85e40-174">Powszechnie zaakceptowany wyjątku jest, aby pominąć nawiasów w krotek dopasowywania do wzorca:</span><span class="sxs-lookup"><span data-stu-id="85e40-174">A commonly accepted exception is to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a><span data-ttu-id="85e40-175">Formatowanie rekordów</span><span class="sxs-lookup"><span data-stu-id="85e40-175">Formatting records</span></span>

<span data-ttu-id="85e40-176">Może być zapisany krótkich rekordów w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="85e40-176">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="85e40-177">Rekordy, które są dłuższe należy używać nowych wierszy dla etykiet:</span><span class="sxs-lookup"><span data-stu-id="85e40-177">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="85e40-178">Wprowadzenie do tokenu otwierania tej samej linii i token zamknięcia w nowym wierszu jest również przeprowadzać:</span><span class="sxs-lookup"><span data-stu-id="85e40-178">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

<span data-ttu-id="85e40-179">Te same zasady mają zastosowanie dla elementów listy i tablicy.</span><span class="sxs-lookup"><span data-stu-id="85e40-179">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="85e40-180">Formatowanie list i tablic</span><span class="sxs-lookup"><span data-stu-id="85e40-180">Formatting lists and arrays</span></span>

<span data-ttu-id="85e40-181">Zapis `x :: l` odstępów wokół `::` — operator (`::` jest operator infiksu, dlatego otoczony spacjami) i `[1; 2; 3]` (`;` jest ogranicznik, dlatego następuje spacja).</span><span class="sxs-lookup"><span data-stu-id="85e40-181">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="85e40-182">Zawsze należy używać co najmniej jeden odstęp między dwa różne operatory przypominającej nawiasu klamrowego.</span><span class="sxs-lookup"><span data-stu-id="85e40-182">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="85e40-183">Na przykład, pozostaw odstęp między `[` i `{`.</span><span class="sxs-lookup"><span data-stu-id="85e40-183">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="85e40-184">List i tablic, które podzielić na wiele wierszy wykonaj podobne reguły, tak jak rekordy:</span><span class="sxs-lookup"><span data-stu-id="85e40-184">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="85e40-185">W przypadku formatowania wyrażenia</span><span class="sxs-lookup"><span data-stu-id="85e40-185">Formatting if expressions</span></span>

<span data-ttu-id="85e40-186">Wcięcie warunków zależy od rozmiarów wyrażeń, które tworzą je.</span><span class="sxs-lookup"><span data-stu-id="85e40-186">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="85e40-187">Jeśli `cond`, `e1` i `e2` są niewielkie, po prostu zapisanie ich w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="85e40-187">If `cond`, `e1` and `e2` are small, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="85e40-188">Jeśli `e1` i `cond` są niewielkie, ale `e2` jest duża:</span><span class="sxs-lookup"><span data-stu-id="85e40-188">If `e1` and `cond` are small, but `e2` is large:</span></span>

```fsharp
if cond then e1
else
    e2
```

<span data-ttu-id="85e40-189">Jeśli `e1` i `cond` większych i `e2` jest mały:</span><span class="sxs-lookup"><span data-stu-id="85e40-189">If `e1` and `cond` are large and `e2` is small:</span></span>

```fsharp
if cond then
    e1
else e2
```

<span data-ttu-id="85e40-190">Jeśli wszystkie wyrażenia są duże:</span><span class="sxs-lookup"><span data-stu-id="85e40-190">If all the expressions are large:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="85e40-191">Wiele warunków z `elif` i `else` tworzone jest wcięcie na tym samym zakresie co `if`:</span><span class="sxs-lookup"><span data-stu-id="85e40-191">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="85e40-192">Konstrukcje dopasowania wzorca</span><span class="sxs-lookup"><span data-stu-id="85e40-192">Pattern matching constructs</span></span>

<span data-ttu-id="85e40-193">Użyj `|` dla każdej klauzuli dopasowania z braku wcięcia.</span><span class="sxs-lookup"><span data-stu-id="85e40-193">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="85e40-194">Jeśli wyrażenie jest krótki, można rozważyć użycie jednego wiersza, jeśli każdy Podwyrażenie jest również proste.</span><span class="sxs-lookup"><span data-stu-id="85e40-194">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="85e40-195">Jeśli wyrażenie po prawej stronie strzałkę dopasowania wzorca jest zbyt duży, przenieś go do następującego wiersza, z wcięciami krok z `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="85e40-195">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="85e40-196">Wzorzec dopasowywania funkcje anonimowe uruchamianie przy `function`, zazwyczaj należy zbyt daleko nie wcięcia.</span><span class="sxs-lookup"><span data-stu-id="85e40-196">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="85e40-197">Na przykład następujący wcięcia jeden zakres jest poprawnie:</span><span class="sxs-lookup"><span data-stu-id="85e40-197">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="85e40-198">Wzorzec dopasowany w funkcjach zdefiniowanych przez `let` lub `let rec` powinien być wcięta 4 miejsca po uruchomieniu programu `let`, nawet jeśli `function` służy słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="85e40-198">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="85e40-199">Nie zaleca się wyrównywanie strzałki.</span><span class="sxs-lookup"><span data-stu-id="85e40-199">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="85e40-200">Formatowanie try / with wyrażenia</span><span class="sxs-lookup"><span data-stu-id="85e40-200">Formatting try/with expressions</span></span>

<span data-ttu-id="85e40-201">Dopasowania wzorca w typ wyjątku powinien być wcięty na tym samym poziomie jako `with`.</span><span class="sxs-lookup"><span data-stu-id="85e40-201">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="85e40-202">Formatowanie aplikacji parametru funkcji</span><span class="sxs-lookup"><span data-stu-id="85e40-202">Formatting function parameter application</span></span>

<span data-ttu-id="85e40-203">Ogólnie rzecz biorąc większość aplikacji parametru funkcji odbywa się w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="85e40-203">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="85e40-204">Jeśli chcesz zastosować parametry do funkcji w nowym wierszu, wcięcie je przez jeden zakres.</span><span class="sxs-lookup"><span data-stu-id="85e40-204">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="85e40-205">Tym samym wytyczne dotyczą wyrażenia lambda jako argumenty funkcji.</span><span class="sxs-lookup"><span data-stu-id="85e40-205">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="85e40-206">Jeżeli treści wyrażenia lambda, treść może mieć innego wiersza, zawiera tylko przez jeden zakres</span><span class="sxs-lookup"><span data-stu-id="85e40-206">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="85e40-207">Jednak jeśli treści wyrażenia lambda jest więcej niż jeden wiersz, należy wziąć pod uwagę factoring je do oddzielnego funkcja zamiast konstrukcję wielowierszowego stosowane jako pojedynczy argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="85e40-207">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="85e40-208">Operatory infiksu formatowania</span><span class="sxs-lookup"><span data-stu-id="85e40-208">Formatting infix operators</span></span>

<span data-ttu-id="85e40-209">Oddzielne operatory przy użyciu spacji.</span><span class="sxs-lookup"><span data-stu-id="85e40-209">Separate operators by spaces.</span></span> <span data-ttu-id="85e40-210">Są oczywiste wyjątki od tej reguły `!` i `.` operatorów.</span><span class="sxs-lookup"><span data-stu-id="85e40-210">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="85e40-211">Wyrażenia infiksu mają zestawienia w tej samej kolumnie OK:</span><span class="sxs-lookup"><span data-stu-id="85e40-211">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="85e40-212">Formatowanie operatorów potoku</span><span class="sxs-lookup"><span data-stu-id="85e40-212">Formatting pipeline operators</span></span>

<span data-ttu-id="85e40-213">Potok `|>` operatory powinien znajdować się pod wyrażenia działają na.</span><span class="sxs-lookup"><span data-stu-id="85e40-213">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="85e40-214">Formatowanie modułów</span><span class="sxs-lookup"><span data-stu-id="85e40-214">Formatting modules</span></span>

<span data-ttu-id="85e40-215">Kod w lokalnym module musi być wcięty względem modułu, ale nie powinien być wcięty kodu w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="85e40-215">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="85e40-216">Nie masz elementy Namespace wcięcia.</span><span class="sxs-lookup"><span data-stu-id="85e40-216">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="85e40-217">Formatowanie obiektu wyrażeń i interfejsów</span><span class="sxs-lookup"><span data-stu-id="85e40-217">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="85e40-218">Wyrażenia obiektów i interfejsy powinno być wyrównane tak samo jak z `member` tworzone jest wcięcie po 4 spacji.</span><span class="sxs-lookup"><span data-stu-id="85e40-218">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a><span data-ttu-id="85e40-219">Formatowanie odstępu w wyrażeniach</span><span class="sxs-lookup"><span data-stu-id="85e40-219">Formatting whitespace in expressions</span></span>

<span data-ttu-id="85e40-220">Unikaj nadmiarowe odstępu w wyrażeniach języka F #.</span><span class="sxs-lookup"><span data-stu-id="85e40-220">Avoid extraneous whitespace in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="85e40-221">Argumenty nazwane również nie powinna mieć miejsca otaczającego `=`:</span><span class="sxs-lookup"><span data-stu-id="85e40-221">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
