---
title: Not, operator
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348307"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="66d4e-102">Not — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66d4e-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="66d4e-103">Wykonuje logiczne negację na wyrażeniu `Boolean` lub bitowe negację na wyrażeniu liczbowym.</span><span class="sxs-lookup"><span data-stu-id="66d4e-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66d4e-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="66d4e-105">Części</span><span class="sxs-lookup"><span data-stu-id="66d4e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="66d4e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66d4e-106">Required.</span></span> <span data-ttu-id="66d4e-107">Dowolne `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="66d4e-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="66d4e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66d4e-108">Required.</span></span> <span data-ttu-id="66d4e-109">Dowolne `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="66d4e-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66d4e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66d4e-110">Remarks</span></span>  
 <span data-ttu-id="66d4e-111">W przypadku wyrażeń `Boolean` w poniższej tabeli przedstawiono sposób, w jaki `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="66d4e-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="66d4e-112">Jeśli `expression` jest</span><span class="sxs-lookup"><span data-stu-id="66d4e-112">If `expression` is</span></span>|<span data-ttu-id="66d4e-113">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="66d4e-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="66d4e-114">W przypadku wyrażeń liczbowych operator `Not` odwraca wartości bitowe dowolnego wyrażenia liczbowego i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="66d4e-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="66d4e-115">Jeśli bit w `expression` jest</span><span class="sxs-lookup"><span data-stu-id="66d4e-115">If bit in `expression` is</span></span>|<span data-ttu-id="66d4e-116">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="66d4e-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="66d4e-117">1</span><span class="sxs-lookup"><span data-stu-id="66d4e-117">1</span></span>|<span data-ttu-id="66d4e-118">0</span><span class="sxs-lookup"><span data-stu-id="66d4e-118">0</span></span>|  
|<span data-ttu-id="66d4e-119">0</span><span class="sxs-lookup"><span data-stu-id="66d4e-119">0</span></span>|<span data-ttu-id="66d4e-120">1</span><span class="sxs-lookup"><span data-stu-id="66d4e-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="66d4e-121">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="66d4e-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="66d4e-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="66d4e-122">Data Types</span></span>  
 <span data-ttu-id="66d4e-123">W przypadku negacji logicznej, typ danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="66d4e-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="66d4e-124">W przypadku negacji bitowej dane wynikowe są takie same jak dla `expression`.</span><span class="sxs-lookup"><span data-stu-id="66d4e-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="66d4e-125">Jeśli jednak wyrażenie jest `Decimal`, wynik jest `Long`.</span><span class="sxs-lookup"><span data-stu-id="66d4e-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="66d4e-126">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="66d4e-126">Overloading</span></span>  
 <span data-ttu-id="66d4e-127">Operator `Not` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować swoje zachowanie, gdy jego operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="66d4e-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="66d4e-128">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="66d4e-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="66d4e-129">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="66d4e-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66d4e-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="66d4e-130">Example</span></span>  
 <span data-ttu-id="66d4e-131">Poniższy przykład używa operatora `Not`, aby przeprowadzić logiczne negację na wyrażeniu `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="66d4e-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="66d4e-132">Wynikiem jest wartość `Boolean`, która reprezentuje zwrot wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="66d4e-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="66d4e-133">Powyższy przykład daje wyniki odpowiednio `False` i `True`.</span><span class="sxs-lookup"><span data-stu-id="66d4e-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66d4e-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="66d4e-134">Example</span></span>  
 <span data-ttu-id="66d4e-135">Poniższy przykład używa operatora `Not` do wykonywania logicznego negacji poszczególnych bitów wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="66d4e-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="66d4e-136">Bit w wzorcu wyniku jest ustawiony na odwrotność odpowiedniego bitu we wzorcu operandu, łącznie z bitem znaku.</span><span class="sxs-lookup"><span data-stu-id="66d4e-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="66d4e-137">Powyższy przykład daje wyniki odpowiednio – 11, – 9 i – 7.</span><span class="sxs-lookup"><span data-stu-id="66d4e-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d4e-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66d4e-138">See also</span></span>

- [<span data-ttu-id="66d4e-139">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66d4e-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="66d4e-140">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66d4e-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="66d4e-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="66d4e-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="66d4e-142">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="66d4e-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
