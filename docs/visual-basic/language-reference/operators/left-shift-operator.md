---
title: << — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 329cdf1aea9ca97db000bb5ced8d9e8d6b7a4f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970561"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="30dde-102">\<\< — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30dde-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="30dde-103">Dokonuje arytmetycznego przesunięcia w lewo wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="30dde-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30dde-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="30dde-105">Części</span><span class="sxs-lookup"><span data-stu-id="30dde-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="30dde-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="30dde-106">Required.</span></span> <span data-ttu-id="30dde-107">Całkowitą wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="30dde-107">Integral numeric value.</span></span> <span data-ttu-id="30dde-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="30dde-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="30dde-109">Typ danych jest taka sama jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="30dde-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="30dde-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="30dde-110">Required.</span></span> <span data-ttu-id="30dde-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="30dde-111">Integral numeric expression.</span></span> <span data-ttu-id="30dde-112">Wzorzec bitowy jest przesuwany.</span><span class="sxs-lookup"><span data-stu-id="30dde-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="30dde-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="30dde-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="30dde-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="30dde-114">Required.</span></span> <span data-ttu-id="30dde-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="30dde-115">Numeric expression.</span></span> <span data-ttu-id="30dde-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="30dde-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="30dde-117">Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="30dde-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30dde-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30dde-118">Remarks</span></span>  
 <span data-ttu-id="30dde-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="30dde-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="30dde-120">W arytmetyczne przesunięcie w lewo bity przesunięte poza zakresem typu danych wyniku są odrzucane i pozycje bitów zwolnione w wyniku po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="30dde-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="30dde-121">Aby zapobiec shift przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar, który odnosi się do typu danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="30dde-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="30dde-122">Liczba przesunięć służy binarne i tych wartości.</span><span class="sxs-lookup"><span data-stu-id="30dde-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="30dde-123">Maski rozmiar są następujące:</span><span class="sxs-lookup"><span data-stu-id="30dde-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="30dde-124">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="30dde-124">Data type of `pattern`</span></span>|<span data-ttu-id="30dde-125">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="30dde-125">Size mask (decimal)</span></span>|<span data-ttu-id="30dde-126">Maska rozmiar (w formacie szesnastkowym)</span><span class="sxs-lookup"><span data-stu-id="30dde-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="30dde-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="30dde-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="30dde-128">7</span><span class="sxs-lookup"><span data-stu-id="30dde-128">7</span></span>|<span data-ttu-id="30dde-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="30dde-129">&H00000007</span></span>|  
|<span data-ttu-id="30dde-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="30dde-130">`Short`, `UShort`</span></span>|<span data-ttu-id="30dde-131">15</span><span class="sxs-lookup"><span data-stu-id="30dde-131">15</span></span>|<span data-ttu-id="30dde-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="30dde-132">&H0000000F</span></span>|  
|<span data-ttu-id="30dde-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="30dde-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="30dde-134">31</span><span class="sxs-lookup"><span data-stu-id="30dde-134">31</span></span>|<span data-ttu-id="30dde-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="30dde-135">&H0000001F</span></span>|  
|<span data-ttu-id="30dde-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="30dde-136">`Long`, `ULong`</span></span>|<span data-ttu-id="30dde-137">63</span><span class="sxs-lookup"><span data-stu-id="30dde-137">63</span></span>|<span data-ttu-id="30dde-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="30dde-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="30dde-139">Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="30dde-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="30dde-140">Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="30dde-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="30dde-141">Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="30dde-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30dde-142">`<<` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="30dde-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="30dde-143">Jeśli kod używa tego operatora dla klasy lub struktury, pamiętaj, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="30dde-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="30dde-144">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="30dde-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30dde-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="30dde-145">Example</span></span>  
 <span data-ttu-id="30dde-146">W poniższym przykładzie użyto `<<` operator, aby wykonać arytmetyki lewo przesunięcia na wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="30dde-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="30dde-147">Wynik ma zawsze taki sam typ jak wyrażenie inne danych.</span><span class="sxs-lookup"><span data-stu-id="30dde-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="30dde-148">Wyniki z poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="30dde-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="30dde-149">`result1` jest 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="30dde-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="30dde-150">`result2` to 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="30dde-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="30dde-151">`result3` to od -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="30dde-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="30dde-152">`result4` jest 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="30dde-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="30dde-153">`result5` to 0 (przesuniętych 15 miejsca po lewej stronie).</span><span class="sxs-lookup"><span data-stu-id="30dde-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="30dde-154">Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="30dde-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dde-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30dde-155">See also</span></span>
- [<span data-ttu-id="30dde-156">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="30dde-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="30dde-157">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="30dde-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="30dde-158"><<=, operator</span><span class="sxs-lookup"><span data-stu-id="30dde-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="30dde-159">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30dde-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="30dde-160">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="30dde-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="30dde-161">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30dde-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
