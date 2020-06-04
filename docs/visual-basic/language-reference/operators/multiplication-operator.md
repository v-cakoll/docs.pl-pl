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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409326"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="67c8e-102">\* Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67c8e-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="67c8e-103">Mnoży dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="67c8e-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67c8e-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="67c8e-105">Części</span><span class="sxs-lookup"><span data-stu-id="67c8e-105">Parts</span></span>  
  
|<span data-ttu-id="67c8e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="67c8e-106">Term</span></span>|<span data-ttu-id="67c8e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="67c8e-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="67c8e-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="67c8e-108">Required.</span></span> <span data-ttu-id="67c8e-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="67c8e-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="67c8e-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="67c8e-110">Required.</span></span> <span data-ttu-id="67c8e-111">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="67c8e-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="67c8e-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="67c8e-112">Result</span></span>  
 <span data-ttu-id="67c8e-113">Wynikiem jest iloczyn `number1` i `number2` .</span><span class="sxs-lookup"><span data-stu-id="67c8e-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="67c8e-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="67c8e-114">Supported Types</span></span>  
 <span data-ttu-id="67c8e-115">Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="67c8e-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67c8e-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67c8e-116">Remarks</span></span>  
 <span data-ttu-id="67c8e-117">Typ danych wyniku zależy od typów operandów.</span><span class="sxs-lookup"><span data-stu-id="67c8e-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="67c8e-118">W poniższej tabeli przedstawiono sposób określania typu danych wyniku.</span><span class="sxs-lookup"><span data-stu-id="67c8e-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="67c8e-119">Typy danych operandu</span><span class="sxs-lookup"><span data-stu-id="67c8e-119">Operand data types</span></span>|<span data-ttu-id="67c8e-120">Typ danych wynikowych</span><span class="sxs-lookup"><span data-stu-id="67c8e-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="67c8e-121">Oba wyrażenia są typami danych całkowitych[(](../data-types/sbyte-data-type.md) [bajty, Byte](../data-types/byte-data-type.md), [krótkie](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger —](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULONG](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="67c8e-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="67c8e-122">Typ danych liczbowych odpowiedni dla typów danych `number1` i `number2` .</span><span class="sxs-lookup"><span data-stu-id="67c8e-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="67c8e-123">Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="67c8e-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="67c8e-124">Oba wyrażenia są [dziesiętne](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="67c8e-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="67c8e-125">Oba wyrażenia są [pojedynczymi](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="67c8e-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="67c8e-126">Oba wyrażenia są typu danych zmiennoprzecinkowych ( `Single` lub [Double](../data-types/double-data-type.md)), ale nie obu `Single` (Uwaga nie `Decimal` jest typem danych zmiennoprzecinkowych)</span><span class="sxs-lookup"><span data-stu-id="67c8e-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="67c8e-127">Jeśli wyrażenie zwróci wartość [Nothing](../nothing.md), jest traktowane jako zero.</span><span class="sxs-lookup"><span data-stu-id="67c8e-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="67c8e-128">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="67c8e-128">Overloading</span></span>  
 <span data-ttu-id="67c8e-129">`*`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="67c8e-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="67c8e-130">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="67c8e-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="67c8e-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67c8e-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67c8e-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="67c8e-132">Example</span></span>  
 <span data-ttu-id="67c8e-133">Ten przykład używa `*` operatora, aby pomnożyć dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="67c8e-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="67c8e-134">Wynikiem jest iloczyn dwóch operandów.</span><span class="sxs-lookup"><span data-stu-id="67c8e-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="67c8e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67c8e-135">See also</span></span>

- [<span data-ttu-id="67c8e-136">Operator \* =</span><span class="sxs-lookup"><span data-stu-id="67c8e-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="67c8e-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="67c8e-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="67c8e-138">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67c8e-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="67c8e-139">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="67c8e-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="67c8e-140">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67c8e-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
