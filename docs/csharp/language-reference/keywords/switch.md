---
title: Instrukcja przełączania języka C#
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
ms.openlocfilehash: 49b3836f17e91ae8de10d68e97fd662aae80d1ff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249321"
---
# <a name="switch-c-reference"></a><span data-ttu-id="eeb1f-102">przełącznik (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="eeb1f-102">switch (C# reference)</span></span>

<span data-ttu-id="eeb1f-103">Ten artykuł `switch` obejmuje instrukcję.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="eeb1f-104">Aby uzyskać `switch` informacje na temat wyrażenia (wprowadzone w języku C# 8.0), zobacz artykuł na [ `switch` wyrażenia](../operators/switch-expression.md) w [wyrażeń i operatorów](../operators/index.md) sekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="eeb1f-105">`switch`jest instrukcją wyboru, która wybiera *sekcję* pojedynczego przełącznika do wykonania z listy kandydatów na podstawie dopasowania wzorca z *wyrażeniem dopasowania*.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="eeb1f-106">Instrukcja `switch` jest często używana jako alternatywa dla [konstrukcji if-else,](if-else.md) jeśli pojedyncze wyrażenie jest testowane pod względem trzech lub więcej warunków.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="eeb1f-107">Na przykład następująca `switch` instrukcja określa, `Color` czy zmienna typu ma jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="eeb1f-108">Jest to równoważne z poniższym `if` - `else` przykładem, który używa konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="eeb1f-109">Wyrażenie dopasowania</span><span class="sxs-lookup"><span data-stu-id="eeb1f-109">The match expression</span></span>

<span data-ttu-id="eeb1f-110">Wyrażenie dopasowania zawiera wartość dopasowaną do `case` wzorców w etykietach.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="eeb1f-111">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="eeb1f-112">W języku C# 6 i wcześniej wyrażenie dopasowania musi być wyrażeniem, które zwraca wartość następujących typów:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="eeb1f-113">[char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="eeb1f-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="eeb1f-114">[ciąg znaków](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="eeb1f-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="eeb1f-115">[bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="eeb1f-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="eeb1f-116">wartości [integralnej,](../builtin-types/integral-numeric-types.md) takiej `int` jak `long`lub .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="eeb1f-117">wartości [wyliczenia.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="eeb1f-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="eeb1f-118">Począwszy od C# 7.0 wyrażenie dopasowania może być dowolne wyrażenie inne niż null.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="eeb1f-119">Sekcja przełącznika</span><span class="sxs-lookup"><span data-stu-id="eeb1f-119">The switch section</span></span>

<span data-ttu-id="eeb1f-120">Instrukcja `switch` zawiera co najmniej jedną sekcję przełącznika.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="eeb1f-121">Każda sekcja przełącznika zawiera jedną lub więcej *etykiet przypadków* (przypadek lub etykietę domyślną), po której następuje co najmniej jedna instrukcja.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="eeb1f-122">Instrukcja `switch` może zawierać co najwyżej jedną domyślną etykietę umieszczona w dowolnej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="eeb1f-123">W poniższym przykładzie przedstawiono prostą `switch` instrukcję, która ma trzy sekcje przełącznika, z których każda zawiera dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="eeb1f-124">Druga sekcja przełącznika `case 2:` `case 3:` zawiera i etykiety.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="eeb1f-125">Instrukcja `switch` może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet przypadków, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="eeb1f-126">Jednak żadne dwie etykiety przypadków nie mogą zawierać tego samego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="eeb1f-127">Wykonuje tylko jedną sekcję przełącznika w instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="eeb1f-128">C# nie zezwala na wykonywanie, aby kontynuować z jednej sekcji przełącznika do następnego.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="eeb1f-129">Z tego powodu następujący kod generuje błąd kompilatora, CS0163: "Kontrola\<nie może przechodzić z jednej etykiety sprawy (etykieta sprawy>) do innej."</span><span class="sxs-lookup"><span data-stu-id="eeb1f-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="eeb1f-130">To wymaganie jest zwykle spełnione przez jawne wyjście z sekcji przełącznika za pomocą [break](break.md), [goto](goto.md)lub [return](return.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="eeb1f-131">Jednak poniższy kod jest również prawidłowy, ponieważ zapewnia, że formant programu nie może spaść do sekcji przełącznika. `default`</span><span class="sxs-lookup"><span data-stu-id="eeb1f-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="eeb1f-132">Wykonanie listy instrukcji w sekcji przełącznika z etykietą sprawy, która pasuje do wyrażenia dopasowania, rozpoczyna się od pierwszej instrukcji `break` `goto case`i `goto label` `return`przebiega `throw`przez listę instrukcji, zazwyczaj do momentu osiągnięcia instrukcji skoku, takiej jak , , , lub ,.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="eeb1f-133">W tym momencie kontrola jest `switch` przenoszona poza instrukcję lub do innej etykiety sprawy.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="eeb1f-134">Instrukcja, `goto` jeśli jest używana, należy przenieść formant do stałej etykiety.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="eeb1f-135">To ograniczenie jest konieczne, ponieważ próba przeniesienia kontroli do etykiety niestanowej może mieć niepożądane skutki uboczne, takie jak przenoszenie kontroli do niezamierzonelokalnie w kodzie lub tworzenie nieskończonej pętli.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="eeb1f-136">Etykiety etui</span><span class="sxs-lookup"><span data-stu-id="eeb1f-136">Case labels</span></span>

<span data-ttu-id="eeb1f-137">Każda etykieta sprawy określa wzorzec do `caseSwitch` porównania z wyrażeniem dopasowania (zmienną w poprzednich przykładach).</span><span class="sxs-lookup"><span data-stu-id="eeb1f-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="eeb1f-138">Jeśli są zgodne, formant jest przenoszony do sekcji przełącznika, która zawiera **pierwszą** etykietę pasujące sprawy.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="eeb1f-139">Jeśli żaden wzorzec etykiety sprawy nie pasuje do wyrażenia `default` dopasowania, formant jest przenoszony do sekcji z etykietą sprawy, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="eeb1f-140">Jeśli nie ma `default` przypadku, nie instrukcje w dowolnej sekcji przełącznik są `switch` wykonywane i kontroli jest przenoszony poza instrukcję.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="eeb1f-141">Aby uzyskać `switch` informacje na temat dopasowywania instrukcji i wzorca, zobacz [Dopasowanie wzorca z sekcją `switch` instrukcji.](#pattern)</span><span class="sxs-lookup"><span data-stu-id="eeb1f-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="eeb1f-142">Ponieważ C# 6 obsługuje tylko stały wzorzec i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości, a tylko jeden wzorzec może odpowiadać wyrażeniu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="eeb1f-143">W rezultacie kolejność, w `case` której pojawiają się instrukcje, jest nieistotna.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="eeb1f-144">W języku C# 7.0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczające się wartości i wiele wzorców może odpowiadać wyrażenie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="eeb1f-145">Ponieważ wykonywane są tylko instrukcje w pierwszej sekcji przełącznika, `case` która zawiera pasujący wzorzec, kolejność, w której pojawiają się instrukcje, jest teraz ważna.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="eeb1f-146">Jeśli C# wykrywa sekcji switch, którego case instrukcji lub instrukcji są równoważne lub są podzbiory poprzednich instrukcji, generuje błąd kompilatora, CS8120, "Przypadek przełącznika został już obsłużony przez poprzedni przypadek."</span><span class="sxs-lookup"><span data-stu-id="eeb1f-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="eeb1f-147">Poniższy przykład ilustruje instrukcję, `switch` która używa różnych wzorców nie wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="eeb1f-148">Jeśli przeniesiesz `case 0:` przełączyć sekcji tak, że nie `switch` jest już pierwszą sekcję w instrukcji, C# generuje błąd kompilatora, ponieważ liczba całkowita, której `case int val` wartość wynosi zero jest podzbiorem wszystkich całkowitej liczby, który jest wzorzec zdefiniowany przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="eeb1f-149">Można rozwiązać ten problem i wyeliminować ostrzeżenie kompilatora na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="eeb1f-150">Zmieniając kolejność sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="eeb1f-151">Za pomocą [when klauzuli](#when) na etykiecie. `case`</span><span class="sxs-lookup"><span data-stu-id="eeb1f-151">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="eeb1f-152">Sprawa `default`</span><span class="sxs-lookup"><span data-stu-id="eeb1f-152">The `default` case</span></span>

<span data-ttu-id="eeb1f-153">Przypadek `default` określa sekcję switch do wykonania, jeśli wyrażenie dopasowania `case` nie pasuje do żadnej innej etykiety.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="eeb1f-154">Jeśli `default` przypadek nie jest obecny, a wyrażenie dopasowania `case` nie pasuje do `switch` żadnej innej etykiety, przepływ programu przechodzi przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="eeb1f-155">Sprawa `default` może pojawić się w `switch` dowolnej kolejności w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="eeb1f-156">Niezależnie od jego kolejności w kodzie źródłowym, zawsze `case` jest oceniane jako ostatni, po wszystkie etykiety zostały ocenione.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="eeb1f-157"><a name="pattern" />Dopasowanie wzorca `switch` do instrukcji</span><span class="sxs-lookup"><span data-stu-id="eeb1f-157"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="eeb1f-158">Każda `case` instrukcja definiuje wzorzec, który, jeśli pasuje do wyrażenia dopasowania, powoduje, że jego sekcja przełączania zawierająca ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="eeb1f-159">Wszystkie wersje języka C# obsługują stały wzorzec.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="eeb1f-160">Pozostałe wzorce są obsługiwane począwszy od języka C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="eeb1f-161">Stały wzór</span><span class="sxs-lookup"><span data-stu-id="eeb1f-161">Constant pattern</span></span>

<span data-ttu-id="eeb1f-162">Wzorzec stały sprawdza, czy wyrażenie dopasowania jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="eeb1f-163">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="eeb1f-164">gdzie *stała* jest wartością, dla której należy testować.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="eeb1f-165">*stała* może być dowolną z następujących wyrażeń stałych:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="eeb1f-166">[Bool](../builtin-types/bool.md) dosłowny: `true` `false`albo lub .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="eeb1f-167">Każda stała [integralna,](../builtin-types/integral-numeric-types.md) `int`taka `long`jak `byte`, a lub .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="eeb1f-168">Nazwa zadeklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="eeb1f-169">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-169">An enumeration constant.</span></span>
- <span data-ttu-id="eeb1f-170">Char [char](../builtin-types/char.md) dosłowny.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="eeb1f-171">Literał [ciągu.](../builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="eeb1f-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="eeb1f-172">Wyrażenie stałe jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="eeb1f-173">Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości języka C# określa, czy wyrażenie zwraca (czyli, czy). `expr == constant`</span><span class="sxs-lookup"><span data-stu-id="eeb1f-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="eeb1f-174">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie metody [statycznej Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))</span><span class="sxs-lookup"><span data-stu-id="eeb1f-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="eeb1f-175">W poniższym przykładzie użyto stałego wzorca, aby określić, czy określona data to weekend, pierwszy dzień tygodnia roboczego, ostatni dzień tygodnia roboczego lub środek tygodnia roboczego.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="eeb1f-176">Ocenia <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwość bieżącego dnia względem członków <xref:System.DayOfWeek> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="eeb1f-177">W poniższym przykładzie użyto stałego wzorca do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje automatyczny ekspres do kawy.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="eeb1f-178">Wzór typu</span><span class="sxs-lookup"><span data-stu-id="eeb1f-178">Type pattern</span></span>

<span data-ttu-id="eeb1f-179">Wzorzec typu umożliwia zwięzłą ocenę typu i konwersję.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="eeb1f-180">W przypadku `switch` użycia z instrukcją do wykonywania dopasowania wzorca, sprawdza, czy wyrażenie może być konwertowane na określony typ i, jeśli może to być, rzutuje go do zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="eeb1f-181">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="eeb1f-182">gdzie *typ* jest nazwą typu, na który ma zostać przekonwertowany wynik *expr,* a *nazwa warna* jest obiektem, na który zostanie przekonwertowany wynik *expr,* jeśli dopasowanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="eeb1f-183">Typ *expr* w czasie kompilacji może być parametrem typu ogólnego, począwszy od języka C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="eeb1f-184">Wyrażenie `case` jest, `true` jeśli którykolwiek z następujących jest true:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="eeb1f-185">*expr* jest wystąpieniem tego samego typu co *typ*.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="eeb1f-186">*expr* jest wystąpieniem typu, który pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="eeb1f-187">Innymi słowy, wynik *expr* może być upcast do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="eeb1f-188">*expr* ma typ czasu kompilacji, który jest klasą podstawową *typu,* a *expr* ma typ środowiska uruchomieniowego, który jest *typem* lub jest pochodną *typu*.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="eeb1f-189">*Typ zmiennej w czasie kompilacji* jest typem zmiennej zdefiniowanym w deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="eeb1f-190">*Typ środowiska wykonawczego* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="eeb1f-191">*expr* jest wystąpieniem typu, który implementuje interfejs *typu.*</span><span class="sxs-lookup"><span data-stu-id="eeb1f-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="eeb1f-192">Jeśli wyrażenie sprawy jest prawdziwe, *varname* jest zdecydowanie przypisany i ma zakres lokalny tylko w sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="eeb1f-193">Należy `null` zauważyć, że nie pasuje do typu.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="eeb1f-194">Aby dopasować program `null`, `case` należy użyć następującej etykiety:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="eeb1f-195">W poniższym przykładzie użyto wzorca typu, aby zapewnić informacje o różnych typach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="eeb1f-196">Zamiast `object`, można zrobić metodę rodzajową, przy użyciu typu kolekcji jako parametr typu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="eeb1f-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="eeb1f-197">Wersja ogólna różni się od pierwszej próbki na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="eeb1f-198">Po pierwsze, nie można `null` użyć przypadku.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="eeb1f-199">Nie można użyć żadnego stałego przypadku, ponieważ kompilator `T` nie może `object`przekonwertować dowolnego typu na dowolny typ inny niż .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="eeb1f-200">Co było `default` w przypadku teraz testy `object`dla non-null .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="eeb1f-201">Oznacza to, `default` że `null`testy przypadku tylko dla .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="eeb1f-202">Bez dopasowywania wzorców ten kod może być zapisywany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="eeb1f-203">Użycie dopasowywania wzorca typu powoduje uzyskanie bardziej kompaktowego, czytelnego kodu, eliminując konieczność sprawdzenia, czy wynikiem konwersji jest `null` a lub wykonywanie powtarzających się rzutowania.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="eeb1f-204"><a name="when" />Oświadczenie `case` i `when` klauzula</span><span class="sxs-lookup"><span data-stu-id="eeb1f-204"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="eeb1f-205">Począwszy od języka C# 7.0, ponieważ case instrukcje `when` nie muszą być wzajemnie wykluczają się, można dodać klauzuli, aby określić dodatkowy warunek, który musi być spełniony dla case instrukcji do oceny true.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="eeb1f-206">Klauzula `when` może być dowolnym wyrażeniem, które zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="eeb1f-207">Poniższy przykład definiuje `Shape` klasę `Rectangle` podstawową, klasę, `Shape`która `Square` wywodzi `Rectangle`się z , i klasę, która pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="eeb1f-208">Używa klauzuli, `when` `ShowShapeInfo` aby upewnić się, że traktuje `Rectangle` obiekt, który został przypisany równe długości i szerokości jako `Square` `Square` nawet jeśli nie został sytuowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="eeb1f-209">Metoda nie próbuje wyświetlić informacji o obiekcie, `null` który jest lub kształt, którego obszar wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="eeb1f-210">Należy zauważyć, że klauzula `when` w przykładzie, który próbuje sprawdzić, czy `Shape` obiekt nie jest `null` wykonywany.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="eeb1f-211">Prawidłowy wzorzec typu `null` `case null:`do przetestowania dla a jest .</span><span class="sxs-lookup"><span data-stu-id="eeb1f-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eeb1f-212">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eeb1f-212">C# language specification</span></span>

<span data-ttu-id="eeb1f-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="eeb1f-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="eeb1f-214">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="eeb1f-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="eeb1f-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eeb1f-215">See also</span></span>

- [<span data-ttu-id="eeb1f-216">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="eeb1f-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eeb1f-217">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="eeb1f-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eeb1f-218">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="eeb1f-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eeb1f-219">if-else</span><span class="sxs-lookup"><span data-stu-id="eeb1f-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="eeb1f-220">Dopasowywanie wzoru</span><span class="sxs-lookup"><span data-stu-id="eeb1f-220">Pattern Matching</span></span>](../../pattern-matching.md)
