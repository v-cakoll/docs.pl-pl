---
title: Sub — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603538"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="1f61b-102">Sub — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f61b-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="1f61b-103">Deklaruje parametry i kod, który definiuje procedurę wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="1f61b-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f61b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f61b-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="1f61b-105">Części</span><span class="sxs-lookup"><span data-stu-id="1f61b-105">Parts</span></span>  
  
|<span data-ttu-id="1f61b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="1f61b-106">Term</span></span>|<span data-ttu-id="1f61b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="1f61b-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="1f61b-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1f61b-108">Optional.</span></span> <span data-ttu-id="1f61b-109">Lista nazwy zmiennych lokalnych, które reprezentują parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="1f61b-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="1f61b-110">Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="1f61b-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="1f61b-111">Aby uzyskać więcej informacji, zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="1f61b-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="1f61b-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1f61b-112">Required.</span></span> <span data-ttu-id="1f61b-113">Jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1f61b-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="1f61b-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1f61b-114">Required.</span></span> <span data-ttu-id="1f61b-115">Lista instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1f61b-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f61b-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f61b-116">Remarks</span></span>  
 <span data-ttu-id="1f61b-117">A *wyrażenia lambda* jest to procedura, która nie ma nazwy i który wykonuje jedną lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1f61b-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="1f61b-118">Można używać wyrażenia lambda w dowolnym służącego typu delegata, z wyjątkiem jako argument `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="1f61b-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="1f61b-119">Aby uzyskać więcej informacji dotyczących obiektów delegowanych i korzystanie z wyrażenia lambda z delegatów, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="1f61b-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="1f61b-120">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="1f61b-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="1f61b-121">Składnia wyrażenia lambda jest podobny do tego standardowe procedury.</span><span class="sxs-lookup"><span data-stu-id="1f61b-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="1f61b-122">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="1f61b-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="1f61b-123">Wyrażenia lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="1f61b-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="1f61b-124">Wyrażenia lambda nie może mieć modyfikatora, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="1f61b-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="1f61b-125">Treść wyrażenia lambda jeden wiersz musi być instrukcję nie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1f61b-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="1f61b-126">Treść może obejmować wywołaniu procedury sub, ale nie wywołanie procedury function.</span><span class="sxs-lookup"><span data-stu-id="1f61b-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="1f61b-127">W wyrażeniu lambda albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="1f61b-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="1f61b-128">Opcjonalne i `ParamArray` parametry są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="1f61b-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="1f61b-129">Parametry ogólne są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="1f61b-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f61b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f61b-130">Example</span></span>  
 <span data-ttu-id="1f61b-131">Poniżej przedstawiono przykład wyrażenia lambda, który zapisuje wartość do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1f61b-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="1f61b-132">W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla procedury.</span><span class="sxs-lookup"><span data-stu-id="1f61b-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="1f61b-133">Aby uzyskać więcej przykładów, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1f61b-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1f61b-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f61b-134">See Also</span></span>  
 [<span data-ttu-id="1f61b-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f61b-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="1f61b-136">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="1f61b-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="1f61b-137">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1f61b-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="1f61b-138">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="1f61b-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="1f61b-139">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="1f61b-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
