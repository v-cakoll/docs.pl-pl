---
title: "Function — Wyrażenie (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="be7ab-102">Function — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be7ab-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="be7ab-103">Deklaruje parametry i kod, który definiuje wyrażenie lambda funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be7ab-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="be7ab-105">Części</span><span class="sxs-lookup"><span data-stu-id="be7ab-105">Parts</span></span>  
  
|<span data-ttu-id="be7ab-106">Termin</span><span class="sxs-lookup"><span data-stu-id="be7ab-106">Term</span></span>|<span data-ttu-id="be7ab-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="be7ab-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="be7ab-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="be7ab-108">Optional.</span></span> <span data-ttu-id="be7ab-109">Lista nazwy zmiennych lokalnych, które reprezentują parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="be7ab-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="be7ab-110">Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="be7ab-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="be7ab-111">Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="be7ab-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="be7ab-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="be7ab-112">Required.</span></span> <span data-ttu-id="be7ab-113">Jedno wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="be7ab-113">A single expression.</span></span> <span data-ttu-id="be7ab-114">Typ wyrażenia jest zwracany typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="be7ab-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="be7ab-115">Required.</span></span> <span data-ttu-id="be7ab-116">Lista instrukcji, która zwraca wartość przy użyciu `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="be7ab-117">(Zobacz [instrukcja Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ wartości zwracanej jest zwracany typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be7ab-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be7ab-118">Remarks</span></span>  
 <span data-ttu-id="be7ab-119">A *wyrażenia lambda* jest funkcją bez nazwy, która jest obliczana i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="be7ab-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="be7ab-120">Można użyć wyrażenia lambda dowolnym można użyć typu delegata, z wyjątkiem jako argument `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="be7ab-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="be7ab-121">Aby uzyskać więcej informacji dotyczących obiektów delegowanych i korzystanie z wyrażenia lambda z delegatów, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="be7ab-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="be7ab-122">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="be7ab-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="be7ab-123">Składnia wyrażenia lambda podobny ze standardową funkcję.</span><span class="sxs-lookup"><span data-stu-id="be7ab-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="be7ab-124">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="be7ab-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="be7ab-125">Wyrażenia lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="be7ab-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="be7ab-126">Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="be7ab-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="be7ab-127">Wyrażenia lambda nie należy używać `As` klauzuli, aby określić typ zwracany funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="be7ab-128">Zamiast tego typu jest wywnioskowany na podstawie wartości, która daje w wyniku treści wyrażenia lambda jeden wiersz lub wartość zwracana w wielowierszowym wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="be7ab-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="be7ab-129">Na przykład, jeśli treść wyrażenia lambda jeden wiersz jest `Where cust.City = "London"`, jego typem zwracanym jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="be7ab-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="be7ab-130">Treść wyrażenia lambda jeden wiersz musi być wyrażeniem, nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="be7ab-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="be7ab-131">Treść może zawierać wywołania procedurę function, ale nie wywołaniu procedury sub.</span><span class="sxs-lookup"><span data-stu-id="be7ab-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="be7ab-132">Albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich.</span><span class="sxs-lookup"><span data-stu-id="be7ab-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="be7ab-133">Parametry opcjonalne i Paramarray są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="be7ab-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="be7ab-134">Parametry ogólne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="be7ab-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be7ab-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="be7ab-135">Example</span></span>  
 <span data-ttu-id="be7ab-136">W poniższych przykładach pokazano dwa sposoby tworzenia wyrażenia lambda proste.</span><span class="sxs-lookup"><span data-stu-id="be7ab-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="be7ab-137">Używa pierwszego `Dim` o podanie nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="be7ab-138">W wywołaniu funkcji, wysyłania wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="be7ab-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="be7ab-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="be7ab-139">Example</span></span>  
 <span data-ttu-id="be7ab-140">Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="be7ab-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="be7ab-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="be7ab-141">Example</span></span>  
 <span data-ttu-id="be7ab-142">Poniżej przedstawiono przykład zwiększa jej argument, który zwraca wartość wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="be7ab-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="be7ab-143">W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="be7ab-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="be7ab-144">Aby uzyskać więcej przykładów, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="be7ab-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="be7ab-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="be7ab-145">Example</span></span>  
 <span data-ttu-id="be7ab-146">Wyrażenia lambda opierają się wiele operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]i może służyć jawnie w zapytaniach oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="be7ab-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="be7ab-147">W poniższym przykładzie przedstawiono typowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, następuje translacja zapytania do formatu — metoda.</span><span class="sxs-lookup"><span data-stu-id="be7ab-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="be7ab-148">Aby uzyskać więcej informacji o metodach zapytania, zobacz [zapytania](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="be7ab-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="be7ab-149">Aby uzyskać więcej informacji dotyczących standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="be7ab-149">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7ab-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be7ab-150">See Also</span></span>  
 [<span data-ttu-id="be7ab-151">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="be7ab-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="be7ab-152">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="be7ab-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="be7ab-153">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="be7ab-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="be7ab-154">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="be7ab-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="be7ab-155">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="be7ab-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="be7ab-156">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="be7ab-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="be7ab-157">Jeśli — Operator</span><span class="sxs-lookup"><span data-stu-id="be7ab-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="be7ab-158">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="be7ab-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
