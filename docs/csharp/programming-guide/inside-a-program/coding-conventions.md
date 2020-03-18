---
title: C# Konwencje kodowania — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 77b173a420f26834855e0bdca3c8d04406ac65d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399736"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="b8d6e-102">konwencje kodowania C# (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b8d6e-102">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="b8d6e-103">Konwencje kodowania służą następującym celom:</span><span class="sxs-lookup"><span data-stu-id="b8d6e-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="b8d6e-104">Tworzą spójny wygląd kodu, dzięki czemu czytelnicy mogą skupić się na zawartości, a nie na układzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="b8d6e-105">Umożliwiają one czytelnikom szybciej zrozumieć kod, dokonując założeń na podstawie wcześniejszego doświadczenia.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="b8d6e-106">Ułatwiają one kopiowanie, zmienianie i obsługa kodu.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="b8d6e-107">Wykazują one C# najlepszych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-107">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="b8d6e-108">Wskazówki w tym artykule są używane przez firmę Microsoft do tworzenia przykładów i dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-108">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="b8d6e-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="b8d6e-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="b8d6e-110">W krótkich przykładach, które nie obejmują [przy użyciu dyrektyw,](../../language-reference/keywords/using-directive.md)użyj kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="b8d6e-111">Jeśli wiesz, że obszar nazw jest importowany domyślnie w projekcie, nie trzeba w pełni kwalifikować nazwy z tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="b8d6e-112">Kwalifikowane nazwy mogą zostać przerwane po kropka (.), jeśli są one zbyt długie dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="b8d6e-113">Nie trzeba zmieniać nazwy obiektów, które zostały utworzone przy użyciu narzędzi projektanta programu Visual Studio, aby dopasować je do innych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="b8d6e-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="b8d6e-114">Layout Conventions</span></span>  

<span data-ttu-id="b8d6e-115">Dobry układ używa formatowania, aby podkreślić strukturę kodu i ułatwić odczytanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="b8d6e-116">Przykłady i przykłady firmy Microsoft są zgodne z następującymi konwencjami:</span><span class="sxs-lookup"><span data-stu-id="b8d6e-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="b8d6e-117">Użyj domyślnych ustawień Edytora kodu (inteligentne wcięcia, czteroznakowe wcięcia, karty zapisane jako spacje).</span><span class="sxs-lookup"><span data-stu-id="b8d6e-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="b8d6e-118">Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu, C#, Formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="b8d6e-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="b8d6e-119">Napisz tylko jedną instrukcję na wiersz.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="b8d6e-120">Napisz tylko jedną deklarację na wiersz.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="b8d6e-121">Jeśli wiersze kontynuacji nie są wcięte automatycznie, wcięcie ich jeden tabulator (cztery spacje).</span><span class="sxs-lookup"><span data-stu-id="b8d6e-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="b8d6e-122">Dodaj co najmniej jedną pustą linię między definicjami metod a definicjami właściwości.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="b8d6e-123">Nawiasy służy do klauzul w wyrażeniu widoczne, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="b8d6e-124">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="b8d6e-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="b8d6e-125">Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="b8d6e-126">Rozpocznij tekst komentarza z literą wielkie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="b8d6e-127">Zakończ tekst komentarza kropką.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="b8d6e-128">Wstaw jedną spcję między ogranicznikiem komentarza (//) a tekstem komentarza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="b8d6e-129">Nie należy tworzyć sformatowanych bloków gwiazdek wokół komentarzy.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="b8d6e-130">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="b8d6e-130">Language Guidelines</span></span>  

<span data-ttu-id="b8d6e-131">W poniższych sekcjach opisano praktyki, które zespół C# następuje do przygotowania przykładów kodu i przykłady.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="b8d6e-132">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="b8d6e-132">String Data Type</span></span>  
  
