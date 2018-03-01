---
title: "* — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 450d728e44ef5639d75369e05b47cb3009b4d769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="fcec8-102">\* Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcec8-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="fcec8-103">Mnoży dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="fcec8-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcec8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcec8-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="fcec8-105">Części</span><span class="sxs-lookup"><span data-stu-id="fcec8-105">Parts</span></span>  
  
|<span data-ttu-id="fcec8-106">Termin</span><span class="sxs-lookup"><span data-stu-id="fcec8-106">Term</span></span>|<span data-ttu-id="fcec8-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="fcec8-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="fcec8-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fcec8-108">Required.</span></span> <span data-ttu-id="fcec8-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="fcec8-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="fcec8-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fcec8-110">Required.</span></span> <span data-ttu-id="fcec8-111">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="fcec8-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="fcec8-112">Wynik</span><span class="sxs-lookup"><span data-stu-id="fcec8-112">Result</span></span>  
 <span data-ttu-id="fcec8-113">Wynik jest iloczyn `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="fcec8-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="fcec8-114">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="fcec8-114">Supported Types</span></span>  
 <span data-ttu-id="fcec8-115">Wszystkie typy liczbowe w tym typy bez znaku i liczb zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fcec8-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcec8-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcec8-116">Remarks</span></span>  
 <span data-ttu-id="fcec8-117">Typ danych w wyniku zależy od typów argumenty operacji.</span><span class="sxs-lookup"><span data-stu-id="fcec8-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="fcec8-118">W poniższej tabeli przedstawiono, jak typ danych wyniku jest określana.</span><span class="sxs-lookup"><span data-stu-id="fcec8-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="fcec8-119">Argument operacji typy danych</span><span class="sxs-lookup"><span data-stu-id="fcec8-119">Operand data types</span></span>|<span data-ttu-id="fcec8-120">Typ danych wyników</span><span class="sxs-lookup"><span data-stu-id="fcec8-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="fcec8-121">Oba wyrażenia są typy całkowite danych ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtów](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krótki](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [całkowitą](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger —](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [długi](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="fcec8-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="fcec8-122">Dane typu liczbowego odpowiednie dla typów danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="fcec8-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="fcec8-123">Zobacz "Całkowitą arytmetycznego" tabele w [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="fcec8-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="fcec8-124">Oba wyrażenia są [dziesiętną](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="fcec8-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="fcec8-125">Oba wyrażenia są [pojedynczego](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="fcec8-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="fcec8-126">Jedno z wyrażeń ma typ danych liczb zmiennoprzecinkowych (`Single` lub [podwójne](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nie oba `Single` (Uwaga `Decimal` nie jest typem danych zmiennoprzecinkowych)</span><span class="sxs-lookup"><span data-stu-id="fcec8-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="fcec8-127">Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="fcec8-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fcec8-128">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="fcec8-128">Overloading</span></span>  
 <span data-ttu-id="fcec8-129">`*` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fcec8-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fcec8-130">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="fcec8-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fcec8-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fcec8-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcec8-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcec8-132">Example</span></span>  
 <span data-ttu-id="fcec8-133">W tym przykładzie użyto `*` operatora, aby pomnożyć dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="fcec8-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="fcec8-134">Wynik jest iloczyn dwóch argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="fcec8-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fcec8-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcec8-135">See Also</span></span>  
 [<span data-ttu-id="fcec8-136">\* = — Operator</span><span class="sxs-lookup"><span data-stu-id="fcec8-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="fcec8-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="fcec8-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="fcec8-138">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcec8-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="fcec8-139">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="fcec8-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="fcec8-140">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcec8-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
