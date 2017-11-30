---
title: "\\ — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38718b109b4b3865238267039908ea1d51d06229
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c2900-102">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2900-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="c2900-103">Dzieli dwie liczby i zwraca wynik liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="c2900-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2900-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2900-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c2900-105">Części</span><span class="sxs-lookup"><span data-stu-id="c2900-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="c2900-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c2900-106">Required.</span></span> <span data-ttu-id="c2900-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="c2900-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c2900-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c2900-108">Required.</span></span> <span data-ttu-id="c2900-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="c2900-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c2900-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="c2900-110">Supported Types</span></span>  
 <span data-ttu-id="c2900-111">Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c2900-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="c2900-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="c2900-112">Result</span></span>  
 <span data-ttu-id="c2900-113">Wynik jest iloraz liczb całkowitych z `expression1` rozdzielonych `expression2`, które odrzuca wszystkie pozostałe i zachowuje całkowitą część.</span><span class="sxs-lookup"><span data-stu-id="c2900-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="c2900-114">Jest to nazywane *obcięcie*.</span><span class="sxs-lookup"><span data-stu-id="c2900-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="c2900-115">Typ danych wyniku jest odpowiednie dla typów dane typu liczbowego `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="c2900-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="c2900-116">Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="c2900-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="c2900-117">[/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Zwraca iloraz pełnego, który zachowuje reszta w część ułamkowa.</span><span class="sxs-lookup"><span data-stu-id="c2900-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2900-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2900-118">Remarks</span></span>  
 <span data-ttu-id="c2900-119">Przed wykonaniem podziału, Visual Basic próbuje przekonwertować zmiennoprzecinkowe wyrażenie liczbowe, aby `Long`.</span><span class="sxs-lookup"><span data-stu-id="c2900-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="c2900-120">Jeśli `Option Strict` jest `On`, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c2900-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="c2900-121">Jeśli `Option Strict` jest `Off`, <xref:System.OverflowException> jest możliwe, jeśli wartość jest poza zakresem [typu danych Long](../../../visual-basic/language-reference/data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c2900-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="c2900-122">Konwersja do `Long` jest również podlegają *zaokrąglenie do zaokrąglania*.</span><span class="sxs-lookup"><span data-stu-id="c2900-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="c2900-123">Aby uzyskać więcej informacji, zobacz "Ułamkowych części" w [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c2900-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="c2900-124">Jeśli `expression1` lub `expression2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="c2900-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="c2900-125">Próba dzielenia przez Zero</span><span class="sxs-lookup"><span data-stu-id="c2900-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="c2900-126">Jeśli `expression2` daje w wyniku wartość 0, `\` zgłasza operator <xref:System.DivideByZeroException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c2900-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="c2900-127">Dotyczy to wszystkich typów danych numerycznych argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="c2900-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2900-128">`\` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c2900-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c2900-129">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="c2900-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c2900-130">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c2900-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2900-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2900-131">Example</span></span>  
 <span data-ttu-id="c2900-132">W poniższym przykładzie użyto `\` operatora, aby wykonać dzielenie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="c2900-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="c2900-133">Wynik jest liczba całkowita, która reprezentuje iloraz liczb całkowitych z dwóch argumentów operacji pozostałych odrzucone.</span><span class="sxs-lookup"><span data-stu-id="c2900-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 <span data-ttu-id="c2900-134">Wyrażenia w poprzednim przykładzie zwracają wartości 2, 3, 33 i -22, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c2900-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2900-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2900-135">See Also</span></span>  
 [<span data-ttu-id="c2900-136">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="c2900-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="c2900-137">/ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2900-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="c2900-138">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c2900-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="c2900-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="c2900-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="c2900-140">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2900-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="c2900-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="c2900-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="c2900-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2900-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
