---
title: Instrukcja switch C#
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
ms.openlocfilehash: 5257d1d677246cdd6d826cd71ed3ffe116d2a4a6
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424124"
---
# <a name="switch-c-reference"></a><span data-ttu-id="50c72-102">Switch (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="50c72-102">switch (C# reference)</span></span>

<span data-ttu-id="50c72-103">`switch` jest instrukcją zaznaczenia, który wybiera jeden *Przełącz sekcję* do wykonania z listy kandydatów na podstawie dopasowania wzorca z *pasuje do wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="50c72-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="50c72-104">`switch` Instrukcji jest często używana jako alternatywa [if-else](if-else.md) konstruowania, jeśli pojedyncze wyrażenie jest testowany dla trzech lub więcej warunków.</span><span class="sxs-lookup"><span data-stu-id="50c72-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="50c72-105">Na przykład następująca `switch` Instrukcja określa, czy zmienna typu `Color` ma jedną z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="50c72-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="50c72-106">Jest to równoważne do poniższego przykładu, który używa `if` - `else` konstruowania.</span><span class="sxs-lookup"><span data-stu-id="50c72-106">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="50c72-107">Wyrażenie dopasowania</span><span class="sxs-lookup"><span data-stu-id="50c72-107">The match expression</span></span>

<span data-ttu-id="50c72-108">Wyrażenie dopasowania udostępnia wartość do dopasowywania wzorców w `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="50c72-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="50c72-109">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="50c72-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="50c72-110">W C# 6 i starszych wersjach, wyrażenie dopasowania musi być wyrażeniem, która zwraca wartość z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="50c72-110">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="50c72-111">[char](char.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-111">a [char](char.md).</span></span>
- <span data-ttu-id="50c72-112">[ciąg](string.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-112">a [string](string.md).</span></span>
- <span data-ttu-id="50c72-113">[bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="50c72-114">wartość całkowita, takich jak [int](../builtin-types/integral-numeric-types.md) lub [długie](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-114">an integral value, such as an [int](../builtin-types/integral-numeric-types.md) or a [long](../builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="50c72-115">[wyliczenia](enum.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="50c72-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="50c72-116">Wyrażenie dopasowania, począwszy od języka C# 7.0, może być dowolnym wyrażeniem inną niż null.</span><span class="sxs-lookup"><span data-stu-id="50c72-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="50c72-117">Sekcja przełącznika</span><span class="sxs-lookup"><span data-stu-id="50c72-117">The switch section</span></span>

<span data-ttu-id="50c72-118">A `switch` wyciąg zawiera jeden lub więcej sekcji przełączników.</span><span class="sxs-lookup"><span data-stu-id="50c72-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="50c72-119">Każda sekcja przełącznika zawiera jedną lub więcej *zamierzone, Zapisz etykiety* (etykieta case lub default) następuje jedna lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="50c72-120">`switch` Instrukcja może zawierać co najwyżej jedną etykietę domyślną umieszczone w żadnej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="50c72-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="50c72-121">W poniższym przykładzie przedstawiono prosty `switch` instrukcję, która zawiera trzy sekcje przełącznika, każdy z nich zawierający dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="50c72-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="50c72-122">Druga sekcja przełącznika zawiera `case 2:` i `case 3:` etykiety.</span><span class="sxs-lookup"><span data-stu-id="50c72-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="50c72-123">A `switch` instrukcji może zawierać dowolną liczbę sekcji przełącznika, a każda sekcja może mieć jedną lub więcej etykiet wielkości liter, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="50c72-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="50c72-124">Jednak żadne dwie etykiety mogą zawierać to samo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="50c72-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="50c72-125">Wykonuje sekcji tylko jednego przełącznika w instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="50c72-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="50c72-126">C#Nie zezwalaj na wykonywanie kontynuowało z jednej sekcji przełączania do następnej.</span><span class="sxs-lookup"><span data-stu-id="50c72-126">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="50c72-127">W związku z tym poniższy kod generuje błąd kompilatora CS0163: "Sterowanie nie może przechodzić od jednej etykiety case (\<etykietę" case ">) do innego."</span><span class="sxs-lookup"><span data-stu-id="50c72-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="50c72-128">Wymóg ten jest zazwyczaj spełniony przy jawnie zamykania sekcji przełącznika, za pomocą [podziału](break.md), [goto](goto.md), lub [zwracają](return.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="50c72-129">Jednak poniższy kod jest również ważne, ponieważ zapewnia, że formant programu nie może przechodzić do `default` Przełącz sekcję.</span><span class="sxs-lookup"><span data-stu-id="50c72-129">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="50c72-130">Wykonanie listy instrukcji w sekcji przełącznika, etykietę case, która odpowiada wyrażeniu dopasowanie rozpoczyna się od pierwszej instrukcji i przechodzi przez listę instrukcji, zwykle aż do instrukcja skoku, takiej jak `break`, `goto case`, `goto label`, `return`, lub `throw`, zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="50c72-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="50c72-131">W tym momencie przekazanie kontroli poza `switch` instrukcji lub do innej etykiety sprawy.</span><span class="sxs-lookup"><span data-stu-id="50c72-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="50c72-132">A `goto` instrukcji, jeśli jest on używany, musi kontrola jest przekazywana do stałej etykiety.</span><span class="sxs-lookup"><span data-stu-id="50c72-132">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="50c72-133">To ograniczenie jest konieczne, ponieważ próby kontrola jest przekazywana do etykiety niestałe może mieć niepożądane skutki uboczne, takie transferowanie formantu do niezamierzonych lokalizacji w kodzie lub tworzenie pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="50c72-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="50c72-134">Etykiety Case</span><span class="sxs-lookup"><span data-stu-id="50c72-134">Case labels</span></span>

<span data-ttu-id="50c72-135">Każda etykieta przypadku określa wzorzec do porównania z wyrażenia dopasowania ( `caseSwitch` zmiennej w poprzednich przykładach).</span><span class="sxs-lookup"><span data-stu-id="50c72-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="50c72-136">Jeśli są zgodne, kontrola jest przekazywana do sekcji przełącznika, który zawiera **pierwszy** odpowiadających im etykiet wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="50c72-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="50c72-137">Jeśli nie wzorzec etykietę "case" pasuje do wyrażenia dopasowania, kontrola jest przekazywana do sekcji z `default` etykiety case, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="50c72-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="50c72-138">W przypadku nie `default` przypadku żadnych deklaracji w żadnej sekcji przełącznika są wykonywane, a kontrola jest przekazywana poza `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-138">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="50c72-139">Instrukcje dotyczące `switch` instrukcji i dopasowywania do wzorca, zobacz [dopasowywania do wzorca z `switch` instrukcji](#pattern) sekcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="50c72-140">Ponieważ C# 6 obsługuje tylko stałe wzorzec i nie zezwala na powtórzenia wartości stałych, etykiet case zdefiniować wartości wzajemnie się wykluczają i tylko jeden wzorzec może być zgodna z wyrażeniem dopasowania.</span><span class="sxs-lookup"><span data-stu-id="50c72-140">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="50c72-141">W rezultacie, kolejność, w której `case` instrukcje są wyświetlane, nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="50c72-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="50c72-142">W języku C# 7.0, ponieważ inne wzorce są obsługiwane, etykiet case nie muszą definiować wartości wzajemnie się wykluczają i wielu wzorców może odnosić się wyrażenie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="50c72-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="50c72-143">Ponieważ wykonywane są tylko instrukcje w pierwszej sekcji przełącznika, który zawiera pasującego wzorca, kolejność, w której `case` instrukcje pojawiają się teraz jest ważne.</span><span class="sxs-lookup"><span data-stu-id="50c72-143">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="50c72-144">Jeśli C# wykryje sekcji przełącznika, których instrukcji case instrukcje są równoważne lub są podzbiorem poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadku switch została już obsłużona przez poprzednią etykietę case."</span><span class="sxs-lookup"><span data-stu-id="50c72-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="50c72-145">W poniższym przykładzie pokazano `switch` instrukcję, która korzysta z rozmaitych wzorców bez wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="50c72-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="50c72-146">Jeśli przeniesiesz `case 0:` Przełącz sekcję, tak aby nie jest już pierwszą sekcją `switch` instrukcji C# generuje błąd kompilatora, ponieważ liczbą całkowitą, którego wartość jest równa zero jest podzbiorem wszystkich liczb całkowitych, która jest wzorzec zdefiniowany przez `case int val` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-146">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="50c72-147">Można rozwiązać ten problem i wyeliminować ostrzeżenia kompilatora, w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="50c72-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="50c72-148">Zmieniając ich kolejność sekcji przełączników.</span><span class="sxs-lookup"><span data-stu-id="50c72-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="50c72-149">Za pomocą [po klauzuli](#when) w `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="50c72-149">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="50c72-150">`default` Case</span><span class="sxs-lookup"><span data-stu-id="50c72-150">The `default` case</span></span>

