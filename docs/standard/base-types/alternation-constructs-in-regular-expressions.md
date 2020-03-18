---
title: Konstrukcje naprzemienne w wyrażeniach regularnych .NET
description: Dowiedz się, jak używać konstrukcji naprzemiennych do uzgadniania warunkowego w wyrażeniach regularnych.
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
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159692"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="f48a0-103">Konstrukcje alternacyjne w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="f48a0-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="f48a0-104">Konstrukcje alternation modyfikują wyrażenie regularne, aby włączyć dopasowywanie warunkowe lub dopasowanie warunkowe.</span><span class="sxs-lookup"><span data-stu-id="f48a0-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="f48a0-105">.NET obsługuje trzy konstrukcje naprzemienne:</span><span class="sxs-lookup"><span data-stu-id="f48a0-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="f48a0-106">Dopasowanie wzorców do &#124;</span><span class="sxs-lookup"><span data-stu-id="f48a0-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="f48a0-107">Warunkowe dopasowanie z (?( wyrażenie)tak&#124;nie)</span><span class="sxs-lookup"><span data-stu-id="f48a0-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="f48a0-108">Uzgadnianie warunkowe na podstawie prawidłowej przechwyconej grupy</span><span class="sxs-lookup"><span data-stu-id="f48a0-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="f48a0-109">Dopasowanie wzorca do &#124;</span><span class="sxs-lookup"><span data-stu-id="f48a0-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="f48a0-110">Można użyć pionowego`|`paska ( ) znaku, aby dopasować dowolny z serii wzorów, gdzie `|` znak oddziela każdy wzór.</span><span class="sxs-lookup"><span data-stu-id="f48a0-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="f48a0-111">Podobnie jak dodatnia `|` klasa znaków, znak może być używany do dopasowania jednego z wielu pojedynczych znaków.</span><span class="sxs-lookup"><span data-stu-id="f48a0-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="f48a0-112">W poniższym przykładzie użyto zarówno dodatniej klasy `|` znaków, jak i dopasowania albo/lub wzorca do znaku, aby zlokalizować wystąpienia słów "szary" lub "szary" w ciągu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="f48a0-113">W takim przypadku `|` znak tworzy wyrażenie regularne, które jest bardziej pełne.</span><span class="sxs-lookup"><span data-stu-id="f48a0-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="f48a0-114">Wyrażenie regularne, które `|` używa `\bgr(a|e)y\b`znaku, jest interpretowane w sposób pokazany w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="f48a0-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="f48a0-115">Wzorce</span><span class="sxs-lookup"><span data-stu-id="f48a0-115">Pattern</span></span>|<span data-ttu-id="f48a0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f48a0-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f48a0-117">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="f48a0-118">Dopasuj znaki "gr".</span><span class="sxs-lookup"><span data-stu-id="f48a0-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="f48a0-119">Dopasowuje znak „a” lub „e”.</span><span class="sxs-lookup"><span data-stu-id="f48a0-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="f48a0-120">Dopasuj "y" na granicy słowa.</span><span class="sxs-lookup"><span data-stu-id="f48a0-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="f48a0-121">Znak `|` może być również używany do wykonywania jednego/lub dopasowania do wielu znaków lub podwyrażeń, które mogą zawierać dowolną kombinację literałów znaków i elementów języka wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="f48a0-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="f48a0-122">(Klasa znaków nie udostępnia tej funkcji). Poniższy przykład używa `|` tego znaku do wyodrębnienia numeru ubezpieczenia społecznego (SSN), który jest 9-cyfrowym numerem o formacie- *ddd*-*ddddd*-*dddd*lub numerem identyfikacyjnym amerykańskiego pracodawcy (EIN), który jest 9-cyfrowym numerem o formacie*dddddddd.* *dd*</span><span class="sxs-lookup"><span data-stu-id="f48a0-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="f48a0-123">Wyrażenie `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` regularne jest interpretowane w sposób pokazany w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="f48a0-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="f48a0-124">Wzorce</span><span class="sxs-lookup"><span data-stu-id="f48a0-124">Pattern</span></span>|<span data-ttu-id="f48a0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f48a0-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f48a0-126">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="f48a0-127">Dopasuj jedną z następujących czynności: dwie cyfry dziesiętne, po których następuje łącznik, po którym następuje siedem cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="f48a0-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="f48a0-128">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="f48a0-129">Warunkowe uzgadnianie z wyrażeniem</span><span class="sxs-lookup"><span data-stu-id="f48a0-129">Conditional matching with an expression</span></span>

