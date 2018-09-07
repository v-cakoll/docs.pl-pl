---
title: konwencje kodowania C# (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 430cf3f1bc5e0b5ebe1a05530059516f36a473a1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076668"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="82f02-102">konwencje kodowania C# (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="82f02-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="82f02-103">Konwencje kodowania służą do następujących celów:</span><span class="sxs-lookup"><span data-stu-id="82f02-103">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="82f02-104">Tworzą spójnego wyglądu w kodzie, dzięki czemu czytelnicy można skupić się na treści, a nie na układzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="82f02-105">Umożliwiają one odbiorcy zrozumieć kod szybciej, wprowadzając założenia na podstawie poprzednich doświadczeń.</span><span class="sxs-lookup"><span data-stu-id="82f02-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="82f02-106">Ułatwiają one, kopiowanie, zmienianie i utrzymanie kodu.</span><span class="sxs-lookup"><span data-stu-id="82f02-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="82f02-107">Pokazują one języka C# najlepszych rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="82f02-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="82f02-108">Wskazówki zawarte w tym temacie są używane przez firmę Microsoft do tworzenia, przykłady i dokumentację.</span><span class="sxs-lookup"><span data-stu-id="82f02-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="82f02-109">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="82f02-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="82f02-110">W przykładach krótki, które nie zawierają [dyrektywy using](../../../csharp/language-reference/keywords/using-directive.md), użyj kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82f02-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="82f02-111">Jeśli wiesz, że przestrzeń nazw jest importowana domyślnie w projekcie, nie masz do pełnej kwalifikacji nazwy z tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="82f02-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="82f02-112">Kwalifikowane nazwy może być uszkodzone po pojedynczego znaku kropki (.) są zbyt długi dla pojedynczego wiersza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="82f02-113">Nie masz zmiany nazw obiektów, które zostały utworzone przy użyciu narzędzia projektanta programu Visual Studio, aby je dopasować przejść do pozostałych wskazówek.</span><span class="sxs-lookup"><span data-stu-id="82f02-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="82f02-114">Konwencje układu</span><span class="sxs-lookup"><span data-stu-id="82f02-114">Layout Conventions</span></span>  
 <span data-ttu-id="82f02-115">Układ dobre używa formatowania do podkreślić strukturę kodu i czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="82f02-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="82f02-116">Przykłady firmy Microsoft i przykłady są zgodne z następujących konwencji:</span><span class="sxs-lookup"><span data-stu-id="82f02-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="82f02-117">Użyj domyślnych ustawień edytora kodu (inteligentne tworzenie wcięć, wcięcia Czteroznakowy kartach, zapisane jako miejsca do magazynowania).</span><span class="sxs-lookup"><span data-stu-id="82f02-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="82f02-118">Aby uzyskać więcej informacji, zobacz [opcje, Edytor tekstu, C#, formatowanie](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="82f02-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="82f02-119">Zapis tylko jednej instrukcji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="82f02-119">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="82f02-120">Zapis tylko jednej deklaracji na wiersz.</span><span class="sxs-lookup"><span data-stu-id="82f02-120">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="82f02-121">Jeśli wierszy kontynuacji nie są przeznaczone automatycznie, wcięcie ich jedną pozycję tabulatora (czterech spacji).</span><span class="sxs-lookup"><span data-stu-id="82f02-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="82f02-122">Dodaj co najmniej jeden pusty wiersz między definicje metod i definicjach właściwości.</span><span class="sxs-lookup"><span data-stu-id="82f02-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="82f02-123">Użyj nawiasów, aby wprowadzić klauzule w wyrażeniu oczywista, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="82f02-124">Konwencje komentowania</span><span class="sxs-lookup"><span data-stu-id="82f02-124">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="82f02-125">Umieść komentarz w osobnym wierszu, a nie na końcu wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="82f02-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="82f02-126">Rozpocznij tekst komentarza wielką literą.</span><span class="sxs-lookup"><span data-stu-id="82f02-126">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="82f02-127">Tekst komentarza zakończenia kropką.</span><span class="sxs-lookup"><span data-stu-id="82f02-127">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="82f02-128">Wstaw jedną spację między ogranicznik komentarza (/ /) i tekst komentarza, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="82f02-129">Nie należy tworzyć sformatowanymi blokami ani gwiazdkami wokół komentarzy.</span><span class="sxs-lookup"><span data-stu-id="82f02-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="82f02-130">Wytyczne dotyczące języka</span><span class="sxs-lookup"><span data-stu-id="82f02-130">Language Guidelines</span></span>  
 <span data-ttu-id="82f02-131">W poniższych sekcjach opisano rozwiązania, aby przygotować przykłady kodu i przykłady z zespołu C#.</span><span class="sxs-lookup"><span data-stu-id="82f02-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="82f02-132">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="82f02-132">String Data Type</span></span>  
  
