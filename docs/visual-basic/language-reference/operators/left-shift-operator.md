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
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768293"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e13b8-102">\<\< — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e13b8-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="e13b8-103">Dokonuje arytmetycznego przesunięcia w lewo wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="e13b8-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e13b8-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="e13b8-105">Części</span><span class="sxs-lookup"><span data-stu-id="e13b8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e13b8-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e13b8-106">Required.</span></span> <span data-ttu-id="e13b8-107">Całkowitą wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="e13b8-107">Integral numeric value.</span></span> <span data-ttu-id="e13b8-108">Wynik przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="e13b8-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="e13b8-109">Typ danych jest taka sama jak w przypadku `pattern`.</span><span class="sxs-lookup"><span data-stu-id="e13b8-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="e13b8-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e13b8-110">Required.</span></span> <span data-ttu-id="e13b8-111">Całkowite wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="e13b8-111">Integral numeric expression.</span></span> <span data-ttu-id="e13b8-112">Wzorzec bitowy jest przesuwany.</span><span class="sxs-lookup"><span data-stu-id="e13b8-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="e13b8-113">Typ danych musi być typem całkowitym (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).</span><span class="sxs-lookup"><span data-stu-id="e13b8-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="e13b8-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e13b8-114">Required.</span></span> <span data-ttu-id="e13b8-115">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e13b8-115">Numeric expression.</span></span> <span data-ttu-id="e13b8-116">Liczba bitów do przesunięcia wzorca bitowego.</span><span class="sxs-lookup"><span data-stu-id="e13b8-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="e13b8-117">Typ danych musi być `Integer` lub mogą zostać poszerzone do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e13b8-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e13b8-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e13b8-118">Remarks</span></span>  
 <span data-ttu-id="e13b8-119">Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="e13b8-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="e13b8-120">W arytmetyczne przesunięcie w lewo bity przesunięte poza zakresem typu danych wyniku są odrzucane i pozycje bitów zwolnione w wyniku po prawej stronie zostaną ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="e13b8-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="e13b8-121">Aby zapobiec shift przez kilka bitów, niż może pomieścić wynik, Visual Basic maskuje wartość `amount` za pomocą maski rozmiar, który odnosi się do typu danych `pattern`.</span><span class="sxs-lookup"><span data-stu-id="e13b8-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="e13b8-122">Liczba przesunięć służy binarne i tych wartości.</span><span class="sxs-lookup"><span data-stu-id="e13b8-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="e13b8-123">Maski rozmiar są następujące:</span><span class="sxs-lookup"><span data-stu-id="e13b8-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="e13b8-124">Typ danych `pattern`</span><span class="sxs-lookup"><span data-stu-id="e13b8-124">Data type of `pattern`</span></span>|<span data-ttu-id="e13b8-125">Rozmiar maski (dziesiętna)</span><span class="sxs-lookup"><span data-stu-id="e13b8-125">Size mask (decimal)</span></span>|<span data-ttu-id="e13b8-126">Maska rozmiar (w formacie szesnastkowym)</span><span class="sxs-lookup"><span data-stu-id="e13b8-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="e13b8-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="e13b8-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="e13b8-128">7</span><span class="sxs-lookup"><span data-stu-id="e13b8-128">7</span></span>|<span data-ttu-id="e13b8-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="e13b8-129">&H00000007</span></span>|  
|<span data-ttu-id="e13b8-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="e13b8-130">`Short`, `UShort`</span></span>|<span data-ttu-id="e13b8-131">15</span><span class="sxs-lookup"><span data-stu-id="e13b8-131">15</span></span>|<span data-ttu-id="e13b8-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="e13b8-132">&H0000000F</span></span>|  
|<span data-ttu-id="e13b8-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="e13b8-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="e13b8-134">31</span><span class="sxs-lookup"><span data-stu-id="e13b8-134">31</span></span>|<span data-ttu-id="e13b8-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="e13b8-135">&H0000001F</span></span>|  
|<span data-ttu-id="e13b8-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="e13b8-136">`Long`, `ULong`</span></span>|<span data-ttu-id="e13b8-137">63</span><span class="sxs-lookup"><span data-stu-id="e13b8-137">63</span></span>|<span data-ttu-id="e13b8-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="e13b8-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="e13b8-139">Jeśli `amount` jest równy zero, wartość `result` jest taka sama jak wartość `pattern`.</span><span class="sxs-lookup"><span data-stu-id="e13b8-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="e13b8-140">Jeśli `amount` jest ujemna, jest traktowana jako wartość nieoznaczona i maskowane symbolami maska odpowiedniego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="e13b8-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="e13b8-141">Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="e13b8-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e13b8-142">`<<` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e13b8-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e13b8-143">Jeśli kod używa tego operatora dla klasy lub struktury, pamiętaj, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="e13b8-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="e13b8-144">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e13b8-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e13b8-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="e13b8-145">Example</span></span>  
 <span data-ttu-id="e13b8-146">W poniższym przykładzie użyto `<<` operator, aby wykonać arytmetyki lewo przesunięcia na wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e13b8-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="e13b8-147">Wynik ma zawsze taki sam typ jak wyrażenie inne danych.</span><span class="sxs-lookup"><span data-stu-id="e13b8-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="e13b8-148">Wyniki z poprzedniego przykładu są następujące:</span><span class="sxs-lookup"><span data-stu-id="e13b8-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="e13b8-149">`result1` jest 192 (0000 0000 1100 0000).</span><span class="sxs-lookup"><span data-stu-id="e13b8-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="e13b8-150">`result2` to 3072 (0000 1100 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="e13b8-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="e13b8-151">`result3` to od -32768 (1000 0000 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="e13b8-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="e13b8-152">`result4` jest 384 (0000 0001 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="e13b8-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="e13b8-153">`result5` to 0 (przesuniętych 15 miejsca po lewej stronie).</span><span class="sxs-lookup"><span data-stu-id="e13b8-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="e13b8-154">Liczba przesunięć dla `result4` jest obliczany jako 17 i 15, która jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="e13b8-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13b8-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e13b8-155">See also</span></span>

- [<span data-ttu-id="e13b8-156">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="e13b8-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="e13b8-157">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="e13b8-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="e13b8-158"><<=, operator</span><span class="sxs-lookup"><span data-stu-id="e13b8-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [<span data-ttu-id="e13b8-159">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e13b8-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e13b8-160">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e13b8-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e13b8-161">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e13b8-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
