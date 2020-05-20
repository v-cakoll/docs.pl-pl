---
title: Wskazówki dotyczące formatowania kodu F#
description: 'Poznaj wskazówki dotyczące formatowania kodu F #.'
ms.date: 11/04/2019
ms.openlocfilehash: dde69c573f1ef58d398ae47676b9403f588680b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617272"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="e4ba1-103">Wskazówki dotyczące formatowania kodu F#</span><span class="sxs-lookup"><span data-stu-id="e4ba1-103">F# code formatting guidelines</span></span>

<span data-ttu-id="e4ba1-104">Ten artykuł zawiera wskazówki dotyczące sposobu formatowania kodu w taki sposób, aby kod języka F #:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="e4ba1-105">Bardziej czytelne</span><span class="sxs-lookup"><span data-stu-id="e4ba1-105">More legible</span></span>
* <span data-ttu-id="e4ba1-106">Zgodnie z konwencjami stosowanymi przez narzędzia formatowania w programie Visual Studio i innych edytorach</span><span class="sxs-lookup"><span data-stu-id="e4ba1-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="e4ba1-107">Podobnie jak w przypadku innych kodów online</span><span class="sxs-lookup"><span data-stu-id="e4ba1-107">Similar to other code online</span></span>

<span data-ttu-id="e4ba1-108">Wytyczne te są oparte na [kompleksowym przewodniku w zakresie stosowania Konwencji formatowania języka F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) przez [Anh-obornik Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="e4ba1-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="e4ba1-109">Ogólne reguły wcięć</span><span class="sxs-lookup"><span data-stu-id="e4ba1-109">General rules for indentation</span></span>

<span data-ttu-id="e4ba1-110">F # domyślnie używa znacznego białego odstępu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-110">F# uses significant white space by default.</span></span> <span data-ttu-id="e4ba1-111">W poniższych wytycznych zawarto informacje na temat sposobu Juggle niektórych wyzwań.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="e4ba1-112">Używanie spacji</span><span class="sxs-lookup"><span data-stu-id="e4ba1-112">Using spaces</span></span>

<span data-ttu-id="e4ba1-113">Gdy jest wymagane wcięcie, należy użyć spacji, a nie tabulacji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="e4ba1-114">Wymagane jest co najmniej jedno miejsce.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-114">At least one space is required.</span></span> <span data-ttu-id="e4ba1-115">Organizacja może tworzyć standardy kodowania, aby określić liczbę spacji do użycia w przypadku wcięcia; dwa, trzy lub cztery spacje wcięcia na każdym poziomie, gdzie występuje wcięcie jest typowe.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="e4ba1-116">**Zalecamy użycie czterech spacji na wcięcie.**</span><span class="sxs-lookup"><span data-stu-id="e4ba1-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="e4ba1-117">Oznacza to, że wcięcie programów jest subiektywne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="e4ba1-118">Różnice są prawidłowe, ale pierwsza reguła, którą należy wykonać, jest *spójna z wcięciem*.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="e4ba1-119">Wybierz ogólnie zaakceptowany styl wcięcia i używaj go systematycznie w całej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="e4ba1-120">Formatowanie białego znaku</span><span class="sxs-lookup"><span data-stu-id="e4ba1-120">Formatting white space</span></span>

<span data-ttu-id="e4ba1-121">W języku F # jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-121">F# is white space sensitive.</span></span> <span data-ttu-id="e4ba1-122">Chociaż większość semantyki z białego znaku jest objęta odpowiednimi wcięciami, należy wziąć pod uwagę pewne inne zagadnienia.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="e4ba1-123">Operatory formatowania w wyrażeniach arytmetycznych</span><span class="sxs-lookup"><span data-stu-id="e4ba1-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="e4ba1-124">Zawsze używaj białych znaków wokół binarnych wyrażeń arytmetycznych:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="e4ba1-125">Operatory jednoargumentowe `-` powinny zawsze występować bezpośrednio po nich wartość negacji:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="e4ba1-126">Dodanie znaku odstępu, gdy `-` operator może prowadzić do pomyłki dla innych.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="e4ba1-127">Podsumowując, ważne jest, aby zawsze:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="e4ba1-128">Otocz operatory binarne z białym znakiem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="e4ba1-129">Nie pozostawiaj pustego odstępu po operatorze jednoargumentowym</span><span class="sxs-lookup"><span data-stu-id="e4ba1-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="e4ba1-130">Wytyczne binarnego operatora arytmetycznego są szczególnie ważne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="e4ba1-131">Nie można ująć operatora binarnego `-` , gdy jest on połączony z pewnymi opcjami formatowania, może prowadzić do interpretowania go jako jednoargumentowy `-` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="e4ba1-132">Umieść niestandardową definicję operatora z białym znakiem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="e4ba1-133">Zawsze używaj białego znaku, aby obsłużyć definicję operatora:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="e4ba1-134">Dla dowolnego operatora niestandardowego, który rozpoczyna się od `*` i który ma więcej niż jeden znak, należy dodać białe miejsce na początku definicji, aby uniknąć niejednoznaczności kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="e4ba1-135">Z tego względu zalecamy, aby po prostu ująć definicje wszystkich operatorów z pojedynczym znakiem odstępu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="e4ba1-136">Strzałki parametru funkcji przestrzenny z białym znakiem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="e4ba1-137">Podczas definiowania sygnatury funkcji należy użyć białego `->` znaku wokół symbolu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="e4ba1-138">Argumenty funkcji przestrzenny z białym znakiem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-138">Surround function arguments with white space</span></span>

<span data-ttu-id="e4ba1-139">Podczas definiowania funkcji należy używać odstępów wokół każdego argumentu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="e4ba1-140">Umieść parametry w nowym wierszu dla długich definicji elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="e4ba1-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="e4ba1-141">W przypadku bardzo długiej definicji elementu członkowskiego należy umieścić parametry w nowych wierszach i wciąć je o jeden zakres.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="e4ba1-142">Dotyczy to również konstruktorów:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="e4ba1-143">Adnotacje typu</span><span class="sxs-lookup"><span data-stu-id="e4ba1-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="e4ba1-144">Adnotacje typu argumentów funkcji po prawej stronie</span><span class="sxs-lookup"><span data-stu-id="e4ba1-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="e4ba1-145">Podczas definiowania argumentów z adnotacjami typu, użyj odstępu po `:` symbolu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="e4ba1-146">Otocz adnotacje typu zwracanego z białym znakiem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="e4ba1-147">W przypadku funkcji lub adnotacji typu wartości (typ zwracany w przypadku funkcji) Użyj odstępu przed i po `:` symbolu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="e4ba1-148">Formatowanie pustych wierszy</span><span class="sxs-lookup"><span data-stu-id="e4ba1-148">Formatting blank lines</span></span>

* <span data-ttu-id="e4ba1-149">Rozdziel funkcję najwyższego poziomu i definicje klas z dwoma pustymi wierszami.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="e4ba1-150">Definicje metod wewnątrz klasy są oddzielone pojedynczym pustym wierszem.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="e4ba1-151">Dodatkowe puste wiersze mogą być używane (oszczędnie) do oddzielenia grup powiązanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="e4ba1-152">Puste wiersze można pominąć między zestawem powiązanych z jednym wierszem (na przykład zestawem implementacji fikcyjnej).</span><span class="sxs-lookup"><span data-stu-id="e4ba1-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="e4ba1-153">Używaj pustych wierszy w funkcjach, oszczędnie, aby wskazać sekcje logiczne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="e4ba1-154">Formatowanie komentarzy</span><span class="sxs-lookup"><span data-stu-id="e4ba1-154">Formatting comments</span></span>

<span data-ttu-id="e4ba1-155">Zwykle Preferuj wiele komentarzy o podwójnym ukośniku w komentarzach bloku w stylu ML.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="e4ba1-156">Komentarze wbudowane powinny rozpoczynać się wielką literą.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="e4ba1-157">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e4ba1-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="e4ba1-158">Użyj camelCase dla wartości powiązanych z klasą, powiązanych z wyrażeniami i funkcji, które są powiązane z wzorcem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-158">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="e4ba1-159">Jest to typowy i zaakceptowany styl języka F # do używania camelCase dla wszystkich nazw związanych ze zmiennymi lokalnymi lub dopasowaniami wzorców i definicjami funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="e4ba1-160">W klasach należy również użyć funkcji camelCase.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-160">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="e4ba1-161">Użyj camelCase dla funkcji publicznych powiązanych z modułem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="e4ba1-162">Gdy funkcja powiązana z modułem jest częścią publicznego interfejsu API, powinna używać camelCase:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="e4ba1-163">Używanie camelCase do wewnętrznych i prywatnych wartości i funkcji powiązanych z modułem</span><span class="sxs-lookup"><span data-stu-id="e4ba1-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="e4ba1-164">Użyj camelCase dla prywatnych wartości związanych z modułem, w tym następujących:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="e4ba1-165">Funkcje ad hoc w skryptach</span><span class="sxs-lookup"><span data-stu-id="e4ba1-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="e4ba1-166">Wartości tworzące wewnętrzną implementację modułu lub typu</span><span class="sxs-lookup"><span data-stu-id="e4ba1-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="e4ba1-167">Użyj camelCase dla parametrów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-167">Use camelCase for parameters</span></span>

<span data-ttu-id="e4ba1-168">Wszystkie parametry powinny używać camelCase zgodnie z konwencjami nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="e4ba1-169">Korzystanie z PascalCase dla modułów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-169">Use PascalCase for modules</span></span>

<span data-ttu-id="e4ba1-170">Wszystkie moduły (najwyższego poziomu, wewnętrzne, prywatne, zagnieżdżone) powinny używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="e4ba1-171">Użyj PascalCase dla deklaracji typu, elementów członkowskich i etykiet</span><span class="sxs-lookup"><span data-stu-id="e4ba1-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="e4ba1-172">Klasy, interfejsy, struktury, wyliczenia, Delegaty, rekordy i związki rozłączne powinny mieć nazwę z PascalCase.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="e4ba1-173">Elementy członkowskie w typach i etykietach dla rekordów i Unii rozłącznych powinny również używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="e4ba1-174">Użyj PascalCase dla konstrukcji wewnętrznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e4ba1-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="e4ba1-175">Przestrzenie nazw, wyjątki, zdarzenia i projekty/ `.dll` nazwy powinny również używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="e4ba1-176">Nie tylko robi to, że użycie z innych języków .NET jest bardziej naturalne dla użytkowników, jest również spójne z konwencjami nazewnictwa platformy .NET, które prawdopodobnie występują.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="e4ba1-177">Unikaj podkreśleń w nazwach</span><span class="sxs-lookup"><span data-stu-id="e4ba1-177">Avoid underscores in names</span></span>

<span data-ttu-id="e4ba1-178">Historycznie Niektóre biblioteki języka F # używały podkreśleń w nazwach.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="e4ba1-179">Nie jest to jednak już powszechnie akceptowane, częściowo ponieważ koliduje z konwencjami nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="e4ba1-180">Tak samo, niektórzy programiści F # używają podkreśleń silnie, częściowo z przyczyn historycznych, a tolerancja i istotność są ważne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="e4ba1-181">Należy jednak pamiętać, że styl często nie jest używany przez inne osoby, które mają możliwość wyboru, czy należy z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="e4ba1-182">Jeden wyjątek obejmuje współdziałanie ze składnikami macierzystymi, w których znaki podkreślenia są wspólne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-182">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="e4ba1-183">Użyj standardowych operatorów języka F #</span><span class="sxs-lookup"><span data-stu-id="e4ba1-183">Use standard F# operators</span></span>

<span data-ttu-id="e4ba1-184">Następujące operatory są zdefiniowane w standardowej bibliotece F # i powinny być używane zamiast definiować odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="e4ba1-185">Przy użyciu tych operatorów zaleca się, aby kod był bardziej czytelny i idiomatyczne.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="e4ba1-186">Deweloperzy z tłem w OCaml lub innym języku programowania funkcjonalnego mogą być przyzwyczajoni do różnych idiomy.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="e4ba1-187">Poniższa lista zawiera podsumowanie zalecanych operatorów języka F #.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="e4ba1-188">Użyj składni prefiksu dla typów ogólnych ( `Foo<T>` ) w preferencjach do przyrostkowej składni ( `T Foo` )</span><span class="sxs-lookup"><span data-stu-id="e4ba1-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="e4ba1-189">F # dziedziczy styl przyrostka (na przykład), a `int list` także styl (na przykład `list<int>` ).</span><span class="sxs-lookup"><span data-stu-id="e4ba1-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="e4ba1-190">Preferuj styl .NET, z wyjątkiem pięciu określonych typów:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="e4ba1-191">Dla list języka F # Użyj przyrostkowej formy: `int list` zamiast `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="e4ba1-192">W przypadku opcji języka F # należy użyć przyrostkowej formy: `int option` zamiast `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="e4ba1-193">W przypadku opcji wartości języka F # Użyj przyrostkowej formy: `int voption` zamiast `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="e4ba1-194">W przypadku tablic języka F # należy użyć nazwy składni `int[]` zamiast `int array` lub `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="e4ba1-195">W przypadku komórek referencyjnych Użyj `int ref` zamiast `ref<int>` lub `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="e4ba1-196">Dla wszystkich innych typów Użyj formy prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="e4ba1-197">Formatowanie krotek</span><span class="sxs-lookup"><span data-stu-id="e4ba1-197">Formatting tuples</span></span>

<span data-ttu-id="e4ba1-198">Tworzenie wystąpienia spójnej kolekcji musi być ujęte w nawiasy, a w tym przecinku należy następować pojedyncze miejsce, na przykład: `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-198">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="e4ba1-199">Jest on powszechnie akceptowany w celu pomijania nawiasów we wzorcu dopasowania spójnych krotek:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="e4ba1-200">Jest również często akceptowane do pomijania nawiasów, jeśli Krotka jest wartością zwracaną funkcji:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="e4ba1-201">W obszarze Podsumowanie zaleca się Tworzenie wystąpień spójnych krotek, ale w przypadku używania krotek w celu dopasowania do wzorca lub wartości zwracanej jest on traktowany jako drobny, aby uniknąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="e4ba1-202">Formatowanie deklaracji związku rozłącznych</span><span class="sxs-lookup"><span data-stu-id="e4ba1-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="e4ba1-203">Wcięcie `|` w definicji typu według czterech spacji:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-203">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="e4ba1-204">Formatowanie związków rozłącznych</span><span class="sxs-lookup"><span data-stu-id="e4ba1-204">Formatting discriminated unions</span></span>

<span data-ttu-id="e4ba1-205">Utworzone przez siebie związki rozłączne, które dzielą się między wiele wierszy, powinny dawać zawarte dane nowe zakresy z wcięciem:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="e4ba1-206">Nawias zamykający może również znajdować się w nowym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="e4ba1-207">Formatowanie deklaracji rekordu</span><span class="sxs-lookup"><span data-stu-id="e4ba1-207">Formatting record declarations</span></span>

<span data-ttu-id="e4ba1-208">Zwiększ wcięcie `{` w definicji typu o cztery spacje i uruchom listę pól w tym samym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-208">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="e4ba1-209">Umieszczenie tokenu otwierającego w nowym wierszu, a token zamykający w nowym wierszu jest preferowany, Jeśli deklarujesz implementacje interfejsów lub składowe w rekordzie:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="e4ba1-210">Formatowanie rekordów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-210">Formatting records</span></span>

<span data-ttu-id="e4ba1-211">Krótkie rekordy można napisać w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="e4ba1-212">Rekordy, które są dłuższe, powinny używać nowych wierszy do etykiet:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="e4ba1-213">Umieszczenie tokenu otwierającego w nowym wierszu, zawartości z zakładkami w jednym zakresie, a token zamykający w nowym wierszu jest preferowany, jeśli:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="e4ba1-214">Przenoszenie rekordów wokół kodu z różnymi zakresami wcięć</span><span class="sxs-lookup"><span data-stu-id="e4ba1-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="e4ba1-215">Przeprzewody do funkcji</span><span class="sxs-lookup"><span data-stu-id="e4ba1-215">Piping them into a function</span></span>

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

<span data-ttu-id="e4ba1-216">Te same reguły dotyczą elementów list i tablic.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="e4ba1-217">Formatowanie wyrażeń kopiowania i aktualizacji</span><span class="sxs-lookup"><span data-stu-id="e4ba1-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="e4ba1-218">Wyrażenie rekordu kopiowania i aktualizacji jest nadal rekordem, więc stosuje się do nich podobne wskazówki.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="e4ba1-219">Krótkie wyrażenia mogą zmieścić się w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="e4ba1-220">Dłuższe wyrażenia powinny używać nowych wierszy:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="e4ba1-221">Podobnie jak w przypadku wskazówek dotyczących rekordu, możesz chcieć oddzielić osobne wiersze dla nawiasów klamrowych i wciąć jeden zakres z prawej strony wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="e4ba1-222">W niektórych specjalnych przypadkach, takich jak Zawijanie wartości z opcjonalną bez nawiasów, może być konieczne pozostawienie nawiasu klamrowego w jednej linii:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-222">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="e4ba1-223">Formatowanie list i tablic</span><span class="sxs-lookup"><span data-stu-id="e4ba1-223">Formatting lists and arrays</span></span>

<span data-ttu-id="e4ba1-224">Pisz `x :: l` ze spacjami wokół `::` operatora ( `::` jest operatorem wrostkowe, dlatego jest ujęty w spacje).</span><span class="sxs-lookup"><span data-stu-id="e4ba1-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="e4ba1-225">Lista i tablice zadeklarowane w jednym wierszu powinny zawierać spację po nawiasie otwierającym i przed nawiasem zamykającym:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="e4ba1-226">Zawsze używaj co najmniej jednego miejsca między dwoma odrębnymi operatorami w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="e4ba1-227">Na przykład pozostaw spację między a `[` i `{` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="e4ba1-228">Te same wytyczne dotyczą list lub tablic krotek.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="e4ba1-229">Listy i tablice, które dzielą się między wiele wierszy, są zgodne z podobną regułą jako rekordy:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="e4ba1-230">Podobnie jak w przypadku rekordów, deklarowanie otwierających i zamykających nawiasów w osobnym wierszu spowoduje, że przenoszenie kodu i potoki do funkcji są łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="e4ba1-231">Podczas tworzenia tablic i list programistycznych należy preferować, `->` `do ... yield` gdy wartość jest zawsze generowana:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="e4ba1-232">W przypadku starszych wersji języka F # wymagane jest określenie `yield` w sytuacjach, w których dane mogą być generowane warunkowo lub mogą być oceniane kolejne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="e4ba1-233">Wolisz pominąć te `yield` słowa kluczowe, chyba że musisz skompilować przy użyciu starszej wersji języka F #:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="e4ba1-234">W niektórych przypadkach `do...yield` może pomóc w czytelności.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="e4ba1-235">Te przypadki, chociaż należy rozważyć, powinny być brane pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="e4ba1-236">Formatowanie wyrażeń if</span><span class="sxs-lookup"><span data-stu-id="e4ba1-236">Formatting if expressions</span></span>

<span data-ttu-id="e4ba1-237">Wcięcia warunkowe są zależne od rozmiarów wyrażeń, które je tworzą.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="e4ba1-238">Jeśli `cond` `e1` i `e2` są krótkie, wystarczy napisać je w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="e4ba1-239">Jeśli jeden `cond` `e1` lub `e2` więcej, ale nie wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="e4ba1-240">Jeśli dowolne wyrażenie ma wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="e4ba1-241">Wiele warunkowych z `elif` i `else` ma wcięcia w tym samym zakresie co `if` :</span><span class="sxs-lookup"><span data-stu-id="e4ba1-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="e4ba1-242">Konstrukcje dopasowania wzorca</span><span class="sxs-lookup"><span data-stu-id="e4ba1-242">Pattern matching constructs</span></span>

<span data-ttu-id="e4ba1-243">Użyj `|` dla każdej klauzuli dopasowania bez wcięcia.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="e4ba1-244">Jeśli wyrażenie jest krótkie, można rozważyć użycie pojedynczej linii, jeśli każde Podwyrażenie jest również proste.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="e4ba1-245">Jeśli wyrażenie po prawej stronie strzałki dopasowania do wzorca jest zbyt duże, przenieś je do poniższego wiersza, z wcięciem jeden krok z `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="e4ba1-246">Dopasowanie wzorców funkcji anonimowych, zaczynające `function` się od, nie powinno być zwykle zbyt dalekie.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="e4ba1-247">Na przykład wcięcie jednego z zakresów w następujący sposób jest następujące:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="e4ba1-248">Dopasowanie wzorca w funkcjach zdefiniowanych przez `let` lub `let rec` powinno mieć wcięcia cztery spacje po uruchomieniu `let` , nawet jeśli `function` jest używane słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-248">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="e4ba1-249">Nie zaleca się wyrównywania strzałek.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="e4ba1-250">Formatowanie wyrażeń try/with</span><span class="sxs-lookup"><span data-stu-id="e4ba1-250">Formatting try/with expressions</span></span>

<span data-ttu-id="e4ba1-251">Dopasowanie wzorca dla typu wyjątku powinno być wcięte na tym samym poziomie co `with` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="e4ba1-252">Formatowanie aplikacji parametrów funkcji</span><span class="sxs-lookup"><span data-stu-id="e4ba1-252">Formatting function parameter application</span></span>

<span data-ttu-id="e4ba1-253">Ogólnie rzecz biorąc, większość aplikacji parametrów funkcji jest wykonywana w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="e4ba1-254">Jeśli chcesz zastosować parametry do funkcji w nowym wierszu, Zwiększ wcięcie według jednego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="e4ba1-255">Te same wskazówki dotyczą wyrażeń lambda jako argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="e4ba1-256">Jeśli treść wyrażenia lambda, treść może mieć inny wiersz, wcięcie według jednego zakresu</span><span class="sxs-lookup"><span data-stu-id="e4ba1-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="e4ba1-257">Jednakże jeśli treść wyrażenia lambda ma więcej niż jeden wiersz, Rozważ umieszczenie go w osobnej funkcji, a nie ma zastosowania jednowierszowej konstrukcji jako pojedynczego argumentu do funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="e4ba1-258">Formatowanie operatorów wrostkowe</span><span class="sxs-lookup"><span data-stu-id="e4ba1-258">Formatting infix operators</span></span>

<span data-ttu-id="e4ba1-259">Oddziel operatory spacjami.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-259">Separate operators by spaces.</span></span> <span data-ttu-id="e4ba1-260">Oczywiste wyjątki od tej reguły to `!` Operatory i `.` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="e4ba1-261">Wyrażenia wrostkowe są prawidłowe dla zestawień w tej samej kolumnie:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="e4ba1-262">Formatowanie operatorów potoku</span><span class="sxs-lookup"><span data-stu-id="e4ba1-262">Formatting pipeline operators</span></span>

<span data-ttu-id="e4ba1-263">Operatory potoku `|>` powinny się znaleźć pod wyrażeniami, w których działają.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="e4ba1-264">Formatowanie modułów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-264">Formatting modules</span></span>

<span data-ttu-id="e4ba1-265">Dla kodu w module lokalnym należy zastosować wcięcie względem modułu, ale nie ma wcięcia kodu w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="e4ba1-266">Elementy przestrzeni nazw nie muszą mieć wcięcia.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="e4ba1-267">Formatowanie wyrażeń i interfejsów obiektów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="e4ba1-268">Wyrażenia i interfejsy obiektów powinny być wyrównane w taki sam sposób, jak w przypadku `member` wcięć z czterech spacji.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="e4ba1-269">Formatowanie białych znaków w wyrażeniach</span><span class="sxs-lookup"><span data-stu-id="e4ba1-269">Formatting white space in expressions</span></span>

<span data-ttu-id="e4ba1-270">Unikaj nadmiarowego odstępu w wyrażeniach języka F #.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="e4ba1-271">Argumenty nazwane nie mogą również zawierać spacji otaczających `=` :</span><span class="sxs-lookup"><span data-stu-id="e4ba1-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="e4ba1-272">Formatowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-272">Formatting attributes</span></span>

<span data-ttu-id="e4ba1-273">[Atrybuty](../language-reference/attributes.md) są umieszczane powyżej konstrukcji:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="e4ba1-274">Formatowanie atrybutów dla parametrów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="e4ba1-275">Atrybuty mogą być również umieszczane w parametrach.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-275">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="e4ba1-276">W takim przypadku należy umieścić w tym samym wierszu co parametr i przed nazwą:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="e4ba1-277">Formatowanie wielu atrybutów</span><span class="sxs-lookup"><span data-stu-id="e4ba1-277">Formatting multiple attributes</span></span>

<span data-ttu-id="e4ba1-278">W przypadku zastosowania wielu atrybutów do konstrukcji, która nie jest parametrem, powinny one zostać umieszczone w taki sposób, że istnieje jeden atrybut na wiersz:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="e4ba1-279">Gdy zastosowano do parametru, muszą one znajdować się w tym samym wierszu i oddzielić `;` separatorem.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="e4ba1-280">Literały formatowania</span><span class="sxs-lookup"><span data-stu-id="e4ba1-280">Formatting literals</span></span>

<span data-ttu-id="e4ba1-281">[Literały F #](../language-reference/literals.md) używające `Literal` atrybutu powinny umieścić atrybut w osobnym wierszu i używać PascalCase nazw:</span><span class="sxs-lookup"><span data-stu-id="e4ba1-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="e4ba1-282">Należy unikać umieszczania atrybutu w tym samym wierszu, w którym znajduje się wartość.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-282">Avoid placing the attribute on the same line as the value.</span></span>