-   <span data-ttu-id="82f02-133">Użyj [Interpolacja ciągów](../../language-reference/tokens/interpolated.md) do łączenia krótkich ciągów, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="82f02-134">Aby dołączyć ciągi w pętli, szczególnie w przypadku, gdy pracujesz z dużych ilości tekstu, należy użyć <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="82f02-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="82f02-135">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="82f02-135">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="82f02-136">Użyj [niejawnego wpisywania](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) dla zmiennych lokalnych, gdy typ zmiennej jest oczywisty z prawej strony przypisania lub gdy dokładny typ nie jest istotna.</span><span class="sxs-lookup"><span data-stu-id="82f02-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="82f02-137">Nie używaj [var](../../../csharp/language-reference/keywords/var.md) gdy typ nie jest jasne, z prawej strony przypisania.</span><span class="sxs-lookup"><span data-stu-id="82f02-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="82f02-138">Nie należy polegać na nazwę zmiennej, aby określić typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="82f02-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="82f02-139">Być może nie być poprawne.</span><span class="sxs-lookup"><span data-stu-id="82f02-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="82f02-140">Unikaj stosowania `var` zamiast [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="82f02-141">Użyć niejawnego wpisywania, aby określić typ zmiennej pętli w [dla](../../../csharp/language-reference/keywords/for.md) i [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="82f02-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="82f02-142">W poniższym przykładzie użyto niejawnego wpisywania w `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="82f02-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="82f02-143">W poniższym przykładzie użyto niejawnego wpisywania w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="82f02-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="82f02-144">Typ danych bez znaku</span><span class="sxs-lookup"><span data-stu-id="82f02-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="82f02-145">Ogólnie rzecz biorąc, użyj `int` zamiast niepodpisanych typów.</span><span class="sxs-lookup"><span data-stu-id="82f02-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="82f02-146">Korzystanie z `int` często w języku C# i łatwiej wchodzić w interakcje z innymi bibliotekami, gdy używasz `int`.</span><span class="sxs-lookup"><span data-stu-id="82f02-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="82f02-147">Tablice</span><span class="sxs-lookup"><span data-stu-id="82f02-147">Arrays</span></span>  
  
-   <span data-ttu-id="82f02-148">Podczas inicjowania tablic w wierszu deklaracji, należy użyć zwięzłej składni.</span><span class="sxs-lookup"><span data-stu-id="82f02-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="82f02-149">Delegaty</span><span class="sxs-lookup"><span data-stu-id="82f02-149">Delegates</span></span>  
  
-   <span data-ttu-id="82f02-150">Aby utworzyć wystąpienia typu delegata, należy użyć składni zwięzły.</span><span class="sxs-lookup"><span data-stu-id="82f02-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="82f02-151">Blok try-catch i przy użyciu instrukcji obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="82f02-151">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="82f02-152">Użyj [try-catch —](../../../csharp/language-reference/keywords/try-catch.md) poufności informacji dla większości wyjątków.</span><span class="sxs-lookup"><span data-stu-id="82f02-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="82f02-153">Uprość kod przy użyciu języka C# [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="82f02-154">Jeśli masz [try-finally](../../../csharp/language-reference/keywords/try-finally.md) instrukcji, w którym tylko kod w `finally` bloku jest wywołaniem <xref:System.IDisposable.Dispose%2A> metody, użyj `using` instrukcji zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="82f02-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="82f02-155">& & i &#124; &#124; operatorów</span><span class="sxs-lookup"><span data-stu-id="82f02-155">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="82f02-156">Aby uniknąć wyjątków i zwiększyć wydajność przez pominięcie niepotrzebnych porównań, należy użyć [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) zamiast [ & ](../../../csharp/language-reference/operators/and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)zamiast [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) podczas wykonywania porównań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="82f02-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="82f02-157">Nowy operator</span><span class="sxs-lookup"><span data-stu-id="82f02-157">New Operator</span></span>  
  
-   <span data-ttu-id="82f02-158">Za pomocą zwięzłe formularza w przypadku tworzenia wystąpienia obiektu niejawnego wpisywania, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="82f02-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="82f02-159">Poprzedniego wiersza jest równoważna następującej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="82f02-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="82f02-160">Użyj inicjatorów obiektów, aby uprościć tworzenie obiektów.</span><span class="sxs-lookup"><span data-stu-id="82f02-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="82f02-161">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="82f02-161">Event Handling</span></span>  
  
-   <span data-ttu-id="82f02-162">Jeśli zamierzasz zdefiniować program obsługi zdarzeń, że nie musisz usunąć później, należy użyć wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="82f02-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="82f02-163">Statyczne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="82f02-163">Static Members</span></span>  
  
-   <span data-ttu-id="82f02-164">Wywołaj [statyczne](../../../csharp/language-reference/keywords/static.md) elementów członkowskich przy użyciu nazwy klasy: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="82f02-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="82f02-165">Tej praktyką sprawia, że kod jest bardziej czytelny, dzięki czemu dostęp do statycznych, wyczyść.</span><span class="sxs-lookup"><span data-stu-id="82f02-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="82f02-166">Nie można rozwiązać członka statycznego zdefiniowana w klasie bazowej o nazwie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="82f02-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="82f02-167">Gdy kompiluje kod, jest mylące czytelność kodu i kodu mogą przestać działać w przyszłości w przypadku dodania statyczny element członkowski o takiej samej nazwie do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="82f02-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="82f02-168">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="82f02-168">LINQ Queries</span></span>  
  
-   <span data-ttu-id="82f02-169">Użyj nazw opisowych dla zmiennych kwerendy.</span><span class="sxs-lookup"><span data-stu-id="82f02-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="82f02-170">W poniższym przykładzie użyto `seattleCustomers` dla klientów, którzy znajdują się w Seattle.</span><span class="sxs-lookup"><span data-stu-id="82f02-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="82f02-171">Należy stosować aliasy, aby upewnić się, że nazwy właściwości anonimowych typów są kapitalizowane poprawnie, przy użyciu obudowy Pascal wielkość liter w wyrazie.</span><span class="sxs-lookup"><span data-stu-id="82f02-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="82f02-172">Zmień nazwę właściwości, gdy nazwy właściwości w wyniku byłby niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="82f02-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="82f02-173">Na przykład, jeśli zapytanie zwraca klienta, nazwy i Identyfikatora dystrybutora, zamiast pozostawiania je jako `Name` i `ID` w wyniku, zmienić ich nazwy, które informuje, że `Name` nazywa się klient, oraz `ID` to identyfikator dystrybutora.</span><span class="sxs-lookup"><span data-stu-id="82f02-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="82f02-174">Należy użyć niejawnego wpisywania w deklaracji zmiennych kwerendy i zmiennych zakresu.</span><span class="sxs-lookup"><span data-stu-id="82f02-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="82f02-175">Wyrównaj klauzule zapytania pod [z](../../../csharp/language-reference/keywords/from-clause.md) klauzuli, jak pokazano w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="82f02-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="82f02-176">Użyj [gdzie](../../../csharp/language-reference/keywords/where-clause.md) klauzule przed inne klauzule zapytania, aby upewnić się, że późniejsze klauzule kwerend działają na mniejsze, filtrowany zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="82f02-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="82f02-177">Używanych jest wiele `from` klauzule zamiast [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) klauzuli do dostępu do kolekcji wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="82f02-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="82f02-178">Na przykład zbiór `Student` każdego obiektów może zawierać zbiór wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="82f02-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="82f02-179">Po wykonaniu następujące zapytanie zwraca każdy wynik, który jest ponad 90, wraz z Nazwisko ucznia, który otrzymał wynik.</span><span class="sxs-lookup"><span data-stu-id="82f02-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="82f02-180">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="82f02-180">Security</span></span>  
 <span data-ttu-id="82f02-181">Postępuj zgodnie z wytycznymi podanymi w [Secure wytycznych kodowania](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f02-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82f02-182">See Also</span></span>

- [<span data-ttu-id="82f02-183">Visual Basic — konwencje kodowania</span><span class="sxs-lookup"><span data-stu-id="82f02-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [<span data-ttu-id="82f02-184">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="82f02-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
