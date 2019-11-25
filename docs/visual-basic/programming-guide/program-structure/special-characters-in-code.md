---
title: Znaki specjalne w Code
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347266"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="23f83-102">Znaki specjalne w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23f83-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="23f83-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span><span class="sxs-lookup"><span data-stu-id="23f83-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="23f83-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span><span class="sxs-lookup"><span data-stu-id="23f83-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="23f83-105">They do not specify an operation to be performed.</span><span class="sxs-lookup"><span data-stu-id="23f83-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="23f83-106">Parentheses</span><span class="sxs-lookup"><span data-stu-id="23f83-106">Parentheses</span></span>  
 <span data-ttu-id="23f83-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span><span class="sxs-lookup"><span data-stu-id="23f83-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="23f83-108">You must enclose all procedure argument lists in parentheses.</span><span class="sxs-lookup"><span data-stu-id="23f83-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="23f83-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span><span class="sxs-lookup"><span data-stu-id="23f83-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="23f83-110">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="23f83-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="23f83-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span><span class="sxs-lookup"><span data-stu-id="23f83-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="23f83-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="23f83-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="23f83-113">The parentheses in the calculation for `e` override the default precedence.</span><span class="sxs-lookup"><span data-stu-id="23f83-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="23f83-114">Separatorach</span><span class="sxs-lookup"><span data-stu-id="23f83-114">Separators</span></span>  
 <span data-ttu-id="23f83-115">Separators do what their name suggests: they separate sections of code.</span><span class="sxs-lookup"><span data-stu-id="23f83-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="23f83-116">In Visual Basic, the separator character is the colon (`:`).</span><span class="sxs-lookup"><span data-stu-id="23f83-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="23f83-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span><span class="sxs-lookup"><span data-stu-id="23f83-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="23f83-118">This saves space and improves the readability of your code.</span><span class="sxs-lookup"><span data-stu-id="23f83-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="23f83-119">The following example shows three statements separated by colons.</span><span class="sxs-lookup"><span data-stu-id="23f83-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="23f83-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="23f83-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="23f83-121">The colon (`:`) character is also used to identify a statement label.</span><span class="sxs-lookup"><span data-stu-id="23f83-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="23f83-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="23f83-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="23f83-123">Połączenie (konkatenacja)</span><span class="sxs-lookup"><span data-stu-id="23f83-123">Concatenation</span></span>  
 <span data-ttu-id="23f83-124">Use the `&` operator for *concatenation*, or linking strings together.</span><span class="sxs-lookup"><span data-stu-id="23f83-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="23f83-125">Do not confuse it with the `+` operator, which adds together numeric values.</span><span class="sxs-lookup"><span data-stu-id="23f83-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="23f83-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span><span class="sxs-lookup"><span data-stu-id="23f83-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="23f83-127">The following example demonstrates this.</span><span class="sxs-lookup"><span data-stu-id="23f83-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="23f83-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span><span class="sxs-lookup"><span data-stu-id="23f83-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="23f83-129">Member Access Operators</span><span class="sxs-lookup"><span data-stu-id="23f83-129">Member Access Operators</span></span>  
 <span data-ttu-id="23f83-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span><span class="sxs-lookup"><span data-stu-id="23f83-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="23f83-131">Dot (.) Operator</span><span class="sxs-lookup"><span data-stu-id="23f83-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="23f83-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span><span class="sxs-lookup"><span data-stu-id="23f83-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="23f83-133">The member can be a field, property, event, or method.</span><span class="sxs-lookup"><span data-stu-id="23f83-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="23f83-134">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="23f83-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="23f83-135">Exclamation Point (!) Operator</span><span class="sxs-lookup"><span data-stu-id="23f83-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="23f83-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span><span class="sxs-lookup"><span data-stu-id="23f83-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="23f83-137">The class or interface must have a default property that accepts a single `String` argument.</span><span class="sxs-lookup"><span data-stu-id="23f83-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="23f83-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span><span class="sxs-lookup"><span data-stu-id="23f83-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="23f83-139">The following example demonstrates this.</span><span class="sxs-lookup"><span data-stu-id="23f83-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="23f83-140">The three output lines of `MsgBox` all display the value `32856`.</span><span class="sxs-lookup"><span data-stu-id="23f83-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="23f83-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span><span class="sxs-lookup"><span data-stu-id="23f83-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="23f83-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span><span class="sxs-lookup"><span data-stu-id="23f83-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="23f83-143">In other words, you cannot use a string literal or string variable.</span><span class="sxs-lookup"><span data-stu-id="23f83-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="23f83-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span><span class="sxs-lookup"><span data-stu-id="23f83-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="23f83-145">References to default collections must be explicit.</span><span class="sxs-lookup"><span data-stu-id="23f83-145">References to default collections must be explicit.</span></span> <span data-ttu-id="23f83-146">In particular, you cannot use the `!` operator on a late-bound variable.</span><span class="sxs-lookup"><span data-stu-id="23f83-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="23f83-147">The `!` character is also used as the `Single` type character.</span><span class="sxs-lookup"><span data-stu-id="23f83-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f83-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f83-148">See also</span></span>

- [<span data-ttu-id="23f83-149">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="23f83-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="23f83-150">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="23f83-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
