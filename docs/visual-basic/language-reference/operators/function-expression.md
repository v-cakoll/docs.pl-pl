---
title: Function — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703001"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="3d92f-102">Function — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d92f-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="3d92f-103">Deklaruje parametry i kod, który definiuje wyrażenie lambda funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d92f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d92f-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="3d92f-105">Części</span><span class="sxs-lookup"><span data-stu-id="3d92f-105">Parts</span></span>  
  
|<span data-ttu-id="3d92f-106">Termin</span><span class="sxs-lookup"><span data-stu-id="3d92f-106">Term</span></span>|<span data-ttu-id="3d92f-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="3d92f-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="3d92f-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3d92f-108">Optional.</span></span> <span data-ttu-id="3d92f-109">Lista nazwy zmiennych lokalnych, które reprezentują parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="3d92f-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="3d92f-110">Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="3d92f-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="3d92f-111">Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="3d92f-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="3d92f-112">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d92f-112">Required.</span></span> <span data-ttu-id="3d92f-113">Pojedyncze wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="3d92f-113">A single expression.</span></span> <span data-ttu-id="3d92f-114">Typ wyrażenia jest zwracany typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="3d92f-115">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d92f-115">Required.</span></span> <span data-ttu-id="3d92f-116">Listę instrukcji, która zwraca wartość przy użyciu `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="3d92f-117">(Zobacz [Return, instrukcja](../../../visual-basic/language-reference/statements/return-statement.md).) Typ wartości zwracanej jest zwracany typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d92f-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d92f-118">Remarks</span></span>  
 <span data-ttu-id="3d92f-119">A *wyrażenia lambda* jest funkcją bez nazwy, który oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="3d92f-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="3d92f-120">Można użyć wyrażenia lambda dowolnym można użyć typu delegata, z wyjątkiem jako argument do `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="3d92f-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="3d92f-121">Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z obiektów delegowanych, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="3d92f-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="3d92f-122">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="3d92f-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="3d92f-123">Składnia wyrażenia lambda przypomina w przypadku standardowej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="3d92f-124">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="3d92f-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="3d92f-125">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="3d92f-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="3d92f-126">Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="3d92f-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="3d92f-127">Nie należy używać wyrażeń lambda `As` klauzuli do wyznaczenia zwracany typ funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="3d92f-128">Zamiast tego typ jest wnioskowany z wartość, która daje w wyniku treść wyrażenia lambda jeden wiersz lub wartość zwracana wyrażenia lambda wielowierszowe.</span><span class="sxs-lookup"><span data-stu-id="3d92f-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="3d92f-129">Na przykład, jeśli treść wyrażenia lambda jednowierszowego jest `Where cust.City = "London"`, jego typem zwracanym jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="3d92f-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="3d92f-130">Treść wyrażenia lambda w pojedynczej linii musi być wyrażeniem, nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="3d92f-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="3d92f-131">Treść może obejmować wywołania procedurę function, ale nie po wywołaniu procedury sub.</span><span class="sxs-lookup"><span data-stu-id="3d92f-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="3d92f-132">Musi mieć określony albo wszystkie parametry można wywnioskować typów danych lub wszystkich.</span><span class="sxs-lookup"><span data-stu-id="3d92f-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="3d92f-133">Parametry opcjonalne i Paramarray nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3d92f-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="3d92f-134">Parametry ogólne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3d92f-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d92f-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d92f-135">Example</span></span>  
 <span data-ttu-id="3d92f-136">W poniższych przykładach pokazano dwa sposoby tworzenia wyrażeń lambda proste.</span><span class="sxs-lookup"><span data-stu-id="3d92f-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="3d92f-137">Używa pierwszego `Dim` Podaj nazwę dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="3d92f-138">Aby wywołać funkcję, Wyślij w wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="3d92f-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3d92f-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d92f-139">Example</span></span>  
 <span data-ttu-id="3d92f-140">Alternatywnie można zadeklarować i uruchom funkcję w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3d92f-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="3d92f-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d92f-141">Example</span></span>  
 <span data-ttu-id="3d92f-142">Oto przykład wyrażenie lambda, która zwiększa jej argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="3d92f-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="3d92f-143">W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="3d92f-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="3d92f-144">Aby uzyskać więcej przykładów, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3d92f-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="3d92f-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d92f-145">Example</span></span>  
 <span data-ttu-id="3d92f-146">Wyrażenia lambda podstawą wielu operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]i może służyć jawnie oparte na metodzie zapytania.</span><span class="sxs-lookup"><span data-stu-id="3d92f-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="3d92f-147">W poniższym przykładzie przedstawiono typowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, następuje tłumaczenie zapytania do formatu metody.</span><span class="sxs-lookup"><span data-stu-id="3d92f-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="3d92f-148">Aby uzyskać więcej informacji na temat metody zapytań, zobacz [zapytania](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d92f-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="3d92f-149">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Przegląd](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d92f-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d92f-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d92f-150">See Also</span></span>  
 [<span data-ttu-id="3d92f-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3d92f-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="3d92f-152">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="3d92f-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="3d92f-153">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="3d92f-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="3d92f-154">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="3d92f-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="3d92f-155">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="3d92f-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="3d92f-156">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="3d92f-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="3d92f-157">If, operator</span><span class="sxs-lookup"><span data-stu-id="3d92f-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="3d92f-158">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="3d92f-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
