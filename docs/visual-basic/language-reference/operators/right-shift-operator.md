---
title: '>> Operator'
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
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347822"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3b3fe-102">>> Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b3fe-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="3b3fe-103">Performs an arithmetic right shift on a bit pattern.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b3fe-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3b3fe-105">Części</span><span class="sxs-lookup"><span data-stu-id="3b3fe-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3b3fe-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-106">Required.</span></span> <span data-ttu-id="3b3fe-107">Integral numeric value.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-107">Integral numeric value.</span></span> <span data-ttu-id="3b3fe-108">The result of shifting the bit pattern.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="3b3fe-109">The data type is the same as that of `pattern`.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="3b3fe-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-110">Required.</span></span> <span data-ttu-id="3b3fe-111">Integral numeric expression.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-111">Integral numeric expression.</span></span> <span data-ttu-id="3b3fe-112">The bit pattern to be shifted.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="3b3fe-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3b3fe-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-114">Required.</span></span> <span data-ttu-id="3b3fe-115">Numeric expression.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-115">Numeric expression.</span></span> <span data-ttu-id="3b3fe-116">The number of bits to shift the bit pattern.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="3b3fe-117">The data type must be `Integer` or widen to `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b3fe-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b3fe-118">Remarks</span></span>  
 <span data-ttu-id="3b3fe-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3b3fe-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="3b3fe-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="3b3fe-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="3b3fe-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="3b3fe-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="3b3fe-125">The binary AND of these values is used for the shift amount.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="3b3fe-126">The size masks are as follows:</span><span class="sxs-lookup"><span data-stu-id="3b3fe-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="3b3fe-127">Data type of `pattern`</span><span class="sxs-lookup"><span data-stu-id="3b3fe-127">Data type of `pattern`</span></span>|<span data-ttu-id="3b3fe-128">Size mask (decimal)</span><span class="sxs-lookup"><span data-stu-id="3b3fe-128">Size mask (decimal)</span></span>|<span data-ttu-id="3b3fe-129">Size mask (hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="3b3fe-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="3b3fe-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="3b3fe-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="3b3fe-131">7</span><span class="sxs-lookup"><span data-stu-id="3b3fe-131">7</span></span>|<span data-ttu-id="3b3fe-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="3b3fe-132">&H00000007</span></span>|  
|<span data-ttu-id="3b3fe-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="3b3fe-133">`Short`, `UShort`</span></span>|<span data-ttu-id="3b3fe-134">15</span><span class="sxs-lookup"><span data-stu-id="3b3fe-134">15</span></span>|<span data-ttu-id="3b3fe-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="3b3fe-135">&H0000000F</span></span>|  
|<span data-ttu-id="3b3fe-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="3b3fe-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="3b3fe-137">31</span><span class="sxs-lookup"><span data-stu-id="3b3fe-137">31</span></span>|<span data-ttu-id="3b3fe-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="3b3fe-138">&H0000001F</span></span>|  
|<span data-ttu-id="3b3fe-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="3b3fe-139">`Long`, `ULong`</span></span>|<span data-ttu-id="3b3fe-140">63</span><span class="sxs-lookup"><span data-stu-id="3b3fe-140">63</span></span>|<span data-ttu-id="3b3fe-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="3b3fe-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="3b3fe-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="3b3fe-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="3b3fe-144">Arithmetic shifts never generate overflow exceptions.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3b3fe-145">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="3b3fe-145">Overloading</span></span>  
 <span data-ttu-id="3b3fe-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3b3fe-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3b3fe-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b3fe-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b3fe-149">Example</span></span>  
 <span data-ttu-id="3b3fe-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="3b3fe-151">The result always has the same data type as that of the expression being shifted.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="3b3fe-152">The results of the preceding example are as follows:</span><span class="sxs-lookup"><span data-stu-id="3b3fe-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="3b3fe-153">`result1` is 2560 (0000 1010 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="3b3fe-154">`result2` is 160 (0000 0000 1010 0000).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="3b3fe-155">`result3` is 2 (0000 0000 0000 0010).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="3b3fe-156">`result4` is 640 (0000 0010 1000 0000).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="3b3fe-157">`result5` is 0 (shifted 15 places to the right).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="3b3fe-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="3b3fe-159">The following example shows arithmetic shifts on a negative value.</span><span class="sxs-lookup"><span data-stu-id="3b3fe-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="3b3fe-160">The results of the preceding example are as follows:</span><span class="sxs-lookup"><span data-stu-id="3b3fe-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="3b3fe-161">`negresult1` is -512 (1111 1110 0000 0000).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="3b3fe-162">`negresult2` is -1 (the sign bit is propagated).</span><span class="sxs-lookup"><span data-stu-id="3b3fe-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3fe-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b3fe-163">See also</span></span>

- [<span data-ttu-id="3b3fe-164">Operatory Bit Shift</span><span class="sxs-lookup"><span data-stu-id="3b3fe-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="3b3fe-165">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="3b3fe-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="3b3fe-166">>>=, operator</span><span class="sxs-lookup"><span data-stu-id="3b3fe-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [<span data-ttu-id="3b3fe-167">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b3fe-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3b3fe-168">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="3b3fe-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3b3fe-169">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b3fe-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
