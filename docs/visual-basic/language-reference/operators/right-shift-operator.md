---
title: '&gt;&gt; — Operator (Visual Basic)'
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
ms.openlocfilehash: 9bb8e82b3f5451417fe1867d08b7601ee1acb036
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605410"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="b30de-102">&gt;&gt; — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b30de-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="b30de-103">Wykonuje arytmetyczne przesunięcie w prawo na ciągu bitowym.</span><span class="sxs-lookup"><span data-stu-id="b30de-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b30de-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b30de-105">Części</span><span class="sxs-lookup"><span data-stu-id="b30de-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b30de-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b30de-106">Required.</span></span> <span data-ttu-id="b30de-107">Całkowite wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="b30de-107">Integral numeric value.</span></span> <span data-ttu-id="b30de-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="b30de-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="b30de-109">Typ danych jest taki sam, jak te `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b30de-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="b30de-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b30de-110">Required.</span></span> <span data-ttu-id="b30de-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="b30de-111">Integral numeric expression.</span></span> <span data-ttu-id="b30de-112">Wzorca bitowego lekkie.</span><span class="sxs-lookup"><span data-stu-id="b30de-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="b30de-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b30de-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b30de-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b30de-114">Required.</span></span> <span data-ttu-id="b30de-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b30de-115">Numeric expression.</span></span> <span data-ttu-id="b30de-116">Liczba bitów przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="b30de-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="b30de-117">Typ danych musi być `Integer` lub rozszerzyć do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b30de-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b30de-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b30de-118">Remarks</span></span>  
 <span data-ttu-id="b30de-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="b30de-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b30de-120">W arytmetyczne przesunięcie w prawo bitów przesunięty poza Pozycja bitu po prawej stronie zostaną odrzucone i lewej strony (znaku) jest propagowana do pozycji z bitowego vacated po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="b30de-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="b30de-121">Oznacza to, że jeśli `pattern` ma wartość ujemną vacated pozycje są ustawione na jedną; w przeciwnym razie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="b30de-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="b30de-122">Należy pamiętać, że typy danych `Byte`, `UShort`, `UInteger`, i `ULong` nie mają znaku, więc nie ma żadnych bitem propagacji.</span><span class="sxs-lookup"><span data-stu-id="b30de-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="b30de-123">Jeśli `pattern` jest niepodpisane dowolnego typu, vacated pozycji zawsze są ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="b30de-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="b30de-124">Aby uniemożliwić ich przesuwanie przez bits więcej niż wynik może pomieścić, Visual Basic maski wartość `amount` za pomocą maski rozmiar odpowiadający typ danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b30de-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="b30de-125">Binarne i tych wartości jest używany dla wielkość przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b30de-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="b30de-126">Rozmiar maski są następujące:</span><span class="sxs-lookup"><span data-stu-id="b30de-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="b30de-127">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="b30de-127">Data type of `pattern`</span></span>|<span data-ttu-id="b30de-128">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="b30de-128">Size mask (decimal)</span></span>|<span data-ttu-id="b30de-129">Rozmiar maski (szesnastkowo)</span><span class="sxs-lookup"><span data-stu-id="b30de-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="b30de-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="b30de-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="b30de-131">7</span><span class="sxs-lookup"><span data-stu-id="b30de-131">7</span></span>|<span data-ttu-id="b30de-132">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="b30de-132">&H00000007</span></span>|  
|<span data-ttu-id="b30de-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="b30de-133">`Short`, `UShort`</span></span>|<span data-ttu-id="b30de-134">15</span><span class="sxs-lookup"><span data-stu-id="b30de-134">15</span></span>|<span data-ttu-id="b30de-135">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="b30de-135">&H0000000F</span></span>|  
|<span data-ttu-id="b30de-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="b30de-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="b30de-137">31</span><span class="sxs-lookup"><span data-stu-id="b30de-137">31</span></span>|<span data-ttu-id="b30de-138">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="b30de-138">&H0000001F</span></span>|  
|<span data-ttu-id="b30de-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="b30de-139">`Long`, `ULong`</span></span>|<span data-ttu-id="b30de-140">63</span><span class="sxs-lookup"><span data-stu-id="b30de-140">63</span></span>|<span data-ttu-id="b30de-141">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="b30de-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="b30de-142">Jeśli `amount` jest zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="b30de-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="b30de-143">Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i maskowane maska odpowiedni rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b30de-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="b30de-144">Arytmetycznego przesunięcia nigdy nie generowanie wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="b30de-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b30de-145">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b30de-145">Overloading</span></span>  
 <span data-ttu-id="b30de-146">`>>` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b30de-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b30de-147">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="b30de-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b30de-148">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b30de-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b30de-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="b30de-149">Example</span></span>  
 <span data-ttu-id="b30de-150">W poniższym przykładzie użyto `>>` operatora, aby wykonać arytmetycznego przesunięcia w prawo w wartości całkowite.</span><span class="sxs-lookup"><span data-stu-id="b30de-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="b30de-151">Wynik ma zawsze taki sam typ jak inne wyrażenia danych.</span><span class="sxs-lookup"><span data-stu-id="b30de-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="b30de-152">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b30de-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="b30de-153">`result1` jest 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b30de-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="b30de-154">`result2` jest 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="b30de-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="b30de-155">`result3` to 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="b30de-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="b30de-156">`result4` jest 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="b30de-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="b30de-157">`result5` to 0 (przesuniętych 15 miejsca z prawej strony).</span><span class="sxs-lookup"><span data-stu-id="b30de-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="b30de-158">Liczba przesunięć dla `result4` jest obliczany jako 18 15 i, która jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="b30de-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="b30de-159">W poniższym przykładzie przedstawiono arytmetycznego przesunięcia na wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="b30de-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="b30de-160">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b30de-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="b30de-161">`negresult1` jest-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="b30de-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="b30de-162">`negresult2` wynosi -1 (propagowane bitem).</span><span class="sxs-lookup"><span data-stu-id="b30de-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b30de-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b30de-163">See Also</span></span>  
 [<span data-ttu-id="b30de-164">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="b30de-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="b30de-165">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="b30de-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="b30de-166">>>=, operator</span><span class="sxs-lookup"><span data-stu-id="b30de-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [<span data-ttu-id="b30de-167">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b30de-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="b30de-168">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b30de-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b30de-169">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b30de-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
