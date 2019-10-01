---
title: Operator < < (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701112"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="76ec3-102">Operator \< @ no__t-1 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76ec3-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="76ec3-103">Wykonuje arytmetyczne przesunięcie w lewo na wzorcu bitowym.</span><span class="sxs-lookup"><span data-stu-id="76ec3-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ec3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76ec3-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="76ec3-105">Części</span><span class="sxs-lookup"><span data-stu-id="76ec3-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="76ec3-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="76ec3-106">Required.</span></span> <span data-ttu-id="76ec3-107">Całkowita wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="76ec3-107">Integral numeric value.</span></span> <span data-ttu-id="76ec3-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="76ec3-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="76ec3-109">Typ danych jest taki sam jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="76ec3-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="76ec3-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="76ec3-110">Required.</span></span> <span data-ttu-id="76ec3-111">Całkowite wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="76ec3-111">Integral numeric expression.</span></span> <span data-ttu-id="76ec3-112">Wzorzec bitowy, który ma zostać przesunięty.</span><span class="sxs-lookup"><span data-stu-id="76ec3-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="76ec3-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="76ec3-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="76ec3-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="76ec3-114">Required.</span></span> <span data-ttu-id="76ec3-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="76ec3-115">Numeric expression.</span></span> <span data-ttu-id="76ec3-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="76ec3-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="76ec3-117">Typ danych musi mieć wartość `Integer` lub być rozszerzony do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="76ec3-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ec3-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76ec3-118">Remarks</span></span>  
 <span data-ttu-id="76ec3-119">Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="76ec3-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="76ec3-120">W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="76ec3-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="76ec3-121">Aby zapobiec przesunięciu przez więcej bitów niż w wyniku, Visual Basic masek `amount` z maską rozmiaru odpowiadającą typowi danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="76ec3-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="76ec3-122">Wartość binarna i z tych wartości są używane na potrzeby przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="76ec3-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="76ec3-123">Maski rozmiaru są następujące:</span><span class="sxs-lookup"><span data-stu-id="76ec3-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="76ec3-124">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="76ec3-124">Data type of `pattern`</span></span>|<span data-ttu-id="76ec3-125">Maska rozmiaru (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="76ec3-125">Size mask (decimal)</span></span>|<span data-ttu-id="76ec3-126">Maska rozmiaru (szesnastkowo)</span><span class="sxs-lookup"><span data-stu-id="76ec3-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="76ec3-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="76ec3-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="76ec3-128">7</span><span class="sxs-lookup"><span data-stu-id="76ec3-128">7</span></span>|<span data-ttu-id="76ec3-129">& H00000007</span><span class="sxs-lookup"><span data-stu-id="76ec3-129">&H00000007</span></span>|  
|<span data-ttu-id="76ec3-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="76ec3-130">`Short`, `UShort`</span></span>|<span data-ttu-id="76ec3-131">15000</span><span class="sxs-lookup"><span data-stu-id="76ec3-131">15</span></span>|<span data-ttu-id="76ec3-132">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="76ec3-132">&H0000000F</span></span>|  
|<span data-ttu-id="76ec3-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="76ec3-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="76ec3-134">niż</span><span class="sxs-lookup"><span data-stu-id="76ec3-134">31</span></span>|<span data-ttu-id="76ec3-135">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="76ec3-135">&H0000001F</span></span>|  
|<span data-ttu-id="76ec3-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="76ec3-136">`Long`, `ULong`</span></span>|<span data-ttu-id="76ec3-137">63</span><span class="sxs-lookup"><span data-stu-id="76ec3-137">63</span></span>|<span data-ttu-id="76ec3-138">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="76ec3-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="76ec3-139">Jeśli `amount` wynosi zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="76ec3-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="76ec3-140">Jeśli wartość `amount` jest ujemna, jest ona traktowana jako nieoznaczona i zamaskowane przy użyciu odpowiedniej maski rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="76ec3-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="76ec3-141">Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="76ec3-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76ec3-142">Operator `<<` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="76ec3-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="76ec3-143">Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="76ec3-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="76ec3-144">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="76ec3-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ec3-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="76ec3-145">Example</span></span>  
 <span data-ttu-id="76ec3-146">Poniższy przykład używa operatora `<<`, aby przeprowadzić arytmetyczne przesunięcie w lewo na wartościach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="76ec3-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="76ec3-147">Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="76ec3-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="76ec3-148">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="76ec3-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="76ec3-149">`result1` to 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="76ec3-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="76ec3-150">`result2` to 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="76ec3-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="76ec3-151">`result3` to-32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="76ec3-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="76ec3-152">`result4` to 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="76ec3-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="76ec3-153">`result5` to 0 (przesunięte 15 miejsc w lewo).</span><span class="sxs-lookup"><span data-stu-id="76ec3-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="76ec3-154">Kwota przesunięcia dla `result4` jest obliczana jako 17 i 15, która jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="76ec3-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ec3-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76ec3-155">See also</span></span>

- [<span data-ttu-id="76ec3-156">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="76ec3-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="76ec3-157">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="76ec3-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="76ec3-158"><<=, operator</span><span class="sxs-lookup"><span data-stu-id="76ec3-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="76ec3-159">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76ec3-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="76ec3-160">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="76ec3-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="76ec3-161">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="76ec3-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
