---
title: "konwencje kodowania C# (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a8806ddb0a9cc62fe68dc9d558917ee2d532e7f
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="6978b-102">konwencje kodowania C# (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6978b-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="6978b-103">Konwencje kodowania służą do następujących celów:</span><span class="sxs-lookup"><span data-stu-id="6978b-103">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="6978b-104">Tak, aby czytelnicy mogą skupić się na zawartości, nie układu tworzenia spójny wygląd w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="6978b-105">Umożliwiają one czytników zrozumienie kod szybciej przez założenie na podstawie doświadczeń w poprzedniej.</span><span class="sxs-lookup"><span data-stu-id="6978b-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="6978b-106">Ułatwiają one kopiowanie, zmienianie i utrzymywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="6978b-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="6978b-107">Pokazują one C# najlepszych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="6978b-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="6978b-108">Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do opracowywania przykłady i dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="6978b-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="6978b-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6978b-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="6978b-110">W przykładach krótkie, które nie zawierają [przy użyciu dyrektyw](../../../csharp/language-reference/keywords/using-directive.md), użyj kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6978b-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="6978b-111">Jeśli wiesz, że przestrzeń nazw jest importowany domyślnie w projekcie, nie masz do pełnej kwalifikacji nazwy z tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="6978b-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="6978b-112">Kwalifikowane nazwy może być przerwane po kropkę (.) Jeśli są zbyt długi i jednym wierszu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="6978b-113">Nie trzeba zmieniać nazwy obiektów, które zostały utworzone przy użyciu narzędzia projektanta programu Visual Studio, aby je dopasować pozostałych wskazówek.</span><span class="sxs-lookup"><span data-stu-id="6978b-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="6978b-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="6978b-114">Layout Conventions</span></span>  
 <span data-ttu-id="6978b-115">Dobrym układu używa formatowania, aby wyróżnić struktura kodu i czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="6978b-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="6978b-116">Przykłady i przykłady firmy Microsoft jest zgodna z następujących konwencji:</span><span class="sxs-lookup"><span data-stu-id="6978b-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="6978b-117">Użyj domyślnych ustawień edytora kodu (inteligentne wcięcie, wcięcia czterech znaków, karty zapisane jako spacji).</span><span class="sxs-lookup"><span data-stu-id="6978b-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="6978b-118">Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstu, C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="6978b-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="6978b-119">Napisać tylko jednej instrukcji w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="6978b-119">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="6978b-120">Napisać tylko jedna deklaracja w wierszu.</span><span class="sxs-lookup"><span data-stu-id="6978b-120">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="6978b-121">Jeśli kontynuacji wierszy nie są przeznaczone automatycznie, wcięcie ich jedną pozycję tabulatora (czterech spacji).</span><span class="sxs-lookup"><span data-stu-id="6978b-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="6978b-122">Dodaj co najmniej jeden pusty wiersz między definicji metody i właściwości definicji.</span><span class="sxs-lookup"><span data-stu-id="6978b-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="6978b-123">Użyj nawiasów, aby klauzule w wyrażeniu oczywista, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="6978b-124">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="6978b-124">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="6978b-125">Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="6978b-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="6978b-126">Rozpocznij tekst komentarza na wielką literę.</span><span class="sxs-lookup"><span data-stu-id="6978b-126">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="6978b-127">Tekst komentarza zakończenia kropką.</span><span class="sxs-lookup"><span data-stu-id="6978b-127">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="6978b-128">Wstawienia jedną spację między ogranicznik komentarza (/ /), a tekst komentarza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="6978b-129">Nie należy tworzyć sformatowany bloki gwiazdek wokół komentarze.</span><span class="sxs-lookup"><span data-stu-id="6978b-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="6978b-130">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="6978b-130">Language Guidelines</span></span>  
 <span data-ttu-id="6978b-131">W poniższych sekcjach opisano wskazówki, które umożliwiają przygotowanie przykłady kodu i przykłady zespołu C#.</span><span class="sxs-lookup"><span data-stu-id="6978b-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="6978b-132">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="6978b-132">String Data Type</span></span>  
  