<span data-ttu-id="f48a0-130">Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy można dopasować wzorzec początkowy.</span><span class="sxs-lookup"><span data-stu-id="f48a0-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="f48a0-131">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="f48a0-131">Its syntax is:</span></span>  

<span data-ttu-id="f48a0-132">`(?(`*wyrażenie* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="f48a0-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="f48a0-133">gdzie *wyrażenie* jest początkowy wzorzec do dopasowania, *tak* jest wzorzec, aby dopasować, jeśli *wyrażenie* jest dopasowane, a *nie* jest opcjonalny wzorzec, aby dopasować, jeśli *wyrażenie* nie jest dopasowane.</span><span class="sxs-lookup"><span data-stu-id="f48a0-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="f48a0-134">Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie o zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie zaliczki w strumieniu wejściowym po ocenia *wyrażenie*.</span><span class="sxs-lookup"><span data-stu-id="f48a0-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="f48a0-135">W związku z tym ta konstrukcja jest odpowiednikiem następujących:</span><span class="sxs-lookup"><span data-stu-id="f48a0-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="f48a0-136">`(?(?=`*wyrażenie* `)` *tak* `|` *nie*`)`</span><span class="sxs-lookup"><span data-stu-id="f48a0-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="f48a0-137">gdzie `(?=` *wyrażenie* `)` jest konstrukcją potwierdzenia o zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="f48a0-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="f48a0-138">(Aby uzyskać więcej informacji, zobacz [Grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md).) Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako kotwicę (twierdzenie o zerowej szerokości), *wyrażenie* musi być potwierdzeniem o zerowej szerokości (aby uzyskać więcej informacji, zobacz [Kotwice)](anchors-in-regular-expressions.md)lub wyrażeniem podrzędnym, które jest również zawarte w *yes*.</span><span class="sxs-lookup"><span data-stu-id="f48a0-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="f48a0-139">W przeciwnym razie nie można dopasować wzorca *tak.*</span><span class="sxs-lookup"><span data-stu-id="f48a0-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f48a0-140">Jeśli *wyrażenie* jest nazwaną lub numerowane grupy przechwytywania, konstrukcja naprzemienna jest interpretowany jako test przechwytywania; Aby uzyskać więcej informacji, zobacz następną sekcję [Dopasowanie warunkowe na podstawie prawidłowej grupy przechwytywania](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="f48a0-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="f48a0-141">Innymi słowy aparat wyrażeń regularnych nie próbuje dopasować przechwyconego podciągu, ale zamiast tego testuje obecność lub brak grupy.</span><span class="sxs-lookup"><span data-stu-id="f48a0-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="f48a0-142">Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji [Dopasowywanie wzorców lub do &#124;.](#Either_Or)</span><span class="sxs-lookup"><span data-stu-id="f48a0-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="f48a0-143">Używa dopasowania warunkowego, aby ustalić, czy pierwsze trzy znaki po granicy wyrazu są dwie mastce, po którym następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="f48a0-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="f48a0-144">Jeśli tak, próbuje dopasować numer identyfikacyjny amerykańskiego pracodawcy (EIN).</span><span class="sxs-lookup"><span data-stu-id="f48a0-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="f48a0-145">Jeśli nie, próbuje dopasować numer ubezpieczenia społecznego USA (SSN).</span><span class="sxs-lookup"><span data-stu-id="f48a0-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="f48a0-146">Wzorzec `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="f48a0-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="f48a0-147">Wzorce</span><span class="sxs-lookup"><span data-stu-id="f48a0-147">Pattern</span></span>|<span data-ttu-id="f48a0-148">Opis</span><span class="sxs-lookup"><span data-stu-id="f48a0-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f48a0-149">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="f48a0-150">Określ, czy następne trzy znaki składają się z dwóch cyfr, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="f48a0-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="f48a0-151">Jeśli poprzedni wzorzec jest zgodny, dopasuj dwie cyfry, po których następuje łącznik, po którym następują siedem cyfr.</span><span class="sxs-lookup"><span data-stu-id="f48a0-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="f48a0-152">Jeśli poprzedni wzorzec nie jest zgodny, dopasuj trzy cyfry dziesiętne: łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="f48a0-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="f48a0-153">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="f48a0-154">Uzgadnianie warunkowe na podstawie prawidłowej przechwyconej grupy</span><span class="sxs-lookup"><span data-stu-id="f48a0-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="f48a0-155">Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy dopasował określoną grupę przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="f48a0-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="f48a0-156">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="f48a0-156">Its syntax is:</span></span>

