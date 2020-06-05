---
title: '\ — Operator'
ms.date: 07/20/2015
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
ms.openlocfilehash: 1f8095afc5f096928b946607adc715af49827022
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370885"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="443a1-102">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443a1-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="443a1-103">Dzieli dwie liczby i zwraca wynik w postaci liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="443a1-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="443a1-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="443a1-105">Części</span><span class="sxs-lookup"><span data-stu-id="443a1-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="443a1-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="443a1-106">Required.</span></span> <span data-ttu-id="443a1-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="443a1-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="443a1-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="443a1-108">Required.</span></span> <span data-ttu-id="443a1-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="443a1-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="443a1-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="443a1-110">Supported Types</span></span>  
 <span data-ttu-id="443a1-111">Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="443a1-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="443a1-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="443a1-112">Result</span></span>  
 <span data-ttu-id="443a1-113">Wynikiem jest iloraz wartości całkowitej `expression1` podzieloną przez `expression2` , która odrzuca resztę i zachowuje tylko część całkowitą.</span><span class="sxs-lookup"><span data-stu-id="443a1-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="443a1-114">Jest to tzw. *obcinanie*.</span><span class="sxs-lookup"><span data-stu-id="443a1-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="443a1-115">Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2` .</span><span class="sxs-lookup"><span data-stu-id="443a1-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="443a1-116">Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="443a1-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="443a1-117">[Operator/(Visual Basic)](floating-point-division-operator.md) zwraca pełny iloraz, który zachowuje resztę części ułamkowej.</span><span class="sxs-lookup"><span data-stu-id="443a1-117">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443a1-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="443a1-118">Remarks</span></span>  
 <span data-ttu-id="443a1-119">Przed przeprowadzeniem dzielenia, Visual Basic próbuje skonwertować dowolne wyrażenie liczbowe zmiennoprzecinkowe na `Long` .</span><span class="sxs-lookup"><span data-stu-id="443a1-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="443a1-120">Jeśli `Option Strict` jest `On` , wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="443a1-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="443a1-121">Jeśli `Option Strict` jest `Off` , <xref:System.OverflowException> jest to możliwe, jeśli wartość znajduje się poza zakresem [długiego typu danych](../data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="443a1-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="443a1-122">Konwersja na `Long` jest również uwarunkowana *zaokrągleniem przez Bank*.</span><span class="sxs-lookup"><span data-stu-id="443a1-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="443a1-123">Aby uzyskać więcej informacji, zobacz "części ułamkowe" w [funkcjach konwersji typów](../functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="443a1-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="443a1-124">Jeśli `expression1` lub `expression2` zwróci wartość [Nothing](../nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="443a1-124">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="443a1-125">Próba dzielenia przez zero</span><span class="sxs-lookup"><span data-stu-id="443a1-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="443a1-126">Jeśli `expression2` wartość jest równa zero, `\` operator zgłasza <xref:System.DivideByZeroException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="443a1-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="443a1-127">Dotyczy to wszystkich typów danych liczbowych argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="443a1-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="443a1-128">`\`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="443a1-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="443a1-129">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="443a1-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="443a1-130">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="443a1-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="443a1-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="443a1-131">Example</span></span>  
 <span data-ttu-id="443a1-132">Poniższy przykład używa operatora, `\` Aby wykonać dzielenie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="443a1-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="443a1-133">Wynik jest liczbą całkowitą, która reprezentuje iloraz liczby całkowitej dwóch operandów, z odrzuconym resztą.</span><span class="sxs-lookup"><span data-stu-id="443a1-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="443a1-134">Wyrażenia w poprzednim przykładzie zwracają odpowiednio wartości 2, 3, 33 i-22.</span><span class="sxs-lookup"><span data-stu-id="443a1-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443a1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="443a1-135">See also</span></span>

- [<span data-ttu-id="443a1-136">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="443a1-136">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="443a1-137">/— Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443a1-137">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="443a1-138">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="443a1-138">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="443a1-139">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="443a1-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="443a1-140">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443a1-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="443a1-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="443a1-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="443a1-142">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="443a1-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
