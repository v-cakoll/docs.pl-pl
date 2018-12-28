---
title: F#wskazówki dotyczące formatowania kodu
description: Dowiedz się, wskazówki dotyczące formatowania F# kodu.
ms.date: 11/26/2018
ms.openlocfilehash: e8e0af2ebffd0e2f3720896bf710961afa11e7bd
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396828"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="69827-103">F#wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="69827-103">F# code formatting guidelines</span></span>

<span data-ttu-id="69827-104">Ten artykuł zawiera wskazówki dotyczące formatowania kodu, aby Twoje F# kod:</span><span class="sxs-lookup"><span data-stu-id="69827-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="69827-105">Zazwyczaj są wyświetlane jako bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="69827-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="69827-106">Jest zgodna z konwencjami stosowane przez formatowanie narzędzi w programie Visual Studio i innych edytorów</span><span class="sxs-lookup"><span data-stu-id="69827-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="69827-107">Podobnie jak inny kod w trybie online</span><span class="sxs-lookup"><span data-stu-id="69827-107">Similar to other code online</span></span>

<span data-ttu-id="69827-108">Te wytyczne są oparte na [kompletny przewodnik dotyczący F# konwencje dotyczące formatowania](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) przez [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="69827-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="69827-109">Ogólne reguły dotyczące wcięć</span><span class="sxs-lookup"><span data-stu-id="69827-109">General rules for indentation</span></span>

<span data-ttu-id="69827-110">F#Domyślnie używa istotnych białych.</span><span class="sxs-lookup"><span data-stu-id="69827-110">F# uses significant white space by default.</span></span> <span data-ttu-id="69827-111">Poniższe wskazówki są przeznaczone do zapewnienia wskazówek dotyczących tego, jak łatwiejszą obsługę niektóre wyzwania, które może to powodować.</span><span class="sxs-lookup"><span data-stu-id="69827-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="69827-112">Przy użyciu miejsc do magazynowania</span><span class="sxs-lookup"><span data-stu-id="69827-112">Using spaces</span></span>

<span data-ttu-id="69827-113">Gdy wymagana jest wcięcia, należy użyć miejsca do magazynowania, nie karty.</span><span class="sxs-lookup"><span data-stu-id="69827-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="69827-114">Wymagane jest co najmniej jedną spację.</span><span class="sxs-lookup"><span data-stu-id="69827-114">At least one space is required.</span></span> <span data-ttu-id="69827-115">Twoja organizacja może tworzyć norm kodowania, aby określić liczbę miejsc do magazynowania na potrzeby wcięć; Typowe jest dwóch, trzech lub czterech spacji wcięcia na każdym poziomie, w którym występuje wcięcia.</span><span class="sxs-lookup"><span data-stu-id="69827-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="69827-116">**Firma Microsoft zaleca 4 odstępów na znak wcięcia.**</span><span class="sxs-lookup"><span data-stu-id="69827-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="69827-117">Inaczej mówiąc, wcięcia programy polega na subiektywnej.</span><span class="sxs-lookup"><span data-stu-id="69827-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="69827-118">Różnice są dozwolone, ale jest pierwszą regułę, należy wykonać *spójności wcięcia*.</span><span class="sxs-lookup"><span data-stu-id="69827-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="69827-119">Wybierz powszechnie akceptowane styl wcięcia i systematycznie używane w całej bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="69827-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="69827-120">Formatowanie biały znak</span><span class="sxs-lookup"><span data-stu-id="69827-120">Formatting white space</span></span>

<span data-ttu-id="69827-121">F#biały znak jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="69827-121">F# is white space sensitive.</span></span> <span data-ttu-id="69827-122">Mimo że większość semantyki z biały znak są objęte właściwe wcięcia, istnieją niektóre inne kwestie należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="69827-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="69827-123">Formatowanie w wyrażeniach arytmetycznych</span><span class="sxs-lookup"><span data-stu-id="69827-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="69827-124">Zawsze używaj odstęp wokół wyrażenia arytmetyczne binarne:</span><span class="sxs-lookup"><span data-stu-id="69827-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="69827-125">Jednoargumentowy `-` operatory zawsze powinien mieć wartość, są one Negacja bezpośrednio po:</span><span class="sxs-lookup"><span data-stu-id="69827-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="69827-126">Znak odstępu, po dodaniu `-` operator może wprowadzać w błąd dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="69827-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="69827-127">Podsumowując jest ważne, aby zawsze:</span><span class="sxs-lookup"><span data-stu-id="69827-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="69827-128">Operatory dwuargumentowe Otocz białymi znakami</span><span class="sxs-lookup"><span data-stu-id="69827-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="69827-129">Nigdy nie miała odstępu, po operator jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="69827-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="69827-130">Wytyczna binarnego operatora arytmetycznego jest szczególnie ważne.</span><span class="sxs-lookup"><span data-stu-id="69827-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="69827-131">Niepowodzenie otoczyć plik binarny `-` operatora w połączeniu z niektórych opcjami formatowania, może prowadzić do interpretacji jako jednoargumentowy `-`.</span><span class="sxs-lookup"><span data-stu-id="69827-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="69827-132">Otocz definicję niestandardowych operatorów białymi znakami</span><span class="sxs-lookup"><span data-stu-id="69827-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="69827-133">Zawsze używaj biały otoczyć definicję operatora:</span><span class="sxs-lookup"><span data-stu-id="69827-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="69827-134">Dla niestandardowego operatora, który rozpoczyna się od `*`, należy dodać biały znak na początku definicji, aby uniknąć niejednoznaczności kompilatora.</span><span class="sxs-lookup"><span data-stu-id="69827-134">For any custom operator that starts with `*`, you'll need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="69827-135">W związku z tym zalecane jest, po prostu Otocz definicje wszystkich operatorów o pojedynczy znak odstępu.</span><span class="sxs-lookup"><span data-stu-id="69827-135">Because of this, it's recommended that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="69827-136">Otocz strzałki parametru funkcji białymi znakami</span><span class="sxs-lookup"><span data-stu-id="69827-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="69827-137">Podczas definiowania podpis funkcji należy używać odstęp wokół `->` symbol:</span><span class="sxs-lookup"><span data-stu-id="69827-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="69827-138">Formatowanie puste wiersze</span><span class="sxs-lookup"><span data-stu-id="69827-138">Formatting blank lines</span></span>

* <span data-ttu-id="69827-139">Oddzielne najwyższego poziomu funkcji i klas definicje z dwóch pustych wierszy.</span><span class="sxs-lookup"><span data-stu-id="69827-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="69827-140">Definicje metody wewnątrz klasy są oddzielone pojedynczy pusty wiersz.</span><span class="sxs-lookup"><span data-stu-id="69827-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="69827-141">Dodatkowe puste wiersze, które mogą (rzadko) używane do oddzielania grup pokrewnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="69827-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="69827-142">Puste wiersze mogą być pominięte między wiele powiązanych one-liners (na przykład set fikcyjne implementacje).</span><span class="sxs-lookup"><span data-stu-id="69827-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="69827-143">Użyj rzadko, puste wiersze w funkcji, aby wskazać logiczne sekcje.</span><span class="sxs-lookup"><span data-stu-id="69827-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="69827-144">Formatowanie komentarze</span><span class="sxs-lookup"><span data-stu-id="69827-144">Formatting comments</span></span>

<span data-ttu-id="69827-145">Zazwyczaj preferują wielu komentarzy podwójnego ukośnika, za pośrednictwem komentarze bloku stylu uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="69827-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="69827-146">Komentarze w tekście powinien wielką literą.</span><span class="sxs-lookup"><span data-stu-id="69827-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="69827-147">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="69827-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="69827-148">Użyj camelCase dla wartości powiązane z klasy, powiązane z wyrażenia i powiązane z wzorca i funkcji</span><span class="sxs-lookup"><span data-stu-id="69827-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="69827-149">Typowe i dopuszczalne jest F# styl do użycia camelCase dla wszystkich nazw powiązany jako zmienne lokalne lub dopasowania do wzorca i definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="69827-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="69827-150">Funkcje lokalnie granicę w klasach należy również użyć camelCase.</span><span class="sxs-lookup"><span data-stu-id="69827-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="69827-151">Użyj camelCase dla funkcji publicznych powiązanych z modułu</span><span class="sxs-lookup"><span data-stu-id="69827-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="69827-152">Gdy funkcja powiązane z modułu jest częścią publicznego interfejsu API, powinna korzystać camelCase:</span><span class="sxs-lookup"><span data-stu-id="69827-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="69827-153">Użyj camelCase dla wartości powiązane z modułu wewnętrzne i prywatne i funkcji</span><span class="sxs-lookup"><span data-stu-id="69827-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="69827-154">Użyj camelCase dla wartości powiązane z modułu prywatne, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="69827-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="69827-155">Funkcje ad hoc w skryptach</span><span class="sxs-lookup"><span data-stu-id="69827-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="69827-156">Tworzących wewnętrzną implementację modułu lub typu wartości</span><span class="sxs-lookup"><span data-stu-id="69827-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="69827-157">Użyj camelCase dla parametrów</span><span class="sxs-lookup"><span data-stu-id="69827-157">Use camelCase for parameters</span></span>

<span data-ttu-id="69827-158">Wszystkie parametry powinny używać camelCase zgodnie z konwencjami nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="69827-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="69827-159">Użyj PascalCase dla modułów</span><span class="sxs-lookup"><span data-stu-id="69827-159">Use PascalCase for modules</span></span>

<span data-ttu-id="69827-160">Wszystkie moduły (najwyższego poziomu wewnętrznej, prywatne i zagnieżdżone) powinny używać PascalCase.</span><span class="sxs-lookup"><span data-stu-id="69827-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="69827-161">PascalCase na użytek deklaracji typów, elementów członkowskich i etykiety</span><span class="sxs-lookup"><span data-stu-id="69827-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="69827-162">Klasy, interfejsy, struktury, wyliczenia, delegatów, rekordy i sumy rozłączne powinny mieć wszystkie nazwę z PascalCase.</span><span class="sxs-lookup"><span data-stu-id="69827-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="69827-163">Członków w ramach typów i etykiet rekordów i sumy rozłączne należy również użyć PascalCase.</span><span class="sxs-lookup"><span data-stu-id="69827-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="69827-164">Użyj PascalCase dla konstrukcji na wewnętrzne dla oprogramowania .NET</span><span class="sxs-lookup"><span data-stu-id="69827-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="69827-165">Przestrzenie nazw, wyjątki, zdarzenia i projekt /`.dll` nazwy należy również użyć PascalCase.</span><span class="sxs-lookup"><span data-stu-id="69827-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="69827-166">Nie tylko jest to, że zużycie z innymi językami .NET bardziej naturalnych dla konsumentów, również jest ona zgodna z konwencjami nazewnictwa platformy .NET, które mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="69827-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="69827-167">Należy unikać podkreślenia w nazwach</span><span class="sxs-lookup"><span data-stu-id="69827-167">Avoid underscores in names</span></span>

<span data-ttu-id="69827-168">W przeszłości, niektóre F# bibliotek używanych w nazwach znaki podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="69827-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="69827-169">Jednak to się nie są już powszechnie akceptowane, częściowo, ponieważ ona jest niezgodna z konwencjami nazewnictwa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="69827-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="69827-170">Jednak niektóre F# programistów używać znaków podkreślenia intensywnie, częściowo powodów historycznych i na uszkodzenia i przestrzegania jest ważne.</span><span class="sxs-lookup"><span data-stu-id="69827-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="69827-171">Należy jednak pamiętać, że styl jest często disliked przez innych użytkowników, którzy mają możliwość wyboru o tym, czy z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="69827-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="69827-172">Niektóre wyjątki obejmuje współdziałanie z składnikami macierzystymi, gdzie są bardzo popularne znaki podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="69827-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="69827-173">Użyj standardowych F# operatorów</span><span class="sxs-lookup"><span data-stu-id="69827-173">Use standard F# operators</span></span>

<span data-ttu-id="69827-174">Następujące operatory są zdefiniowane w F# biblioteki standardowej i powinny być używane zamiast zdefiniowanie odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="69827-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="69827-175">Korzystanie z tych operatorów jest zalecane, ponieważ sprawia kod bardziej czytelne i idiomatyczną.</span><span class="sxs-lookup"><span data-stu-id="69827-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="69827-176">Deweloperów z doświadczeniem w OCaml lub innych funkcjonalny język programowania może być przyzwyczajeni do różnych idiomy.</span><span class="sxs-lookup"><span data-stu-id="69827-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="69827-177">Poniższa lista zawiera podsumowanie zalecanych F# operatorów.</span><span class="sxs-lookup"><span data-stu-id="69827-177">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="69827-178">Użyj składni prefiks dla typów ogólnych (`Foo<T>`) zamiast składni przyrostka (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="69827-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="69827-179">F#dziedziczy zarówno przyrostkowe ML styl nazewnictwa typów ogólnych (na przykład `int list`) oraz prefiks stylu .NET (na przykład `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="69827-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="69827-180">Preferuj styl .NET, z wyjątkiem czterech określonych typów:</span><span class="sxs-lookup"><span data-stu-id="69827-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="69827-181">Aby uzyskać F# listy, formularz przyrostkowe: `int list` zamiast `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="69827-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="69827-182">Aby uzyskać F# opcje formularz przyrostkowe: `int option` zamiast `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="69827-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="69827-183">Aby uzyskać F# tablic, użyj składni nazwy `int[]` zamiast `int array` lub `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="69827-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="69827-184">Komórki odwołań, można użyć `int ref` zamiast `ref<int>` lub `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="69827-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="69827-185">W przypadku wszystkich innych typów formularz prefiks.</span><span class="sxs-lookup"><span data-stu-id="69827-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="69827-186">Formatowanie krotki</span><span class="sxs-lookup"><span data-stu-id="69827-186">Formatting tuples</span></span>

<span data-ttu-id="69827-187">Wystąpienia krotki powinien być ujęty w nawiasy i ograniczająca przecinkami w ramach powinno następować pojedyncza spacja, na przykład: `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="69827-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="69827-188">Przyjęto często pominąć nawiasów w krotek dopasowywanie do wzorców:</span><span class="sxs-lookup"><span data-stu-id="69827-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="69827-189">Formatowanie Suma rozłączna deklaracje złożeń</span><span class="sxs-lookup"><span data-stu-id="69827-189">Formatting discriminated union declarations</span></span>

<span data-ttu-id="69827-190">Zwiększ wcięcie `|` w definicji typu spacjami 4:</span><span class="sxs-lookup"><span data-stu-id="69827-190">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="69827-191">Formatowanie rekord z wariantami</span><span class="sxs-lookup"><span data-stu-id="69827-191">Formatting discriminated unions</span></span>

<span data-ttu-id="69827-192">Utworzona Suma rozłączna Unii, które podzielone między wiele wierszy, powinien zapewnić zawartymi danymi nowego zakresu z wcięciem:</span><span class="sxs-lookup"><span data-stu-id="69827-192">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="69827-193">Nawias zamykający mogą być także w nowym wierszu:</span><span class="sxs-lookup"><span data-stu-id="69827-193">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="69827-194">Formatowanie deklaracje rekordu</span><span class="sxs-lookup"><span data-stu-id="69827-194">Formatting record declarations</span></span>

<span data-ttu-id="69827-195">Zwiększ wcięcie `{` w typie definicji przez 4 spacji i umożliwia rozpoczęcie listy pól w tym samym wierszu:</span><span class="sxs-lookup"><span data-stu-id="69827-195">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="69827-196">Wprowadzenie do tokenu otwierającym znakiem nowego wiersza i token zamknięcia w nowym wierszu jest preferrable, jeśli są deklarowanie implementacje interfejsu lub elementów członkowskich, które znajdują się w rekordzie:</span><span class="sxs-lookup"><span data-stu-id="69827-196">Placing the opening token on a new line and the closing token on a new line is preferrable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField : int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="69827-197">Formatowanie rekordów</span><span class="sxs-lookup"><span data-stu-id="69827-197">Formatting records</span></span>

<span data-ttu-id="69827-198">Krótkie rekordy mogą być napisane w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="69827-198">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="69827-199">Rekordy, które są dłuższe należy używać nowych wierszy dla etykiet:</span><span class="sxs-lookup"><span data-stu-id="69827-199">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="69827-200">Wprowadzenie do otwarcia tokenu w nowym wierszu, zawartość z kartami jednego zakresu, a token zamknięcia w nowym wierszu jest preferrable, jeśli:</span><span class="sxs-lookup"><span data-stu-id="69827-200">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferrable if you are:</span></span>

* <span data-ttu-id="69827-201">Poruszanie się w rekordów w kodzie z zakresami różnych wcięć</span><span class="sxs-lookup"><span data-stu-id="69827-201">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="69827-202">Przekazanie w potoku je do funkcji</span><span class="sxs-lookup"><span data-stu-id="69827-202">Piping them into a function</span></span>

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
        SomeField : int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="69827-203">Te same zasady mają zastosowanie dla elementów listy i tablicy.</span><span class="sxs-lookup"><span data-stu-id="69827-203">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="69827-204">Formatowanie, list i tablice</span><span class="sxs-lookup"><span data-stu-id="69827-204">Formatting lists and arrays</span></span>

<span data-ttu-id="69827-205">Zapis `x :: l` zawierające spacje wokół `::` — operator (`::` jest operator wrostkowe, dlatego otoczony spacjami).</span><span class="sxs-lookup"><span data-stu-id="69827-205">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="69827-206">Lista i tablice deklarowane w pojedynczym wierszu powinny mieć odstęp po nawiasie otwierającym, a także przed nawiasem zamykającym:</span><span class="sxs-lookup"><span data-stu-id="69827-206">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="69827-207">Zawsze należy używać co najmniej jedną spację między dwa różne operatory podobne do nawiasu klamrowego.</span><span class="sxs-lookup"><span data-stu-id="69827-207">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="69827-208">Na przykład, pozostaw odstęp między `[` i `{`.</span><span class="sxs-lookup"><span data-stu-id="69827-208">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="69827-209">Tym samym wytyczna ma zastosowanie do listy lub tablic krotek.</span><span class="sxs-lookup"><span data-stu-id="69827-209">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="69827-210">Listy i tablic, które podzielone między wiele wierszy wykonaj regułę podobne jak rekordy:</span><span class="sxs-lookup"><span data-stu-id="69827-210">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="69827-211">I podobnie jak w przypadku rekordów, deklarowanie otwierania i zamykających nawiasów kwadratowych w ich własnych wierszu ułatwi przenoszenie kodu wokół i przesyłanie potokowe do funkcji.</span><span class="sxs-lookup"><span data-stu-id="69827-211">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="69827-212">Jeśli formatowania wyrażeń</span><span class="sxs-lookup"><span data-stu-id="69827-212">Formatting if expressions</span></span>

<span data-ttu-id="69827-213">Wcięcie warunkowych zależy od wielkości wyrażeń, które je tworzą.</span><span class="sxs-lookup"><span data-stu-id="69827-213">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="69827-214">Jeśli `cond`, `e1` i `e2` krótki, po prostu zostaną zapisane w jednym wierszu:</span><span class="sxs-lookup"><span data-stu-id="69827-214">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="69827-215">Jeśli `cond`, `e1` lub `e2` dłużej, ale nie wiele wierszy:</span><span class="sxs-lookup"><span data-stu-id="69827-215">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="69827-216">Jeśli dowolne wyrażenie z wielowierszowym:</span><span class="sxs-lookup"><span data-stu-id="69827-216">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="69827-217">Wiele warunkowych z `elif` i `else` tworzone jest wcięcie na tym samym zakresie co `if`:</span><span class="sxs-lookup"><span data-stu-id="69827-217">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="69827-218">Konstrukcje dopasowywania wzorca</span><span class="sxs-lookup"><span data-stu-id="69827-218">Pattern matching constructs</span></span>

<span data-ttu-id="69827-219">Użyj `|` dla każdej klauzuli dopasowania z wcięciem nie.</span><span class="sxs-lookup"><span data-stu-id="69827-219">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="69827-220">Jeśli wyrażenie jest krótki, można rozważyć użycie pojedynczy wiersz, jeśli każdy Podwyrażenie również jest proste.</span><span class="sxs-lookup"><span data-stu-id="69827-220">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="69827-221">Jeśli wyrażenie po prawej stronie strzałkę dopasowania wzorca jest zbyt duży, przenieś go do następujący wiersz z wcięciami jeden krok z `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="69827-221">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="69827-222">Dopasowanie z funkcjami anonimowymi uruchomienie wzorca `function`, powinien ogólnie nie twórz wcięcie zbyt daleko.</span><span class="sxs-lookup"><span data-stu-id="69827-222">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="69827-223">Na przykład następujący wcięcia jeden zakres jest w dobrym stanie:</span><span class="sxs-lookup"><span data-stu-id="69827-223">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="69827-224">Dopasowanie do wzorca w funkcje zdefiniowane przez `let` lub `let rec` powinien być z wcięciami 4 spacji po uruchomieniu programu `let`nawet wtedy, gdy `function` słowo kluczowe jest używane:</span><span class="sxs-lookup"><span data-stu-id="69827-224">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="69827-225">Nie zaleca się dopasowanie strzałki.</span><span class="sxs-lookup"><span data-stu-id="69827-225">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="69827-226">Spróbuj formatowania / przy użyciu wyrażeń</span><span class="sxs-lookup"><span data-stu-id="69827-226">Formatting try/with expressions</span></span>

<span data-ttu-id="69827-227">Powinien być wcięty dopasowania do wzorca w typ wyjątku, w tym samym poziomie co `with`.</span><span class="sxs-lookup"><span data-stu-id="69827-227">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="69827-228">Formatowanie aplikacji parametru — funkcja</span><span class="sxs-lookup"><span data-stu-id="69827-228">Formatting function parameter application</span></span>

<span data-ttu-id="69827-229">Ogólnie rzecz biorąc większość funkcji parametr aplikacji odbywa się w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="69827-229">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="69827-230">Jeśli chcesz zastosować parametrów do funkcji w nowym wierszu wcięcie je przez jeden zakres.</span><span class="sxs-lookup"><span data-stu-id="69827-230">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="69827-231">Te same wytyczne mają zastosowanie w przypadku wyrażenia lambda jako argumenty funkcji.</span><span class="sxs-lookup"><span data-stu-id="69827-231">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="69827-232">Jeżeli treść wyrażenia lambda, jednostka może mieć innego wiersza, zawiera tylko przez jeden zakres</span><span class="sxs-lookup"><span data-stu-id="69827-232">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="69827-233">Jednakże jeśli treść wyrażenia lambda jest więcej niż jeden wiersz, należy wziąć pod uwagę, uwzględniając ją w to oddzielna funkcja zamiast konstrukcję wielowierszowe stosowane jako pojedynczy argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="69827-233">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="69827-234">Formatowanie operatory wrostkowe</span><span class="sxs-lookup"><span data-stu-id="69827-234">Formatting infix operators</span></span>

<span data-ttu-id="69827-235">Oddzielne operatory spacjami.</span><span class="sxs-lookup"><span data-stu-id="69827-235">Separate operators by spaces.</span></span> <span data-ttu-id="69827-236">Oczywiste wyjątki od tej reguły są `!` i `.` operatorów.</span><span class="sxs-lookup"><span data-stu-id="69827-236">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="69827-237">Wyrażenia wrostkowe są OK oferty na tej samej kolumnie:</span><span class="sxs-lookup"><span data-stu-id="69827-237">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="69827-238">Formatowanie operatorów potoku</span><span class="sxs-lookup"><span data-stu-id="69827-238">Formatting pipeline operators</span></span>

<span data-ttu-id="69827-239">Potok `|>` operatory powinny przechodzić poniżej wyrażeń działają na.</span><span class="sxs-lookup"><span data-stu-id="69827-239">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="69827-240">Formatowanie modułów</span><span class="sxs-lookup"><span data-stu-id="69827-240">Formatting modules</span></span>

<span data-ttu-id="69827-241">Kod w lokalnym module musi być wcięty względem modułu, ale nie powinien być wcięty kodu w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="69827-241">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="69827-242">Nie masz elementy Namespace wcięcia.</span><span class="sxs-lookup"><span data-stu-id="69827-242">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="69827-243">Wyrażenia obiektów formatowania i interfejsy</span><span class="sxs-lookup"><span data-stu-id="69827-243">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="69827-244">Wyrażenia obiektów i interfejsy, które powinno być wyrównane tak samo jak przy użyciu `member` tworzone jest wcięcie po 4 miejsc do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="69827-244">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="69827-245">Formatowanie biały znak w wyrażeniach</span><span class="sxs-lookup"><span data-stu-id="69827-245">Formatting white space in expressions</span></span>

<span data-ttu-id="69827-246">Należy unikać nadmiarowe biały znak w F# wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="69827-246">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="69827-247">Argumenty nazwane również nie powinny mieć miejsca wokół `=`:</span><span class="sxs-lookup"><span data-stu-id="69827-247">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="69827-248">Formatowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="69827-248">Formatting attributes</span></span>

<span data-ttu-id="69827-249">[Atrybuty](../language-reference/attributes.md) są umieszczane powyżej konstrukcję:</span><span class="sxs-lookup"><span data-stu-id="69827-249">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="69827-250">Atrybuty formatowania w parametrach</span><span class="sxs-lookup"><span data-stu-id="69827-250">Formatting attributes on parameters</span></span>

<span data-ttu-id="69827-251">Atrybuty mogą być także miejsca w parametrach.</span><span class="sxs-lookup"><span data-stu-id="69827-251">Attributes can also be places on parameters.</span></span> <span data-ttu-id="69827-252">W tym przypadku umieść następnie, w tym samym wierszu jako parametru i przed nazwą:</span><span class="sxs-lookup"><span data-stu-id="69827-252">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="69827-253">Formatowanie wiele atrybutów</span><span class="sxs-lookup"><span data-stu-id="69827-253">Formatting multiple attributes</span></span>

<span data-ttu-id="69827-254">Gdy wiele atrybutów są stosowane do konstrukcja, która nie jest parametrem, powinien zostać umieszczony taki sposób, że istnieje jeden atrybut na wiersz:</span><span class="sxs-lookup"><span data-stu-id="69827-254">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="69827-255">Po zastosowaniu do parametru, musi znajdować się na tym samym wierszu i oddzielone `;` separatora.</span><span class="sxs-lookup"><span data-stu-id="69827-255">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="69827-256">Literały formatowania</span><span class="sxs-lookup"><span data-stu-id="69827-256">Formatting literals</span></span>

<span data-ttu-id="69827-257">[F#literały](../language-reference/literals.md) przy użyciu `Literal` atrybut powinien należy umieścić atrybut w osobnym wierszu i użyj nazw camelCase:</span><span class="sxs-lookup"><span data-stu-id="69827-257">[F# literals](../language-reference/literals.md) using the `Literal` attribute should should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="69827-258">Należy unikać wprowadzania atrybutu na tym samym wierszu jako wartość.</span><span class="sxs-lookup"><span data-stu-id="69827-258">Avoid placing the attribute on the same line as the value.</span></span>
