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
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345395"
---
# <a name="switch-c-reference"></a><span data-ttu-id="99c71-102">przełącznik (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="99c71-102">switch (C# reference)</span></span>

<span data-ttu-id="99c71-103">`switch`jest instrukcją wyboru, która wybiera *pojedynczą sekcję przełącznika* do wykonania z listy kandydatów na podstawie dopasowania wzorca do *wyrażenia dopasowania*.</span><span class="sxs-lookup"><span data-stu-id="99c71-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="99c71-104">Instrukcja `switch` jest często używana jako alternatywa dla konstrukcji [if-else,](if-else.md) jeśli pojedyncze wyrażenie jest testowane na trzy lub więcej warunków.</span><span class="sxs-lookup"><span data-stu-id="99c71-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="99c71-105">Na przykład następująca `switch` instrukcja określa, `Color` czy zmienna typu ma jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="99c71-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="99c71-106">Jest to odpowiednik następującego przykładu, `if` - `else` który używa konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="99c71-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="99c71-107">Wyrażenie dopasowania</span><span class="sxs-lookup"><span data-stu-id="99c71-107">The match expression</span></span>

<span data-ttu-id="99c71-108">Wyrażenie dopasowania zapewnia wartość, aby dopasować `case` do wzorców w etykietach.</span><span class="sxs-lookup"><span data-stu-id="99c71-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="99c71-109">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="99c71-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="99c71-110">W języku C# 6 i starszym wyrażenie dopasowania musi być wyrażeniem zwracającym wartość następujących typów:</span><span class="sxs-lookup"><span data-stu-id="99c71-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="99c71-111">[char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="99c71-111">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="99c71-112">[ciąg .](../builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="99c71-112">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="99c71-113">[bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="99c71-113">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="99c71-114">wartości [integralnej,](../builtin-types/integral-numeric-types.md) takiej `int` jak `long`wartość lub .</span><span class="sxs-lookup"><span data-stu-id="99c71-114">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="99c71-115">wartości [wyliczenia.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="99c71-115">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="99c71-116">Począwszy od Języka C# 7.0 wyrażenie dopasowania może być dowolne wyrażenie inne niż null.</span><span class="sxs-lookup"><span data-stu-id="99c71-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="99c71-117">Sekcja przełącznika</span><span class="sxs-lookup"><span data-stu-id="99c71-117">The switch section</span></span>

