---
title: 'Porady: dopasowywanie ciągu do wzorca'
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
ms.openlocfilehash: 49328a72c2cff78b8fe13ca73209d224495ad7a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343641"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="3153b-102">Porady: dopasowywanie ciągu do wzorca (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3153b-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="3153b-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3153b-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="3153b-104">`Like` takes two operands.</span><span class="sxs-lookup"><span data-stu-id="3153b-104">`Like` takes two operands.</span></span> <span data-ttu-id="3153b-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span><span class="sxs-lookup"><span data-stu-id="3153b-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="3153b-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span><span class="sxs-lookup"><span data-stu-id="3153b-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="3153b-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span><span class="sxs-lookup"><span data-stu-id="3153b-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="3153b-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span><span class="sxs-lookup"><span data-stu-id="3153b-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="3153b-109">To match a character in the string expression against a specific character</span><span class="sxs-lookup"><span data-stu-id="3153b-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="3153b-110">Put the specific character directly in the pattern string.</span><span class="sxs-lookup"><span data-stu-id="3153b-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="3153b-111">Certain special characters must be enclosed in brackets (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="3153b-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="3153b-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3153b-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="3153b-113">The following example tests whether `myString` consists exactly of the single character `H`.</span><span class="sxs-lookup"><span data-stu-id="3153b-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="3153b-114">To match a character in the string expression against a wildcard character</span><span class="sxs-lookup"><span data-stu-id="3153b-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="3153b-115">Put a question mark (`?`) in the pattern string.</span><span class="sxs-lookup"><span data-stu-id="3153b-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="3153b-116">Any valid character in this position makes a successful match.</span><span class="sxs-lookup"><span data-stu-id="3153b-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="3153b-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span><span class="sxs-lookup"><span data-stu-id="3153b-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="3153b-118">To match a character in the string expression against a list of characters</span><span class="sxs-lookup"><span data-stu-id="3153b-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="3153b-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span><span class="sxs-lookup"><span data-stu-id="3153b-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="3153b-120">Do not separate the characters with commas or any other separator.</span><span class="sxs-lookup"><span data-stu-id="3153b-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="3153b-121">Any single character in the list makes a successful match.</span><span class="sxs-lookup"><span data-stu-id="3153b-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="3153b-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span><span class="sxs-lookup"><span data-stu-id="3153b-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="3153b-123">Note that this match is case-sensitive.</span><span class="sxs-lookup"><span data-stu-id="3153b-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="3153b-124">To match a character in the string expression against a range of characters</span><span class="sxs-lookup"><span data-stu-id="3153b-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="3153b-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span><span class="sxs-lookup"><span data-stu-id="3153b-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="3153b-126">Any single character within the range makes a successful match.</span><span class="sxs-lookup"><span data-stu-id="3153b-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="3153b-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span><span class="sxs-lookup"><span data-stu-id="3153b-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="3153b-128">Note that this match is case-sensitive.</span><span class="sxs-lookup"><span data-stu-id="3153b-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="3153b-129">Matching Empty Strings</span><span class="sxs-lookup"><span data-stu-id="3153b-129">Matching Empty Strings</span></span>

<span data-ttu-id="3153b-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span><span class="sxs-lookup"><span data-stu-id="3153b-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="3153b-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span><span class="sxs-lookup"><span data-stu-id="3153b-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="3153b-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span><span class="sxs-lookup"><span data-stu-id="3153b-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="3153b-133">To match a character in the string expression against a list of characters or no character</span><span class="sxs-lookup"><span data-stu-id="3153b-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="3153b-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3153b-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="3153b-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="3153b-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="3153b-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span><span class="sxs-lookup"><span data-stu-id="3153b-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="3153b-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span><span class="sxs-lookup"><span data-stu-id="3153b-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="3153b-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3153b-138">See also</span></span>

- [<span data-ttu-id="3153b-139">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="3153b-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="3153b-140">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="3153b-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="3153b-141">Like, operator</span><span class="sxs-lookup"><span data-stu-id="3153b-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="3153b-142">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="3153b-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
