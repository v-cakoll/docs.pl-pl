---
title: "Sub — Wyrażenie (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43e35bd0386bc56478603ec36437981785cc8ffb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="71038-102">Sub — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71038-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="71038-103">Deklaruje parametry i kod, który definiuje procedurę wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="71038-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71038-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71038-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="71038-105">Części</span><span class="sxs-lookup"><span data-stu-id="71038-105">Parts</span></span>  
  
|<span data-ttu-id="71038-106">Termin</span><span class="sxs-lookup"><span data-stu-id="71038-106">Term</span></span>|<span data-ttu-id="71038-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="71038-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="71038-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="71038-108">Optional.</span></span> <span data-ttu-id="71038-109">Lista nazwy zmiennych lokalnych, które reprezentują parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="71038-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="71038-110">Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="71038-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="71038-111">Aby uzyskać więcej informacji, zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="71038-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="71038-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="71038-112">Required.</span></span> <span data-ttu-id="71038-113">Jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="71038-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="71038-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="71038-114">Required.</span></span> <span data-ttu-id="71038-115">Lista instrukcji.</span><span class="sxs-lookup"><span data-stu-id="71038-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71038-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71038-116">Remarks</span></span>  
 <span data-ttu-id="71038-117">A *wyrażenia lambda* jest to procedura, która nie ma nazwy i który wykonuje jedną lub więcej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="71038-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="71038-118">Można używać wyrażenia lambda w dowolnym służącego typu delegata, z wyjątkiem jako argument `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="71038-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="71038-119">Aby uzyskać więcej informacji dotyczących obiektów delegowanych i korzystanie z wyrażenia lambda z delegatów, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="71038-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="71038-120">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="71038-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="71038-121">Składnia wyrażenia lambda jest podobny do tego standardowe procedury.</span><span class="sxs-lookup"><span data-stu-id="71038-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="71038-122">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="71038-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="71038-123">Wyrażenia lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="71038-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="71038-124">Wyrażenia lambda nie może mieć modyfikatora, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="71038-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="71038-125">Treść wyrażenia lambda jeden wiersz musi być instrukcję nie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="71038-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="71038-126">Treść może obejmować wywołaniu procedury sub, ale nie wywołanie procedury function.</span><span class="sxs-lookup"><span data-stu-id="71038-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="71038-127">W wyrażeniu lambda albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich parametrów.</span><span class="sxs-lookup"><span data-stu-id="71038-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="71038-128">Opcjonalne i `ParamArray` parametry są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="71038-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="71038-129">Parametry ogólne są niedozwolone w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="71038-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71038-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="71038-130">Example</span></span>  
 <span data-ttu-id="71038-131">Poniżej przedstawiono przykład wyrażenia lambda, który zapisuje wartość do konsoli.</span><span class="sxs-lookup"><span data-stu-id="71038-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="71038-132">W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla procedury.</span><span class="sxs-lookup"><span data-stu-id="71038-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="71038-133">Aby uzyskać więcej przykładów, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="71038-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="71038-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71038-134">See Also</span></span>  
 [<span data-ttu-id="71038-135">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="71038-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="71038-136">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="71038-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="71038-137">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="71038-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="71038-138">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="71038-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="71038-139">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="71038-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
