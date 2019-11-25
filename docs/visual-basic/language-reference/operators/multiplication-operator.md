---
title: '* Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4f6a8ea2c5f4e23791afdfe98d2a08bf67219048
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348364"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="089e3-102">\* Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="089e3-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="089e3-103">Multiplies two numbers.</span><span class="sxs-lookup"><span data-stu-id="089e3-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="089e3-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="089e3-105">Części</span><span class="sxs-lookup"><span data-stu-id="089e3-105">Parts</span></span>  
  
|<span data-ttu-id="089e3-106">Termin</span><span class="sxs-lookup"><span data-stu-id="089e3-106">Term</span></span>|<span data-ttu-id="089e3-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="089e3-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="089e3-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="089e3-108">Required.</span></span> <span data-ttu-id="089e3-109">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="089e3-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="089e3-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="089e3-110">Required.</span></span> <span data-ttu-id="089e3-111">Any numeric expression.</span><span class="sxs-lookup"><span data-stu-id="089e3-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="089e3-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="089e3-112">Result</span></span>  
 <span data-ttu-id="089e3-113">The result is the product of `number1` and `number2`.</span><span class="sxs-lookup"><span data-stu-id="089e3-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="089e3-114">Supported Types</span><span class="sxs-lookup"><span data-stu-id="089e3-114">Supported Types</span></span>  
 <span data-ttu-id="089e3-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="089e3-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="089e3-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="089e3-116">Remarks</span></span>  
 <span data-ttu-id="089e3-117">The data type of the result depends on the types of the operands.</span><span class="sxs-lookup"><span data-stu-id="089e3-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="089e3-118">The following table shows how the data type of the result is determined.</span><span class="sxs-lookup"><span data-stu-id="089e3-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="089e3-119">Operand data types</span><span class="sxs-lookup"><span data-stu-id="089e3-119">Operand data types</span></span>|<span data-ttu-id="089e3-120">Result data type</span><span class="sxs-lookup"><span data-stu-id="089e3-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="089e3-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="089e3-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="089e3-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span><span class="sxs-lookup"><span data-stu-id="089e3-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="089e3-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="089e3-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="089e3-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="089e3-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="089e3-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="089e3-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="089e3-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span><span class="sxs-lookup"><span data-stu-id="089e3-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="089e3-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span><span class="sxs-lookup"><span data-stu-id="089e3-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="089e3-128">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="089e3-128">Overloading</span></span>  
 <span data-ttu-id="089e3-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="089e3-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="089e3-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="089e3-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="089e3-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="089e3-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="089e3-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="089e3-132">Example</span></span>  
 <span data-ttu-id="089e3-133">This example uses the `*` operator to multiply two numbers.</span><span class="sxs-lookup"><span data-stu-id="089e3-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="089e3-134">The result is the product of the two operands.</span><span class="sxs-lookup"><span data-stu-id="089e3-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="089e3-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="089e3-135">See also</span></span>

- [<span data-ttu-id="089e3-136">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="089e3-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="089e3-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="089e3-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="089e3-138">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="089e3-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="089e3-139">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="089e3-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="089e3-140">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="089e3-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
