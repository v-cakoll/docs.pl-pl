---
title: C#Konwencje kodowania C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: c56d673de958f49a9ace60350442e89039e1d69f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712107"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="b7bfb-102">konwencje kodowania C# (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b7bfb-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="b7bfb-103">Konwencje kodowania mają następujące cele:</span><span class="sxs-lookup"><span data-stu-id="b7bfb-103">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="b7bfb-104">Tworzą one spójny wygląd kodu, dzięki czemu czytelnicy mogą skupić się na zawartości, a nie w układzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="b7bfb-105">Umożliwiają one czytelnikom szybsze zrozumienie kodu dzięki założeniu założeń na podstawie poprzedniego środowiska.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="b7bfb-106">Ułatwiają one kopiowanie, zmienianie i utrzymywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="b7bfb-107">Przedstawiają C# one najlepsze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="b7bfb-108">Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do tworzenia przykładów i dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="b7bfb-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="b7bfb-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="b7bfb-110">W krótkich przykładach, które nie obejmują [dyrektywy using](../../language-reference/keywords/using-directive.md), należy używać kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-110">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="b7bfb-111">Jeśli wiesz, że przestrzeń nazw jest domyślnie importowana w projekcie, nie musisz w pełni kwalifikować nazw z tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="b7bfb-112">Kwalifikowane nazwy mogą być uszkodzone po kropce (.), jeśli są zbyt długie dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="b7bfb-113">Nie trzeba zmieniać nazw obiektów, które zostały utworzone przy użyciu narzędzi projektanta programu Visual Studio, aby dopasować je do innych wytycznych.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="b7bfb-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="b7bfb-114">Layout Conventions</span></span>  
 <span data-ttu-id="b7bfb-115">Dobry układ używa formatowania, aby wyróżnić strukturę kodu i ułatwić odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="b7bfb-116">Przykłady i próbki firmy Microsoft są zgodne z następującymi konwencjami:</span><span class="sxs-lookup"><span data-stu-id="b7bfb-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="b7bfb-117">Użyj domyślnych ustawień edytora kodu (inteligentne wcięcia, cztery znaki wcięcia, karty zapisane jako spacje).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="b7bfb-118">Aby uzyskać więcej informacji, zobacz [Opcje, Edytor tekstu C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="b7bfb-119">Napisz tylko jedną instrukcję na wiersz.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-119">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="b7bfb-120">Napisz tylko jedną deklarację na wiersz.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-120">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="b7bfb-121">Jeśli linie kontynuacji nie mają wcięcia automatycznie, Zwiększ wcięcie z jednego tabulatora (cztery spacje).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="b7bfb-122">Dodaj co najmniej jeden pusty wiersz między definicjami metod i definicjami właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="b7bfb-123">Użyj nawiasów, aby tworzyć klauzule w wyrażeniu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="b7bfb-124">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="b7bfb-124">Commenting Conventions</span></span>  
  
- <span data-ttu-id="b7bfb-125">Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="b7bfb-126">Zacznij komentować tekst, używając wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-126">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="b7bfb-127">Koniec tekstu komentarza z kropką.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-127">End comment text with a period.</span></span>  
  
