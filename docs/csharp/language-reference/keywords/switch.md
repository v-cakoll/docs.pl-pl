---
title: Switch — słowo kluczowe (odwołanie w C#)
ms.date: 03/07/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 47
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6506278edb782f61b83cecfccba3126282c0ecf8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="switch-c-reference"></a><span data-ttu-id="a7c45-102">switch (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a7c45-102">switch (C# Reference)</span></span>
<span data-ttu-id="a7c45-103">`switch` jest instrukcja wyboru, która wybiera jeden *przełącznika sekcji* do wykonania z listy kandydatów na podstawie dopasowania wzorca z *pasuje do wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="a7c45-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 [!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

<span data-ttu-id="a7c45-104">`switch` Instrukcji jest często używana jako alternatywę [if-else](if-else.md) utworzenia, jeśli jedno wyrażenie jest testowana co najmniej trzy warunki.</span><span class="sxs-lookup"><span data-stu-id="a7c45-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="a7c45-105">Na przykład następująca `switch` instrukcji określa, czy zmienna typu `Color` ma jeden z trzech wartości:</span><span class="sxs-lookup"><span data-stu-id="a7c45-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

<span data-ttu-id="a7c45-106">Jest to równoważne do poniższego przykładu, która używa `if` - `else` utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a7c45-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a><span data-ttu-id="a7c45-107">Wyrażenie dopasowania</span><span class="sxs-lookup"><span data-stu-id="a7c45-107">The match expression</span></span>

<span data-ttu-id="a7c45-108">Wyrażenie dopasowania zawiera wartość do dopasowania do wzorców w `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="a7c45-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="a7c45-109">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="a7c45-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="a7c45-110">W języku C# 6 wyrażenie dopasowania musi być wyrażenie zwracające wartości z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="a7c45-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="a7c45-111">[char](char.md).</span><span class="sxs-lookup"><span data-stu-id="a7c45-111">a [char](char.md).</span></span>
- <span data-ttu-id="a7c45-112">[ciąg](string.md).</span><span class="sxs-lookup"><span data-stu-id="a7c45-112">a [string](string.md).</span></span>
- <span data-ttu-id="a7c45-113">[bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="a7c45-113">a [bool](bool.md).</span></span> 
- <span data-ttu-id="a7c45-114">wartość typem całkowitym, takich jak [int](int.md) lub [długi](long.md).</span><span class="sxs-lookup"><span data-stu-id="a7c45-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="a7c45-115">[wyliczenia](enum.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="a7c45-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="a7c45-116">Począwszy od wersji 7.0 C#, wyrażenie dopasowania może być dowolne wyrażenie inne niż null.</span><span class="sxs-lookup"><span data-stu-id="a7c45-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="a7c45-117">W sekcji przełącznika</span><span class="sxs-lookup"><span data-stu-id="a7c45-117">The switch section</span></span>
 
 <span data-ttu-id="a7c45-118">A `switch` instrukcja zawiera co najmniej jednej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="a7c45-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="a7c45-119">Każda sekcja przełącznika zawiera jeden lub więcej *etykiety case* następuje jeden lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-119">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="a7c45-120">W poniższym przykładzie przedstawiono prosty `switch` instrukcji, która zawiera trzy sekcje przełącznika.</span><span class="sxs-lookup"><span data-stu-id="a7c45-120">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="a7c45-121">Każda sekcja przełącznika ma jednej etykiety case, takich jak `case 1:`, a dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="a7c45-121">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="a7c45-122">A `switch` instrukcja może zawierać dowolną liczbę sekcjach przełącznik, a każda sekcja może mieć co najmniej jeden etykiety case, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a7c45-122">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="a7c45-123">Jednak dwie etykiety case nie może zawierać jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a7c45-123">However, no two case labels may contain the same expression.</span></span>  

 [!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 <span data-ttu-id="a7c45-124">Wykonuje sekcji tylko jednego przełącznika w instrukcji switch.</span><span class="sxs-lookup"><span data-stu-id="a7c45-124">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="a7c45-125">C# nie zezwala na kontynuację z jednej sekcji przełącznika do następnego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a7c45-125">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="a7c45-126">W związku z tym następujący kod generuje błąd kompilatora CS0163: "Sterowanie nie może przechodzić od jednej etykiety case (<case label>) do innej."</span><span class="sxs-lookup"><span data-stu-id="a7c45-126">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>  

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
<span data-ttu-id="a7c45-127">To wymaganie można spełnić zwykle przez jawnie Kończenie sekcji przełącznika za pomocą [podziału](break.md), [goto](goto.md), lub [zwracać](return.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-127">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="a7c45-128">Poniższy kod jest jednak również nieprawidłowe, ponieważ gwarantuje, że formant programu nie może przechodzić do `default` przełącznika sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-128">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 [!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 <span data-ttu-id="a7c45-129">Wykonanie na liście instrukcji w sekcji przełącznika wielkości etykietą, która odpowiada wyrażeniu dopasowania rozpoczyna się od pierwszej instrukcji i obejmującego na liście instrukcji zwykle do instrukcji szybkiego dostępu, takich jak `break`, `goto case`, `goto label`, `return`, lub `throw`, który limit zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="a7c45-129">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="a7c45-130">W tym momencie sterowania są przesyłane poza `switch` instrukcji lub innej etykiety case.</span><span class="sxs-lookup"><span data-stu-id="a7c45-130">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="a7c45-131">A `goto` instrukcji, jeśli jest on używany, należy przenieść formant do stałej etykiety.</span><span class="sxs-lookup"><span data-stu-id="a7c45-131">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="a7c45-132">To ograniczenie jest konieczne, ponieważ próby przekazywania kontroli z etykietą niestałe może mieć niepożądane skutki uboczne, takie transferowanie formantu do niezamierzone lokalizacji w kodzie lub tworzenia pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="a7c45-132">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="a7c45-133">Etykiety Case</span><span class="sxs-lookup"><span data-stu-id="a7c45-133">Case labels</span></span>

 <span data-ttu-id="a7c45-134">Każda etykieta case Określa wzorzec do porównania wyrażenie dopasowania ( `caseSwitch` zmiennej w poprzednich przykładach).</span><span class="sxs-lookup"><span data-stu-id="a7c45-134">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="a7c45-135">Jeśli są zgodne, sterowanie jest przekazywane do sekcji przełącznika, który zawiera **pierwszy** pasującego etykiety case.</span><span class="sxs-lookup"><span data-stu-id="a7c45-135">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="a7c45-136">Jeśli nie etykiety case wzorzec jest zgodny z wyrażeniem dopasowania, formantu zostanie przeniesiony do sekcji o `default` etykiety case, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="a7c45-136">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="a7c45-137">W przypadku nie `default` przypadku żadnych instrukcji w żadnej sekcji przełącznika są wykonywane i sterowania są przesyłane poza `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-137">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="a7c45-138">Aby uzyskać informacje dotyczące `switch` instrukcji i dopasowywanie do wzorców, zobacz [dopasowywanie do wzorca za `switch` instrukcji](#pattern) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-138">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="a7c45-139">C# 6 obsługuje tylko stałe wzorzec i nie zezwala na powtarzanie stałe wartości, dlatego etykiety case zdefiniować wartości wykluczają się wzajemnie, a tylko jeden wzorzec może dopasować wyrażenie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a7c45-139">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="a7c45-140">W rezultacie, w kolejności `case` instrukcje wyświetlane jest bez znaczenia.</span><span class="sxs-lookup"><span data-stu-id="a7c45-140">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="a7c45-141">W języku C# w wersji 7.0 jednak ponieważ inne wzorce są obsługiwane, etykiety case nie należy definiować wartości wykluczają się wzajemnie, a wielu wzorców może dopasować wyrażenie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a7c45-141">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="a7c45-142">Ponieważ są wykonywane tylko instrukcji w sekcji przełącznika, który zawiera pierwszy pasujący wzorzec, w kolejności `case` instrukcje pojawiają się teraz jest ważne.</span><span class="sxs-lookup"><span data-stu-id="a7c45-142">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="a7c45-143">Jeśli C# wykryje sekcji przełącznika, których instrukcji case lub instrukcje są równoważne lub są podzbiorami poprzednich instrukcji, generuje błąd kompilatora, CS8120, "przypadek switch już został obsłużony w przypadku poprzednich."</span><span class="sxs-lookup"><span data-stu-id="a7c45-143">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="a7c45-144">Poniższy przykład przedstawia `switch` instrukcji, która korzysta z różnych wzorców nie wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a7c45-144">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="a7c45-145">Jeśli przeniesiesz `case 0:` przełącznika sekcji, dzięki czemu nie jest już w pierwszej sekcji `switch` instrukcji, C# generuje błąd kompilatora, ponieważ całkowitą, którego wartość wynosi zero jest podzbiorem wszystkich liczb całkowitych, czyli wzorcowi określonemu przez `case int val` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-145">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 [!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

<span data-ttu-id="a7c45-146">Można rozwiązać ten problem i wyeliminować ostrzeżenia kompilatora w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="a7c45-146">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="a7c45-147">Zmieniając kolejność sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="a7c45-147">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="a7c45-148">Przy użyciu < /a name = "kiedy" > po klauzuli</a> w `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="a7c45-148">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="a7c45-149">`default` Case</span><span class="sxs-lookup"><span data-stu-id="a7c45-149">The `default` case</span></span>

<span data-ttu-id="a7c45-150">`default` Case określa sekcji przełącznika do wykonania, jeśli wyrażenie dopasowania nie jest zgodna z wszystkimi innymi `case` etykiety.</span><span class="sxs-lookup"><span data-stu-id="a7c45-150">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="a7c45-151">Jeśli `default` case nie jest obecny i wyrażenie dopasowania nie odpowiada żadnej innej `case` etykiety, przepływem programu znajduje się za pośrednictwem `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-151">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="a7c45-152">`default` Przypadku mogą być wyświetlane w dowolnej kolejności w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-152">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="a7c45-153">Niezależnie od ich kolejność w kodzie źródłowym jest zawsze Szacowana ostatnio, po wszystkich `case` zostały ocenione etykiety.</span><span class="sxs-lookup"><span data-stu-id="a7c45-153">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="a7c45-154"><a name="pattern" /> Dopasowywanie do wzorca za `switch` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a7c45-154"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="a7c45-155">Każdy `case` instrukcji definiuje wzorzec powodujący, jeśli jest on zgodny wyrażenie dopasowania zawierającego sekcji przełącznika do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7c45-155">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="a7c45-156">Wszystkie wersje języka C# obsługuje stałe wzorzec.</span><span class="sxs-lookup"><span data-stu-id="a7c45-156">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="a7c45-157">Pozostałe wzorce są obsługiwane począwszy od wersji 7.0 C#.</span><span class="sxs-lookup"><span data-stu-id="a7c45-157">The remaining patterns are supported beginning with C# 7.0.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="a7c45-158">Stałe wzorzec</span><span class="sxs-lookup"><span data-stu-id="a7c45-158">Constant pattern</span></span> 

<span data-ttu-id="a7c45-159">Stałe wzorzec sprawdza, czy wyrażenie dopasowania jest równe określonej stałej.</span><span class="sxs-lookup"><span data-stu-id="a7c45-159">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="a7c45-160">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="a7c45-160">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="a7c45-161">gdzie *stałej* jest wartość do testowania.</span><span class="sxs-lookup"><span data-stu-id="a7c45-161">where *constant* is the value to test for.</span></span> <span data-ttu-id="a7c45-162">*Stała* może być dowolny z następujących wyrażenia stałe:</span><span class="sxs-lookup"><span data-stu-id="a7c45-162">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="a7c45-163">A [bool](bool.md) literału, albo `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="a7c45-163">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="a7c45-164">Wszystkie typy całkowite stałej, takich jak [int](int.md), [długi](long.md), lub [bajtów](byte.md).</span><span class="sxs-lookup"><span data-stu-id="a7c45-164">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="a7c45-165">Nazwy deklarowanych `const` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a7c45-165">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="a7c45-166">Stała wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7c45-166">An enumeration constant.</span></span>
- <span data-ttu-id="a7c45-167">A [char](char.md) literału.</span><span class="sxs-lookup"><span data-stu-id="a7c45-167">A [char](char.md) literal.</span></span>
- <span data-ttu-id="a7c45-168">A [ciąg](string.md) literału.</span><span class="sxs-lookup"><span data-stu-id="a7c45-168">A [string](string.md) literal.</span></span>

<span data-ttu-id="a7c45-169">Stałe wyrażenie jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a7c45-169">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="a7c45-170">Jeśli *wyrażenie* i *stałej* są typy całkowite operator równości C# Określa, czy wyrażenie zwraca `true` (to znaczy czy `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="a7c45-170">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="a7c45-171">W przeciwnym razie wartość wyrażenia jest określana przez wywołanie do statycznego [Object.Equals (wyrażenie stałej)](xref:System.Object.Equals(System.Object,System.Object)) metody.</span><span class="sxs-lookup"><span data-stu-id="a7c45-171">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="a7c45-172">W poniższym przykładzie użyto stałe wzorzec czy określonej daty jest weekendy, pierwszego dnia tygodnia pracy, ostatni dzień tygodnia pracy lub w środku tygodnia pracy.</span><span class="sxs-lookup"><span data-stu-id="a7c45-172">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="a7c45-173">Oblicza <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> właściwości bieżącego dnia dla członków <xref:System.DayOfWeek> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7c45-173">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span> 

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="a7c45-174">W poniższym przykładzie użyto stałe wzorzec do obsługi danych wejściowych użytkownika w aplikacji konsoli, która symuluje maszyny do automatycznego kawy.</span><span class="sxs-lookup"><span data-stu-id="a7c45-174">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 [!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a><span data-ttu-id="a7c45-175">Wzorzec typu</span><span class="sxs-lookup"><span data-stu-id="a7c45-175">Type pattern</span></span>

<span data-ttu-id="a7c45-176">Wzorzec typu umożliwia oceny zwięzła, typ i konwersji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-176">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="a7c45-177">W przypadku użycia z `switch` instrukcji, aby wykonać dopasowywania do wzorca on sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli można ją, rzutuje zmiennej tego typu.</span><span class="sxs-lookup"><span data-stu-id="a7c45-177">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="a7c45-178">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="a7c45-178">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="a7c45-179">gdzie *typu* jest nazwa typu, do którego wynik *wyrażenie* należy skonwertować i *nazwa_zmiennej* obiektu, do którego wynik *wyrażenie*przekonwertowaniu Jeśli dopasowania zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a7c45-179">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="a7c45-180">`case` Wyrażenie jest `true` Jeśli jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a7c45-180">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="a7c45-181">*wyrażenie* jest wystąpienie tego samego typu co *typu*.</span><span class="sxs-lookup"><span data-stu-id="a7c45-181">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="a7c45-182">*wyrażenie* jest wystąpieniem typu pochodzącego od *typu*.</span><span class="sxs-lookup"><span data-stu-id="a7c45-182">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="a7c45-183">Innymi słowy, wynik *wyrażenie* może być upcast na wystąpienie *typu*.</span><span class="sxs-lookup"><span data-stu-id="a7c45-183">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="a7c45-184">*wyrażenie* zawiera typ kompilacji jest klasą podstawową *typu*, i *wyrażenie* ma typ obsługi, który jest *typu* lub pochodzi z *typu*.</span><span class="sxs-lookup"><span data-stu-id="a7c45-184">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="a7c45-185">*Typu kompilacji* zmiennej jest typu zmienną, zgodnie z definicją w jego deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="a7c45-185">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="a7c45-186">*Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, który jest przypisany do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a7c45-186">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="a7c45-187">*wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a7c45-187">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="a7c45-188">Jeśli wyrażenie case ma wartość true, *nazwa_zmiennej* ostatecznie jest przypisany i ma zasięg lokalny w ramach tej sekcji przełącznika.</span><span class="sxs-lookup"><span data-stu-id="a7c45-188">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="a7c45-189">Należy pamiętać, że `null` jest niezgodny z typem.</span><span class="sxs-lookup"><span data-stu-id="a7c45-189">Note that `null` does not match a type.</span></span> <span data-ttu-id="a7c45-190">Aby dopasować `null`, użyj następującego `case` etykiety:</span><span class="sxs-lookup"><span data-stu-id="a7c45-190">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="a7c45-191">W poniższym przykładzie użyto ze wzorcem typu, aby podać informacje o różnych rodzajów typy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a7c45-191">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="a7c45-192">Bez wzorca dopasowania, ten kod może być zapisana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a7c45-192">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="a7c45-193">Użycie typu dopasowanie wzorca tworzy kodu mniejszych, który może zostać odczytany, eliminując konieczność, aby sprawdzić, czy wynik konwersji jest `null` lub wykonać rzutowania powtórzony.</span><span class="sxs-lookup"><span data-stu-id="a7c45-193">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="a7c45-194">`case` Instrukcji i `when` — klauzula</span><span class="sxs-lookup"><span data-stu-id="a7c45-194">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="a7c45-195">Uruchamianie z C# w wersji 7.0, ponieważ instrukcji case nie muszą być wykluczają się wzajemnie, można użyć dodać `when` klauzuli, aby określić dodatkowe warunku muszą być spełnione dla instrukcji case wyliczona jako true.</span><span class="sxs-lookup"><span data-stu-id="a7c45-195">Starting with C# 7.0, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="a7c45-196">`when` Klauzula może być dowolne wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="a7c45-196">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="a7c45-197">Jedną z najczęściej zastosowania `when` jest używana do sekcji przełącznika uniemożliwić wykonywanie, gdy wartość wyrażenia dopasowanie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="a7c45-197">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="a7c45-198">W poniższym przykładzie zdefiniowano podstawowej `Shape` klasy, `Rectangle` klasą pochodzącą z `Shape`, a `Square` klasą pochodzącą z `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="a7c45-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="a7c45-199">Używa `when` klauzuli, aby upewnić się, że `ShowShapeInfo` traktuje `Rectangle` obiekt, który został przypisany równy długości i szerokości jako `Square` nawet jeśli nie zostało utworzone jako `Square` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a7c45-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="a7c45-200">Metoda nie jest podejmowana próba wyświetlenia informacji o obiekt, który jest `null` lub kształt, w których obszar wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="a7c45-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
<span data-ttu-id="a7c45-201">Należy pamiętać, że `when` klauzuli w przykładzie podejmowanych w celu przetestowania czy `Shape` obiekt jest `null` nie wykonuj.</span><span class="sxs-lookup"><span data-stu-id="a7c45-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="a7c45-202">Wzorzec poprawnego typu do testowania `null` jest `case null:`.</span><span class="sxs-lookup"><span data-stu-id="a7c45-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a7c45-203">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a7c45-203">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7c45-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7c45-204">See Also</span></span>  

 [<span data-ttu-id="a7c45-205">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a7c45-205">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="a7c45-206">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a7c45-206">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="a7c45-207">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a7c45-207">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="a7c45-208">if-else</span><span class="sxs-lookup"><span data-stu-id="a7c45-208">if-else</span></span>](if-else.md)  
 [<span data-ttu-id="a7c45-209">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="a7c45-209">Pattern Matching</span></span>](../../pattern-matching.md)  
 

 