<span data-ttu-id="f48a0-157">`(?(`*nazwa* `)` *tak nie* `|` *no*`)`</span><span class="sxs-lookup"><span data-stu-id="f48a0-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="f48a0-158">lub</span><span class="sxs-lookup"><span data-stu-id="f48a0-158">or</span></span>

<span data-ttu-id="f48a0-159">`(?(`*liczba* `)` *tak nie* `|` *no*`)`</span><span class="sxs-lookup"><span data-stu-id="f48a0-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="f48a0-160">gdzie *nazwa* jest nazwą, a *liczba* jest numerem grupy przechwytywania, *tak* jest wyrażeniem pasującym, jeśli *nazwa* lub *liczba* ma dopasowanie, a *nie* jest opcjonalnym wyrażeniem, które jest zgodne, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="f48a0-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="f48a0-161">Jeśli *nazwa* nie odpowiada nazwie grupy przechwytywania, która jest używana w wzorcu wyrażenia regularnego, konstrukcja naprzemienna jest interpretowana jako test wyrażenia, jak wyjaśniono w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f48a0-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="f48a0-162">Zazwyczaj oznacza to, *expression* że wyrażenie `false`oblicza .</span><span class="sxs-lookup"><span data-stu-id="f48a0-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="f48a0-163">Jeśli *liczba* nie odpowiada numerowanej grupie przechwytywania, która jest używana we wzorcu <xref:System.ArgumentException>wyrażenia regularnego, aparat wyrażeń regularnych zgłasza plik .</span><span class="sxs-lookup"><span data-stu-id="f48a0-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="f48a0-164">Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji [Dopasowywanie wzorców lub do &#124;.](#Either_Or)</span><span class="sxs-lookup"><span data-stu-id="f48a0-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="f48a0-165">Używa grupy przechwytywania o `n2` nazwie, która składa się z dwóch cyfr, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="f48a0-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="f48a0-166">Konstrukcja naprzemienna sprawdza, czy ta grupa przechwytywania została dopasowana w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="f48a0-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="f48a0-167">Jeśli tak, konstrukcja naprzemienna próbuje dopasować ostatnie siedem cyfr dziewięciocyfrowego numeru identyfikacyjnego pracodawcy (EIN).</span><span class="sxs-lookup"><span data-stu-id="f48a0-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="f48a0-168">Jeśli tak nie jest, próbuje dopasować dziewięciocyfrowy numer ubezpieczenia społecznego (SSN).</span><span class="sxs-lookup"><span data-stu-id="f48a0-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="f48a0-169">Wzorzec `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` wyrażenia regularnego jest interpretowany w sposób pokazany w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="f48a0-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="f48a0-170">Wzorce</span><span class="sxs-lookup"><span data-stu-id="f48a0-170">Pattern</span></span>|<span data-ttu-id="f48a0-171">Opis</span><span class="sxs-lookup"><span data-stu-id="f48a0-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f48a0-172">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="f48a0-173">Dopasuj zero lub jedno wystąpienie dwóch cyfr, po którym następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="f48a0-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="f48a0-174">Nazwij tę `n2`grupę przechwytywania .</span><span class="sxs-lookup"><span data-stu-id="f48a0-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="f48a0-175">Sprawdź, `n2` czy został dopasowany w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="f48a0-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="f48a0-176">Jeśli `n2` został dopasowany, dopasuj siedem cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="f48a0-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="f48a0-177">Jeśli `n2` nie został dopasowany, dopasuj trzy cyfry dziesiętne: łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="f48a0-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="f48a0-178">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="f48a0-178">Match a word boundary.</span></span>|  

<span data-ttu-id="f48a0-179">Odmiana tego przykładu, która używa ponumerowanej grupy zamiast nazwanej grupy jest pokazana w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f48a0-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="f48a0-180">Jego wzorzec wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="f48a0-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="f48a0-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f48a0-181">See also</span></span>

- [<span data-ttu-id="f48a0-182">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="f48a0-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
