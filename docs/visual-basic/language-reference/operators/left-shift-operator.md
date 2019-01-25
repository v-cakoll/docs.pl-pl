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
ms.openlocfilehash: d39a134390591e3c72887a38e8aacb4631c71d87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539041"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="0bb59-102">&lt;&lt; — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bb59-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="0bb59-103">Dokonuje arytmetycznego przesunięcia w lewo wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="0bb59-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bb59-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="0bb59-105">Części</span><span class="sxs-lookup"><span data-stu-id="0bb59-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0bb59-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0bb59-106">Required.</span></span> <span data-ttu-id="0bb59-107">Całkowitą wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="0bb59-107">Integral numeric value.</span></span> <span data-ttu-id="0bb59-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="0bb59-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="0bb59-109">Typ danych jest taka sama jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="0bb59-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="0bb59-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0bb59-110">Required.</span></span> <span data-ttu-id="0bb59-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="0bb59-111">Integral numeric expression.</span></span> <span data-ttu-id="0bb59-112">Wzorzec bitowy jest przesuwany.</span><span class="sxs-lookup"><span data-stu-id="0bb59-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="0bb59-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="0bb59-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="0bb59-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0bb59-114">Required.</span></span> <span data-ttu-id="0bb59-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="0bb59-115">Numeric expression.</span></span> <span data-ttu-id="0bb59-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="0bb59-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="0bb59-117">Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0bb59-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bb59-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bb59-118">Remarks</span></span>  
 <span data-ttu-id="0bb59-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="0bb59-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="0bb59-120">W arytmetyczne przesunięcie w lewo bity przesunięte poza zakresem typu danych wyniku są odrzucane i pozycje bitów zwolnione w wyniku po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="0bb59-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="0bb59-121">Aby zapobiec shift przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar, który odnosi się do typu danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="0bb59-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="0bb59-122">Liczba przesunięć służy binarne i tych wartości.</span><span class="sxs-lookup"><span data-stu-id="0bb59-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="0bb59-123">Maski rozmiar są następujące:</span><span class="sxs-lookup"><span data-stu-id="0bb59-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="0bb59-124">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="0bb59-124">Data type of `pattern`</span></span>|<span data-ttu-id="0bb59-125">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="0bb59-125">Size mask (decimal)</span></span>|<span data-ttu-id="0bb59-126">Maska rozmiar (w formacie szesnastkowym)</span><span class="sxs-lookup"><span data-stu-id="0bb59-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="0bb59-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="0bb59-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="0bb59-128">7</span><span class="sxs-lookup"><span data-stu-id="0bb59-128">7</span></span>|<span data-ttu-id="0bb59-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="0bb59-129">&H00000007</span></span>|  
|<span data-ttu-id="0bb59-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="0bb59-130">`Short`, `UShort`</span></span>|<span data-ttu-id="0bb59-131">15</span><span class="sxs-lookup"><span data-stu-id="0bb59-131">15</span></span>|<span data-ttu-id="0bb59-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="0bb59-132">&H0000000F</span></span>|  
|<span data-ttu-id="0bb59-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="0bb59-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="0bb59-134">31</span><span class="sxs-lookup"><span data-stu-id="0bb59-134">31</span></span>|<span data-ttu-id="0bb59-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="0bb59-135">&H0000001F</span></span>|  
|<span data-ttu-id="0bb59-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="0bb59-136">`Long`, `ULong`</span></span>|<span data-ttu-id="0bb59-137">63</span><span class="sxs-lookup"><span data-stu-id="0bb59-137">63</span></span>|<span data-ttu-id="0bb59-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="0bb59-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="0bb59-139">Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="0bb59-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="0bb59-140">Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="0bb59-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="0bb59-141">Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="0bb59-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bb59-142">`<<` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="0bb59-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0bb59-143">Jeśli kod używa tego operatora dla klasy lub struktury, pamiętaj, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="0bb59-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="0bb59-144">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0bb59-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb59-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bb59-145">Example</span></span>  
 <span data-ttu-id="0bb59-146">W poniższym przykładzie użyto `<<` operator, aby wykonać arytmetyki lewo przesunięcia na wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0bb59-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="0bb59-147">Wynik ma zawsze taki sam typ jak wyrażenie inne danych.</span><span class="sxs-lookup"><span data-stu-id="0bb59-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="0bb59-148">Wyniki z poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="0bb59-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="0bb59-149">`result1` jest 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="0bb59-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="0bb59-150">`result2` to 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0bb59-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="0bb59-151">`result3` to od -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="0bb59-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="0bb59-152">`result4` jest 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="0bb59-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="0bb59-153">`result5` to 0 (przesuniętych 15 miejsca po lewej stronie).</span><span class="sxs-lookup"><span data-stu-id="0bb59-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="0bb59-154">Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="0bb59-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb59-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bb59-155">See also</span></span>
- [<span data-ttu-id="0bb59-156">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="0bb59-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="0bb59-157">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="0bb59-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="0bb59-158"><<=, operator</span><span class="sxs-lookup"><span data-stu-id="0bb59-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="0bb59-159">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bb59-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0bb59-160">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="0bb59-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0bb59-161">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bb59-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