-   <span data-ttu-id="6978b-133">Użyj `+` operatora łączenia krótkich ciągów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-133">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="6978b-134">Aby dołączyć ciągów w pętli, szczególnie w przypadku pracy z dużą ilością tekstu, należy użyć <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6978b-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="6978b-135">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="6978b-135">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="6978b-136">Użyj [niejawne wpisując](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest widoczne z prawej strony przypisania lub gdy dokładny typ nie jest istotna.</span><span class="sxs-lookup"><span data-stu-id="6978b-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="6978b-137">Nie używaj [var](../../../csharp/language-reference/keywords/var.md) gdy typ nie jest widoczna z prawej strony przypisania.</span><span class="sxs-lookup"><span data-stu-id="6978b-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="6978b-138">Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6978b-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="6978b-139">Może nie być poprawne.</span><span class="sxs-lookup"><span data-stu-id="6978b-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="6978b-140">Unikaj używania `var` zamiast [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="6978b-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="6978b-141">Umożliwia wpisanie niejawne określają typ zmiennej pętli w [dla](../../../csharp/language-reference/keywords/for.md) i [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="6978b-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="6978b-142">W poniższym przykładzie użyto niejawne wpisanie `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6978b-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="6978b-143">W poniższym przykładzie użyto niejawne wpisanie `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6978b-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="6978b-144">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="6978b-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="6978b-145">Ogólnie rzecz biorąc, użyj `int` zamiast typy bez znaku.</span><span class="sxs-lookup"><span data-stu-id="6978b-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="6978b-146">Korzystanie z `int` jest typowe w C# i możliwe jest łatwiejsze do interakcji z innych bibliotek, korzystając z `int`.</span><span class="sxs-lookup"><span data-stu-id="6978b-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="6978b-147">Tablice</span><span class="sxs-lookup"><span data-stu-id="6978b-147">Arrays</span></span>  
  
-   <span data-ttu-id="6978b-148">Podczas inicjowania tablic w wierszu deklaracji, należy użyć składni zwięzły.</span><span class="sxs-lookup"><span data-stu-id="6978b-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="6978b-149">Delegaty</span><span class="sxs-lookup"><span data-stu-id="6978b-149">Delegates</span></span>  
  
-   <span data-ttu-id="6978b-150">Umożliwia utworzenie wystąpienia typu delegata zwięzłą składnią.</span><span class="sxs-lookup"><span data-stu-id="6978b-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="6978b-151">Blok try-catch i przy użyciu instrukcji obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="6978b-151">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="6978b-152">Użyj [try-catch](../../../csharp/language-reference/keywords/try-catch.md) instrukcji dla większości obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6978b-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="6978b-153">Uprościć kod przy użyciu języka C# [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6978b-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="6978b-154">Jeśli masz [try-finally](../../../csharp/language-reference/keywords/try-finally.md) instrukcji, w którym tylko kod w `finally` blok jest wywołanie <xref:System.IDisposable.Dispose%2A> metody, użyj `using` instrukcji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="6978b-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="6978b-155">& & i &#124; &#124; Operatory</span><span class="sxs-lookup"><span data-stu-id="6978b-155">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="6978b-156">Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań, użyj [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) zamiast [ & ](../../../csharp/language-reference/operators/and-operator.md) i [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) zamiast [&#124;](../../../csharp/language-reference/operators/or-operator.md) po wykonaniu porównań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6978b-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="6978b-157">Nowy operator</span><span class="sxs-lookup"><span data-stu-id="6978b-157">New Operator</span></span>  
  
-   <span data-ttu-id="6978b-158">Formularz zwięzły konkretyzacji obiektu w trakcie pisania niejawne, jak pokazano w poniższych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6978b-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="6978b-159">Następujące oświadczenie odpowiada poprzedniego wiersza.</span><span class="sxs-lookup"><span data-stu-id="6978b-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="6978b-160">Inicjatory obiektów można użyć, aby uprościć tworzenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="6978b-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="6978b-161">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6978b-161">Event Handling</span></span>  
  
-   <span data-ttu-id="6978b-162">Jeśli definiujesz program obsługi zdarzeń, które trzeba usunąć później, należy użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="6978b-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="6978b-163">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6978b-163">Static Members</span></span>  
  
-   <span data-ttu-id="6978b-164">Wywołanie [statycznych](../../../csharp/language-reference/keywords/static.md) elementy członkowskie przy użyciu nazwy klasy: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="6978b-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="6978b-165">Takie rozwiązanie sprawia, że kod jest bardziej przejrzysta dokonując statycznych dostęp, wyczyść.</span><span class="sxs-lookup"><span data-stu-id="6978b-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="6978b-166">Nie można rozwiązać członka statycznego zdefiniowana w klasie podstawowej z nazwą klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6978b-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="6978b-167">Kompiluje kod, jest mylące czytelność kodu i kodu mogą być dzielone w przyszłości, jeśli dodasz statyczny element członkowski o takiej samej nazwie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6978b-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="6978b-168">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="6978b-168">LINQ Queries</span></span>  
  
-   <span data-ttu-id="6978b-169">Użyj łatwy do rozpoznania nazwy zmiennych zapytania.</span><span class="sxs-lookup"><span data-stu-id="6978b-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="6978b-170">W poniższym przykładzie użyto `seattleCustomers` dla klientów, którzy znajdują się w Seattle.</span><span class="sxs-lookup"><span data-stu-id="6978b-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="6978b-171">Upewnij się, że nazwy właściwości typu anonimowego są poprawnie pisany wielkimi literami, przy użyciu Pascal za pomocą aliasów wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="6978b-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="6978b-172">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłoby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="6978b-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="6978b-173">Na przykład, jeśli zapytanie zwraca klienta nazwa i identyfikator dystrybutora, zamiast zostawiać je jako `Name` i `ID` w wyniku, zmień ich wyjaśnienia, że `Name` nazywa się klient, oraz `ID` jest Identyfikatorem dystrybutora.</span><span class="sxs-lookup"><span data-stu-id="6978b-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="6978b-174">Użycie niejawne, wpisując w deklaracji zmiennych zapytania i zmiennych zakresu.</span><span class="sxs-lookup"><span data-stu-id="6978b-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="6978b-175">Dopasuj klauzule zapytań w obszarze [z](../../../csharp/language-reference/keywords/from-clause.md) klauzuli, jak pokazano w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="6978b-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="6978b-176">Użyj [gdzie](../../../csharp/language-reference/keywords/where-clause.md) klauzule przed inne klauzule zapytań, aby upewnić się, że nowsze klauzule zapytań działają na zmniejszenie, filtrowane zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="6978b-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="6978b-177">Używanych jest wiele `from` klauzule zamiast [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) klauzuli można uzyskać dostępu do kolekcji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="6978b-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="6978b-178">Na przykład kolekcja `Student` każdego obiekty mogą zawierać kolekcji wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="6978b-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="6978b-179">Po wykonaniu następujące zapytanie zwraca każdego wynik, który jest ponad 90, wraz z nazwisko studentów, który otrzymał wynik.</span><span class="sxs-lookup"><span data-stu-id="6978b-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="6978b-180">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6978b-180">Security</span></span>  
 <span data-ttu-id="6978b-181">Postępuj zgodnie z wytycznymi w [Secure wytyczne kodowania](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="6978b-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6978b-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6978b-182">See Also</span></span>  
 [<span data-ttu-id="6978b-183">Visual Basic — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="6978b-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [<span data-ttu-id="6978b-184">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="6978b-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