- <span data-ttu-id="b8d6e-133">Interpolacja [ciągów służy](../../language-reference/tokens/interpolated.md) do łączenia krótkich ciągów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="b8d6e-134">Aby dołączać ciągi w pętlach, szczególnie podczas pracy z <xref:System.Text.StringBuilder> dużą ilością tekstu, należy użyć obiektu.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="b8d6e-135">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="b8d6e-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="b8d6e-136">Użyj [niejawnego wpisywania](../classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest oczywisty po prawej stronie przypisania lub gdy dokładny typ nie jest ważny.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="b8d6e-137">Nie należy używać [var,](../../language-reference/keywords/var.md) gdy typ nie jest widoczny po prawej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="b8d6e-138">Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="b8d6e-139">To może nie być poprawne.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="b8d6e-140">Unikaj używania `var` w miejsce [dynamicznego](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b8d6e-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="b8d6e-141">Użyj niejawnego pisania, aby określić typ zmiennej pętli w [pętli.](../../language-reference/keywords/for.md)</span><span class="sxs-lookup"><span data-stu-id="b8d6e-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="b8d6e-142">W poniższym przykładzie użyto `for` niejawnego wpisywania w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="b8d6e-143">Nie należy używać niejawnego pisania, aby określić typ zmiennej pętli w [pętlach foreach.](../../language-reference/keywords/foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="b8d6e-143">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="b8d6e-144">W poniższym przykładzie użyto `foreach` jawnego wpisywania w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-144">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="b8d6e-145">Należy uważać, aby nie przypadkowo zmienić typ elementu iterable kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-145">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="b8d6e-146">Na przykład jest łatwe przełączenie <xref:System.Collections.IEnumerable?displayProperty=nameWithType> z `foreach` <xref:System.Linq.IQueryable?displayProperty=nameWithType> w instrukcji, która zmienia wykonanie kwerendy.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-146">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="b8d6e-147">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="b8d6e-147">Unsigned Data Type</span></span>  
  
<span data-ttu-id="b8d6e-148">Ogólnie rzecz `int` biorąc użyj zamiast niepodpisanych typów.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-148">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="b8d6e-149">Użycie `int` jest wspólne w całym języku C#, i łatwiej jest `int`wchodzić w interakcje z innymi bibliotekami podczas korzystania .</span><span class="sxs-lookup"><span data-stu-id="b8d6e-149">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="b8d6e-150">Tablice</span><span class="sxs-lookup"><span data-stu-id="b8d6e-150">Arrays</span></span>  
  
<span data-ttu-id="b8d6e-151">Użyj zwięzłej składni podczas inicjowania tablic w wierszu deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-151">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="b8d6e-152">Delegaty</span><span class="sxs-lookup"><span data-stu-id="b8d6e-152">Delegates</span></span>  
  
<span data-ttu-id="b8d6e-153">Składnia zwięzła służy do tworzenia wystąpień typu delegata.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-153">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="b8d6e-154">Blok try-catch i przy użyciu instrukcji obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="b8d6e-154">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="b8d6e-155">Użyj instrukcji [try-catch](../../language-reference/keywords/try-catch.md) dla większości obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-155">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="b8d6e-156">Uprość kod przy użyciu instrukcji C# [.](../../language-reference/keywords/using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b8d6e-156">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="b8d6e-157">Jeśli masz [instrukcję try-finally,](../../language-reference/keywords/try-finally.md) w której `finally` jedynym kodem <xref:System.IDisposable.Dispose%2A> w bloku `using` jest wywołanie metody, należy użyć instrukcji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-157">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="b8d6e-158">Operatorzy && i &#124;&#124; </span><span class="sxs-lookup"><span data-stu-id="b8d6e-158">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="b8d6e-159">Aby uniknąć wyjątków i zwiększyć wydajność, [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) pomijając [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) niepotrzebne porównania, należy użyć zamiast i [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) zamiast [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) podczas wykonywania porównań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-159">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="b8d6e-160">Nowy operator</span><span class="sxs-lookup"><span data-stu-id="b8d6e-160">New Operator</span></span>  
  
- <span data-ttu-id="b8d6e-161">Użyj zwięzłej formy wystąpienia obiektu z niejawnym wpisywaniem, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-161">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="b8d6e-162">Poprzedni wiersz jest odpowiednikiem następującej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-162">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="b8d6e-163">Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-163">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="b8d6e-164">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b8d6e-164">Event Handling</span></span>  
  
<span data-ttu-id="b8d6e-165">Jeśli definiujesz program obsługi zdarzeń, którego nie trzeba później usuwać, użyj wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-165">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="b8d6e-166">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b8d6e-166">Static Members</span></span>  
  
<span data-ttu-id="b8d6e-167">Wywołaj [elementy statyczne](../../language-reference/keywords/static.md) przy użyciu nazwy klasy: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-167">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="b8d6e-168">Ta praktyka sprawia, że kod jest bardziej czytelny, dzięki czemu dostęp statyczny jest przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-168">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="b8d6e-169">Nie należy kwalifikować statyczny element członkowski zdefiniowany w klasie podstawowej o nazwie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-169">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="b8d6e-170">Podczas gdy ten kod kompiluje, czytelność kodu jest mylące, a kod może zostać przerwany w przyszłości, jeśli dodasz statyczny element członkowski o tej samej nazwie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-170">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="b8d6e-171">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="b8d6e-171">LINQ Queries</span></span>  
  
- <span data-ttu-id="b8d6e-172">Użyj znaczących nazw dla zmiennych kwerend.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-172">Use meaningful names for query variables.</span></span> <span data-ttu-id="b8d6e-173">Poniższy przykład `seattleCustomers` używa dla klientów, którzy znajdują się w Seattle.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-173">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="b8d6e-174">Użyj aliasów, aby upewnić się, że nazwy właściwości typów anonimowych są poprawnie kapitalizowane przy użyciu wielkości liter Pascala.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-174">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="b8d6e-175">Zmień nazwy właściwości, gdy nazwy właściwości w wyniku będzie niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-175">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="b8d6e-176">Na przykład jeśli kwerenda zwraca nazwę klienta i identyfikator dystrybutora, `ID` zamiast pozostawiać je jako `Name` `Name` wynik, zmień ich nazwę, aby wyjaśnić, że jest to nazwa klienta i `ID` jest identyfikatorem dystrybutora.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-176">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="b8d6e-177">Użyj niejawnego wpisywania w deklaracji zmiennych zapytania i zmiennych zakresu.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-177">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="b8d6e-178">Wyrównaj klauzule zapytania zgodnie z klauzulą [from,](../../language-reference/keywords/from-clause.md) jak pokazano w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-178">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="b8d6e-179">Użyj [where](../../language-reference/keywords/where-clause.md) klauzule przed innymi klauzulami kwerendy, aby upewnić się, że później klauzule kwerendy działają na zredukowanym, filtrowanym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-179">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="b8d6e-180">Użyj `from` wielu klauzul zamiast [join](../../language-reference/keywords/join-clause.md) klauzuli, aby uzyskać dostęp do kolekcji wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-180">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="b8d6e-181">Na przykład kolekcja `Student` obiektów może zawierać kolekcję wyników testów.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-181">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="b8d6e-182">Po wykonaniu następującego zapytania zwraca każdy wynik, który jest powyżej 90, wraz z nazwiskiem studenta, który otrzymał wynik.</span><span class="sxs-lookup"><span data-stu-id="b8d6e-182">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="b8d6e-183">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="b8d6e-183">Security</span></span>  

<span data-ttu-id="b8d6e-184">Postępuj zgodnie z wytycznymi w [Wytycznych bezpiecznego kodowania](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="b8d6e-184">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d6e-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8d6e-185">See also</span></span>

- [<span data-ttu-id="b8d6e-186">Visual Basic — Konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="b8d6e-186">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="b8d6e-187">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b8d6e-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
