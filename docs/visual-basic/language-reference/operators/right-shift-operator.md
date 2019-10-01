---
title: '>> Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 337d651e831dc2ab132056f6e9a1f2b5300bf7f8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701331"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="55caa-102">Operator > > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55caa-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="55caa-103">Wykonuje arytmetyczne przesunięcie w prawo na wzorcu bitowym.</span><span class="sxs-lookup"><span data-stu-id="55caa-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55caa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55caa-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="55caa-105">Części</span><span class="sxs-lookup"><span data-stu-id="55caa-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="55caa-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="55caa-106">Required.</span></span> <span data-ttu-id="55caa-107">Całkowita wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="55caa-107">Integral numeric value.</span></span> <span data-ttu-id="55caa-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="55caa-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="55caa-109">Typ danych jest taki sam jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="55caa-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="55caa-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="55caa-110">Required.</span></span> <span data-ttu-id="55caa-111">Całkowite wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="55caa-111">Integral numeric expression.</span></span> <span data-ttu-id="55caa-112">Wzorzec bitowy, który ma zostać przesunięty.</span><span class="sxs-lookup"><span data-stu-id="55caa-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="55caa-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="55caa-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="55caa-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="55caa-114">Required.</span></span> <span data-ttu-id="55caa-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="55caa-115">Numeric expression.</span></span> <span data-ttu-id="55caa-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="55caa-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="55caa-117">Typ danych musi mieć wartość `Integer` lub być rozszerzony do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="55caa-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55caa-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55caa-118">Remarks</span></span>  
 <span data-ttu-id="55caa-119">Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="55caa-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="55caa-120">W wyniku przesunięcia w prawo, bity przesunięte poza skrajną prawą pozycję bitową są odrzucane, a w lewej (znak) bit jest propagowany do pozycji bitowych opuszczone.</span><span class="sxs-lookup"><span data-stu-id="55caa-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="55caa-121">Oznacza to, że jeśli `pattern` ma wartość ujemną, pozycje opuszczone są ustawione na jeden. w przeciwnym razie jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="55caa-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="55caa-122">Należy zauważyć, że typy danych `Byte`, `UShort`, `UInteger` i `ULong` są podpisane, dlatego nie istnieje bit znaku do propagowania.</span><span class="sxs-lookup"><span data-stu-id="55caa-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="55caa-123">Jeśli `pattern` jest dowolnego typu bez znaku, pozycje opuszczone są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="55caa-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="55caa-124">Aby zapobiec przesunięciu przez więcej bitów, niż można obsłużyć, Visual Basic maskować wartość `amount` z maską rozmiaru odpowiadającą typowi danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="55caa-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="55caa-125">Wartość binarna i z tych wartości są używane na potrzeby przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="55caa-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="55caa-126">Maski rozmiaru są następujące:</span><span class="sxs-lookup"><span data-stu-id="55caa-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="55caa-127">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="55caa-127">Data type of `pattern`</span></span>|<span data-ttu-id="55caa-128">Maska rozmiaru (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="55caa-128">Size mask (decimal)</span></span>|<span data-ttu-id="55caa-129">Maska rozmiaru (szesnastkowo)</span><span class="sxs-lookup"><span data-stu-id="55caa-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="55caa-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="55caa-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="55caa-131">7</span><span class="sxs-lookup"><span data-stu-id="55caa-131">7</span></span>|<span data-ttu-id="55caa-132">& H00000007</span><span class="sxs-lookup"><span data-stu-id="55caa-132">&H00000007</span></span>|  
|<span data-ttu-id="55caa-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="55caa-133">`Short`, `UShort`</span></span>|<span data-ttu-id="55caa-134">15000</span><span class="sxs-lookup"><span data-stu-id="55caa-134">15</span></span>|<span data-ttu-id="55caa-135">& H0000000F</span><span class="sxs-lookup"><span data-stu-id="55caa-135">&H0000000F</span></span>|  
|<span data-ttu-id="55caa-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="55caa-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="55caa-137">niż</span><span class="sxs-lookup"><span data-stu-id="55caa-137">31</span></span>|<span data-ttu-id="55caa-138">& H0000001F</span><span class="sxs-lookup"><span data-stu-id="55caa-138">&H0000001F</span></span>|  
|<span data-ttu-id="55caa-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="55caa-139">`Long`, `ULong`</span></span>|<span data-ttu-id="55caa-140">63</span><span class="sxs-lookup"><span data-stu-id="55caa-140">63</span></span>|<span data-ttu-id="55caa-141">& H0000003F</span><span class="sxs-lookup"><span data-stu-id="55caa-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="55caa-142">Jeśli `amount` wynosi zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="55caa-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="55caa-143">Jeśli wartość `amount` jest ujemna, jest ona traktowana jako nieoznaczona i zamaskowane przy użyciu odpowiedniej maski rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="55caa-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="55caa-144">Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="55caa-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="55caa-145">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="55caa-145">Overloading</span></span>  
 <span data-ttu-id="55caa-146">Operator `>>` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="55caa-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="55caa-147">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="55caa-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="55caa-148">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="55caa-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55caa-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="55caa-149">Example</span></span>  
 <span data-ttu-id="55caa-150">Poniższy przykład używa operatora `>>`, aby przeprowadzić arytmetyczne przesunięcie w prawo na wartościach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="55caa-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="55caa-151">Wynik zawsze ma ten sam typ danych co w przypadku przesunięcia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="55caa-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="55caa-152">W powyższym przykładzie przedstawiono następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="55caa-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="55caa-153">`result1` to 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="55caa-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="55caa-154">`result2` to 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="55caa-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="55caa-155">`result3` to 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="55caa-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="55caa-156">`result4` to 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="55caa-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="55caa-157">`result5` to 0 (przesunięte 15 miejsc w prawo).</span><span class="sxs-lookup"><span data-stu-id="55caa-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="55caa-158">Wartość przesunięcia dla `result4` jest obliczana jako 18 i 15, która jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="55caa-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="55caa-159">W poniższym przykładzie pokazano arytmetyczne przesunięcia na wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="55caa-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="55caa-160">W powyższym przykładzie przedstawiono następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="55caa-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="55caa-161">`negresult1` to-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="55caa-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="55caa-162">`negresult2` to-1 (jest propagowany bit znaku).</span><span class="sxs-lookup"><span data-stu-id="55caa-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55caa-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55caa-163">See also</span></span>

- [<span data-ttu-id="55caa-164">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="55caa-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="55caa-165">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="55caa-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="55caa-166">>>=, operator</span><span class="sxs-lookup"><span data-stu-id="55caa-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="55caa-167">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55caa-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="55caa-168">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="55caa-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="55caa-169">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55caa-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
