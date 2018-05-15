---
title: '&lt;&lt; — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="68a4c-102">&lt;&lt; — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68a4c-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="68a4c-103">Wykonuje arytmetyczne przesunięcie w lewo na ciągu bitowym.</span><span class="sxs-lookup"><span data-stu-id="68a4c-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a4c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68a4c-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="68a4c-105">Części</span><span class="sxs-lookup"><span data-stu-id="68a4c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="68a4c-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="68a4c-106">Required.</span></span> <span data-ttu-id="68a4c-107">Całkowite wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="68a4c-107">Integral numeric value.</span></span> <span data-ttu-id="68a4c-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="68a4c-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="68a4c-109">Typ danych jest taki sam, jak te `pattern`.</span><span class="sxs-lookup"><span data-stu-id="68a4c-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="68a4c-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="68a4c-110">Required.</span></span> <span data-ttu-id="68a4c-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="68a4c-111">Integral numeric expression.</span></span> <span data-ttu-id="68a4c-112">Wzorca bitowego lekkie.</span><span class="sxs-lookup"><span data-stu-id="68a4c-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="68a4c-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="68a4c-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="68a4c-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="68a4c-114">Required.</span></span> <span data-ttu-id="68a4c-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="68a4c-115">Numeric expression.</span></span> <span data-ttu-id="68a4c-116">Liczba bitów przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="68a4c-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="68a4c-117">Typ danych musi być `Integer` lub rozszerzyć do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="68a4c-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68a4c-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68a4c-118">Remarks</span></span>  
 <span data-ttu-id="68a4c-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="68a4c-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="68a4c-120">W arytmetyczne przesunięcie w lewo bitów przesunięty poza zakresem typu danych zostaną odrzucone i pozycji z bitowego vacated po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="68a4c-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="68a4c-121">Aby zapobiec shift przez bits więcej niż wynik może pomieścić, Visual Basic maski wartość `amount` za pomocą maski rozmiar, która odnosi się do typu danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="68a4c-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="68a4c-122">Binarne i tych wartości jest używany dla wielkość przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="68a4c-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="68a4c-123">Rozmiar maski są następujące:</span><span class="sxs-lookup"><span data-stu-id="68a4c-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="68a4c-124">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="68a4c-124">Data type of `pattern`</span></span>|<span data-ttu-id="68a4c-125">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="68a4c-125">Size mask (decimal)</span></span>|<span data-ttu-id="68a4c-126">Rozmiar maski (szesnastkowo)</span><span class="sxs-lookup"><span data-stu-id="68a4c-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="68a4c-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="68a4c-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="68a4c-128">7</span><span class="sxs-lookup"><span data-stu-id="68a4c-128">7</span></span>|<span data-ttu-id="68a4c-129">&AMP; H00000007</span><span class="sxs-lookup"><span data-stu-id="68a4c-129">&H00000007</span></span>|  
|<span data-ttu-id="68a4c-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="68a4c-130">`Short`, `UShort`</span></span>|<span data-ttu-id="68a4c-131">15</span><span class="sxs-lookup"><span data-stu-id="68a4c-131">15</span></span>|<span data-ttu-id="68a4c-132">&AMP; H0000000F</span><span class="sxs-lookup"><span data-stu-id="68a4c-132">&H0000000F</span></span>|  
|<span data-ttu-id="68a4c-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="68a4c-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="68a4c-134">31</span><span class="sxs-lookup"><span data-stu-id="68a4c-134">31</span></span>|<span data-ttu-id="68a4c-135">&AMP; H0000001F</span><span class="sxs-lookup"><span data-stu-id="68a4c-135">&H0000001F</span></span>|  
|<span data-ttu-id="68a4c-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="68a4c-136">`Long`, `ULong`</span></span>|<span data-ttu-id="68a4c-137">63</span><span class="sxs-lookup"><span data-stu-id="68a4c-137">63</span></span>|<span data-ttu-id="68a4c-138">&AMP; H0000003F</span><span class="sxs-lookup"><span data-stu-id="68a4c-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="68a4c-139">Jeśli `amount` jest zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="68a4c-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="68a4c-140">Jeśli `amount` jest ujemna, jest traktowana jako wartość bez znaku i maskowane maska odpowiedni rozmiar.</span><span class="sxs-lookup"><span data-stu-id="68a4c-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="68a4c-141">Arytmetycznego przesunięcia nigdy nie generowanie wyjątków przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="68a4c-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68a4c-142">`<<` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="68a4c-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="68a4c-143">Jeśli kod używa tego operatora dla klasy lub struktury, należy się zapoznać z jego zachowanie ponownie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="68a4c-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="68a4c-144">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="68a4c-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68a4c-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="68a4c-145">Example</span></span>  
 <span data-ttu-id="68a4c-146">W poniższym przykładzie użyto `<<` operatora, aby wykonać arytmetyki przesunięcia w lewo na wartościach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="68a4c-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="68a4c-147">Wynik ma zawsze taki sam typ jak inne wyrażenia danych.</span><span class="sxs-lookup"><span data-stu-id="68a4c-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="68a4c-148">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="68a4c-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="68a4c-149">`result1` jest 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="68a4c-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="68a4c-150">`result2` jest 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="68a4c-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="68a4c-151">`result3` jest -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="68a4c-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="68a4c-152">`result4` jest 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="68a4c-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="68a4c-153">`result5` to 0 (przesuniętych 15 miejsca po lewej stronie).</span><span class="sxs-lookup"><span data-stu-id="68a4c-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="68a4c-154">Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="68a4c-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a4c-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68a4c-155">See Also</span></span>  
 [<span data-ttu-id="68a4c-156">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="68a4c-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="68a4c-157">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="68a4c-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="68a4c-158"><<=, operator</span><span class="sxs-lookup"><span data-stu-id="68a4c-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="68a4c-159">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68a4c-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="68a4c-160">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="68a4c-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="68a4c-161">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68a4c-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
