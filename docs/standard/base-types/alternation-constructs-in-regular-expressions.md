---
title: Konstrukcje alternacyjne w wyrażeniach regularnych programu .NET
description: Dowiedz się, jak na potrzeby konstrukcje dopasowanie warunkowe w wyrażeniach regularnych.
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 756d63be456dce10ca9e95963ed25602e6f4aec1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634784"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="5069e-103">Konstrukcje alternacyjne w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="5069e-103">Alternation Constructs in Regular Expressions</span></span>
<a name="top"></a> <span data-ttu-id="5069e-104">Konstrukcje zmiany modyfikują wyrażenie regularne, aby włączyć opcję / lub lub dopasowanie warunkowe.</span><span class="sxs-lookup"><span data-stu-id="5069e-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="5069e-105">.NET obsługuje trzy konstrukcje zmiany:</span><span class="sxs-lookup"><span data-stu-id="5069e-105">.NET supports three alternation constructs:</span></span>  
  
- [<span data-ttu-id="5069e-106">Dopasowywanie wzorca z&#124;</span><span class="sxs-lookup"><span data-stu-id="5069e-106">Pattern matching with &#124;</span></span>](#Either_Or)  
  
- [<span data-ttu-id="5069e-107">Dopasowanie warunkowe z (? () wyrażenie) tak&#124;nie)</span><span class="sxs-lookup"><span data-stu-id="5069e-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)  
  
- [<span data-ttu-id="5069e-108">Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach</span><span class="sxs-lookup"><span data-stu-id="5069e-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)  
  
<a name="Either_Or"></a>   
## <a name="pattern-matching-with-124"></a><span data-ttu-id="5069e-109">Dopasowywanie wzorca z&#124;</span><span class="sxs-lookup"><span data-stu-id="5069e-109">Pattern Matching with &#124;</span></span>  
 <span data-ttu-id="5069e-110">Można użyć pionowy pasek (`|`) znaku, aby dopasować dowolny z szeregu wzorców, gdzie `|` rozdziela każdy wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5069e-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>  
  
 <span data-ttu-id="5069e-111">Klasy znaków pozytywnych, takich jak `|` znak może być użyty do dopasowania dowolną liczbę pojedynczych znaków.</span><span class="sxs-lookup"><span data-stu-id="5069e-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="5069e-112">W poniższym przykładzie użyto klasy znaków pozytywnych i albo / lub za pomocą dopasowywania do wzorca `|` znaku, aby zlokalizować wystąpienia słowa "szarym" lub "szare" w ciągu.</span><span class="sxs-lookup"><span data-stu-id="5069e-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="5069e-113">W tym przypadku `|` znaków generuje wyrażeń regularnych, które jest pełniejszy.</span><span class="sxs-lookup"><span data-stu-id="5069e-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
 [!code-vb[RegularExpressions.Language.Alternation#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]  
  
 <span data-ttu-id="5069e-114">Wyrażenie regularne, które używa `|` znak `\bgr(a|e)y\b`, jest interpretowane tak jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5069e-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5069e-115">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5069e-115">Pattern</span></span>|<span data-ttu-id="5069e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5069e-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="5069e-117">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="5069e-118">Dopasowuje znaki "gr".</span><span class="sxs-lookup"><span data-stu-id="5069e-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="5069e-119">Dopasowuje znak „a” lub „e”.</span><span class="sxs-lookup"><span data-stu-id="5069e-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="5069e-120">Dopasowuje "y" na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-120">Match a "y" on a word boundary.</span></span>|  
  
 <span data-ttu-id="5069e-121">`|` Znaku można również przeprowadzić albo / lub zgodne z wielu znaków lub podwyrażenia, które mogą obejmować dowolną kombinację literały znakowe i elementy języka wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="5069e-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="5069e-122">(Klasy znaku nie zapewnia tej funkcji). W poniższym przykładzie użyto `|` znaków do wyodrębnienia albo USA Numer ubezpieczenia społecznego (SSN), czyli 9 cyfr w formacie *ddd*-*dd*-*dddd*, lub Pracodawca Identyfikacja numeru (NIP), czyli 9 cyfr w formacie *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="5069e-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
 [!code-vb[RegularExpressions.Language.Alternation#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  
  
 <span data-ttu-id="5069e-123">Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5069e-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5069e-124">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5069e-124">Pattern</span></span>|<span data-ttu-id="5069e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5069e-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="5069e-126">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="5069e-127">Odpowiada jednej z następujących pozycji: dwie cyfry dziesiętne, następuje łącznik następuje siedmiu cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="5069e-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="5069e-128">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-128">End the match at a word boundary.</span></span>|  
  
 [<span data-ttu-id="5069e-129">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="5069e-129">Back to top</span></span>](#top)  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="5069e-130">Dopasowanie warunkowe z wyrażeniem</span><span class="sxs-lookup"><span data-stu-id="5069e-130">Conditional Matching with an Expression</span></span>  
 <span data-ttu-id="5069e-131">Ten element języka podejmuje próbę dopasowania, jednym z dwóch wzorców w zależności od tego, czy może dopasować wzorca początkowej.</span><span class="sxs-lookup"><span data-stu-id="5069e-131">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="5069e-132">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5069e-132">Its syntax is:</span></span>  
  
 <span data-ttu-id="5069e-133">`(?(` *wyrażenie* `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="5069e-133">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="5069e-134">gdzie *wyrażenie* jest początkowa wzorzec do dopasowania, *tak* jest wzorzec do dopasowania, jeśli *wyrażenie* jest dopasowywany i *nie* jest opcjonalna wzorzec do dopasowania, jeśli *wyrażenie* nie został dopasowany.</span><span class="sxs-lookup"><span data-stu-id="5069e-134">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="5069e-135">Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie awansować w strumień wejściowy po ocenia *wyrażenie*.</span><span class="sxs-lookup"><span data-stu-id="5069e-135">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="5069e-136">Dlatego ta konstrukcja jest odpowiednikiem następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5069e-136">Therefore, this construct is equivalent to the following:</span></span>  
  
 <span data-ttu-id="5069e-137">`(?(?=` *wyrażenie* `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="5069e-137">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="5069e-138">gdzie `(?=` *wyrażenie* `)` to konstrukcja asercja o zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="5069e-138">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="5069e-139">(Aby uzyskać więcej informacji, zobacz [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako elementu zakotwiczenia (asercja o zerowej szerokości), *wyrażenie* musi być asercja o zerowej szerokości (Aby uzyskać więcej informacji, zobacz [ Kotwice](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) lub Podwyrażenie, które również znajdują się w *tak*.</span><span class="sxs-lookup"><span data-stu-id="5069e-139">(For more information, see [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="5069e-140">W przeciwnym razie *tak* nie można dopasować wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5069e-140">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5069e-141">Jeśli *wyrażenie*jest nazwana lub numerowana grupa przechwytywania, konstrukcje jest interpretowana jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [warunkowego dopasowania na podstawie prawidłowej grupy przechwytywania](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="5069e-141">If *expression*is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="5069e-142">Innymi słowy aparat wyrażeń regularnych nie jest podejmowana próba Dopasuj podciąg przechwycony, ale zamiast tego sprawdza obecność lub Brak grupy.</span><span class="sxs-lookup"><span data-stu-id="5069e-142">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
 <span data-ttu-id="5069e-143">Poniższy przykład jest odmianą przykładu, który pojawia się w [albo / lub za pomocą dopasowywania do wzorca &#124; ](#Either_Or) sekcji.</span><span class="sxs-lookup"><span data-stu-id="5069e-143">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="5069e-144">Aby ustalić, czy pierwsze trzy znaki po granicy słowa dwie cyfry, następuje łącznik używa dopasowanie warunkowe.</span><span class="sxs-lookup"><span data-stu-id="5069e-144">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="5069e-145">Jeśli są one podejmuje próbę dopasowania Federalny Numer identyfikacji podatkowej (NIP).</span><span class="sxs-lookup"><span data-stu-id="5069e-145">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="5069e-146">W przeciwnym razie podejmuje próbę dopasowania Federalny Numer ubezpieczenia społecznego (SSN).</span><span class="sxs-lookup"><span data-stu-id="5069e-146">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
 [!code-vb[RegularExpressions.Language.Alternation#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]  
  
 <span data-ttu-id="5069e-147">Definicję wzorca wyrażenia regularnego `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5069e-147">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5069e-148">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5069e-148">Pattern</span></span>|<span data-ttu-id="5069e-149">Opis</span><span class="sxs-lookup"><span data-stu-id="5069e-149">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="5069e-150">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-150">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="5069e-151">Ustal, czy kolejne trzy znaki składają się z dwóch cyfr następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="5069e-151">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="5069e-152">Jeśli poprzedni wzorzec jest zgodny, dopasowuje dwie cyfry, następuje łącznik następuje siedmiu cyfr.</span><span class="sxs-lookup"><span data-stu-id="5069e-152">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="5069e-153">Jeśli poprzedni wzorzec nie jest zgodny, zgodne trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="5069e-153">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="5069e-154">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-154">Match a word boundary.</span></span>|  
  
 [<span data-ttu-id="5069e-155">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="5069e-155">Back to top</span></span>](#top)  
  
<a name="Conditional_Group"></a>   
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="5069e-156">Dopasowanie warunkowe oparte na prawidłowo przechwyconych grupach</span><span class="sxs-lookup"><span data-stu-id="5069e-156">Conditional Matching Based on a Valid Captured Group</span></span>  
 <span data-ttu-id="5069e-157">Ten element języka podejmuje próbę dopasowania, jednym z dwóch wzorców w zależności od tego, czy dopasowywane określonej grupy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="5069e-157">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="5069e-158">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5069e-158">Its syntax is:</span></span>  
  
 <span data-ttu-id="5069e-159">`(?(` *Nazwa* `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="5069e-159">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="5069e-160">lub</span><span class="sxs-lookup"><span data-stu-id="5069e-160">or</span></span>  
  
 <span data-ttu-id="5069e-161">`(?(` *Liczba* `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="5069e-161">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>  
  
 <span data-ttu-id="5069e-162">gdzie *nazwa* nazywa się i *numer* jest numerem grupy przechwytywania, *tak* jest wyrażeniem które pasują, jeśli *nazwa* lub *numer* jest zgodny, oraz *nie* jest opcjonalne wyrażenie dopasowania, jeśli nie ma.</span><span class="sxs-lookup"><span data-stu-id="5069e-162">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>  
  
 <span data-ttu-id="5069e-163">Jeśli *nazwa* nie odpowiada na nazwę grupy przechwytywania, który jest używany we wzorcu wyrażenia regularnego, konstrukcje jest interpretowana jako test wyrażenia, zgodnie z opisem w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5069e-163">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="5069e-164">Zazwyczaj oznacza to, że *wyrażenie* daje w wyniku `false`.</span><span class="sxs-lookup"><span data-stu-id="5069e-164">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="5069e-165">Jeśli *numer* nie odpowiada numerowaną grupę przechwytywania, który jest używany we wzorcu wyrażenia regularnego zgłasza aparat wyrażeń regularnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="5069e-165">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>  
  
 <span data-ttu-id="5069e-166">Poniższy przykład jest odmianą przykładu, który pojawia się w [albo / lub za pomocą dopasowywania do wzorca &#124; ](#Either_Or) sekcji.</span><span class="sxs-lookup"><span data-stu-id="5069e-166">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="5069e-167">Używa ona grupa przechwytywania o nazwie `n2` składający się z dwóch cyfr następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="5069e-167">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="5069e-168">Konstrukcja testów czy ta grupa przechwytywania został dopasowany do ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="5069e-168">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="5069e-169">Jeśli tak, konstrukcja warunkowa próbuje dopasować ostatnich siedmiu cyfr US dziewięciu cyfr Numer identyfikacji podatkowej (NIP).</span><span class="sxs-lookup"><span data-stu-id="5069e-169">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="5069e-170">Jeśli nie ma on podejmuje próbę dopasowania USA dziewięciu cyfr Numer ubezpieczenia społecznego (SSN).</span><span class="sxs-lookup"><span data-stu-id="5069e-170">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
 [!code-vb[RegularExpressions.Language.Alternation#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]  
  
 <span data-ttu-id="5069e-171">Definicję wzorca wyrażenia regularnego `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane tak jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5069e-171">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="5069e-172">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5069e-172">Pattern</span></span>|<span data-ttu-id="5069e-173">Opis</span><span class="sxs-lookup"><span data-stu-id="5069e-173">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="5069e-174">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-174">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="5069e-175">Dopasowanie zera lub jednego wystąpienia dwie cyfry, następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="5069e-175">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="5069e-176">Określ nazwę tej grupy przechwytywania `n2`.</span><span class="sxs-lookup"><span data-stu-id="5069e-176">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="5069e-177">Test czy `n2` zostały dopasowane do ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="5069e-177">Test whether `n2` was matched in the input string.</span></span>|  
|`)\d{7}`|<span data-ttu-id="5069e-178">Jeśli `n2` został dopasowany, pasuje do siedmiu cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="5069e-178">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="5069e-179">Jeśli `n2` nie zostały dopasowane do elementu, dopasowania trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="5069e-179">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="5069e-180">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="5069e-180">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="5069e-181">Zmiany w tym przykładzie, która używa numerowanej grupy zamiast nazwaną grupę przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5069e-181">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="5069e-182">Jej wzorca wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="5069e-182">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Alternation#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
 [!code-vb[RegularExpressions.Language.Alternation#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5069e-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5069e-183">See also</span></span>

- [<span data-ttu-id="5069e-184">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="5069e-184">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
