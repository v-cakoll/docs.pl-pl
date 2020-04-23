---
title: Wskazówki dotyczące formatowania kodu F#
description: Poznaj wskazówki dotyczące formatowania kodu języka F#.
ms.date: 11/04/2019
ms.openlocfilehash: dd48380a90ee92b2c1edaaabc116fa1cd8010390
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102492"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="7168f-103">Wskazówki dotyczące formatowania kodu F#</span><span class="sxs-lookup"><span data-stu-id="7168f-103">F# code formatting guidelines</span></span>

<span data-ttu-id="7168f-104">Ten artykuł zawiera wskazówki dotyczące formatowania kodu, tak aby kod języka F# był:</span><span class="sxs-lookup"><span data-stu-id="7168f-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="7168f-105">Bardziej czytelne</span><span class="sxs-lookup"><span data-stu-id="7168f-105">More legible</span></span>
* <span data-ttu-id="7168f-106">Zgodnie z konwencjami stosowanymi przez narzędzia formatowania w programie Visual Studio i innych edytorach</span><span class="sxs-lookup"><span data-stu-id="7168f-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="7168f-107">Podobne do innych kodów online</span><span class="sxs-lookup"><span data-stu-id="7168f-107">Similar to other code online</span></span>

<span data-ttu-id="7168f-108">Wytyczne te są oparte na [kompleksowym przewodniku po konwencjach formatowania F#](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [autorstwa Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="7168f-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="7168f-109">Ogólne zasady wcięci</span><span class="sxs-lookup"><span data-stu-id="7168f-109">General rules for indentation</span></span>

<span data-ttu-id="7168f-110">F# domyślnie używa znacznych odstępów.</span><span class="sxs-lookup"><span data-stu-id="7168f-110">F# uses significant white space by default.</span></span> <span data-ttu-id="7168f-111">Poniższe wytyczne mają na celu zapewnienie wskazówek, jak żonglować niektórymi wyzwaniami, które może narzucić.</span><span class="sxs-lookup"><span data-stu-id="7168f-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="7168f-112">Korzystanie z przestrzeni</span><span class="sxs-lookup"><span data-stu-id="7168f-112">Using spaces</span></span>

<span data-ttu-id="7168f-113">Jeśli wymagane jest wcięcie, należy użyć spacji, a nie kart.</span><span class="sxs-lookup"><span data-stu-id="7168f-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="7168f-114">Wymagana jest co najmniej jedna przestrzeń.</span><span class="sxs-lookup"><span data-stu-id="7168f-114">At least one space is required.</span></span> <span data-ttu-id="7168f-115">Organizacja może tworzyć standardy kodowania, aby określić liczbę spacji do użycia do wcięci; dwie, trzy lub cztery spacje wcięci na każdym poziomie, na którym występuje wcięcie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="7168f-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="7168f-116">**Zalecamy cztery spacje na wcięcie.**</span><span class="sxs-lookup"><span data-stu-id="7168f-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="7168f-117">To powiedzia się, wcięcie programów jest kwestią subiektywną.</span><span class="sxs-lookup"><span data-stu-id="7168f-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="7168f-118">Odmiany są OK, ale pierwszą zasadą, którą należy przestrzegać, jest *spójność wcięcia*.</span><span class="sxs-lookup"><span data-stu-id="7168f-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="7168f-119">Wybierz ogólnie akceptowany styl wcięci i używaj go systematycznie w całej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="7168f-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="7168f-120">Formatowanie odstępu</span><span class="sxs-lookup"><span data-stu-id="7168f-120">Formatting white space</span></span>

<span data-ttu-id="7168f-121">F# jest czuły na białe przesiewowe.</span><span class="sxs-lookup"><span data-stu-id="7168f-121">F# is white space sensitive.</span></span> <span data-ttu-id="7168f-122">Chociaż większość semantyki z białych spacji są objęte prawidłowym wcięciem, istnieje kilka innych rzeczy do rozważenia.</span><span class="sxs-lookup"><span data-stu-id="7168f-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="7168f-123">Operatory formatowania w wyrażeniach arytmetycznych</span><span class="sxs-lookup"><span data-stu-id="7168f-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="7168f-124">Zawsze używaj odstępu wokół binarnych wyrażeń arytmetycznych:</span><span class="sxs-lookup"><span data-stu-id="7168f-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="7168f-125">Operatory `-` dwuary powinny być zawsze natychmiast następuje wartość, którą negują:</span><span class="sxs-lookup"><span data-stu-id="7168f-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="7168f-126">Dodawanie znaku odstępu po `-` operatorze może prowadzić do zamieszania dla innych.</span><span class="sxs-lookup"><span data-stu-id="7168f-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="7168f-127">Podsumowując, ważne jest, aby zawsze:</span><span class="sxs-lookup"><span data-stu-id="7168f-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="7168f-128">Operatory binarne surround z odstępem</span><span class="sxs-lookup"><span data-stu-id="7168f-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="7168f-129">Nigdy nie ma spływu białym po operatorze bezemisowym</span><span class="sxs-lookup"><span data-stu-id="7168f-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="7168f-130">Szczególnie ważne są wytyczne dotyczące operatora arytmetycznego binarnego.</span><span class="sxs-lookup"><span data-stu-id="7168f-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="7168f-131">Nieoczynienie `-` otoczyć operatora binarnego w połączeniu z pewnymi opcjami formatowania może prowadzić do interpretacji go jako dwuarchiwa. `-`</span><span class="sxs-lookup"><span data-stu-id="7168f-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="7168f-132">Otaczanie niestandardowej definicji operatora z białymi znakami</span><span class="sxs-lookup"><span data-stu-id="7168f-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="7168f-133">Zawsze używaj odstępu do otaczania definicji operatora:</span><span class="sxs-lookup"><span data-stu-id="7168f-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="7168f-134">Dla dowolnego niestandardowego operatora, który rozpoczyna się `*` i który ma więcej niż jeden znak, należy dodać biały znak na początku definicji, aby uniknąć niejednoznaczności kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7168f-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="7168f-135">Z tego powodu zaleca się po prostu otoczyć definicje wszystkich operatorów z jednym znakiem odstępu.</span><span class="sxs-lookup"><span data-stu-id="7168f-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="7168f-136">Strzałki parametrów funkcji otoczyć z białymi znakami</span><span class="sxs-lookup"><span data-stu-id="7168f-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="7168f-137">Podczas definiowania podpisu funkcji należy użyć `->` odstępu wokół symbolu:</span><span class="sxs-lookup"><span data-stu-id="7168f-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="7168f-138">Argumenty funkcji surround z odstępem</span><span class="sxs-lookup"><span data-stu-id="7168f-138">Surround function arguments with white space</span></span>

<span data-ttu-id="7168f-139">Podczas definiowania funkcji należy użyć odstępu wokół każdego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7168f-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="7168f-140">Umieszczanie parametrów w nowym wierszu dla długich definicji elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7168f-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="7168f-141">Jeśli masz bardzo długą definicję elementu członkowskiego, umieść parametry w nowych wierszach i wcięj je jednym zakresem.</span><span class="sxs-lookup"><span data-stu-id="7168f-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="7168f-142">Dotyczy to również konstruktorów:</span><span class="sxs-lookup"><span data-stu-id="7168f-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="7168f-143">Wpisz adnotacje</span><span class="sxs-lookup"><span data-stu-id="7168f-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="7168f-144">Adnotacje typu argumentu funkcji panelu prawego</span><span class="sxs-lookup"><span data-stu-id="7168f-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="7168f-145">Podczas definiowania argumentów z adnotacjami `:` typu należy używać odstępu za symbolem:</span><span class="sxs-lookup"><span data-stu-id="7168f-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="7168f-146">Adnotacje typu surround z odstępem</span><span class="sxs-lookup"><span data-stu-id="7168f-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="7168f-147">W funkcji let-bound lub adnotacji typu wartości (typ zwracany w przypadku funkcji) należy użyć odstępu przed i po symbolu: `:`</span><span class="sxs-lookup"><span data-stu-id="7168f-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="7168f-148">Formatowanie pustych wierszy</span><span class="sxs-lookup"><span data-stu-id="7168f-148">Formatting blank lines</span></span>

* <span data-ttu-id="7168f-149">Oddziel definicje funkcji najwyższego poziomu i klas dwoma pustymi wierszami.</span><span class="sxs-lookup"><span data-stu-id="7168f-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="7168f-150">Definicje metod wewnątrz klasy są oddzielone pojedynczą pustą linią.</span><span class="sxs-lookup"><span data-stu-id="7168f-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="7168f-151">Dodatkowe puste wiersze mogą być używane (oszczędnie) do oddzielnych grup powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7168f-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="7168f-152">Puste wiersze mogą być pominięte między kilka powiązanych one-liners (na przykład zestaw implementacji manekina).</span><span class="sxs-lookup"><span data-stu-id="7168f-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="7168f-153">W funkcjach należy oszczędnie wskazywać sekcje logiczne pustymi wierszami w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="7168f-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="7168f-154">Formatowanie komentarzy</span><span class="sxs-lookup"><span data-stu-id="7168f-154">Formatting comments</span></span>

<span data-ttu-id="7168f-155">Ogólnie preferuje wiele komentarzy z podwójnym ukośnikiem nad komentarzami blokowym w stylu ML.</span><span class="sxs-lookup"><span data-stu-id="7168f-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="7168f-156">Komentarze w komentarzach powinny być pisane kapitułą pierwszej litery.</span><span class="sxs-lookup"><span data-stu-id="7168f-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="7168f-157">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="7168f-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="7168f-158">Użyj camelCase dla wartości i funkcji związanych z klasą, wyrażeniami i wzorcem</span><span class="sxs-lookup"><span data-stu-id="7168f-158">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="7168f-159">Jest to typowe i akceptowane F# styl używać camelCase dla wszystkich nazw związanych jako zmienne lokalne lub w dopasowywanie wzorca i definicje funkcji.</span><span class="sxs-lookup"><span data-stu-id="7168f-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="7168f-160">Lokalnie związane funkcje w klasach należy również użyć camelCase.</span><span class="sxs-lookup"><span data-stu-id="7168f-160">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="7168f-161">Użyj camelCase do funkcji publicznych związanych z modułem</span><span class="sxs-lookup"><span data-stu-id="7168f-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="7168f-162">Gdy funkcja związana z modułem jest częścią publicznego interfejsu API, należy użyć camelCase:</span><span class="sxs-lookup"><span data-stu-id="7168f-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="7168f-163">Użyj camelCase dla wewnętrznych i prywatnych wartości i funkcji związanych z modułem</span><span class="sxs-lookup"><span data-stu-id="7168f-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="7168f-164">Użyj camelCase dla prywatnych wartości związanych z modułem, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="7168f-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="7168f-165">Funkcje ad hoc w skryptach</span><span class="sxs-lookup"><span data-stu-id="7168f-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="7168f-166">Wartości tworzące wewnętrzną implementację modułu lub typu</span><span class="sxs-lookup"><span data-stu-id="7168f-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="7168f-167">Użyj camelCase dla parametrów</span><span class="sxs-lookup"><span data-stu-id="7168f-167">Use camelCase for parameters</span></span>

<span data-ttu-id="7168f-168">Wszystkie parametry powinny używać camelCase zgodnie z konwencjami nazewnictwa .NET.</span><span class="sxs-lookup"><span data-stu-id="7168f-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="7168f-169">Użyj PascalCase dla modułów</span><span class="sxs-lookup"><span data-stu-id="7168f-169">Use PascalCase for modules</span></span>

<span data-ttu-id="7168f-170">Wszystkie moduły (najwyższego poziomu, wewnętrzne, prywatne, zagnieżdżone) powinny używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="7168f-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="7168f-171">PascalCase służy do oznaczania deklaracji typów, elementów członkowskich i etykiet</span><span class="sxs-lookup"><span data-stu-id="7168f-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="7168f-172">Klasy, interfejsy, struktury, wyliczenia, delegatów, rekordy i dyskryminowane związki powinny być nazwane pascalcase.</span><span class="sxs-lookup"><span data-stu-id="7168f-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="7168f-173">Członkowie w ramach typów i etykiet dla rekordów i dyskryminowanych związków powinny również używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="7168f-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="7168f-174">PascalCase używa konstrukcji wewnętrznych do platformy .NET</span><span class="sxs-lookup"><span data-stu-id="7168f-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="7168f-175">Obszary nazw, wyjątki, zdarzenia i`.dll` nazwy projektu/ powinny również używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="7168f-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="7168f-176">Nie tylko to sprawiają, że zużycie z innych języków platformy .NET jest bardziej naturalne dla konsumentów, jest również zgodne z konwencjami nazewnictwa .NET, które mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="7168f-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="7168f-177">Unikaj podkreśleń w nazwach</span><span class="sxs-lookup"><span data-stu-id="7168f-177">Avoid underscores in names</span></span>

<span data-ttu-id="7168f-178">Historycznie niektóre biblioteki Języka F# używały podkreśleń w nazwach.</span><span class="sxs-lookup"><span data-stu-id="7168f-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="7168f-179">Jednak nie jest to już powszechnie akceptowane, częściowo dlatego, że ściera się z konwencjami nazewnictwa .NET.</span><span class="sxs-lookup"><span data-stu-id="7168f-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="7168f-180">To powiedziawia, że niektórzy programiści F# używają podkreśla mocno, częściowo ze względów historycznych, a tolerancja i szacunek jest ważne.</span><span class="sxs-lookup"><span data-stu-id="7168f-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="7168f-181">Należy jednak pamiętać, że styl jest często nielubiany przez innych, którzy mają wybór, czy go używać.</span><span class="sxs-lookup"><span data-stu-id="7168f-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="7168f-182">Jeden wyjątek obejmuje współdziałanie ze składnikami macierzystymi, gdzie podkreślenia są wspólne.</span><span class="sxs-lookup"><span data-stu-id="7168f-182">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="7168f-183">Użyj standardowych operatorów Języka F#</span><span class="sxs-lookup"><span data-stu-id="7168f-183">Use standard F# operators</span></span>

<span data-ttu-id="7168f-184">Następujące operatory są zdefiniowane w bibliotece standardowej języka F# i powinny być używane zamiast definiowania odpowiedników.</span><span class="sxs-lookup"><span data-stu-id="7168f-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="7168f-185">Korzystanie z tych operatorów jest zalecane, ponieważ ma tendencję do kodu bardziej czytelny i idiomatyczny.</span><span class="sxs-lookup"><span data-stu-id="7168f-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="7168f-186">Deweloperzy z tła w OCaml lub inny funkcjonalny język programowania mogą być przyzwyczajeni do różnych idiomów.</span><span class="sxs-lookup"><span data-stu-id="7168f-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="7168f-187">Poniższa lista zawiera podsumowanie zalecanych operatorów języka F#.</span><span class="sxs-lookup"><span data-stu-id="7168f-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="7168f-188">Użyj składni prefiksu`Foo<T>`dla generycznych ( )`T Foo`zamiast składni poprawek ( )</span><span class="sxs-lookup"><span data-stu-id="7168f-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="7168f-189">F# dziedziczy zarówno postfix STYL ML nazewnictwa `int list`typów ogólnych (na przykład), jak również `list<int>`prefiks .NET style (na przykład).</span><span class="sxs-lookup"><span data-stu-id="7168f-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="7168f-190">Preferuj styl .NET, z wyjątkiem pięciu określonych typów:</span><span class="sxs-lookup"><span data-stu-id="7168f-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="7168f-191">W przypadku list F# użyj `int list` formularza `list<int>`postfix: zamiast .</span><span class="sxs-lookup"><span data-stu-id="7168f-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="7168f-192">W przypadku opcji języka F# `int option` użyj `option<int>`formularza postfix: zamiast .</span><span class="sxs-lookup"><span data-stu-id="7168f-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="7168f-193">W przypadku opcji wartości języka F#użyj formularza postfix: `int voption` zamiast `voption<int>`.</span><span class="sxs-lookup"><span data-stu-id="7168f-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="7168f-194">W przypadku tablic F# użyj nazwy `int[]` składni, a nie `int array` lub `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="7168f-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="7168f-195">W przypadku komórek `int ref` referencyjnych należy użyć zamiast `ref<int>` lub `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="7168f-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="7168f-196">W przypadku wszystkich innych typów należy użyć formularza prefiksu.</span><span class="sxs-lookup"><span data-stu-id="7168f-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="7168f-197">Krotek formatowania</span><span class="sxs-lookup"><span data-stu-id="7168f-197">Formatting tuples</span></span>

<span data-ttu-id="7168f-198">Wystąpienie krotki powinno być w nawiasie, a po rozdzielającym przecinkach w nim `(1, 2)`powinno `(x, y, z)`następować pojedyncza spacja, na przykład: , .</span><span class="sxs-lookup"><span data-stu-id="7168f-198">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="7168f-199">Jest powszechnie akceptowane pominąć nawiasy w dopasowywania wzorów krotek:</span><span class="sxs-lookup"><span data-stu-id="7168f-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="7168f-200">Jest również powszechnie akceptowane pominąć nawiasy, jeśli krotka jest zwracana wartość funkcji:</span><span class="sxs-lookup"><span data-stu-id="7168f-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="7168f-201">Podsumowując, preferuj nawiasy wystąpienia spójnej strony, ale podczas korzystania z krotek do dopasowywania wzorców lub wartości zwracanej, jest uważany za w porządku, aby uniknąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7168f-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="7168f-202">Formatowanie dyskryminowanych deklaracji związków zawodowych</span><span class="sxs-lookup"><span data-stu-id="7168f-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="7168f-203">Wcięcie `|` w definicji typu przez cztery spacje:</span><span class="sxs-lookup"><span data-stu-id="7168f-203">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="7168f-204">Formatowanie dyskryminowanych związków</span><span class="sxs-lookup"><span data-stu-id="7168f-204">Formatting discriminated unions</span></span>

<span data-ttu-id="7168f-205">Wystąpienia dyskryminowanych związków, które podzielone na wiele wierszy powinny nadać zawartym danym nowy zakres z wcięciem:</span><span class="sxs-lookup"><span data-stu-id="7168f-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="7168f-206">Nawias zamykający może również znajdować się w nowym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="7168f-207">Formatowanie deklaracji rekordów</span><span class="sxs-lookup"><span data-stu-id="7168f-207">Formatting record declarations</span></span>

<span data-ttu-id="7168f-208">Wcięcie `{` w definicji typu przez cztery spacje i rozpoczęcie listy pól w tym samym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-208">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="7168f-209">Umieszczenie tokenu otwarcia w nowym wierszu i token zamknięcia w nowym wierszu jest korzystne, jeśli deklarujesz implementacje interfejsu lub członków w rekordzie:</span><span class="sxs-lookup"><span data-stu-id="7168f-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="7168f-210">Formatowanie rekordów</span><span class="sxs-lookup"><span data-stu-id="7168f-210">Formatting records</span></span>

<span data-ttu-id="7168f-211">Krótkie rekordy mogą być zapisywane w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="7168f-212">Rekordy, które są dłuższe, powinny używać nowych wierszy dla etykiet:</span><span class="sxs-lookup"><span data-stu-id="7168f-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="7168f-213">Umieszczenie tokenu otwarcia w nowym wierszu, zawartość z kartami w jednym zakresie i token zamknięcia w nowym wierszu jest preferowane, jeśli:</span><span class="sxs-lookup"><span data-stu-id="7168f-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="7168f-214">Przenoszenie rekordów w kodzie z różnymi zakresami wcięci</span><span class="sxs-lookup"><span data-stu-id="7168f-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="7168f-215">Wprowadzenie ich do funkcji</span><span class="sxs-lookup"><span data-stu-id="7168f-215">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
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

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="7168f-216">Te same reguły mają zastosowanie do elementów listy i tablicy.</span><span class="sxs-lookup"><span data-stu-id="7168f-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="7168f-217">Formatowanie wyrażeń rekordu kopiowania i aktualizowania</span><span class="sxs-lookup"><span data-stu-id="7168f-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="7168f-218">Wyrażenie rekordu kopiowania i aktualizacji jest nadal rekordem, więc obowiązują podobne wytyczne.</span><span class="sxs-lookup"><span data-stu-id="7168f-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="7168f-219">Krótkie wyrażenia mogą zmieścić się w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="7168f-220">Dłuższe wyrażenia powinny używać nowych wierszy:</span><span class="sxs-lookup"><span data-stu-id="7168f-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="7168f-221">Podobnie jak w przypadku wskazówek dotyczących rekordu, można poświęcić oddzielne wiersze dla nawiasów klamrowych i wcięcie jednego zakresu po prawej stronie za pomocą wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7168f-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="7168f-222">W niektórych szczególnych przypadkach, takich jak zawijanie wartości z opcjonalnym bez nawiasów, może być konieczne utrzymanie nawiasu w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-222">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="7168f-223">Formatowanie list i tablic</span><span class="sxs-lookup"><span data-stu-id="7168f-223">Formatting lists and arrays</span></span>

<span data-ttu-id="7168f-224">Pisz `x :: l` z spacjami wokół `::` operatora (`::` jest operatorem infix, stąd otoczony spacjami).</span><span class="sxs-lookup"><span data-stu-id="7168f-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="7168f-225">Lista i tablice zadeklarowane w jednym wierszu powinny mieć spację po nawiasie otwierającym i przed nawiasem zamykającym:</span><span class="sxs-lookup"><span data-stu-id="7168f-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="7168f-226">Zawsze należy używać co najmniej jednej spacji między dwoma różnymi operatorami przypominającymi nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="7168f-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="7168f-227">Na przykład pozostaw `[` spację `{`między a a .</span><span class="sxs-lookup"><span data-stu-id="7168f-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="7168f-228">Te same wytyczne dotyczą list lub tablic krotek.</span><span class="sxs-lookup"><span data-stu-id="7168f-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="7168f-229">Listy i tablice podzielone na wiele wierszy są zgodne z podobną regułą jak rekordy:</span><span class="sxs-lookup"><span data-stu-id="7168f-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="7168f-230">I podobnie jak w rekordach, deklarowanie nawiasów otwierających i zamykających na własnej linii ułatwi przenoszenie kodu i tworzenie rurociągów do funkcji.</span><span class="sxs-lookup"><span data-stu-id="7168f-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="7168f-231">Podczas generowania tablic i list programowo `do ... yield` preferuj, `->` gdy zawsze jest generowana wartość:</span><span class="sxs-lookup"><span data-stu-id="7168f-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="7168f-232">Starsze wersje języka F# wymagane `yield` określania w sytuacjach, gdy dane mogą być generowane warunkowo lub mogą być kolejne wyrażenia do oceny.</span><span class="sxs-lookup"><span data-stu-id="7168f-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="7168f-233">Preferuj pominięcie tych `yield` słów kluczowych, chyba że musisz skompilować ze starszą wersją języka F#:</span><span class="sxs-lookup"><span data-stu-id="7168f-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="7168f-234">W niektórych `do...yield` przypadkach, może pomóc w czytelności.</span><span class="sxs-lookup"><span data-stu-id="7168f-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="7168f-235">Przypadki te, choć subiektywne, powinny być brane pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="7168f-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="7168f-236">Formatowanie, jeśli wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7168f-236">Formatting if expressions</span></span>

<span data-ttu-id="7168f-237">Wcięcie warunkowości zależy od rozmiarów wyrażeń, które je tworzą.</span><span class="sxs-lookup"><span data-stu-id="7168f-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="7168f-238">Jeśli `cond` `e1` , `e2` i są krótkie, po prostu napisz je w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="7168f-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="7168f-239">Jeśli albo `cond` `e1` , `e2` lub są dłuższe, ale nie wieloliniowe:</span><span class="sxs-lookup"><span data-stu-id="7168f-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="7168f-240">Jeśli którekolwiek z wyrażeń jest wielowierszowe:</span><span class="sxs-lookup"><span data-stu-id="7168f-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="7168f-241">Wiele warunków z `elif` `else` i są wcięciami `if`w tym samym zakresie co:</span><span class="sxs-lookup"><span data-stu-id="7168f-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="7168f-242">Konstrukcje dopasowywania wzorców</span><span class="sxs-lookup"><span data-stu-id="7168f-242">Pattern matching constructs</span></span>

<span data-ttu-id="7168f-243">Użyj `|` a dla każdej klauzuli dopasowania bez wcięci.</span><span class="sxs-lookup"><span data-stu-id="7168f-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="7168f-244">Jeśli wyrażenie jest krótkie, można rozważyć użycie pojedynczego wiersza, jeśli każde wyrażenie podrzędne jest również proste.</span><span class="sxs-lookup"><span data-stu-id="7168f-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="7168f-245">Jeśli wyrażenie po prawej stronie strzałki dopasowania wzorca jest zbyt duże, przenieś go `match` / `|`do następującego wiersza, wciętego o jeden krok od .</span><span class="sxs-lookup"><span data-stu-id="7168f-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="7168f-246">Dopasowywanie wzorców funkcji `function`anonimowych, począwszy od , na ogół nie powinno wcięcie zbyt daleko.</span><span class="sxs-lookup"><span data-stu-id="7168f-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="7168f-247">Na przykład wcięcie jednego zakresu w następujący sposób jest w porządku:</span><span class="sxs-lookup"><span data-stu-id="7168f-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="7168f-248">Dopasowywanie wzorca `let rec` w funkcjach zdefiniowanych przez `let` `let` lub `function` powinny być wcięte cztery spacje po rozpoczęciu , nawet jeśli używane jest słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="7168f-248">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="7168f-249">Nie zaleca się wyrównywania strzałek.</span><span class="sxs-lookup"><span data-stu-id="7168f-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="7168f-250">Formatowanie try/z wyrażeniami</span><span class="sxs-lookup"><span data-stu-id="7168f-250">Formatting try/with expressions</span></span>

<span data-ttu-id="7168f-251">Dopasowanie wzorca na typie wyjątku powinno być `with`wcięcie na tym samym poziomie co .</span><span class="sxs-lookup"><span data-stu-id="7168f-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="7168f-252">Aplikacja parametrów funkcji formatowania</span><span class="sxs-lookup"><span data-stu-id="7168f-252">Formatting function parameter application</span></span>

<span data-ttu-id="7168f-253">Ogólnie rzecz biorąc większość aplikacji parametr funkcji odbywa się w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="7168f-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="7168f-254">Jeśli chcesz zastosować parametry do funkcji w nowym wierszu, wcięj je według jednego zakresu.</span><span class="sxs-lookup"><span data-stu-id="7168f-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="7168f-255">Te same wytyczne dotyczą wyrażeń lambda jako argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="7168f-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="7168f-256">Jeśli treść wyrażenia lambda, obiekt może mieć inny wiersz, wcięcie przez jeden zakres</span><span class="sxs-lookup"><span data-stu-id="7168f-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="7168f-257">Jeśli jednak treść wyrażenia lambda jest więcej niż jeden wiersz, należy wziąć pod uwagę faktoringu go do oddzielnej funkcji, a nie mają wielowierszowej konstrukcji stosowane jako pojedynczy argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="7168f-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="7168f-258">Formatowanie operatorów infix</span><span class="sxs-lookup"><span data-stu-id="7168f-258">Formatting infix operators</span></span>

<span data-ttu-id="7168f-259">Oddziel operatory według spacji.</span><span class="sxs-lookup"><span data-stu-id="7168f-259">Separate operators by spaces.</span></span> <span data-ttu-id="7168f-260">Oczywiste wyjątki od tej `!` `.` reguły są i operatorów.</span><span class="sxs-lookup"><span data-stu-id="7168f-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="7168f-261">Wyrażenia Infix są ok do linii w tej samej kolumnie:</span><span class="sxs-lookup"><span data-stu-id="7168f-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="7168f-262">Formatowanie operatorów potoków</span><span class="sxs-lookup"><span data-stu-id="7168f-262">Formatting pipeline operators</span></span>

<span data-ttu-id="7168f-263">Operatorzy potoku `|>` powinny przejść pod wyrażenia, na których działają.</span><span class="sxs-lookup"><span data-stu-id="7168f-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="7168f-264">Moduły formatowania</span><span class="sxs-lookup"><span data-stu-id="7168f-264">Formatting modules</span></span>

<span data-ttu-id="7168f-265">Kod w module lokalnym musi być wcięcie względem modułu, ale kod w module najwyższego poziomu nie powinny być wcięcie.</span><span class="sxs-lookup"><span data-stu-id="7168f-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="7168f-266">Elementy obszaru nazw nie muszą być wcięciowe.</span><span class="sxs-lookup"><span data-stu-id="7168f-266">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="7168f-267">Formatowanie wyrażeń i interfejsów obiektów</span><span class="sxs-lookup"><span data-stu-id="7168f-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="7168f-268">Wyrażenia i interfejsy obiektów powinny być wyrównane `member` w taki sam sposób, jak wcięcie po czterech spacjach.</span><span class="sxs-lookup"><span data-stu-id="7168f-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="7168f-269">Formatowanie odstępu w wyrażeniach</span><span class="sxs-lookup"><span data-stu-id="7168f-269">Formatting white space in expressions</span></span>

<span data-ttu-id="7168f-270">Unikaj obcych odstępów w wyrażeniach Języka F#.</span><span class="sxs-lookup"><span data-stu-id="7168f-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="7168f-271">Nazwane argumenty nie powinny `=`również mieć miejsca wokół :</span><span class="sxs-lookup"><span data-stu-id="7168f-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="7168f-272">Atrybuty formatowania</span><span class="sxs-lookup"><span data-stu-id="7168f-272">Formatting attributes</span></span>

<span data-ttu-id="7168f-273">[Atrybuty](../language-reference/attributes.md) są umieszczane nad konstrukcją:</span><span class="sxs-lookup"><span data-stu-id="7168f-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="7168f-274">Formatowanie atrybutów parametrów</span><span class="sxs-lookup"><span data-stu-id="7168f-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="7168f-275">Atrybuty można również umieszczać na parametrach.</span><span class="sxs-lookup"><span data-stu-id="7168f-275">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="7168f-276">W takim przypadku umieść następnie w tym samym wierszu co parametr i przed nazwą:</span><span class="sxs-lookup"><span data-stu-id="7168f-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="7168f-277">Formatowanie wielu atrybutów</span><span class="sxs-lookup"><span data-stu-id="7168f-277">Formatting multiple attributes</span></span>

<span data-ttu-id="7168f-278">Gdy wiele atrybutów są stosowane do konstrukcji, która nie jest parametrem, powinny być umieszczone w taki sposób, że istnieje jeden atrybut na wiersz:</span><span class="sxs-lookup"><span data-stu-id="7168f-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="7168f-279">Po zastosowaniu do parametru, muszą one znajdować się `;` w tej samej linii i oddzielone separatorem.</span><span class="sxs-lookup"><span data-stu-id="7168f-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="7168f-280">Formatowanie literałów</span><span class="sxs-lookup"><span data-stu-id="7168f-280">Formatting literals</span></span>

<span data-ttu-id="7168f-281">[Literały F#](../language-reference/literals.md) używające atrybutu `Literal` powinny umieszczać atrybut we własnym wierszu i używać nazewnictwa PascalCase:</span><span class="sxs-lookup"><span data-stu-id="7168f-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="7168f-282">Należy unikać umieszczania atrybutu w tym samym wierszu co wartość.</span><span class="sxs-lookup"><span data-stu-id="7168f-282">Avoid placing the attribute on the same line as the value.</span></span>