<span data-ttu-id="99c71-118">Instrukcja `switch` zawiera jedną lub więcej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="99c71-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="99c71-119">Każda sekcja przełącznika zawiera jedną lub więcej *etykiet sprawy* (case lub etykietę domyślną), po której następuje jedna lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="99c71-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="99c71-120">Instrukcja `switch` może zawierać co najwyżej jedną domyślną etykietę umieszczoną w dowolnej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="99c71-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="99c71-121">W poniższym przykładzie `switch` przedstawiono prostą instrukcję, która ma trzy sekcje przełącznika, z których każda zawiera dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="99c71-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="99c71-122">Druga sekcja przełącznika `case 2:` `case 3:` zawiera etykiety i etykiety.</span><span class="sxs-lookup"><span data-stu-id="99c71-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="99c71-123">Instrukcja `switch` może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet sprawy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="99c71-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="99c71-124">Jednak nie dwie etykiety przypadku może zawierać to samo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="99c71-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="99c71-125">Wykonuje się tylko jedną sekcję przełącznika w instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="99c71-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="99c71-126">C# nie zezwala na wykonywanie kontynuować z jednej sekcji przełącznika do następnego.</span><span class="sxs-lookup"><span data-stu-id="99c71-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="99c71-127">Z tego powodu następujący kod generuje błąd kompilatora, CS0163: "Kontrola\<nie może przechodzić z jednej etykiety przypadku (etykieta przypadku>) do innego."</span><span class="sxs-lookup"><span data-stu-id="99c71-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="99c71-128">Wymóg ten jest zwykle spełniony przez jawne zamknięcie sekcji przełącznika za pomocą [instrukcji break,](break.md) [goto](goto.md)lub [return.](return.md)</span><span class="sxs-lookup"><span data-stu-id="99c71-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="99c71-129">Jednak poniższy kod jest również prawidłowy, ponieważ zapewnia, że kontrola `default` programu nie może przechodzić do sekcji przełączania.</span><span class="sxs-lookup"><span data-stu-id="99c71-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="99c71-130">Wykonanie listy instrukcji w sekcji przełącznika z etykietą przypadku, która pasuje do wyrażenia dopasowania, rozpoczyna się od pierwszej `break`instrukcji `goto case` `goto label`i `return`przechodzi `throw`przez listę instrukcji, zazwyczaj do momentu osiągnięcia instrukcji skoku, takiej jak , , , , lub , .</span><span class="sxs-lookup"><span data-stu-id="99c71-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="99c71-131">W tym momencie kontrola jest `switch` przekazywana poza instrukcję lub do innej etykiety sprawy.</span><span class="sxs-lookup"><span data-stu-id="99c71-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="99c71-132">Instrukcja, `goto` jeśli jest używana, musi przenieść kontrolę do stałej etykiety.</span><span class="sxs-lookup"><span data-stu-id="99c71-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="99c71-133">To ograniczenie jest konieczne, ponieważ próba przeniesienia kontroli do etykiety niestałej może mieć niepożądane skutki uboczne, takie przeniesienie kontroli do niezamierzonej lokalizacji w kodzie lub tworzenie nieskończonej pętli.</span><span class="sxs-lookup"><span data-stu-id="99c71-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="99c71-134">Etykiety obudowy</span><span class="sxs-lookup"><span data-stu-id="99c71-134">Case labels</span></span>

