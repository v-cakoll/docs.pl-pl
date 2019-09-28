---
title: Function — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592205"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="059ea-102">Function — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="059ea-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="059ea-103">Deklaruje parametry i kod, który definiuje funkcję wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="059ea-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="059ea-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="059ea-105">Części</span><span class="sxs-lookup"><span data-stu-id="059ea-105">Parts</span></span>  
  
|<span data-ttu-id="059ea-106">Termin</span><span class="sxs-lookup"><span data-stu-id="059ea-106">Term</span></span>|<span data-ttu-id="059ea-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="059ea-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="059ea-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="059ea-108">Optional.</span></span> <span data-ttu-id="059ea-109">Lista nazw zmiennych lokalnych, które reprezentują parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="059ea-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="059ea-110">Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="059ea-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="059ea-111">Zobacz [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="059ea-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="059ea-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="059ea-112">Required.</span></span> <span data-ttu-id="059ea-113">Pojedyncze wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="059ea-113">A single expression.</span></span> <span data-ttu-id="059ea-114">Typ wyrażenia jest zwracanym typem funkcji.</span><span class="sxs-lookup"><span data-stu-id="059ea-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="059ea-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="059ea-115">Required.</span></span> <span data-ttu-id="059ea-116">Lista instrukcji zwracających wartość przy użyciu instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="059ea-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="059ea-117">(Patrz [instrukcja return](../../../visual-basic/language-reference/statements/return-statement.md)). Typ zwracanej wartości jest zwracanym typem funkcji.</span><span class="sxs-lookup"><span data-stu-id="059ea-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="059ea-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="059ea-118">Remarks</span></span>  
 <span data-ttu-id="059ea-119">*Wyrażenie lambda* jest funkcją bez nazwy, która oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="059ea-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="059ea-120">Możesz użyć wyrażenia lambda wszędzie tam, gdzie można użyć typu delegata, z wyjątkiem argumentu `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="059ea-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="059ea-121">Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) i [Swobodna konwersja delegata](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="059ea-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="059ea-122">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="059ea-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="059ea-123">Składnia wyrażenia lambda jest podobna do funkcji standardowej.</span><span class="sxs-lookup"><span data-stu-id="059ea-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="059ea-124">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="059ea-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="059ea-125">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="059ea-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="059ea-126">Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="059ea-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="059ea-127">Wyrażenia lambda nie używają klauzuli `As` do wyznaczania zwracanego typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="059ea-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="059ea-128">Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda pojedynczego wiersza, lub wartości zwracanej wielowierszowego wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="059ea-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="059ea-129">Na przykład jeśli treść wyrażenia lambda pojedynczego wiersza jest `Where cust.City = "London"`, jego typ zwracany to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="059ea-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="059ea-130">Treść wyrażenia lambda pojedynczego wiersza musi być wyrażeniem, a nie instrukcją.</span><span class="sxs-lookup"><span data-stu-id="059ea-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="059ea-131">Treść może składać się z wywołania procedury funkcji, ale nie wywołania procedury Sub.</span><span class="sxs-lookup"><span data-stu-id="059ea-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="059ea-132">Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="059ea-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="059ea-133">Parametry opcjonalne i ParamArray są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="059ea-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="059ea-134">Parametry ogólne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="059ea-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="059ea-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="059ea-135">Example</span></span>  
 <span data-ttu-id="059ea-136">W poniższych przykładach pokazano dwa sposoby tworzenia prostych wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="059ea-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="059ea-137">Pierwszy używa `Dim`, aby podać nazwę funkcji.</span><span class="sxs-lookup"><span data-stu-id="059ea-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="059ea-138">Aby wywołać funkcję, należy wysłać w wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="059ea-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="059ea-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="059ea-139">Example</span></span>  
 <span data-ttu-id="059ea-140">Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="059ea-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="059ea-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="059ea-141">Example</span></span>  
 <span data-ttu-id="059ea-142">Poniżej znajduje się przykład wyrażenia lambda, które zwiększa jego argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="059ea-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="059ea-143">Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="059ea-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="059ea-144">Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="059ea-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="059ea-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="059ea-145">Example</span></span>  
 <span data-ttu-id="059ea-146">Wyrażenia lambda podstawą wiele operatorów zapytań w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] i mogą być używane jawnie w zapytaniach opartych na metodzie.</span><span class="sxs-lookup"><span data-stu-id="059ea-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="059ea-147">W poniższym przykładzie przedstawiono typowe zapytanie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a następnie tłumaczenie zapytania do formatu metody.</span><span class="sxs-lookup"><span data-stu-id="059ea-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="059ea-148">Aby uzyskać więcej informacji na temat metod zapytań, zobacz [zapytania](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="059ea-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="059ea-149">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="059ea-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059ea-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="059ea-150">See also</span></span>

- [<span data-ttu-id="059ea-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="059ea-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="059ea-152">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="059ea-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="059ea-153">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="059ea-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="059ea-154">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="059ea-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="059ea-155">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="059ea-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="059ea-156">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="059ea-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="059ea-157">If, operator</span><span class="sxs-lookup"><span data-stu-id="059ea-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="059ea-158">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="059ea-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
