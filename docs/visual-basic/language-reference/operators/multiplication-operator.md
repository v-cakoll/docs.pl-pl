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
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828956"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ba336-102">\* Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba336-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="ba336-103">Mnoży dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="ba336-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba336-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba336-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="ba336-105">Części</span><span class="sxs-lookup"><span data-stu-id="ba336-105">Parts</span></span>  
  
|<span data-ttu-id="ba336-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ba336-106">Term</span></span>|<span data-ttu-id="ba336-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ba336-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="ba336-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ba336-108">Required.</span></span> <span data-ttu-id="ba336-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="ba336-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="ba336-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ba336-110">Required.</span></span> <span data-ttu-id="ba336-111">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="ba336-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="ba336-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="ba336-112">Result</span></span>  
 <span data-ttu-id="ba336-113">Wynik jest wynikiem `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="ba336-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="ba336-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="ba336-114">Supported Types</span></span>  
 <span data-ttu-id="ba336-115">Wszystkie typy liczbowe, w tym typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ba336-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba336-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba336-116">Remarks</span></span>  
 <span data-ttu-id="ba336-117">Typ danych wynik zależy od typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="ba336-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="ba336-118">W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.</span><span class="sxs-lookup"><span data-stu-id="ba336-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="ba336-119">Argumentami o typach danych</span><span class="sxs-lookup"><span data-stu-id="ba336-119">Operand data types</span></span>|<span data-ttu-id="ba336-120">Typ danych wyniku</span><span class="sxs-lookup"><span data-stu-id="ba336-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="ba336-121">Oba wyrażenia są integralnymi typami danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długie](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="ba336-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="ba336-122">Typ danych numerycznych, odpowiednie dla typów danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="ba336-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="ba336-123">Zobacz tabele "Integer arytmetyczny" w [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="ba336-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="ba336-124">Oba wyrażenia są [dziesiętna](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ba336-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="ba336-125">Oba wyrażenia są [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="ba336-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="ba336-126">Albo wyrażenie jest typu zmiennoprzecinkowego (`Single` lub [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie obu `Single` (Uwaga `Decimal` nie jest typu zmiennoprzecinkowego)</span><span class="sxs-lookup"><span data-stu-id="ba336-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="ba336-127">Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.</span><span class="sxs-lookup"><span data-stu-id="ba336-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ba336-128">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="ba336-128">Overloading</span></span>  
 <span data-ttu-id="ba336-129">`*` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ba336-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ba336-130">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="ba336-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ba336-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ba336-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba336-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba336-132">Example</span></span>  
 <span data-ttu-id="ba336-133">W tym przykładzie użyto `*` operatora mnożenia dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="ba336-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="ba336-134">Wynik jest iloczyn dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="ba336-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ba336-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba336-135">See also</span></span>

- [<span data-ttu-id="ba336-136">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="ba336-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="ba336-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="ba336-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ba336-138">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba336-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ba336-139">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="ba336-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ba336-140">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba336-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
