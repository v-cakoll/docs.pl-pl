---
title: Function, wyrażenie
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371184"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="b964b-102">Function — Wyrażenie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b964b-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="b964b-103">Deklaruje parametry i kod, który definiuje funkcję wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b964b-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b964b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b964b-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="b964b-105">Części</span><span class="sxs-lookup"><span data-stu-id="b964b-105">Parts</span></span>  
  
|<span data-ttu-id="b964b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b964b-106">Term</span></span>|<span data-ttu-id="b964b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b964b-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="b964b-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b964b-108">Optional.</span></span> <span data-ttu-id="b964b-109">Lista nazw zmiennych lokalnych, które reprezentują parametry tej procedury.</span><span class="sxs-lookup"><span data-stu-id="b964b-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="b964b-110">Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta.</span><span class="sxs-lookup"><span data-stu-id="b964b-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="b964b-111">Zobacz [listę parametrów](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b964b-111">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="b964b-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b964b-112">Required.</span></span> <span data-ttu-id="b964b-113">Pojedyncze wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b964b-113">A single expression.</span></span> <span data-ttu-id="b964b-114">Typ wyrażenia jest zwracanym typem funkcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="b964b-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b964b-115">Required.</span></span> <span data-ttu-id="b964b-116">Lista instrukcji zwracających wartość przy użyciu `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="b964b-117">(Patrz [instrukcja return](../statements/return-statement.md)). Typ zwracanej wartości jest zwracanym typem funkcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-117">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b964b-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b964b-118">Remarks</span></span>  
 <span data-ttu-id="b964b-119">*Wyrażenie lambda* jest funkcją bez nazwy, która oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="b964b-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="b964b-120">Możesz użyć wyrażenia lambda wszędzie tam, gdzie można użyć typu delegata, z wyjątkiem argumentu `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="b964b-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="b964b-121">Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../statements/delegate-statement.md) i [Swobodna konwersja delegata](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="b964b-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="b964b-122">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="b964b-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="b964b-123">Składnia wyrażenia lambda jest podobna do funkcji standardowej.</span><span class="sxs-lookup"><span data-stu-id="b964b-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="b964b-124">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="b964b-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="b964b-125">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="b964b-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="b964b-126">Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="b964b-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="b964b-127">Wyrażenia lambda nie używają `As` klauzuli do wyznaczania zwracanego typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="b964b-128">Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda pojedynczego wiersza, lub wartości zwracanej wielowierszowego wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b964b-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="b964b-129">Na przykład jeśli treść wyrażenia lambda pojedynczego wiersza ma wartość `Where cust.City = "London"` , jego typem zwracanym jest `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b964b-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="b964b-130">Treść wyrażenia lambda pojedynczego wiersza musi być wyrażeniem, a nie instrukcją.</span><span class="sxs-lookup"><span data-stu-id="b964b-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="b964b-131">Treść może składać się z wywołania procedury funkcji, ale nie wywołania procedury Sub.</span><span class="sxs-lookup"><span data-stu-id="b964b-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="b964b-132">Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="b964b-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="b964b-133">Parametry opcjonalne i ParamArray są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="b964b-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="b964b-134">Parametry ogólne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="b964b-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b964b-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="b964b-135">Example</span></span>  
 <span data-ttu-id="b964b-136">W poniższych przykładach pokazano dwa sposoby tworzenia prostych wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="b964b-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="b964b-137">Pierwszy używa `Dim` do podania nazwy dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="b964b-138">Aby wywołać funkcję, należy wysłać w wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="b964b-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b964b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="b964b-139">Example</span></span>  
 <span data-ttu-id="b964b-140">Alternatywnie można zadeklarować i uruchomić funkcję w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b964b-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b964b-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="b964b-141">Example</span></span>  
 <span data-ttu-id="b964b-142">Poniżej znajduje się przykład wyrażenia lambda, które zwiększa jego argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="b964b-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="b964b-143">Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="b964b-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="b964b-144">Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b964b-144">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b964b-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="b964b-145">Example</span></span>  
 <span data-ttu-id="b964b-146">Wyrażenia lambda podstawą wiele operatorów zapytań w zapytaniach zintegrowanych z językiem (LINQ) i mogą być używane jawnie w zapytaniach opartych na metodzie.</span><span class="sxs-lookup"><span data-stu-id="b964b-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="b964b-147">W poniższym przykładzie przedstawiono typowe zapytanie LINQ, po którym następuje tłumaczenie zapytania do formatu metody.</span><span class="sxs-lookup"><span data-stu-id="b964b-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="b964b-148">Aby uzyskać więcej informacji na temat metod zapytań, zobacz [zapytania](../queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="b964b-148">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="b964b-149">Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b964b-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b964b-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b964b-150">See also</span></span>

- [<span data-ttu-id="b964b-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b964b-151">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="b964b-152">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="b964b-152">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="b964b-153">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="b964b-153">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="b964b-154">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="b964b-154">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="b964b-155">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="b964b-155">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="b964b-156">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="b964b-156">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="b964b-157">If, operator</span><span class="sxs-lookup"><span data-stu-id="b964b-157">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="b964b-158">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="b964b-158">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
