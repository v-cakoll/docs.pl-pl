---
title: 'Instrukcje: Dopasowuje ciąg do wzorca (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054153"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="346dc-102">Instrukcje: Dopasowuje ciąg do wzorca (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="346dc-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="346dc-103">Jeśli chcesz dowiedzieć się, czy wyrażenie [typu danych ciąg](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia warunki wzorca, możesz użyć [operatora like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="346dc-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="346dc-104">`Like`przyjmuje dwa operandy.</span><span class="sxs-lookup"><span data-stu-id="346dc-104">`Like` takes two operands.</span></span> <span data-ttu-id="346dc-105">Lewy operand jest wyrażeniem ciągu, a prawy operand jest ciągiem zawierającym wzorzec, który ma być używany do dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="346dc-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="346dc-106">`Like``Boolean` zwraca wartość wskazującą czy wyrażenie ciągu spełnia warunki wzorca.</span><span class="sxs-lookup"><span data-stu-id="346dc-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="346dc-107">Można dopasować każdy znak w wyrażeniu ciągu do określonego znaku, symbolu wieloznacznego, listy znaków lub zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="346dc-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="346dc-108">Pozycje specyfikacji w ciągu wzorca odpowiadają pozycjom znaków, które mają być dopasowane w wyrażeniu ciągu.</span><span class="sxs-lookup"><span data-stu-id="346dc-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="346dc-109">Aby dopasować znak w wyrażeniu ciągu do określonego znaku</span><span class="sxs-lookup"><span data-stu-id="346dc-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="346dc-110">Umieść określony znak bezpośrednio w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="346dc-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="346dc-111">Niektóre znaki specjalne muszą być ujęte w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="346dc-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="346dc-112">Aby uzyskać więcej informacji, zobacz [operator like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="346dc-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="346dc-113">Poniższy przykład sprawdza, czy `myString` zawiera dokładnie jeden znak. `H`</span><span class="sxs-lookup"><span data-stu-id="346dc-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="346dc-114">Aby dopasować znak w wyrażeniu ciągu do symbolu wieloznacznego</span><span class="sxs-lookup"><span data-stu-id="346dc-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="346dc-115">Umieść znak zapytania (`?`) w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="346dc-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="346dc-116">Każdy prawidłowy znak w tym miejscu powoduje pomyślne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="346dc-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="346dc-117">Poniższy przykład sprawdza, czy `myString` składa się z pojedynczego `W` znaku, po którym następuje dokładnie dwa znaki każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="346dc-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="346dc-118">Aby dopasować znak w wyrażeniu ciągu do listy znaków</span><span class="sxs-lookup"><span data-stu-id="346dc-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="346dc-119">Umieść nawiasy`[ ]`() w ciągu wzorca i wewnątrz nawiasów, umieszczając listę znaków.</span><span class="sxs-lookup"><span data-stu-id="346dc-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="346dc-120">Nie oddzielaj znaków przecinkami ani innymi separatorami.</span><span class="sxs-lookup"><span data-stu-id="346dc-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="346dc-121">Każdy pojedynczy znak na liście powoduje pomyślne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="346dc-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="346dc-122">Poniższy przykład sprawdza, czy `myString` składa się z dowolnego prawidłowego znaku, po którym występuje dokładnie `A`jeden `C`z znaków `E`, lub.</span><span class="sxs-lookup"><span data-stu-id="346dc-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="346dc-123">Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="346dc-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="346dc-124">Aby dopasować znak w wyrażeniu ciągu do zakresu znaków</span><span class="sxs-lookup"><span data-stu-id="346dc-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="346dc-125">Umieść nawiasy`[ ]`() w ciągu wzorca, a wewnątrz nawiasów Umieść najniższy i najwyższe znaki z zakresu, oddzielone łącznikiem (`–`).</span><span class="sxs-lookup"><span data-stu-id="346dc-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="346dc-126">Każdy pojedynczy znak w zakresie powoduje pomyślne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="346dc-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="346dc-127">Poniższy przykład sprawdza, czy `myString` zawiera znaki `num` , po których następuje dokładnie jeden `k`z `m`znaków `i`, `j`,, `l`, lub `n`.</span><span class="sxs-lookup"><span data-stu-id="346dc-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="346dc-128">Należy pamiętać, że ten odpowiednik uwzględnia wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="346dc-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="346dc-129">Dopasowywanie pustych ciągów</span><span class="sxs-lookup"><span data-stu-id="346dc-129">Matching Empty Strings</span></span>

<span data-ttu-id="346dc-130">`Like`traktuje sekwencję `[]` jako ciąg o zerowej długości`""`().</span><span class="sxs-lookup"><span data-stu-id="346dc-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="346dc-131">Można użyć `[]` do sprawdzenia, czy całe wyrażenie ciągu jest puste, ale nie można go użyć do przetestowania, jeśli określone położenie w wyrażeniu ciągu jest puste.</span><span class="sxs-lookup"><span data-stu-id="346dc-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="346dc-132">Jeśli puste położenie jest jedną z opcji, które należy wykonać w celu przetestowania, można `Like` użyć więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="346dc-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="346dc-133">Aby dopasować znak w wyrażeniu ciągu do listy znaków lub bez znaku</span><span class="sxs-lookup"><span data-stu-id="346dc-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="346dc-134">Wywołaj [](../../../../visual-basic/language-reference/operators/or-operator.md) operatora dwa razy w tym samym wyrażeniu ciągu i połącz dwa wywołania z operatorem OR lub [operatorem OrElse.](../../../../visual-basic/language-reference/operators/orelse-operator.md) `Like`</span><span class="sxs-lookup"><span data-stu-id="346dc-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="346dc-135">W ciągu wzorca dla pierwszej `Like` klauzuli należy uwzględnić listę znaków ujętą w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="346dc-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="346dc-136">W ciągu wzorca dla drugiej `Like` klauzuli nie umieszczaj żadnego znaku w podanym położeniu.</span><span class="sxs-lookup"><span data-stu-id="346dc-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="346dc-137">Poniższy przykład sprawdza numer `phoneNum` telefonu siedmiu cyfr dla dokładnie trzech cyfr, po którym następuje spacja, łącznik (`–`), kropka (`.`) lub bez znaku, a następnie dokładnie cztery cyfry.</span><span class="sxs-lookup"><span data-stu-id="346dc-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="346dc-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="346dc-138">See also</span></span>

- [<span data-ttu-id="346dc-139">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="346dc-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="346dc-140">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="346dc-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="346dc-141">Like, operator</span><span class="sxs-lookup"><span data-stu-id="346dc-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="346dc-142">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="346dc-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
