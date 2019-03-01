---
title: Sub — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5e8c66f4f2b21a890b8c61e6fc642ce276df6f60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966726"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="f7b45-102">Sub — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7b45-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="f7b45-103">Deklaruje parametry i kod, który definiuje procedurę wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="f7b45-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7b45-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="f7b45-105">Części</span><span class="sxs-lookup"><span data-stu-id="f7b45-105">Parts</span></span>  
  
|<span data-ttu-id="f7b45-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f7b45-106">Term</span></span>|<span data-ttu-id="f7b45-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f7b45-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="f7b45-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f7b45-108">Optional.</span></span> <span data-ttu-id="f7b45-109">Lista nazwy zmiennych lokalnych, które reprezentują parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="f7b45-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="f7b45-110">Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="f7b45-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="f7b45-111">Aby uzyskać więcej informacji, zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="f7b45-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="f7b45-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f7b45-112">Required.</span></span> <span data-ttu-id="f7b45-113">Pojedynczą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="f7b45-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="f7b45-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f7b45-114">Required.</span></span> <span data-ttu-id="f7b45-115">Lista instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f7b45-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7b45-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7b45-116">Remarks</span></span>  
 <span data-ttu-id="f7b45-117">A *wyrażenia lambda* jest to procedura, która nie ma nazwy i który wykonuje jedną lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f7b45-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="f7b45-118">Użyć wyrażenia lambda w dowolnym miejscu, typu delegata, można użyć z wyjątkiem jako argument do `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="f7b45-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="f7b45-119">Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z obiektów delegowanych, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="f7b45-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="f7b45-120">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f7b45-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="f7b45-121">Składnia wyrażenia lambda przypomina w przypadku standardowe procedury.</span><span class="sxs-lookup"><span data-stu-id="f7b45-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="f7b45-122">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="f7b45-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="f7b45-123">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="f7b45-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="f7b45-124">Wyrażenie lambda nie może mieć modyfikatora, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="f7b45-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="f7b45-125">Treść wyrażenia lambda w pojedynczej linii musi być instrukcja nie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f7b45-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="f7b45-126">Treść może składać się po wywołaniu procedury sub, ale nie po wywołaniu procedury function.</span><span class="sxs-lookup"><span data-stu-id="f7b45-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="f7b45-127">W wyrażeniu lambda albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="f7b45-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="f7b45-128">Opcjonalne i `ParamArray` parametry są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="f7b45-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="f7b45-129">Parametry ogólne są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="f7b45-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7b45-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7b45-130">Example</span></span>  
 <span data-ttu-id="f7b45-131">Oto przykład wyrażenie lambda, która zapisuje wartości do konsoli.</span><span class="sxs-lookup"><span data-stu-id="f7b45-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="f7b45-132">W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda do procedurę.</span><span class="sxs-lookup"><span data-stu-id="f7b45-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="f7b45-133">Aby uzyskać więcej przykładów, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f7b45-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="f7b45-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7b45-134">See also</span></span>
- [<span data-ttu-id="f7b45-135">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f7b45-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f7b45-136">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f7b45-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="f7b45-137">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f7b45-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="f7b45-138">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="f7b45-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="f7b45-139">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="f7b45-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