<span data-ttu-id="99c71-135">Każda etykieta przypadku określa wzorzec do `caseSwitch` porównania z wyrażeniem dopasowania (zmienna w poprzednich przykładach).</span><span class="sxs-lookup"><span data-stu-id="99c71-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="99c71-136">Jeśli są one zgodne, formant jest przenoszony do sekcji przełącznika, który zawiera **pierwszą** etykietę pasującego przypadku.</span><span class="sxs-lookup"><span data-stu-id="99c71-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="99c71-137">Jeśli żaden wzorzec etykiety przypadku nie pasuje do `default` wyrażenia dopasowania, formant jest przenoszony do sekcji z etykietą sprawy, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="99c71-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="99c71-138">Jeśli nie ma `default` przypadku, żadne instrukcje w sekcji przełącznika są wykonywane, a kontrola jest przekazywana poza instrukcję. `switch`</span><span class="sxs-lookup"><span data-stu-id="99c71-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="99c71-139">Aby uzyskać `switch` informacje na temat dopasowania instrukcji i wzorca, zobacz [pattern dopasowania do `switch` instrukcji](#pattern) sekcji.</span><span class="sxs-lookup"><span data-stu-id="99c71-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="99c71-140">Ponieważ C# 6 obsługuje tylko wzorzec stały i nie zezwala na powtarzanie wartości stałych, etykiety przypadków definiują wzajemnie wykluczające się wartości i tylko jeden wzorzec może odpowiadać wyrażeniu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="99c71-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="99c71-141">W rezultacie kolejność, `case` w jakiej pojawiają się instrukcje, jest nieistotna.</span><span class="sxs-lookup"><span data-stu-id="99c71-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="99c71-142">W języku C# 7.0, jednak ponieważ inne wzorce są obsługiwane, etykiety przypadków nie muszą definiować wzajemnie wykluczające się wartości i wiele wzorców można dopasować wyrażenie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="99c71-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="99c71-143">Ponieważ wykonywane są tylko instrukcje w pierwszej sekcji przełącznika, `case` która zawiera pasujący wzorzec, kolejność, w jakiej pojawiają się instrukcje, jest teraz ważna.</span><span class="sxs-lookup"><span data-stu-id="99c71-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="99c71-144">Jeśli C# wykryje sekcję przełączania, której instrukcje case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "Sprawa przełącznika została już obsłużena przez poprzedni przypadek."</span><span class="sxs-lookup"><span data-stu-id="99c71-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="99c71-145">W poniższym przykładzie `switch` przedstawiono instrukcję, która używa różnych wzorców nie wykluczasię wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="99c71-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="99c71-146">Jeśli `case 0:` przesuniesz sekcję przełącznika tak, aby nie `switch` była już pierwszą sekcją w instrukcji, C# generuje błąd kompilatora, ponieważ liczba całkowita, `case int val` której wartość wynosi zero, jest podzbiorem wszystkich liczb całkowitych, który jest wzorcem zdefiniowanym przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="99c71-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="99c71-147">Ten problem można rozwiązać i wyeliminować ostrzeżenie kompilatora na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="99c71-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="99c71-148">Zmieniając kolejność sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="99c71-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="99c71-149">Za pomocą [when klauzuli](#when) w etykiecie. `case`</span><span class="sxs-lookup"><span data-stu-id="99c71-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="99c71-150">Sprawa `default`</span><span class="sxs-lookup"><span data-stu-id="99c71-150">The `default` case</span></span>

<span data-ttu-id="99c71-151">Przypadek `default` określa sekcję switch do wykonania, jeśli wyrażenie dopasowania `case` nie pasuje do żadnej innej etykiety.</span><span class="sxs-lookup"><span data-stu-id="99c71-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="99c71-152">Jeśli `default` sprawa nie jest obecna, a wyrażenie dopasowania `case` nie pasuje do `switch` żadnej innej etykiety, przepływ programu przechodzi przez instrukcję.</span><span class="sxs-lookup"><span data-stu-id="99c71-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="99c71-153">Sprawa `default` może pojawić się w `switch` dowolnej kolejności w oświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="99c71-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="99c71-154">Niezależnie od jego kolejności w kodzie źródłowym, zawsze jest `case` oceniana jako ostatnia, po ocenie wszystkich etykiet.</span><span class="sxs-lookup"><span data-stu-id="99c71-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="99c71-155"><a name="pattern" />Dopasowanie wzorca `switch` do instrukcji</span><span class="sxs-lookup"><span data-stu-id="99c71-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="99c71-156">Każda `case` instrukcja definiuje wzorzec, który, jeśli pasuje do wyrażenia dopasowania, powoduje, że jego sekcja przełącznika zawierające do wykonania.</span><span class="sxs-lookup"><span data-stu-id="99c71-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="99c71-157">Wszystkie wersje języka C# obsługują wzorzec stały.</span><span class="sxs-lookup"><span data-stu-id="99c71-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="99c71-158">Pozostałe wzorce są obsługiwane począwszy od języka C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="99c71-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="99c71-159">Stały wzór</span><span class="sxs-lookup"><span data-stu-id="99c71-159">Constant pattern</span></span>

<span data-ttu-id="99c71-160">Wzorzec stały sprawdza, czy wyrażenie dopasowania jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="99c71-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="99c71-161">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="99c71-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="99c71-162">gdzie *stała* jest wartością do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="99c71-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="99c71-163">*stała* może być dowolne z następujących wyrażeń stałych:</span><span class="sxs-lookup"><span data-stu-id="99c71-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="99c71-164">[Bool](../builtin-types/bool.md) dosłowny: albo `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="99c71-164">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="99c71-165">Każda [stała integralna,](../builtin-types/integral-numeric-types.md) `int`taka `long`jak `byte`, a , lub .</span><span class="sxs-lookup"><span data-stu-id="99c71-165">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="99c71-166">Nazwa zadeklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99c71-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="99c71-167">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="99c71-167">An enumeration constant.</span></span>
- <span data-ttu-id="99c71-168">[Char](../builtin-types/char.md) dosłowne.</span><span class="sxs-lookup"><span data-stu-id="99c71-168">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="99c71-169">Literał [ciągu.](../builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="99c71-169">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="99c71-170">Wyrażenie stałe jest oceniane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="99c71-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="99c71-171">Jeśli *expr* i *stała* są typami integralnymi, operator `true` równości Języka C# określa, czy wyrażenie zwraca (czyli czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="99c71-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="99c71-172">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [Object.Equals(expr, stała)](xref:System.Object.Equals(System.Object,System.Object)) metoda.</span><span class="sxs-lookup"><span data-stu-id="99c71-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="99c71-173">W poniższym przykładzie użyto stałego wzorca, aby określić, czy dana data jest weekendem, pierwszym dniem tygodnia roboczego, ostatnim dniem tygodnia roboczego lub środkiem tygodnia roboczego.</span><span class="sxs-lookup"><span data-stu-id="99c71-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="99c71-174">Oblicza <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwość bieżącego dnia względem członków wyliczenia. <xref:System.DayOfWeek></span><span class="sxs-lookup"><span data-stu-id="99c71-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="99c71-175">W poniższym przykładzie użyto stałego wzorca do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje automatyczny ekspres do kawy.</span><span class="sxs-lookup"><span data-stu-id="99c71-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="99c71-176">Wzorzec tekstu</span><span class="sxs-lookup"><span data-stu-id="99c71-176">Type pattern</span></span>

<span data-ttu-id="99c71-177">Wzorzec typu umożliwia zwięzłe oceny typu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="99c71-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="99c71-178">W przypadku `switch` użycia z instrukcją do wykonywania dopasowania wzorca, sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może być, rzutuje go do zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="99c71-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="99c71-179">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="99c71-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="99c71-180">gdzie *typ* jest nazwą typu, na który wynik *expr* ma zostać przekonwertowany, a *varname* jest obiektem, na który jest konwertowany wynik *expr,* jeśli dopasowanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="99c71-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="99c71-181">Typ czasu kompilacji *expr* może być parametrtypu ogólnego, począwszy od C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="99c71-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="99c71-182">Wyrażenie `case` jest, `true` jeśli którakolwiek z następujących wartości jest true:</span><span class="sxs-lookup"><span data-stu-id="99c71-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="99c71-183">*expr* jest wystąpieniem tego samego typu co *typ*.</span><span class="sxs-lookup"><span data-stu-id="99c71-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="99c71-184">*expr* jest wystąpieniem typu, który pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="99c71-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="99c71-185">Innymi słowy wynik *expr* może być rzutnie na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="99c71-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="99c71-186">*expr* ma typ kompilacji w czasie, który jest klasą podstawową *typu*, a *expr* ma typ czasu wykonywania, który jest *typem* lub pochodzi od *typu*.</span><span class="sxs-lookup"><span data-stu-id="99c71-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="99c71-187">*Typ czasu kompilacji* zmiennej jest typem zmiennej zdefiniowanym w deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="99c71-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="99c71-188">*Typ czasu wykonywania* zmiennej jest typem wystąpienia przypisanego do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99c71-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="99c71-189">*expr* jest wystąpieniem typu, który implementuje interfejs *typu.*</span><span class="sxs-lookup"><span data-stu-id="99c71-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="99c71-190">Jeśli wyrażenie sprawy jest prawdziwe, *varname* jest zdecydowanie przypisany i ma zakres lokalny tylko w sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="99c71-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="99c71-191">Pamiętaj, `null` że nie pasuje do typu.</span><span class="sxs-lookup"><span data-stu-id="99c71-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="99c71-192">Aby dopasować `null`, należy `case` użyć następującej etykiety:</span><span class="sxs-lookup"><span data-stu-id="99c71-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="99c71-193">W poniższym przykładzie użyto wzorca typu, aby zapewnić informacje o różnych typach typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="99c71-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="99c71-194">Zamiast `object`, można zrobić metodę rodzajową, przy użyciu typu kolekcji jako parametr typu, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="99c71-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="99c71-195">Wersja ogólna różni się od pierwszej próbki na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="99c71-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="99c71-196">Po pierwsze, nie można `null` użyć sprawy.</span><span class="sxs-lookup"><span data-stu-id="99c71-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="99c71-197">Nie można użyć żadnej stałej sprawy, ponieważ kompilator `T` nie może `object`przekonwertować dowolnego typu na dowolny typ inny niż .</span><span class="sxs-lookup"><span data-stu-id="99c71-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="99c71-198">Co było `default` w przypadku teraz testy `object`dla non-null .</span><span class="sxs-lookup"><span data-stu-id="99c71-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="99c71-199">Oznacza to, że `default` `null`testy przypadku tylko dla .</span><span class="sxs-lookup"><span data-stu-id="99c71-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="99c71-200">Bez dopasowywania wzorców ten kod może być napisany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="99c71-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="99c71-201">Użycie dopasowania wzorca typu tworzy bardziej kompaktowy, czytelny kod, eliminując konieczność `null` testowania, czy wynik konwersji jest lub do wykonywania wielokrotnych rzutowania.</span><span class="sxs-lookup"><span data-stu-id="99c71-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="99c71-202"><a name="when" />Oświadczenie `case` i `when` klauzula</span><span class="sxs-lookup"><span data-stu-id="99c71-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="99c71-203">Począwszy od języka C# 7.0, ponieważ instrukcje case nie `when` muszą się wzajemnie wykluczać, można dodać klauzulę, aby określić dodatkowy warunek, który musi być spełniony dla instrukcji case, aby ocenić wartość true.</span><span class="sxs-lookup"><span data-stu-id="99c71-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="99c71-204">Klauzula `when` może być dowolne wyrażenie, które zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="99c71-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="99c71-205">Poniższy przykład definiuje klasę `Shape` podstawową, `Rectangle` klasę, `Shape`która pochodzi `Square` z , `Rectangle`i klasy, która pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="99c71-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="99c71-206">Używa `when` klauzuli, aby `ShowShapeInfo` upewnić się, że traktuje `Rectangle` obiekt, który został przypisany równe długości i szerokości jako `Square` `Square` nawet jeśli nie został utworzyony jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="99c71-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="99c71-207">Metoda nie próbuje wyświetlić informacji o obiekcie, `null` który jest lub kształt, którego obszar wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="99c71-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="99c71-208">Należy zauważyć, że klauzula `when` w przykładzie, który próbuje sprawdzić, `Shape` czy obiekt nie jest `null` wykonywany.</span><span class="sxs-lookup"><span data-stu-id="99c71-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="99c71-209">Prawidłowy wzorzec `null` typu `case null:`do testowania dla a jest .</span><span class="sxs-lookup"><span data-stu-id="99c71-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="99c71-210">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99c71-210">C# language specification</span></span>

<span data-ttu-id="99c71-211">Aby uzyskać więcej informacji, zobacz [Switch instrukcji](~/_csharplang/spec/statements.md#the-switch-statement) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="99c71-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="99c71-212">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="99c71-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="99c71-213">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99c71-213">See also</span></span>

- [<span data-ttu-id="99c71-214">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="99c71-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99c71-215">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="99c71-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="99c71-216">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="99c71-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="99c71-217">if-else</span><span class="sxs-lookup"><span data-stu-id="99c71-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="99c71-218">Dopasowywanie wzorców</span><span class="sxs-lookup"><span data-stu-id="99c71-218">Pattern Matching</span></span>](../../pattern-matching.md)
