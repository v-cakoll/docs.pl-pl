---
title: 'Porady: dopasowywanie ciągu do wzorca (Visual Basic)'
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
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655215"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="2a09e-102">Porady: dopasowywanie ciągu do wzorca (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a09e-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="2a09e-103">Aby sprawdzić, czy wyrażenie [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia wzorzec, a następnie można użyć [operatora Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2a09e-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="2a09e-104">`Like` przyjmuje dwa argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="2a09e-104">`Like` takes two operands.</span></span> <span data-ttu-id="2a09e-105">Lewy argument operacji jest wyrażeniem i prawy argument operacji ma postać ciągu zawierającego wzorzec służący do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2a09e-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="2a09e-106">`Like` Zwraca `Boolean` wartość wskazującą, czy wyrażenie ciągu spełnia wzorzec.</span><span class="sxs-lookup"><span data-stu-id="2a09e-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="2a09e-107">Można dopasować do każdego znaku wyrażenia ciągu względem określony znak symbolu wieloznacznego, listę znaku albo zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="2a09e-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="2a09e-108">Pozycje specyfikacji w ciągu wzorca odpowiadają pozycji znaków w wyrażenia ciągu.</span><span class="sxs-lookup"><span data-stu-id="2a09e-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="2a09e-109">Aby uwzględnić znak w wyrażeniu ciągu względem określonego znaku</span><span class="sxs-lookup"><span data-stu-id="2a09e-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="2a09e-110">Umieść określonego znaku bezpośrednio w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="2a09e-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="2a09e-111">Niektóre znaki specjalne musi być ujęta w nawiasy kwadratowe (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="2a09e-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="2a09e-112">Aby uzyskać więcej informacji, zobacz [operatora Like](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2a09e-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="2a09e-113">Następujące testy przykład czy `myString` zawiera dokładnie jednego znaku `H`.</span><span class="sxs-lookup"><span data-stu-id="2a09e-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="2a09e-114">Aby uwzględnić znak w wyrażeniu ciągu z symbolem wieloznacznym</span><span class="sxs-lookup"><span data-stu-id="2a09e-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="2a09e-115">Umieść znak zapytania (`?`) w ciągu wzorca.</span><span class="sxs-lookup"><span data-stu-id="2a09e-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="2a09e-116">Dowolny znak prawidłowy w tym miejscu powoduje, że pomyślnego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2a09e-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="2a09e-117">Następujące testy przykład czy `myString` składa się z jednego znaku `W` następują dokładnie dwa znaki z wartości.</span><span class="sxs-lookup"><span data-stu-id="2a09e-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="2a09e-118">Aby uwzględnić znak w wyrażeniu ciąg z listą znaków</span><span class="sxs-lookup"><span data-stu-id="2a09e-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="2a09e-119">Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów umieścić na liście znaków.</span><span class="sxs-lookup"><span data-stu-id="2a09e-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="2a09e-120">Nie należy oddzielić znaki przecinków lub wszelkich innych separatorów.</span><span class="sxs-lookup"><span data-stu-id="2a09e-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="2a09e-121">Dowolny pojedynczy znak na liście sprawia, że pomyślnie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2a09e-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="2a09e-122">Następujące testy przykład czy `myString` składa się z dowolny prawidłowy znak następuje dokładnie jeden ze znaków `A`, `C`, lub `E`.</span><span class="sxs-lookup"><span data-stu-id="2a09e-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     <span data-ttu-id="2a09e-123">Należy pamiętać, że tego dopasowania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2a09e-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="2a09e-124">Aby uwzględnić znak w wyrażeniu ciąg z zakresu znaków</span><span class="sxs-lookup"><span data-stu-id="2a09e-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="2a09e-125">Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów wprowadzone znaki najmniejsza i największa w zakresie rozdzielonych łącznikiem (`–`).</span><span class="sxs-lookup"><span data-stu-id="2a09e-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="2a09e-126">Dowolny pojedynczy znak z zakresu sprawia, że pomyślnie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2a09e-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="2a09e-127">Następujące testy przykład czy `myString` składa się ze znaków `num` następuje dokładnie jeden ze znaków `i`, `j`, `k`, `l`, `m`, lub `n`.</span><span class="sxs-lookup"><span data-stu-id="2a09e-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     <span data-ttu-id="2a09e-128">Należy pamiętać, że tego dopasowania jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="2a09e-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="2a09e-129">Dopasowywanie puste ciągi</span><span class="sxs-lookup"><span data-stu-id="2a09e-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="2a09e-130">`Like` traktuje Sekwencja `[]` jako ciąg o zerowej długości (`""`).</span><span class="sxs-lookup"><span data-stu-id="2a09e-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="2a09e-131">Można użyć `[]` Aby sprawdzić, czy wyrażenie cały ciąg jest pusty, ale nie można użyć go, aby sprawdzić, czy w określonej pozycji w wyrażeniu ciąg jest pusty.</span><span class="sxs-lookup"><span data-stu-id="2a09e-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="2a09e-132">Jeśli pozycja pusty jest jedną z opcji należy przeprowadzić testy dla służy `Like` więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="2a09e-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="2a09e-133">Aby uwzględnić znak w wyrażeniu ciąg z listą znaków lub nie znaku</span><span class="sxs-lookup"><span data-stu-id="2a09e-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="2a09e-134">Wywołanie `Like` operator dwukrotnie w tym samym wyrażenia ciągu i uzyskuj dostęp do tych dwóch wywołań albo [lub Operator](../../../../visual-basic/language-reference/operators/or-operator.md) lub [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2a09e-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="2a09e-135">W ciągu wzorca w pierwszym `Like` klauzuli zawierają listy znaków w nawiasach (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="2a09e-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="2a09e-136">W ciągu wzorca dla drugiego `Like` klauzuli, nie należy umieszczać dowolny znak na pozycji zagrożona.</span><span class="sxs-lookup"><span data-stu-id="2a09e-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="2a09e-137">Poniższy przykład testów 7 cyfrowy numer telefonu `phoneNum` dla dokładnie trzech cyfr, spację, łącznik (`–`), okres (`.`), lub nie znaku, następuje dokładnie cztery cyfry.</span><span class="sxs-lookup"><span data-stu-id="2a09e-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2a09e-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a09e-138">See Also</span></span>  
 [<span data-ttu-id="2a09e-139">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="2a09e-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="2a09e-140">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="2a09e-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="2a09e-141">Like, operator</span><span class="sxs-lookup"><span data-stu-id="2a09e-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="2a09e-142">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="2a09e-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