- <span data-ttu-id="b7bfb-128">Wstaw jedną spację między ogranicznikiem komentarza (//) i tekstem komentarza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="b7bfb-129">Nie twórz sformatowanych bloków gwiazdek wokół komentarzy.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="b7bfb-130">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="b7bfb-130">Language Guidelines</span></span>  
 <span data-ttu-id="b7bfb-131">W poniższych sekcjach opisano sposób, C# w jaki zespół postępuje zgodnie z przygotowaniem przykładów i przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="b7bfb-132">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="b7bfb-132">String Data Type</span></span>  
  
- <span data-ttu-id="b7bfb-133">Użyj [interpolacji ciągów](../../language-reference/tokens/interpolated.md) , aby połączyć krótkie ciągi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="b7bfb-134">Aby dołączyć ciągi w pętlach, szczególnie podczas pracy z dużymi ilościami tekstu, użyj obiektu <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="b7bfb-135">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="b7bfb-135">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="b7bfb-136">Użyj [niejawnego wpisywania](../classes-and-structs/implicitly-typed-local-variables.md) zmiennych lokalnych, gdy typ zmiennej jest oczywisty z prawej strony przypisania lub jeśli dokładny typ nie jest ważny.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-136">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="b7bfb-137">Nie należy używać [var](../../language-reference/keywords/var.md) , gdy typ nie jest widoczny po prawej stronie przypisania.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-137">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="b7bfb-138">Nie należy polegać na nazwie zmiennej, aby określić typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="b7bfb-139">Może nie być poprawna.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="b7bfb-140">Unikaj stosowania `var` zamiast [dynamicznych](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-140">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="b7bfb-141">Użyj niejawnego wpisywania, aby określić typ zmiennej pętli w pętlach [for](../../language-reference/keywords/for.md) i [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="b7bfb-141">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) and [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="b7bfb-142">Poniższy przykład używa niejawnego wpisywania w instrukcji `for`.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
     <span data-ttu-id="b7bfb-143">Poniższy przykład używa niejawnego wpisywania w instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="b7bfb-144">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="b7bfb-144">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="b7bfb-145">Ogólnie rzecz biorąc, użyj `int`, a nie niepodpisanych typów.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="b7bfb-146">Korzystanie z `int` jest wspólne w całym C#systemie i ułatwia korzystanie z innych bibliotek przy użyciu `int`.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="b7bfb-147">Tablice</span><span class="sxs-lookup"><span data-stu-id="b7bfb-147">Arrays</span></span>  
  
- <span data-ttu-id="b7bfb-148">Użyj zwięzłej składni podczas inicjowania tablic w wierszu deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="b7bfb-149">Delegaty</span><span class="sxs-lookup"><span data-stu-id="b7bfb-149">Delegates</span></span>  
  
- <span data-ttu-id="b7bfb-150">Użyj zwięzłej składni, aby utworzyć wystąpienia typu delegata.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="b7bfb-151">Blok try-catch i przy użyciu instrukcji obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="b7bfb-151">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="b7bfb-152">Użyj instrukcji [try-catch](../../language-reference/keywords/try-catch.md) dla większości obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-152">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="b7bfb-153">Uprość kod przy użyciu C# [instrukcji using](../../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-153">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="b7bfb-154">Jeśli masz instrukcję [try-finally](../../language-reference/keywords/try-finally.md) , w której jedyny kod w bloku `finally` jest wywołaniem metody <xref:System.IDisposable.Dispose%2A>, zamiast tego należy użyć instrukcji `using`.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-154">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="b7bfb-155">& & i &#124; &#124; operatory</span><span class="sxs-lookup"><span data-stu-id="b7bfb-155">&& and &#124;&#124; Operators</span></span>  
  
- <span data-ttu-id="b7bfb-156">Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań [](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) , użyj&&[](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) zamiast&[ &#124; ](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) i zamiast [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) przeprowadzania porównań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="b7bfb-157">Nowy operator</span><span class="sxs-lookup"><span data-stu-id="b7bfb-157">New Operator</span></span>  
  
- <span data-ttu-id="b7bfb-158">Użyj zwięzłej formy tworzenia wystąpień obiektów z niejawnym wpisywaniem, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="b7bfb-159">Poprzedni wiersz jest równoważny z następującą deklaracją.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="b7bfb-160">Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="b7bfb-161">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b7bfb-161">Event Handling</span></span>  
  
- <span data-ttu-id="b7bfb-162">W przypadku definiowania programu obsługi zdarzeń, którego nie trzeba później usuwać, należy użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="b7bfb-163">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7bfb-163">Static Members</span></span>  
  
- <span data-ttu-id="b7bfb-164">Wywołaj [statyczne](../../language-reference/keywords/static.md) elementy członkowskie przy użyciu nazwy klasy: *ClassName. StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-164">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="b7bfb-165">Dzięki temu kod jest bardziej czytelny, co oznacza, że statyczny dostęp jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="b7bfb-166">Nie kwalifikuj statycznej składowej zdefiniowanej w klasie bazowej z nazwą klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="b7bfb-167">Podczas kompilowania kodu, czytelność kodu jest myląca, a kod może ulec przerwie w przyszłości, jeśli dodasz statyczną składową o tej samej nazwie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="b7bfb-168">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="b7bfb-168">LINQ Queries</span></span>  
  
- <span data-ttu-id="b7bfb-169">Użyj znaczących nazw zmiennych zapytania.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="b7bfb-170">Poniższy przykład używa `seattleCustomers` dla klientów, którzy znajdują się w Seattle.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="b7bfb-171">Użyj aliasów, aby upewnić się, że nazwy właściwości typów anonimowych są prawidłowo pisane wielkimi literami przy użyciu wielkości liter w Pascalu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="b7bfb-172">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłyby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="b7bfb-173">Na przykład, jeśli zapytanie zwróci nazwę klienta i identyfikator dystrybutora, zamiast opuszczania ich jako `Name` i `ID` w wyniku, należy zmienić ich nazwy, aby wyjaśnić, że `Name` jest nazwą klienta, a `ID` jest IDENTYFIKATORem dystrybutora.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="b7bfb-174">Użyj niejawnego wpisywania w deklaracji zmiennych zapytania i zmiennych zakresów.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="b7bfb-175">Wyrównaj klauzule kwerendy pod klauzulą [from](../../language-reference/keywords/from-clause.md) , jak pokazano w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-175">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="b7bfb-176">Użyj klauzul [WHERE](../../language-reference/keywords/where-clause.md) przed innymi klauzulami zapytania, aby upewnić się, że późniejsze klauzule zapytań działają na zmniejszonym, filtrowanym zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-176">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="b7bfb-177">Do uzyskiwania dostępu do kolekcji wewnętrznych używaj wielu klauzul `from` zamiast klauzuli [Join](../../language-reference/keywords/join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="b7bfb-177">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="b7bfb-178">Na przykład kolekcja obiektów `Student` może zawierać kolekcję wyników testu.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="b7bfb-179">Gdy wykonywane jest następujące zapytanie, zwraca każdy wynik o wartości ponad 90, a także nazwisko studenta, który otrzymał wynik.</span><span class="sxs-lookup"><span data-stu-id="b7bfb-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="b7bfb-180">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="b7bfb-180">Security</span></span>  
 <span data-ttu-id="b7bfb-181">Postępuj zgodnie z wytycznymi w temacie [zasady bezpiecznego kodowania](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="b7bfb-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bfb-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7bfb-182">See also</span></span>

- [<span data-ttu-id="b7bfb-183">Visual Basic konwencji kodowania</span><span class="sxs-lookup"><span data-stu-id="b7bfb-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="b7bfb-184">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b7bfb-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
