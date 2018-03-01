---
title: "Mod — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="3dc81-102">Mod — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dc81-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="3dc81-103">Dzieli dwie liczby i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="3dc81-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dc81-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="3dc81-105">Części</span><span class="sxs-lookup"><span data-stu-id="3dc81-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="3dc81-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3dc81-106">Required.</span></span> <span data-ttu-id="3dc81-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3dc81-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="3dc81-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3dc81-108">Required.</span></span> <span data-ttu-id="3dc81-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3dc81-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="3dc81-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="3dc81-110">Supported Types</span></span>  
 <span data-ttu-id="3dc81-111">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="3dc81-111">All numeric types.</span></span> <span data-ttu-id="3dc81-112">Obejmuje to typy bez znaku i zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="3dc81-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="3dc81-113">Wynik</span><span class="sxs-lookup"><span data-stu-id="3dc81-113">Result</span></span>  
 <span data-ttu-id="3dc81-114">Wynik jest resztę po `number1` przez `number2`.</span><span class="sxs-lookup"><span data-stu-id="3dc81-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="3dc81-115">Na przykład, wyrażenie `14 Mod 4` ocenia się na 2.</span><span class="sxs-lookup"><span data-stu-id="3dc81-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc81-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dc81-116">Remarks</span></span>  
 <span data-ttu-id="3dc81-117">Jeśli dowolny `number1` lub `number2` jest wartość zmiennoprzecinkową zmiennoprzecinkowe pozostałej części podziału jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="3dc81-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="3dc81-118">Typ danych wyniku to najmniejsza typu danych, który może posiadać wszystkie możliwe wartości wynikających z dzielenia z typami danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="3dc81-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="3dc81-119">Jeśli `number1` lub `number2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="3dc81-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="3dc81-120">Operatory powiązane są następujące:</span><span class="sxs-lookup"><span data-stu-id="3dc81-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="3dc81-121">[\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczbą całkowitą z dzielenia.</span><span class="sxs-lookup"><span data-stu-id="3dc81-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="3dc81-122">Na przykład, wyrażenie `14 \ 4` daje w wyniku 3.</span><span class="sxs-lookup"><span data-stu-id="3dc81-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="3dc81-123">[/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Zwraca iloraz pełne, łącznie z pozostałą, jako liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="3dc81-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="3dc81-124">Na przykład, wyrażenie `14 / 4` daje w wyniku 3.5.</span><span class="sxs-lookup"><span data-stu-id="3dc81-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="3dc81-125">Próba dzielenia przez Zero</span><span class="sxs-lookup"><span data-stu-id="3dc81-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="3dc81-126">Jeśli `number2` daje w wyniku wartość zero, zachowanie `Mod` operator zależy od typu danych operandów.</span><span class="sxs-lookup"><span data-stu-id="3dc81-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="3dc81-127">Zgłasza całkowitą dzielenia <xref:System.DivideByZeroException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3dc81-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="3dc81-128">Zwraca dzielenia liczb zmiennoprzecinkowych <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="3dc81-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="3dc81-129">Formuła równoważne</span><span class="sxs-lookup"><span data-stu-id="3dc81-129">Equivalent Formula</span></span>  
 <span data-ttu-id="3dc81-130">Wyrażenie `a Mod b` odpowiada jednej z następujących formuły:</span><span class="sxs-lookup"><span data-stu-id="3dc81-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="3dc81-131">Zmiennoprzecinkowe błędu</span><span class="sxs-lookup"><span data-stu-id="3dc81-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="3dc81-132">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dc81-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="3dc81-133">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="3dc81-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="3dc81-134">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="3dc81-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3dc81-135">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="3dc81-135">Overloading</span></span>  
 <span data-ttu-id="3dc81-136">`Mod` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania.</span><span class="sxs-lookup"><span data-stu-id="3dc81-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="3dc81-137">Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która obejmuje takie przeciążenia, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="3dc81-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3dc81-138">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3dc81-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dc81-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dc81-139">Example</span></span>  
 <span data-ttu-id="3dc81-140">W poniższym przykładzie użyto `Mod` operator do dzielenia dwie liczby i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="3dc81-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="3dc81-141">Jeśli liczba zmiennoprzecinkowa, albo liczbą wynik jest reprezentujący Pozostała liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="3dc81-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3dc81-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dc81-142">Example</span></span>  
 <span data-ttu-id="3dc81-143">W poniższym przykładzie pokazano ryzyko błędu argumentów operacji zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="3dc81-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="3dc81-144">W pierwszej instrukcji argumenty operacji są `Double`, i 0,2 jest nieskończenie identycznych ułamek binarnego z wartością przechowywaną 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="3dc81-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="3dc81-145">W drugim instrukcji literału znaku typu `D` wymusza oba argumenty do `Decimal`, i 0,2 ma reprezentację dokładne.</span><span class="sxs-lookup"><span data-stu-id="3dc81-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3dc81-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dc81-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="3dc81-147">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="3dc81-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="3dc81-148">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3dc81-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="3dc81-149">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="3dc81-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="3dc81-150">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="3dc81-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="3dc81-151">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3dc81-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="3dc81-152">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dc81-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
