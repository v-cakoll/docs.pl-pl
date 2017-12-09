---
title: "Konstrukcje alternacyjne w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6ad632130b6f111ff863648b8b1a3b2835c27660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="ca16c-102">Konstrukcje alternacyjne w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="ca16c-102">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a><span data-ttu-id="ca16c-103">Konstrukcje alternacyjne zmodyfikować wyrażenie regularne, aby włączyć opcję / lub lub pasujące warunkowego.</span><span class="sxs-lookup"><span data-stu-id="ca16c-103">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="ca16c-104">.NET obsługuje trzy konstrukcje alternacyjne:</span><span class="sxs-lookup"><span data-stu-id="ca16c-104">.NET supports three alternation constructs:</span></span>  
  
-   [<span data-ttu-id="ca16c-105">Dopasowywanie do wzorca za &#124;</span><span class="sxs-lookup"><span data-stu-id="ca16c-105">Pattern matching with &#124;</span></span>](#Either_Or)  
  
-   [<span data-ttu-id="ca16c-106">Warunkowe dopasowywanie (? () wyrażenie) tak &#124; nie)</span><span class="sxs-lookup"><span data-stu-id="ca16c-106">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
-   [<span data-ttu-id="ca16c-107">Dopasowywanie warunkowego oparte na prawidłową grupę przechwycony</span><span class="sxs-lookup"><span data-stu-id="ca16c-107">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="ca16c-108">Dopasowywanie do wzorca z &#124;</span><span class="sxs-lookup"><span data-stu-id="ca16c-108">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="ca16c-109">Można użyć pionowy pasek (`|`) znaków do dopasowania któregokolwiek z serii wzorców, gdzie `|` rozdziela każdego wzorca.</span><span class="sxs-lookup"><span data-stu-id="ca16c-109">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="ca16c-110">Klasa dodatnią znaków, takich jak `|` znak może być użyty do dopasowania dowolną liczbę pojedynczy znaki.</span><span class="sxs-lookup"><span data-stu-id="ca16c-110">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="ca16c-111">W poniższym przykładzie użyto zarówno klasy znaku dodatnią i albo / lub dopasowywanie do wzorca za `|` znak, aby zlokalizować wystąpienia wyrazy "szarym" lub "szare" w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-111">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="ca16c-112">W takim przypadku `|` znak tworzy wyrażenie regularne jest na pełniejsze.</span><span class="sxs-lookup"><span data-stu-id="ca16c-112">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="ca16c-113">Wyrażenie regularne, która używa `|` znak, `\bgr(a|e)y\b`, jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ca16c-113">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ca16c-114">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ca16c-114">Pattern</span></span>|<span data-ttu-id="ca16c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ca16c-115">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ca16c-116">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-116">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="ca16c-117">Pasować do znaków "gr".</span><span class="sxs-lookup"><span data-stu-id="ca16c-117">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="ca16c-118">Dopasowuje znak „a” lub „e”.</span><span class="sxs-lookup"><span data-stu-id="ca16c-118">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="ca16c-119">Odpowiada na granicy słowa "y".</span><span class="sxs-lookup"><span data-stu-id="ca16c-119">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="ca16c-120">`|` Znak można również wykonać jedno / lub pasuje do wielu znaków lub zakresie, które może zawierać dowolną kombinację znaków literały i elementy języka wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="ca16c-120">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="ca16c-121">(Klasy znaku nie zapewnia tę funkcję). W poniższym przykładzie użyto `|` znak wyodrębnić albo stany USA Numer ubezpieczenia społecznego (SSN), który jest 9 cyfr w formacie *ddd*-*dd*-*dddd*, lub stany USA Pracodawcy Identyfikacja numeru (NIP), czyli 9 cyfr w formacie *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="ca16c-121">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="ca16c-122">Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ca16c-122">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ca16c-123">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ca16c-123">Pattern</span></span>|<span data-ttu-id="ca16c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ca16c-124">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ca16c-125">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-125">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="ca16c-126">Pasuje do żadnej z następujących czynności: dwie cyfry dziesiętne następuje myślnik następuje siedmiu cyfr dziesiętnych; lub trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="ca16c-126">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="ca16c-127">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-127">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="ca16c-128">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ca16c-128">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="ca16c-129">Dopasowanie warunkowe z wyrażeniem</span><span class="sxs-lookup"><span data-stu-id="ca16c-129">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="ca16c-130">Ten element języka próbuje pasuje do jednej z dwóch wzorców w zależności od tego, czy dopasowania wzorca początkowej.</span><span class="sxs-lookup"><span data-stu-id="ca16c-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="ca16c-131">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="ca16c-131">Its syntax is:</span></span>  
  
 <span data-ttu-id="ca16c-132">`(?(`*wyrażenie* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="ca16c-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="ca16c-133">gdzie *wyrażenie* jest początkowej wzorzec do dopasowania, *tak* jest wzorzec do dopasowania, jeśli *wyrażenie* dopasowaniu, i *nie* jest opcjonalny wzorzec do dopasowania, jeśli *wyrażenie* nie jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="ca16c-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="ca16c-134">Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie wcześniejszego w strumieniu wejściowym po oblicza *wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="ca16c-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="ca16c-135">W związku z tym ta konstrukcja jest odpowiednikiem następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ca16c-135">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="ca16c-136">`(?(?=`*wyrażenie* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="ca16c-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="ca16c-137">gdzie `(?=` *wyrażenie* `)` jest konstrukcję potwierdzenia zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="ca16c-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="ca16c-138">(Aby uzyskać więcej informacji, zobacz [konstrukcji grupowania](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako swojej kotwicy (Potwierdzenie zerowej szerokości), *wyrażenie* musi być potwierdzenia zerowej szerokości (Aby uzyskać więcej informacji, zobacz [ Kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) lub Podwyrażenie, które również znajdują się w *tak*.</span><span class="sxs-lookup"><span data-stu-id="ca16c-138">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="ca16c-139">W przeciwnym razie *tak* nie można dopasować wzorzec.</span><span class="sxs-lookup"><span data-stu-id="ca16c-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca16c-140">Jeśli *wyrażenie*jest nazwane lub numerem grupy przechwytywania, konstrukcja alternacyjne jest interpretowany jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [warunkowego dopasowania na podstawie prawidłową grupę przechwytywania](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="ca16c-140">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="ca16c-141">Innymi słowy aparat wyrażeń regularnych nie próbował dopasować podciąg przechwycony, ale zamiast tego testów dla obecności lub braku grupy.</span><span class="sxs-lookup"><span data-stu-id="ca16c-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="ca16c-142">Poniższy przykład jest odmianą przykładu, która jest wyświetlana w [albo / lub z dopasowywanie do wzorców &#124;](#Either_Or) sekcji.</span><span class="sxs-lookup"><span data-stu-id="ca16c-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="ca16c-143">Aby ustalić, czy pierwsze trzy znaki po granic word dwie cyfry następuje łącznik używa warunkowego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ca16c-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="ca16c-144">Jeśli są one go próbuje dopasować stany USA Numer identyfikacyjny pracodawcy (NIP).</span><span class="sxs-lookup"><span data-stu-id="ca16c-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="ca16c-145">Jeśli nie, jego próbuje dopasować stany USA Numer ubezpieczenia społecznego (SSN).</span><span class="sxs-lookup"><span data-stu-id="ca16c-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="ca16c-146">Wzorzec wyrażenia regularnego `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ca16c-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ca16c-147">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ca16c-147">Pattern</span></span>|<span data-ttu-id="ca16c-148">Opis</span><span class="sxs-lookup"><span data-stu-id="ca16c-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ca16c-149">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="ca16c-150">Ustal, czy trzech kolejnych znaków składają się z dwóch cyfr zostały wykonane przez łącznik.</span><span class="sxs-lookup"><span data-stu-id="ca16c-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="ca16c-151">Jeśli poprzednie wzorzec jest zgodny, odpowiadać dwie cyfry następuje myślnik następuje siedem cyfr.</span><span class="sxs-lookup"><span data-stu-id="ca16c-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="ca16c-152">Niezgodna wcześniejszego wzorca odpowiada trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="ca16c-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="ca16c-153">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-153">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="ca16c-154">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="ca16c-154">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="ca16c-155">Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach</span><span class="sxs-lookup"><span data-stu-id="ca16c-155">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="ca16c-156">Ten element języka próbuje pasuje do jednej z dwóch wzorców w zależności od tego, czy dopasowywane określonej grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="ca16c-156">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="ca16c-157">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="ca16c-157">Its syntax is:</span></span>  
  
 <span data-ttu-id="ca16c-158">`(?(`*nazwa* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="ca16c-158">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="ca16c-159">lub</span><span class="sxs-lookup"><span data-stu-id="ca16c-159">or</span></span>  
  
 <span data-ttu-id="ca16c-160">`(?(`*numer* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="ca16c-160">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="ca16c-161">gdzie *nazwa* jest nazwą i *numer* jest numer grupy przechwytywania, *tak* jest wyrażeniem do dopasowania, jeśli *nazwa* lub *numer* jest zgodny i *nie* wyrażenie opcjonalne do dopasowania, jeśli nie jest.</span><span class="sxs-lookup"><span data-stu-id="ca16c-161">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="ca16c-162">Jeśli *nazwa* nie odpowiada na nazwę grupy przechwytywania, który jest używany w wzorzec wyrażenia regularnego, konstrukcja alternacyjne jest interpretowana jako testu wyrażenie zgodnie z objaśnieniem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ca16c-162">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="ca16c-163">Zazwyczaj oznacza to, że *wyrażenie* daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="ca16c-163">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="ca16c-164">Jeśli *numer* jest niezgodne z numerem grupy przechwytywania, używanym w wzorzec wyrażenia regularnego zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="ca16c-164">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="ca16c-165">Poniższy przykład jest odmianą przykładu, która jest wyświetlana w [albo / lub z dopasowywanie do wzorców &#124;](#Either_Or) sekcji.</span><span class="sxs-lookup"><span data-stu-id="ca16c-165">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="ca16c-166">Używa przechwytywania grupę o nazwie `n2` składający się z dwóch cyfr zostały wykonane przez łącznik.</span><span class="sxs-lookup"><span data-stu-id="ca16c-166">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="ca16c-167">Wyrażenia warunkowe utworzenia testów, czy ta grupa przechwytywania ma dopasowane w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="ca16c-167">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="ca16c-168">Jeśli ma ona alternacyjne skonstruować próbuje dopasować ostatnich siedmiu cyfr US dziewięciu cyfr Numer identyfikacyjny pracodawcy (NIP).</span><span class="sxs-lookup"><span data-stu-id="ca16c-168">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="ca16c-169">Jeśli go nie ma, próbuje odpowiada USA dziewięciu cyfr Numer ubezpieczenia społecznego (SSN).</span><span class="sxs-lookup"><span data-stu-id="ca16c-169">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="ca16c-170">Wzorzec wyrażenia regularnego `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowany, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ca16c-170">The regular expression pattern `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="ca16c-171">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="ca16c-171">Pattern</span></span>|<span data-ttu-id="ca16c-172">Opis</span><span class="sxs-lookup"><span data-stu-id="ca16c-172">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="ca16c-173">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-173">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)*`|<span data-ttu-id="ca16c-174">Wystąpienie dopasowania zero lub jeden dwie cyfry oraz łącznik.</span><span class="sxs-lookup"><span data-stu-id="ca16c-174">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="ca16c-175">Określ nazwę tej grupy przechwytywania `n2`.</span><span class="sxs-lookup"><span data-stu-id="ca16c-175">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="ca16c-176">Test czy `n2` został uzyskany w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="ca16c-176">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="ca16c-177">Jeśli `n2` został zgodne, zgodne siedmiu cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="ca16c-177">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="ca16c-178">Jeśli `n2` nie było zgodne, zgodne trzech cyfr dziesiętnych, łącznik dwóch cyfr dziesiętnych, inny łącznik i czterech cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="ca16c-178">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="ca16c-179">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="ca16c-179">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="ca16c-180">W poniższym przykładzie przedstawiono zmiany w tym przykładzie, który korzysta z numerem grupy zamiast nazwaną grupę.</span><span class="sxs-lookup"><span data-stu-id="ca16c-180">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="ca16c-181">Jest jego wzorzec wyrażenia regularnego `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="ca16c-181">Its regular expression pattern is `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ca16c-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca16c-182">See Also</span></span>  
 [<span data-ttu-id="ca16c-183">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="ca16c-183">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
