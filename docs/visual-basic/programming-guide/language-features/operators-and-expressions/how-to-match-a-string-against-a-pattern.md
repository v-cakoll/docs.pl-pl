---
title: 'Instrukcje: Dopasowanie ciągu do wzorca (Visual Basic)'
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
ms.openlocfilehash: c14aa35ce15549ad9eccabe2330a7c43b6795140
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864705"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="89a8f-102">Instrukcje: Dopasowanie ciągu do wzorca (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89a8f-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="89a8f-103">Jeśli chcesz sprawdzić, czy wyrażenie [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia wzorzec, wówczas można użyć [takich jak Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="89a8f-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="89a8f-104">`Like` przyjmuje dwa argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="89a8f-104">`Like` takes two operands.</span></span> <span data-ttu-id="89a8f-105">Lewy operand jest wyrażeniem, a prawy operand jest ciąg zawierający wzorzec, który ma być używany do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="89a8f-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="89a8f-106">`Like` Zwraca `Boolean` wartość wskazującą, czy wyrażenie ciągu spełnia wzorzec.</span><span class="sxs-lookup"><span data-stu-id="89a8f-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="89a8f-107">Można dopasować do każdego znaku w wyrażeniu ciąg względem określonego znaku, symbolu wieloznacznego, lista znak lub zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="89a8f-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="89a8f-108">Położenie specyfikacji w ciągu wzorca odpowiadają pozycji znaków, które mają zostać dopasowane w wyrażenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="89a8f-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="89a8f-109">Aby dopasować znak w wyrażeniu ciąg względem określonego znaku</span><span class="sxs-lookup"><span data-stu-id="89a8f-109">To match a character in the string expression against a specific character</span></span>  
  
- <span data-ttu-id="89a8f-110">Umieść znaków specyficznych bezpośrednio w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="89a8f-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="89a8f-111">Niektóre znaki specjalne, muszą być ujęte w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="89a8f-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="89a8f-112">Aby uzyskać więcej informacji, zobacz [takich jak Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="89a8f-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="89a8f-113">Poniższy przykład sprawdza czy `myString` składa się dokładnie z jednego znaku `H`.</span><span class="sxs-lookup"><span data-stu-id="89a8f-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="89a8f-114">Aby dopasować znak w wyrażeniu ciąg z symbolem wieloznacznym</span><span class="sxs-lookup"><span data-stu-id="89a8f-114">To match a character in the string expression against a wildcard character</span></span>  
  
- <span data-ttu-id="89a8f-115">Umieść znak zapytania (`?`) w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="89a8f-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="89a8f-116">Dowolny prawidłowy znak, w tym miejscu sprawia, że udane dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="89a8f-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="89a8f-117">Poniższy przykład sprawdza czy `myString` składa się z jednego znaku `W` następuje dokładnie dwa znaki żadnych wartości.</span><span class="sxs-lookup"><span data-stu-id="89a8f-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="89a8f-118">Aby dopasować znak w wyrażeniu ciąg z listą znaków</span><span class="sxs-lookup"><span data-stu-id="89a8f-118">To match a character in the string expression against a list of characters</span></span>  
  
- <span data-ttu-id="89a8f-119">Umieść nawiasy kwadratowe (`[ ]`) w ciągu wzorca, znajduje się wewnątrz nawiasów, umieść listę znaków.</span><span class="sxs-lookup"><span data-stu-id="89a8f-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="89a8f-120">Nie należy oddzielić znaków za pomocą przecinków lub wszelkich innych separatorów.</span><span class="sxs-lookup"><span data-stu-id="89a8f-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="89a8f-121">Dowolny pojedynczy znak na liście sprawia, że udane dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="89a8f-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="89a8f-122">Poniższy przykład sprawdza czy `myString` składa się z dowolnym prawidłowym znakiem następuje z dokładnie jednym ze znaków `A`, `C`, lub `E`.</span><span class="sxs-lookup"><span data-stu-id="89a8f-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     <span data-ttu-id="89a8f-123">Należy pamiętać, że ta rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="89a8f-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="89a8f-124">Aby dopasować znak w wyrażeniu ciąg z zakresu znaków</span><span class="sxs-lookup"><span data-stu-id="89a8f-124">To match a character in the string expression against a range of characters</span></span>  
  
- <span data-ttu-id="89a8f-125">Umieść nawiasy kwadratowe (`[ ]`) w ciągu wzorca oraz w nawiasie umieścić najmniejsza i największa znaki w zakresie rozdzielonych łącznikiem (`–`).</span><span class="sxs-lookup"><span data-stu-id="89a8f-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="89a8f-126">Dowolny pojedynczy znak w zakresie sprawia, że udane dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="89a8f-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="89a8f-127">Poniższy przykład sprawdza czy `myString` składa się ze znaków `num` następuje z dokładnie jednym ze znaków `i`, `j`, `k`, `l`, `m`, lub `n`.</span><span class="sxs-lookup"><span data-stu-id="89a8f-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     <span data-ttu-id="89a8f-128">Należy pamiętać, że ta rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="89a8f-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="89a8f-129">Dopasowywanie puste ciągi</span><span class="sxs-lookup"><span data-stu-id="89a8f-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="89a8f-130">`Like` traktuje sekwencji `[]` jako ciąg o zerowej długości (`""`).</span><span class="sxs-lookup"><span data-stu-id="89a8f-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="89a8f-131">Możesz użyć `[]` do sprawdzenia, czy wyrażenie cały ciąg jest pusty, ale nie można użyć go, aby sprawdzić, czy w określonej pozycji w wyrażeniu ciąg jest pusty.</span><span class="sxs-lookup"><span data-stu-id="89a8f-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="89a8f-132">Jeśli pusty pozycja jest jedną z opcji należy przetestować dla można użyć `Like` więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="89a8f-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="89a8f-133">Aby dopasować znak w wyrażeniu ciąg z listą znaków lub nie znaku</span><span class="sxs-lookup"><span data-stu-id="89a8f-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1. <span data-ttu-id="89a8f-134">Wywołaj `Like` operator dwa razy na tym samym wyrażenia ciągu i połączyć z dwoma połączeniami z oboma [operatora Or](../../../../visual-basic/language-reference/operators/or-operator.md) lub [orelse — Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="89a8f-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2. <span data-ttu-id="89a8f-135">W ciągu wzorca w pierwszym `Like` klauzuli zawierają listę znaków, ujęte w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="89a8f-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3. <span data-ttu-id="89a8f-136">W ciągu wzorca dla drugiego `Like` klauzuli, nie umieszczaj dowolny znak na pozycji w danym.</span><span class="sxs-lookup"><span data-stu-id="89a8f-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="89a8f-137">Następujący przykład sprawdza 7 cyfrowy numer telefonu `phoneNum` dla dokładnie trzech cyfr, spację, myślnik (`–`), okres (`.`), lub nie znaku, a następnie dokładnie cztery cyfry.</span><span class="sxs-lookup"><span data-stu-id="89a8f-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="89a8f-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89a8f-138">See also</span></span>

- [<span data-ttu-id="89a8f-139">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="89a8f-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="89a8f-140">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="89a8f-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="89a8f-141">Like, operator</span><span class="sxs-lookup"><span data-stu-id="89a8f-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="89a8f-142">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="89a8f-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
