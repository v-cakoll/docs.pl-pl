---
title: '* — Operator (Visual Basic)'
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
ms.openlocfilehash: e723667b6397fe758ae2f33babe27c0e41887aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641177"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5caaf-102">\* Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5caaf-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="5caaf-103">Mnoży dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="5caaf-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5caaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5caaf-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="5caaf-105">Części</span><span class="sxs-lookup"><span data-stu-id="5caaf-105">Parts</span></span>  
  
|<span data-ttu-id="5caaf-106">Termin</span><span class="sxs-lookup"><span data-stu-id="5caaf-106">Term</span></span>|<span data-ttu-id="5caaf-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="5caaf-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="5caaf-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5caaf-108">Required.</span></span> <span data-ttu-id="5caaf-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="5caaf-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="5caaf-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5caaf-110">Required.</span></span> <span data-ttu-id="5caaf-111">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="5caaf-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="5caaf-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="5caaf-112">Result</span></span>  
 <span data-ttu-id="5caaf-113">Wynik jest wynikiem `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="5caaf-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="5caaf-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="5caaf-114">Supported Types</span></span>  
 <span data-ttu-id="5caaf-115">Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5caaf-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5caaf-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5caaf-116">Remarks</span></span>  
 <span data-ttu-id="5caaf-117">Typ danych wynik zależy od typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="5caaf-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="5caaf-118">W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.</span><span class="sxs-lookup"><span data-stu-id="5caaf-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="5caaf-119">Argumentami o typach danych</span><span class="sxs-lookup"><span data-stu-id="5caaf-119">Operand data types</span></span>|<span data-ttu-id="5caaf-120">Typ danych wyniku</span><span class="sxs-lookup"><span data-stu-id="5caaf-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="5caaf-121">Oba wyrażenia są integralnymi typami danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="5caaf-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="5caaf-122">Typ danych numerycznych, odpowiednie dla typów danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="5caaf-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="5caaf-123">Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5caaf-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="5caaf-124">Oba wyrażenia są [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5caaf-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="5caaf-125">Oba wyrażenia są [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5caaf-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="5caaf-126">Albo wyrażenie jest typu zmiennoprzecinkowego (`Single` lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie obu `Single` (Uwaga `Decimal` nie jest typu zmiennoprzecinkowego)</span><span class="sxs-lookup"><span data-stu-id="5caaf-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="5caaf-127">Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.</span><span class="sxs-lookup"><span data-stu-id="5caaf-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5caaf-128">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="5caaf-128">Overloading</span></span>  
 <span data-ttu-id="5caaf-129">`*` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5caaf-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5caaf-130">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5caaf-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5caaf-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5caaf-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5caaf-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="5caaf-132">Example</span></span>  
 <span data-ttu-id="5caaf-133">W tym przykładzie użyto `*` operatora mnożenia dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="5caaf-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="5caaf-134">Wynik jest iloczyn dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="5caaf-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5caaf-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5caaf-135">See also</span></span>
- [<span data-ttu-id="5caaf-136">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="5caaf-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="5caaf-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="5caaf-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="5caaf-138">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5caaf-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5caaf-139">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5caaf-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5caaf-140">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5caaf-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
