---
title: Konstrukcje warunkowe w wyrażeniach regularnych programu .NET
description: Dowiedz się, w jaki sposób używać konstrukcji warunkowych do dopasowywania w wyrażeniach regularnych.
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
ms.custom: seodec18
ms.openlocfilehash: 352cfd65cd4620d8274ff0a14ea507cd49522470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140555"
---
# <a name="alternation-constructs-in-regular-expressions"></a><span data-ttu-id="9209f-103">Konstrukcje alternacyjne w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="9209f-103">Alternation Constructs in Regular Expressions</span></span>

<span data-ttu-id="9209f-104">Konstrukcje warunkowe modyfikują wyrażenie regularne, aby umożliwić Dopasowanie warunkowe/lub lub.</span><span class="sxs-lookup"><span data-stu-id="9209f-104">Alternation constructs modify a regular expression to enable either/or or conditional matching.</span></span> <span data-ttu-id="9209f-105">Platforma .NET obsługuje trzy konstrukcje warunkowe:</span><span class="sxs-lookup"><span data-stu-id="9209f-105">.NET supports three alternation constructs:</span></span>

- [<span data-ttu-id="9209f-106">Dopasowanie wzorca z&#124;</span><span class="sxs-lookup"><span data-stu-id="9209f-106">Pattern matching with &#124;</span></span>](#Either_Or)
- [<span data-ttu-id="9209f-107">Warunkowe dopasowanie do (? ( wyrażenie) tak&#124;nie)</span><span class="sxs-lookup"><span data-stu-id="9209f-107">Conditional matching with (?(expression)yes&#124;no)</span></span>](#Conditional_Expr)
- [<span data-ttu-id="9209f-108">Dopasowanie warunkowe oparte na prawidłowej przechwyconej grupie</span><span class="sxs-lookup"><span data-stu-id="9209f-108">Conditional matching based on a valid captured group</span></span>](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a><span data-ttu-id="9209f-109">Dopasowanie wzorca z&#124;</span><span class="sxs-lookup"><span data-stu-id="9209f-109">Pattern Matching with &#124;</span></span>

<span data-ttu-id="9209f-110">Można użyć znaku kreski pionowej (`|`), aby dopasować każdą z serii wzorców, gdzie znak `|` oddziela każdy wzorzec.</span><span class="sxs-lookup"><span data-stu-id="9209f-110">You can use the vertical bar (`|`) character to match any one of a series of patterns, where the `|` character separates each pattern.</span></span>

<span data-ttu-id="9209f-111">Podobnie jak w przypadku klasy znaków pozytywnych, znak `|` może być używany w celu dopasowania do jednej z wielu pojedynczych znaków.</span><span class="sxs-lookup"><span data-stu-id="9209f-111">Like the positive character class, the `|` character can be used to match any one of a number of single characters.</span></span> <span data-ttu-id="9209f-112">Poniższy przykład używa zarówno klasy znaku dodatniego, jak i/lub dopasowania wzorca ze znakiem `|`, aby zlokalizować wystąpienia wyrazów "szary" lub "szary" w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9209f-112">The following example uses both a positive character class and either/or pattern matching with the `|` character to locate occurrences of the words "gray" or "grey" in a string.</span></span> <span data-ttu-id="9209f-113">W tym przypadku znak `|` generuje wyrażenie regularne, które jest bardziej pełne.</span><span class="sxs-lookup"><span data-stu-id="9209f-113">In this case, the `|` character produces a regular expression that is more verbose.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

<span data-ttu-id="9209f-114">Wyrażenie regularne używające znaku `|`, `\bgr(a|e)y\b`, jest interpretowane jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="9209f-114">The regular expression that uses the `|` character, `\bgr(a|e)y\b`, is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="9209f-115">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="9209f-115">Pattern</span></span>|<span data-ttu-id="9209f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9209f-116">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="9209f-117">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-117">Start at a word boundary.</span></span>|  
|`gr`|<span data-ttu-id="9209f-118">Dopasowuje znaki "gr".</span><span class="sxs-lookup"><span data-stu-id="9209f-118">Match the characters "gr".</span></span>|  
|<code>(a&#124;e)</code>|<span data-ttu-id="9209f-119">Dopasowuje znak „a” lub „e”.</span><span class="sxs-lookup"><span data-stu-id="9209f-119">Match either an "a" or an "e".</span></span>|  
|`y\b`|<span data-ttu-id="9209f-120">Dopasowuje znak "y" na granicy słowa.</span><span class="sxs-lookup"><span data-stu-id="9209f-120">Match a "y" on a word boundary.</span></span>|  

<span data-ttu-id="9209f-121">Znaku `|` można również użyć do wykonania elementu/lub dopasowania z wieloma znakami lub podwyrażeniami, które mogą zawierać dowolną kombinację literałów znakowych i elementy języka wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="9209f-121">The `|` character can also be used to perform an either/or match with multiple characters or subexpressions, which can include any combination of character literals and regular expression language elements.</span></span> <span data-ttu-id="9209f-122">(Klasa znaku nie zapewnia tej funkcji). Poniższy przykład używa znaku `|`, aby wyodrębnić numer ubezpieczenia społecznego (SSN) w Stanach Zjednoczonych, który jest 9-cyfrowym numerem w formacie *ddd*-*DD*-*dddd*lub numerem identyfikacyjnym pracodawcy USA (EIN), który jest 9-cyfrowym numerem z formatem *dd*-*ddddddd*.</span><span class="sxs-lookup"><span data-stu-id="9209f-122">(The character class does not provide this functionality.) The following example uses the `|` character to extract either a U.S. Social Security Number (SSN), which is a 9-digit number with the format *ddd*-*dd*-*dddd*, or a U.S. Employer Identification Number (EIN), which is a 9-digit number with the format *dd*-*ddddddd*.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

<span data-ttu-id="9209f-123">Wyrażenie regularne `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` jest interpretowane jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="9209f-123">The regular expression `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>
  
|<span data-ttu-id="9209f-124">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="9209f-124">Pattern</span></span>|<span data-ttu-id="9209f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9209f-125">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="9209f-126">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-126">Start at a word boundary.</span></span>|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|<span data-ttu-id="9209f-127">Dopasowuje jedną z następujących wartości: dwie cyfry dziesiętne, po których następuje łącznik, a po nich siedem cyfr dziesiętnych; lub trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="9209f-127">Match either of the following: two decimal digits followed by a hyphen followed by seven decimal digits; or three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\d`|<span data-ttu-id="9209f-128">Kończy dopasowanie na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-128">End the match at a word boundary.</span></span>|  
  
<a name="Conditional_Expr"></a>   
## <a name="conditional-matching-with-an-expression"></a><span data-ttu-id="9209f-129">Warunkowe dopasowanie z wyrażeniem</span><span class="sxs-lookup"><span data-stu-id="9209f-129">Conditional matching with an expression</span></span>

<span data-ttu-id="9209f-130">Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy może on pasować do wzorca początkowego.</span><span class="sxs-lookup"><span data-stu-id="9209f-130">This language element attempts to match one of two patterns depending on whether it can match an initial pattern.</span></span> <span data-ttu-id="9209f-131">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="9209f-131">Its syntax is:</span></span>  

<span data-ttu-id="9209f-132">*wyrażenie* `(?(` `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="9209f-132">`(?(` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="9209f-133">*wyrażenie* WHERE jest wzorcem początkowym, *tak* aby pasowało do wzorca, jeśli *wyrażenie* jest dopasowane, a *nie* jest opcjonalnym wzorcem do dopasowania, jeśli *wyrażenie* nie jest zgodne.</span><span class="sxs-lookup"><span data-stu-id="9209f-133">where *expression* is the initial pattern to match, *yes* is the pattern to match if *expression* is matched, and *no* is the optional pattern to match if *expression* is not matched.</span></span> <span data-ttu-id="9209f-134">Aparat wyrażeń regularnych traktuje *wyrażenie* jako potwierdzenie o zerowej szerokości; oznacza to, że aparat wyrażeń regularnych nie postępuje w strumieniu wejściowym po obliczeniu *wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="9209f-134">The regular expression engine treats *expression* as a zero-width assertion; that is, the regular expression engine does not advance in the input stream after it evaluates *expression*.</span></span> <span data-ttu-id="9209f-135">W związku z tym konstrukcja ta jest równoważna następującym:</span><span class="sxs-lookup"><span data-stu-id="9209f-135">Therefore, this construct is equivalent to the following:</span></span>

<span data-ttu-id="9209f-136">*wyrażenie* `(?(?=` `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="9209f-136">`(?(?=` *expression* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="9209f-137">gdzie `(?=`*expression*`)` jest konstrukcja potwierdzenia o zerowej szerokości.</span><span class="sxs-lookup"><span data-stu-id="9209f-137">where `(?=`*expression*`)` is a zero-width assertion construct.</span></span> <span data-ttu-id="9209f-138">(Aby uzyskać więcej informacji, zobacz [grupowanie konstrukcji](grouping-constructs-in-regular-expressions.md)). Ponieważ aparat wyrażeń regularnych interpretuje *wyrażenie* jako zakotwiczenie (potwierdzenie o zerowej szerokości), *wyrażenie* musi być potwierdzeniem o zerowej szerokości (Aby uzyskać więcej informacji, zobacz [kotwice](anchors-in-regular-expressions.md)) lub Podwyrażenie, które jest również zawarte w *tak*.</span><span class="sxs-lookup"><span data-stu-id="9209f-138">(For more information, see [Grouping Constructs](grouping-constructs-in-regular-expressions.md).) Because the regular expression engine interprets *expression* as an anchor (a zero-width assertion), *expression* must either be a zero-width assertion (for more information, see [Anchors](anchors-in-regular-expressions.md)) or a subexpression that is also contained in *yes*.</span></span> <span data-ttu-id="9209f-139">W przeciwnym razie nie można dopasować wzorca *tak* .</span><span class="sxs-lookup"><span data-stu-id="9209f-139">Otherwise, the *yes* pattern cannot be matched.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9209f-140">Jeśli *wyrażenie* jest nazwaną lub numerowaną grupą przechwytywania, konstrukcja alternatywna jest interpretowana jako test przechwytywania. Aby uzyskać więcej informacji, zobacz następną sekcję, [Dopasowanie warunkowe na podstawie prawidłowej grupy przechwytywania](#Conditional_Group).</span><span class="sxs-lookup"><span data-stu-id="9209f-140">If *expression* is a named or numbered capturing group, the alternation construct is interpreted as a capture test; for more information, see the next section, [Conditional Matching Based on a Valid Capture Group](#Conditional_Group).</span></span> <span data-ttu-id="9209f-141">Innymi słowy aparat wyrażeń regularnych nie próbuje dopasować przechwyconego podciągu, ale zamiast tego testuje obecność lub brak grupy.</span><span class="sxs-lookup"><span data-stu-id="9209f-141">In other words, the regular expression engine does not attempt to match the captured substring, but instead tests for the presence or absence of the group.</span></span>  
  
<span data-ttu-id="9209f-142">Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji " [dopasowanie &#124; do wzorca" i](#Either_Or) .</span><span class="sxs-lookup"><span data-stu-id="9209f-142">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="9209f-143">Używa dopasowania warunkowego, aby określić, czy pierwsze trzy znaki po granicy słowa są dwiema cyframi, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="9209f-143">It uses conditional matching to determine whether the first three characters after a word boundary are two digits followed by a hyphen.</span></span> <span data-ttu-id="9209f-144">Jeśli są, próbuje dopasować numer identyfikacyjny (EIN) (USA).</span><span class="sxs-lookup"><span data-stu-id="9209f-144">If they are, it attempts to match a U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="9209f-145">Jeśli nie, próbuje dopasować numer PESEL (USA).</span><span class="sxs-lookup"><span data-stu-id="9209f-145">If not, it attempts to match a U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

<span data-ttu-id="9209f-146">`\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="9209f-146">The regular expression pattern `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="9209f-147">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="9209f-147">Pattern</span></span>|<span data-ttu-id="9209f-148">Opis</span><span class="sxs-lookup"><span data-stu-id="9209f-148">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="9209f-149">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-149">Start at a word boundary.</span></span>|  
|`(?(\d{2}-)`|<span data-ttu-id="9209f-150">Ustal, czy następne trzy znaki składają się z dwóch cyfr, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="9209f-150">Determine whether the next three characters consist of two digits followed by a hyphen.</span></span>|  
|`\d{2}-\d{7}`|<span data-ttu-id="9209f-151">Jeśli poprzedni wzorzec jest zgodny, dopasowuje dwie cyfry, po których następuje łącznik, po którym następuje siedem cyfr.</span><span class="sxs-lookup"><span data-stu-id="9209f-151">If the previous pattern matches, match two digits followed by a hyphen followed by seven digits.</span></span>|  
|`\d{3}-\d{2}-\d{4}`|<span data-ttu-id="9209f-152">Jeśli poprzedni wzorzec nie jest zgodny, Dopasuj trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="9209f-152">If the previous pattern does not match, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="9209f-153">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-153">Match a word boundary.</span></span>|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a><span data-ttu-id="9209f-154">Dopasowanie warunkowe oparte na prawidłowej przechwyconej grupie</span><span class="sxs-lookup"><span data-stu-id="9209f-154">Conditional matching based on a valid captured group</span></span>

<span data-ttu-id="9209f-155">Ten element języka próbuje dopasować jeden z dwóch wzorców w zależności od tego, czy jest on zgodny z określoną grupą przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="9209f-155">This language element attempts to match one of two patterns depending on whether it has matched a specified capturing group.</span></span> <span data-ttu-id="9209f-156">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="9209f-156">Its syntax is:</span></span>

<span data-ttu-id="9209f-157">*nazwa* `(?(` `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="9209f-157">`(?(` *name* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="9209f-158">lub</span><span class="sxs-lookup"><span data-stu-id="9209f-158">or</span></span>

<span data-ttu-id="9209f-159">*numer* `(?(` `)` *tak* `|` *nie* `)`</span><span class="sxs-lookup"><span data-stu-id="9209f-159">`(?(` *number* `)` *yes* `|` *no* `)`</span></span>

<span data-ttu-id="9209f-160">gdzie *name* to nazwa i *numer* jest liczbą grupy przechwytywania, *tak* jest wyrażenie do dopasowania, jeśli *Nazwa* lub *Liczba* ma dopasowanie, a wartość *nie* jest wyrażeniem opcjonalnym do dopasowania, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="9209f-160">where *name* is the name and *number* is the number of a capturing group, *yes* is the expression to match if *name* or *number* has a match, and *no* is the optional expression to match if it does not.</span></span>

<span data-ttu-id="9209f-161">Jeśli *Nazwa* nie odpowiada nazwie grupy przechwytywania używanej we wzorcu wyrażenia regularnego, konstrukcja alternatywna jest interpretowana jako test wyrażenia, jak wyjaśniono w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9209f-161">If *name* does not correspond to the name of a capturing group that is used in the regular expression pattern, the alternation construct is interpreted as an expression test, as explained in the previous section.</span></span> <span data-ttu-id="9209f-162">Zazwyczaj oznacza to, że *wyrażenie* oblicza `false`.</span><span class="sxs-lookup"><span data-stu-id="9209f-162">Typically, this means that *expression* evaluates to `false`.</span></span> <span data-ttu-id="9209f-163">Jeśli *Liczba* nie odpowiada numerowanej grupie przechwytywania używanej we wzorcu wyrażenia regularnego, aparat wyrażeń regularnych zgłasza <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="9209f-163">If *number* does not correspond to a numbered capturing group that is used in the regular expression pattern, the regular expression engine throws an <xref:System.ArgumentException>.</span></span>

<span data-ttu-id="9209f-164">Poniższy przykład jest odmianą przykładu, który pojawia się w sekcji " [dopasowanie &#124; do wzorca" i](#Either_Or) .</span><span class="sxs-lookup"><span data-stu-id="9209f-164">The following example is a variation of the example that appears in the [Either/Or Pattern Matching with &#124;](#Either_Or) section.</span></span> <span data-ttu-id="9209f-165">Używa grupy przechwytywania o nazwie `n2`, która składa się z dwóch cyfr, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="9209f-165">It uses a capturing group named `n2` that consists of two digits followed by a hyphen.</span></span> <span data-ttu-id="9209f-166">Konstrukcja alternatywna testuje, czy ta grupa przechwytywania została dopasowana w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="9209f-166">The alternation construct tests whether this capturing group has been matched in the input string.</span></span> <span data-ttu-id="9209f-167">Jeśli ma, konstrukcja alternatywna próbuje dopasować do ostatnich siedmiu cyfr dziewięciu-cyfrowego numeru identyfikacyjnego (EIN).</span><span class="sxs-lookup"><span data-stu-id="9209f-167">If it has, the alternation construct attempts to match the last seven digits of a nine-digit U.S. Employer Identification Number (EIN).</span></span> <span data-ttu-id="9209f-168">Jeśli nie, próbuje dopasować dziewięć-cyfrowy numer PESEL (USA).</span><span class="sxs-lookup"><span data-stu-id="9209f-168">If it has not, it attempts to match a nine-digit U.S. Social Security Number (SSN).</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

<span data-ttu-id="9209f-169">`\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` wzorzec wyrażenia regularnego jest interpretowany jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="9209f-169">The regular expression pattern `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` is interpreted as shown in the following table:</span></span>

|<span data-ttu-id="9209f-170">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="9209f-170">Pattern</span></span>|<span data-ttu-id="9209f-171">Opis</span><span class="sxs-lookup"><span data-stu-id="9209f-171">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="9209f-172">Rozpoczyna na granicy wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-172">Start at a word boundary.</span></span>|  
|`(?<n2>\d{2}-)?`|<span data-ttu-id="9209f-173">Dopasowanie do zera lub jednego wystąpienia dwóch cyfr, po których następuje łącznik.</span><span class="sxs-lookup"><span data-stu-id="9209f-173">Match zero or one occurrence of two digits followed by a hyphen.</span></span> <span data-ttu-id="9209f-174">Nadaj nazwę tej grupie przechwytywania `n2`.</span><span class="sxs-lookup"><span data-stu-id="9209f-174">Name this capturing group `n2`.</span></span>|  
|`(?(n2)`|<span data-ttu-id="9209f-175">Sprawdź, czy `n2` został dopasowany w ciągu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="9209f-175">Test whether `n2` was matched in the input string.</span></span>|  
|`\d{7}`|<span data-ttu-id="9209f-176">Jeśli `n2` zostało dopasowane, Dopasuj siedem cyfr dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="9209f-176">If `n2` was matched, match seven decimal digits.</span></span>|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|<span data-ttu-id="9209f-177">Jeśli `n2` nie zostały dopasowane, Dopasuj trzy cyfry dziesiętne, łącznik, dwie cyfry dziesiętne, inny łącznik i cztery cyfry dziesiętne.</span><span class="sxs-lookup"><span data-stu-id="9209f-177">If `n2` was not matched, match three decimal digits, a hyphen, two decimal digits, another hyphen, and four decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="9209f-178">Dopasowuje granicę wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9209f-178">Match a word boundary.</span></span>|  

<span data-ttu-id="9209f-179">W poniższym przykładzie przedstawiono odmianę tego przykładu, która używa numerowanej grupy zamiast nazwanej grupy.</span><span class="sxs-lookup"><span data-stu-id="9209f-179">A variation of this example that uses a numbered group instead of a named group is shown in the following example.</span></span> <span data-ttu-id="9209f-180">Jego wzorzec wyrażenia regularnego jest `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span><span class="sxs-lookup"><span data-stu-id="9209f-180">Its regular expression pattern is `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.</span></span>

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a><span data-ttu-id="9209f-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9209f-181">See also</span></span>

- [<span data-ttu-id="9209f-182">Język wyrażeń regularnych — podręczny wykaz</span><span class="sxs-lookup"><span data-stu-id="9209f-182">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