<span data-ttu-id="50c72-151">`default` Case określa sekcji przełącznika, do wykonania, jeśli wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="50c72-151">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="50c72-152">Jeśli `default` przypadek nie jest obecny i wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety, przepływem programu przypada za pośrednictwem `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-152">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="50c72-153">`default` Przypadków mogą być wyświetlane w dowolnej kolejności w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="50c72-154">Niezależnie od ich kolejność, w kodzie źródłowym, będzie zawsze oceniana, last, po wszystkich `case` etykiety zostały ocenione.</span><span class="sxs-lookup"><span data-stu-id="50c72-154">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="50c72-155"><a name="pattern" /> Za pomocą dopasowywania do wzorca `switch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="50c72-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="50c72-156">Każdy `case` instrukcja definiuje wzorzec pasujący wyrażenie dopasowania powoduje, że jego zawierającego sekcji przełącznika, do wykonania.</span><span class="sxs-lookup"><span data-stu-id="50c72-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="50c72-157">Wszystkie wersje języka C# obsługuje wzór stałej.</span><span class="sxs-lookup"><span data-stu-id="50c72-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="50c72-158">Pozostałe wzorce są obsługiwane, począwszy od języka C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="50c72-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="50c72-159">Wzór stałej</span><span class="sxs-lookup"><span data-stu-id="50c72-159">Constant pattern</span></span>

