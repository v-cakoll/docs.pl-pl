---
title: C#Switch, instrukcja
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 76c778d1e2d45990793b5d9c7d4a8ee5a99fed46
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422298"
---
# <a name="switch-c-reference"></a><span data-ttu-id="c9b37-102">przełącznik (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="c9b37-102">switch (C# reference)</span></span>

<span data-ttu-id="c9b37-103">`switch` jest instrukcją wyboru, która wybiera pojedynczy *przełącznik* , który ma zostać wykonany z listy kandydatów na podstawie dopasowania wzorca z *wyrażeniem Match*.</span><span class="sxs-lookup"><span data-stu-id="c9b37-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="c9b37-104">Instrukcja `switch` jest często używana jako alternatywa dla konstrukcji [if-else](if-else.md) , jeśli pojedyncze wyrażenie jest testowane w oparciu o trzy lub więcej warunków.</span><span class="sxs-lookup"><span data-stu-id="c9b37-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="c9b37-105">Na przykład następująca instrukcja `switch` określa, czy zmienna typu `Color` ma jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="c9b37-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="c9b37-106">Jest to odpowiednik poniższego przykładu korzystającego z `if`-`else` konstrukcja.</span><span class="sxs-lookup"><span data-stu-id="c9b37-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="c9b37-107">Wyrażenie dopasowania</span><span class="sxs-lookup"><span data-stu-id="c9b37-107">The match expression</span></span>

