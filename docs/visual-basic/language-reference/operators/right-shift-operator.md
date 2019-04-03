---
title: '>> — Operator (Visual Basic)'
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
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816970"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9bbbf-102">>> — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bbbf-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="9bbbf-103">Wykonuje arytmetyczne przesunięcie w prawo przy użyciu wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bbbf-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="9bbbf-105">Części</span><span class="sxs-lookup"><span data-stu-id="9bbbf-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9bbbf-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-106">Required.</span></span> <span data-ttu-id="9bbbf-107">Całkowitą wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-107">Integral numeric value.</span></span> <span data-ttu-id="9bbbf-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="9bbbf-109">Typ danych jest taka sama jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="9bbbf-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-110">Required.</span></span> <span data-ttu-id="9bbbf-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-111">Integral numeric expression.</span></span> <span data-ttu-id="9bbbf-112">Wzorzec bitowy jest przesuwany.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="9bbbf-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="9bbbf-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-114">Required.</span></span> <span data-ttu-id="9bbbf-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-115">Numeric expression.</span></span> <span data-ttu-id="9bbbf-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="9bbbf-117">Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bbbf-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bbbf-118">Remarks</span></span>  
 <span data-ttu-id="9bbbf-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="9bbbf-120">W arytmetyczne przesunięcie w prawo bity przesunięte poza Pozycja bitu po prawej stronie są odrzucane i bitu skrajnie po lewej stronie (znak) jest propagowana do pozycji bitów zwolnione w wyniku po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="9bbbf-121">Oznacza to, że jeśli `pattern` ma wartość ujemną, opuszczone pozycje są ustawione na jedną; w przeciwnym razie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="9bbbf-122">Należy pamiętać, że typy danych `Byte`, `UShort`, `UInteger`, i `ULong` są bez znaku, więc nie ma żadnych bitu znaku do propagowania.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="9bbbf-123">Jeśli `pattern` jest dowolny bez znaku typu, opuszczone pozycje są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="9bbbf-124">Aby zapobiec przesunięcie przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar odpowiadający typowi danych z `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="9bbbf-125">Liczba przesunięć służy binarne i tych wartości.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="9bbbf-126">Maski rozmiar są następujące:</span><span class="sxs-lookup"><span data-stu-id="9bbbf-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="9bbbf-127">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="9bbbf-127">Data type of `pattern`</span></span>|<span data-ttu-id="9bbbf-128">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="9bbbf-128">Size mask (decimal)</span></span>|<span data-ttu-id="9bbbf-129">Maska rozmiar (w formacie szesnastkowym)</span><span class="sxs-lookup"><span data-stu-id="9bbbf-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="9bbbf-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="9bbbf-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="9bbbf-131">7</span><span class="sxs-lookup"><span data-stu-id="9bbbf-131">7</span></span>|<span data-ttu-id="9bbbf-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="9bbbf-132">&H00000007</span></span>|  
|<span data-ttu-id="9bbbf-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="9bbbf-133">`Short`, `UShort`</span></span>|<span data-ttu-id="9bbbf-134">15</span><span class="sxs-lookup"><span data-stu-id="9bbbf-134">15</span></span>|<span data-ttu-id="9bbbf-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="9bbbf-135">&H0000000F</span></span>|  
|<span data-ttu-id="9bbbf-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="9bbbf-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="9bbbf-137">31</span><span class="sxs-lookup"><span data-stu-id="9bbbf-137">31</span></span>|<span data-ttu-id="9bbbf-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="9bbbf-138">&H0000001F</span></span>|  
|<span data-ttu-id="9bbbf-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="9bbbf-139">`Long`, `ULong`</span></span>|<span data-ttu-id="9bbbf-140">63</span><span class="sxs-lookup"><span data-stu-id="9bbbf-140">63</span></span>|<span data-ttu-id="9bbbf-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="9bbbf-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="9bbbf-142">Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="9bbbf-143">Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="9bbbf-144">Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9bbbf-145">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="9bbbf-145">Overloading</span></span>  
 <span data-ttu-id="9bbbf-146">`>>` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9bbbf-147">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9bbbf-148">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbbf-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bbbf-149">Example</span></span>  
 <span data-ttu-id="9bbbf-150">W poniższym przykładzie użyto `>>` operatora do wykonania arytmetycznego przesunięcia w prawo w wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="9bbbf-151">Wynik ma zawsze taki sam typ jak wyrażenie inne danych.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="9bbbf-152">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="9bbbf-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="9bbbf-153">`result1` jest 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="9bbbf-154">`result2` jest 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="9bbbf-155">`result3` to 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="9bbbf-156">`result4` to 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="9bbbf-157">`result5` to 0 (przesuniętych 15 miejsc z prawej strony).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="9bbbf-158">Liczba przesunięć dla `result4` jest obliczany jako 18 i 15, która jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="9bbbf-159">Poniższy przykład pokazuje arytmetycznego przesunięcia na wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="9bbbf-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="9bbbf-160">Wyniki poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="9bbbf-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="9bbbf-161">`negresult1` jest-512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="9bbbf-162">`negresult2` wynosi -1 (propagowane bitem znaku).</span><span class="sxs-lookup"><span data-stu-id="9bbbf-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbbf-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bbbf-163">See also</span></span>

- [<span data-ttu-id="9bbbf-164">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="9bbbf-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="9bbbf-165">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="9bbbf-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="9bbbf-166">>>=, operator</span><span class="sxs-lookup"><span data-stu-id="9bbbf-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="9bbbf-167">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bbbf-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9bbbf-168">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="9bbbf-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9bbbf-169">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bbbf-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