<span data-ttu-id="50c72-160">Wzór stałej sprawdza, czy wyrażenie dopasowania jest równa określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="50c72-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="50c72-161">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="50c72-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="50c72-162">gdzie *stałej* jest wartością do testowania.</span><span class="sxs-lookup"><span data-stu-id="50c72-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="50c72-163">*Stała* może być dowolną z następujących stałych wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="50c72-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="50c72-164">A [bool](bool.md) literału, albo `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="50c72-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="50c72-165">Dowolnego całkowitego stałych, takich jak [int](../builtin-types/integral-numeric-types.md), [długie](../builtin-types/integral-numeric-types.md), lub [bajt](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-165">Any integral constant, such as an [int](../builtin-types/integral-numeric-types.md), a [long](../builtin-types/integral-numeric-types.md), or a [byte](../builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="50c72-166">Nazwa deklarowanej `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50c72-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="50c72-167">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="50c72-167">An enumeration constant.</span></span>
- <span data-ttu-id="50c72-168">A [char](char.md) literału.</span><span class="sxs-lookup"><span data-stu-id="50c72-168">A [char](char.md) literal.</span></span>
- <span data-ttu-id="50c72-169">A [ciąg](string.md) literału.</span><span class="sxs-lookup"><span data-stu-id="50c72-169">A [string](string.md) literal.</span></span>

<span data-ttu-id="50c72-170">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="50c72-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="50c72-171">Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="50c72-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="50c72-172">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="50c72-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="50c72-173">W poniższym przykładzie użyto wzór stałej, aby ustalić, czy określoną datę w weekendy, pierwszego dnia tygodnia pracy, ostatni dzień tygodnia pracy lub w środku tygodnia pracy.</span><span class="sxs-lookup"><span data-stu-id="50c72-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="50c72-174">Powoduje ono obliczenie <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwości bieżącego dnia w odniesieniu do składowych aspektów <xref:System.DayOfWeek> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="50c72-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="50c72-175">W poniższym przykładzie użyto wzór stałej do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje maszyny do automatycznego kawy.</span><span class="sxs-lookup"><span data-stu-id="50c72-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="50c72-176">Wpisz wzór</span><span class="sxs-lookup"><span data-stu-id="50c72-176">Type pattern</span></span>