<span data-ttu-id="c9b37-108">Wyrażenie Match zawiera wartość do dopasowania względem wzorców w etykietach `case`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="c9b37-109">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="c9b37-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="c9b37-110">W C# 6 i wcześniejszych wyrażenia dopasowania musi być wyrażeniem zwracającym wartość następujących typów:</span><span class="sxs-lookup"><span data-stu-id="c9b37-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="c9b37-111">[znak](char.md).</span><span class="sxs-lookup"><span data-stu-id="c9b37-111">a [char](char.md).</span></span>
- <span data-ttu-id="c9b37-112">[ciąg](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9b37-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="c9b37-113">wartość [logiczna](bool.md).</span><span class="sxs-lookup"><span data-stu-id="c9b37-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="c9b37-114">wartość całkowita, taka jak [int](../builtin-types/integral-numeric-types.md) lub [Long](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9b37-114">an integral value, such as an [int](../builtin-types/integral-numeric-types.md) or a [long](../builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="c9b37-115">wartość [wyliczenia](enum.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="c9b37-116">Począwszy od C# 7,0, wyrażenie dopasowania może być dowolnym wyrażeniem o wartości innej niż null.</span><span class="sxs-lookup"><span data-stu-id="c9b37-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="c9b37-117">Sekcja Switch</span><span class="sxs-lookup"><span data-stu-id="c9b37-117">The switch section</span></span>

<span data-ttu-id="c9b37-118">Instrukcja `switch` zawiera jedną lub więcej sekcji przełączników.</span><span class="sxs-lookup"><span data-stu-id="c9b37-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="c9b37-119">Każda sekcja przełącznika zawiera jedną lub więcej *etykiet przypadków* (literę lub etykietę domyślną), po której następuje jedna lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9b37-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="c9b37-120">Instrukcja `switch` może zawierać co najwyżej jedną etykietę domyślną umieszczoną w dowolnej sekcji Switch.</span><span class="sxs-lookup"><span data-stu-id="c9b37-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="c9b37-121">Poniższy przykład pokazuje prostą instrukcję `switch`, która ma trzy sekcje przełączników, z których każda zawiera dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="c9b37-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="c9b37-122">Druga sekcja Switch zawiera etykiety `case 2:` i `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="c9b37-123">Instrukcja `switch` może zawierać dowolną liczbę sekcji przełączników, a Każda sekcja może mieć jedną lub więcej etykiet wielkości liter, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c9b37-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="c9b37-124">Jednak żadne dwie etykiety wielkości liter nie mogą zawierać tego samego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c9b37-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="c9b37-125">W instrukcji switch jest wykonywana tylko jedna sekcja Switch.</span><span class="sxs-lookup"><span data-stu-id="c9b37-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="c9b37-126">C#nie zezwala na kontynuowanie wykonywania z jednej sekcji przełącznika do następnej.</span><span class="sxs-lookup"><span data-stu-id="c9b37-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="c9b37-127">W związku z tym Poniższy kod generuje błąd kompilatora, CS0163: "kontrolka nie może przechodzić z jednej etykiety case (\<etykieta przypadku >) do innej".</span><span class="sxs-lookup"><span data-stu-id="c9b37-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="c9b37-128">To wymaganie jest zwykle spełnione przez jawne opuszczenie sekcji Switch za pomocą instrukcji [Break](break.md), [goto](goto.md)lub [Return](return.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="c9b37-129">Jednak następujący kod jest również prawidłowy, ponieważ gwarantuje, że formant programu nie przechodzi do sekcji przełącznika `default`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="c9b37-130">Wykonanie listy instrukcji w sekcji Switch z etykietą Case, która pasuje do wyrażenia Match rozpoczyna się od pierwszej instrukcji i przechodzi przez listę instrukcji, zwykle do momentu, aż do instrukcji skoku, takiej jak `break`, `goto case``goto label`, `return`lub `throw`, zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="c9b37-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="c9b37-131">W tym momencie kontrola jest przekazywana poza instrukcją `switch` lub do innej etykiety case.</span><span class="sxs-lookup"><span data-stu-id="c9b37-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="c9b37-132">Instrukcja `goto`, jeśli jest używana, musi przekazywać kontrolę do stałej etykiety.</span><span class="sxs-lookup"><span data-stu-id="c9b37-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="c9b37-133">To ograniczenie jest konieczne, ponieważ próba przetransferowania kontroli do etykiety niestałej może mieć niepożądane efekty uboczne, takie przeniesienie kontroli do niezamierzonej lokalizacji w kodzie lub utworzenie pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="c9b37-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="c9b37-134">Etykiety przypadku</span><span class="sxs-lookup"><span data-stu-id="c9b37-134">Case labels</span></span>

<span data-ttu-id="c9b37-135">Każda etykieta przypadku określa wzorzec do porównania z wyrażeniem dopasowania (zmienna `caseSwitch` w poprzednich przykładach).</span><span class="sxs-lookup"><span data-stu-id="c9b37-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="c9b37-136">Jeśli są one zgodne, sterowanie jest przekazywane do sekcji Switch, która zawiera **pierwszą** pasującą etykietę case.</span><span class="sxs-lookup"><span data-stu-id="c9b37-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="c9b37-137">Jeśli żaden wzorzec etykiety case nie jest zgodny z wyrażeniem Match, formant jest przenoszony do sekcji z etykietą przypadku `default`, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="c9b37-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="c9b37-138">Jeśli nie ma `default`j wielkości liter, nie są wykonywane żadne instrukcje w żadnej sekcji Switch, a kontrolka jest transferowana poza instrukcją `switch`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="c9b37-139">Aby uzyskać informacje na temat instrukcji `switch` i dopasowania do wzorca, zobacz Zgodność [wzorców z sekcją `switch` instrukcji](#pattern) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="c9b37-140">Ponieważ C# 6 obsługuje tylko wzorce stałe i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości, a tylko jeden wzorzec może być zgodny z wyrażeniem Match.</span><span class="sxs-lookup"><span data-stu-id="c9b37-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="c9b37-141">W związku z tym kolejność, w której pojawiają się instrukcje `case`, jest nieważna.</span><span class="sxs-lookup"><span data-stu-id="c9b37-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="c9b37-142">W C# 7,0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczających się wartości, a wiele wzorców może pasować do wyrażenia Match.</span><span class="sxs-lookup"><span data-stu-id="c9b37-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="c9b37-143">Ponieważ są wykonywane tylko instrukcje w pierwszej sekcji przełącznika, które zawiera pasujący wzorzec, kolejność, w której pojawiają się instrukcje `case`, jest teraz ważna.</span><span class="sxs-lookup"><span data-stu-id="c9b37-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="c9b37-144">Jeśli C# program wykryje sekcję Switch, której instrukcją Case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadek przełączania został już obsłużony przez poprzednią literę".</span><span class="sxs-lookup"><span data-stu-id="c9b37-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="c9b37-145">Poniższy przykład ilustruje instrukcję `switch`, która używa różnych niewzajemnie wykluczających się wzorców.</span><span class="sxs-lookup"><span data-stu-id="c9b37-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="c9b37-146">Jeśli przeniesiesz sekcję Switch `case 0:` tak, aby nie była już pierwszą sekcją w instrukcji `switch`, program C# generuje błąd kompilatora, ponieważ liczba całkowita, której wartością jest zero, jest podzbiorem wszystkich liczb całkowitych, które jest wzorcem zdefiniowanym przez instrukcję `case int val` .</span><span class="sxs-lookup"><span data-stu-id="c9b37-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="c9b37-147">Możesz rozwiązać ten problem i wyeliminować Ostrzeżenie kompilatora na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="c9b37-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="c9b37-148">Zmieniając kolejność sekcji Switch.</span><span class="sxs-lookup"><span data-stu-id="c9b37-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="c9b37-149">Za pomocą [klauzuli when](#when) w etykiecie `case`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="c9b37-150">`default` przypadku</span><span class="sxs-lookup"><span data-stu-id="c9b37-150">The `default` case</span></span>

<span data-ttu-id="c9b37-151">`default` Case określa sekcję Switch, która ma zostać wykonana, jeśli wyrażenie Match nie pasuje do żadnej innej etykiety `case`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="c9b37-152">Jeśli `default` przypadku nie istnieje i wyrażenie Match nie jest zgodne z żadną inną etykietą `case`, przepływ programu odbywa się za pomocą instrukcji `switch`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="c9b37-153">Przypadek `default` może występować w dowolnej kolejności w instrukcji `switch`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="c9b37-154">Bez względu na jego kolejność w kodzie źródłowym jest zawsze Szacowana jako Ostatnia, po ocenie wszystkich etykiet `case`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="c9b37-155"><a name="pattern" /> dopasowywania do wzorca przy użyciu instrukcji `switch`</span><span class="sxs-lookup"><span data-stu-id="c9b37-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="c9b37-156">Każda instrukcja `case` definiuje wzorzec, który jest zgodny z wyrażeniem Match, powoduje, że jego sekcja Switch zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="c9b37-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="c9b37-157">Wszystkie wersje programu C# obsługują stałe wzorce.</span><span class="sxs-lookup"><span data-stu-id="c9b37-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="c9b37-158">Pozostałe wzorce są obsługiwane począwszy od C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="c9b37-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="c9b37-159">Wzorzec stałej</span><span class="sxs-lookup"><span data-stu-id="c9b37-159">Constant pattern</span></span>

<span data-ttu-id="c9b37-160">Wzorzec stałej testuje, czy wyrażenie dopasowania jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="c9b37-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="c9b37-161">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="c9b37-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="c9b37-162">gdzie *stała* jest wartością do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="c9b37-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="c9b37-163">*stała* może być dowolnym z następujących wyrażeń stałych:</span><span class="sxs-lookup"><span data-stu-id="c9b37-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="c9b37-164">Literał [bool](bool.md) , `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="c9b37-165">Dowolna stała całkowita, taka jak [int](../builtin-types/integral-numeric-types.md), [Long](../builtin-types/integral-numeric-types.md)lub [Byte](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9b37-165">Any integral constant, such as an [int](../builtin-types/integral-numeric-types.md), a [long](../builtin-types/integral-numeric-types.md), or a [byte](../builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="c9b37-166">Nazwa zadeklarowanej zmiennej `const`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="c9b37-167">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c9b37-167">An enumeration constant.</span></span>
- <span data-ttu-id="c9b37-168">Literał [znakowy](char.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-168">A [char](char.md) literal.</span></span>
- <span data-ttu-id="c9b37-169">Literał [ciągu](../builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="c9b37-170">Wyrażenie stałe jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c9b37-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="c9b37-171">Jeśli *wyrażenie* i *stała* są typami całkowitymi, C# operator równości określa, czy wyrażenie zwróci `true` (to znaczy czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="c9b37-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="c9b37-172">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody static [obiektu. Equals (wyrażenie, stała)](xref:System.Object.Equals(System.Object,System.Object)) .</span><span class="sxs-lookup"><span data-stu-id="c9b37-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="c9b37-173">W poniższym przykładzie za pomocą wzorca stałego można określić, czy konkretna data to weekend, pierwszy dzień tygodnia pracy, ostatni dzień tygodnia pracy lub środek tygodnia pracy.</span><span class="sxs-lookup"><span data-stu-id="c9b37-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="c9b37-174">Oblicza Właściwość <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> bieżącego dnia względem elementów członkowskich wyliczenia <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="c9b37-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="c9b37-175">Poniższy przykład używa wzorca stałego do obsługi danych wejściowych użytkownika w aplikacji konsolowej, która symuluje automatyczną maszynę Kawową.</span><span class="sxs-lookup"><span data-stu-id="c9b37-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="c9b37-176">Wzorzec typu</span><span class="sxs-lookup"><span data-stu-id="c9b37-176">Type pattern</span></span>

<span data-ttu-id="c9b37-177">Wzorzec typu umożliwia obliczanie i konwersję zwięzłego typu.</span><span class="sxs-lookup"><span data-stu-id="c9b37-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="c9b37-178">Gdy jest używany z instrukcją `switch`, aby wykonać dopasowanie do wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ, i, jeśli to możliwe, rzutuje go na zmienną tego typu.</span><span class="sxs-lookup"><span data-stu-id="c9b37-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="c9b37-179">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="c9b37-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="c9b37-180">Where *Type* jest nazwą typu, do którego zostanie przekonwertowany wynik *wyrażenia* , a *nazwa_zmiennej* jest obiektem, do którego zostanie przekonwertowany wynik *wyrażenia* , jeśli dopasowanie się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="c9b37-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="c9b37-181">Typ "czas kompilacji" *wyrażenia* może być parametrem typu ogólnego, rozpoczynając od C# 7,1.</span><span class="sxs-lookup"><span data-stu-id="c9b37-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="c9b37-182">Wyrażenie `case` jest `true`, jeśli którykolwiek z następujących warunków jest spełniony:</span><span class="sxs-lookup"><span data-stu-id="c9b37-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="c9b37-183">*wyrażenie* jest wystąpieniem tego samego typu co *Typ*.</span><span class="sxs-lookup"><span data-stu-id="c9b37-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="c9b37-184">*wyrażenie* jest wystąpieniem typu, który pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="c9b37-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="c9b37-185">Innymi słowy, wynik *wyrażenia* może być rzutowany na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="c9b37-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="c9b37-186">*wyrażenie* ma typ czasu kompilacji, który jest klasą bazową *typu*, a *wyrażenie* ma typ środowiska uruchomieniowego, który jest *typem* lub pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="c9b37-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="c9b37-187">*Typ czasu kompilacji* zmiennej to typ zmiennej, zgodnie z definicją w deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="c9b37-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="c9b37-188">*Typ środowiska uruchomieniowego* zmiennej to typ wystąpienia, które jest przypisane do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c9b37-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="c9b37-189">*wyrażenie* jest wystąpieniem typu, który implementuje interfejs *typu* .</span><span class="sxs-lookup"><span data-stu-id="c9b37-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="c9b37-190">Jeśli wyrażenie CASE ma wartość true, właściwość *nazwa_zmiennej* jest ostatecznie przypisana i ma zakres lokalny tylko w sekcji Switch.</span><span class="sxs-lookup"><span data-stu-id="c9b37-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="c9b37-191">Należy zauważyć, że `null` nie pasuje do typu.</span><span class="sxs-lookup"><span data-stu-id="c9b37-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="c9b37-192">Aby dopasować `null`, należy użyć następującej etykiety `case`:</span><span class="sxs-lookup"><span data-stu-id="c9b37-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="c9b37-193">Poniższy przykład używa wzorca typu, aby podać informacje dotyczące różnych rodzajów typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c9b37-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="c9b37-194">Zamiast `object`można utworzyć metodę rodzajową przy użyciu typu kolekcji jako parametru typu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c9b37-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="c9b37-195">Wersja ogólna różni się od pierwszej próbki na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="c9b37-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="c9b37-196">Najpierw nie można użyć przypadku `null`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="c9b37-197">Nie można użyć żadnego ze stałych przypadków, ponieważ kompilator nie może konwertować dowolnego dowolnego typu `T` na dowolny typ inny niż `object`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="c9b37-198">Co było `default` przypadku teraz testuje `object`o wartości innej niż null.</span><span class="sxs-lookup"><span data-stu-id="c9b37-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="c9b37-199">Oznacza to, że `default` testy przypadku `null`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="c9b37-200">Bez dopasowania do wzorca ten kod może być zapisany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="c9b37-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="c9b37-201">Użycie dopasowania wzorca typu daje bardziej zwarty, czytelny kod, eliminując konieczność sprawdzenia, czy wynik konwersji jest `null`, czy też do wykonywania powtarzających się rzutowania.</span><span class="sxs-lookup"><span data-stu-id="c9b37-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="c9b37-202"><a name="when" /> instrukcji `case` i klauzuli `when`</span><span class="sxs-lookup"><span data-stu-id="c9b37-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="c9b37-203">Począwszy od C# 7,0, ponieważ instrukcje Case nie muszą się wzajemnie wykluczać, można dodać klauzulę `when`, aby określić dodatkowy warunek, który musi być spełniony dla instrukcji case, aby obliczyć wartość true.</span><span class="sxs-lookup"><span data-stu-id="c9b37-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="c9b37-204">Klauzula `when` może być dowolnym wyrażeniem zwracającym wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="c9b37-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="c9b37-205">W poniższym przykładzie zdefiniowano klasę podstawową `Shape`, klasy `Rectangle`, która pochodzi od `Shape`i klasy `Square`, która pochodzi od `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="c9b37-206">Używa klauzuli `when`, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, do którego przypisano równe długości i szerokości jako `Square` nawet wtedy, gdy nie został skonkretyzowany jako obiekt `Square`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="c9b37-207">Metoda nie próbuje wyświetlić informacji o obiekcie `null` lub kształcie, którego obszar ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="c9b37-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="c9b37-208">Należy zauważyć, że klauzula `when` w przykładzie, która próbuje sprawdzić, czy obiekt `Shape` jest `null` nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c9b37-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="c9b37-209">Poprawna wzorzec typu do testowania dla `null` jest `case null:`.</span><span class="sxs-lookup"><span data-stu-id="c9b37-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c9b37-210">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9b37-210">C# language specification</span></span>

<span data-ttu-id="c9b37-211">Aby uzyskać więcej informacji, zobacz [instrukcję Switch](~/_csharplang/spec/statements.md#the-switch-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c9b37-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="c9b37-212">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="c9b37-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9b37-213">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9b37-213">See also</span></span>

- [<span data-ttu-id="c9b37-214">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="c9b37-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9b37-215">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9b37-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9b37-216">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c9b37-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c9b37-217">if-else</span><span class="sxs-lookup"><span data-stu-id="c9b37-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="c9b37-218">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="c9b37-218">Pattern Matching</span></span>](../../pattern-matching.md)