<span data-ttu-id="50c72-177">Wpisz wzór umożliwia ocenę zwięzły typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="50c72-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="50c72-178">Gdy jest używane z `switch` instrukcję do realizacji dopasowania do wzorca, jego testuje, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="50c72-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="50c72-179">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="50c72-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="50c72-180">gdzie *typu* jest nazwą typu, do której wynik *expr* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr*jest konwertowany, jeśli dopasowanie się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="50c72-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="50c72-181">Typ kompilacji *expr* może być parametrem typu ogólnego, począwszy od C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="50c72-181">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="50c72-182">`case` Wyrażenie jest `true` jeśli spełniony jest dowolny z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="50c72-182">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="50c72-183">*wyrażenie* to wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="50c72-183">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="50c72-184">*wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*.</span><span class="sxs-lookup"><span data-stu-id="50c72-184">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="50c72-185">Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.</span><span class="sxs-lookup"><span data-stu-id="50c72-185">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="50c72-186">*wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*.</span><span class="sxs-lookup"><span data-stu-id="50c72-186">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="50c72-187">*Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="50c72-187">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="50c72-188">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50c72-188">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="50c72-189">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="50c72-189">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="50c72-190">Jeśli wyrażenie case ma wartość true, *nazwa_zmiennej* jest zdecydowanie przypisana, a ma zakres lokalny w ramach tej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="50c72-190">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="50c72-191">Należy pamiętać, że `null` nie jest zgodny z typem.</span><span class="sxs-lookup"><span data-stu-id="50c72-191">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="50c72-192">Aby dopasować `null`, użyj następującego `case` etykiety:</span><span class="sxs-lookup"><span data-stu-id="50c72-192">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="50c72-193">W poniższym przykładzie użyto wzorca typu, aby podać informacje o różnych rodzajów typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="50c72-193">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="50c72-194">Zamiast `object`, można utworzyć metody ogólnej przy użyciu typu kolekcji jako parametr typu, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="50c72-194">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="50c72-195">Ogólny wersja jest inna niż pierwszy przykład na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="50c72-195">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="50c72-196">Po pierwsze, nie można użyć `null` przypadek.</span><span class="sxs-lookup"><span data-stu-id="50c72-196">First, you can't use the `null` case.</span></span> <span data-ttu-id="50c72-197">Nie można używać każdy przypadek, stałe, ponieważ kompilator nie może przekonwertować dowolny typ dowolnego `T` do dowolnego typu innego niż `object`.</span><span class="sxs-lookup"><span data-stu-id="50c72-197">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="50c72-198">Był `default` zamierzone, Zapisz teraz testy dla innych niż null `object`.</span><span class="sxs-lookup"><span data-stu-id="50c72-198">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="50c72-199">Oznacza to, że `default` zamierzone, Zapisz testy tylko w przypadku `null`.</span><span class="sxs-lookup"><span data-stu-id="50c72-199">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="50c72-200">Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="50c72-200">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="50c72-201">Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null` lub do wykonywania powtarzających rzutowania.</span><span class="sxs-lookup"><span data-stu-id="50c72-201">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="50c72-202"><a name="when" /> `case` Instrukcji i `when` — klauzula</span><span class="sxs-lookup"><span data-stu-id="50c72-202"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="50c72-203">Uruchamianie przy użyciu języka C# 7.0, ponieważ instrukcji case nie muszą być wzajemnie się wykluczają, możesz dodać `when` klauzulę, aby określić dodatkowy warunek muszą być spełnione dla instrukcji case na wartość true.</span><span class="sxs-lookup"><span data-stu-id="50c72-203">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="50c72-204">`when` Klauzuli może być dowolne wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="50c72-204">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="50c72-205">W poniższym przykładzie zdefiniowano podstawowej `Shape` klasy `Rectangle` klasę pochodzącą od `Shape`, a `Square` klasę pochodzącą od `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="50c72-205">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="50c72-206">Używa ona `when` klauzuli, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, który został przypisany równy długości i szerokości jako `Square` nawet wtedy, gdy nie został uruchomiony jako `Square` obiektu.</span><span class="sxs-lookup"><span data-stu-id="50c72-206">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="50c72-207">Metoda nie próbuje wyświetlać informacje o obiekt, który jest `null` lub kształtu, w których obszar jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="50c72-207">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="50c72-208">Należy pamiętać, że `when` klauzuli w przykładzie, który próbuje testów czy `Shape` obiekt jest `null` nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="50c72-208">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="50c72-209">Wzorzec poprawnego typu do testowania `null` jest `case null:`.</span><span class="sxs-lookup"><span data-stu-id="50c72-209">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="50c72-210">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="50c72-210">C# language specification</span></span>

<span data-ttu-id="50c72-211">Aby uzyskać więcej informacji, zobacz [instrukcji switch](~/_csharplang/spec/statements.md#the-switch-statement) w [specyfikacji języka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="50c72-211">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="50c72-212">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="50c72-212">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="50c72-213">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50c72-213">See also</span></span>

- [<span data-ttu-id="50c72-214">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="50c72-214">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50c72-215">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50c72-215">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50c72-216">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="50c72-216">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50c72-217">if-else</span><span class="sxs-lookup"><span data-stu-id="50c72-217">if-else</span></span>](if-else.md)
- [<span data-ttu-id="50c72-218">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="50c72-218">Pattern Matching</span></span>](../../pattern-matching.md)
