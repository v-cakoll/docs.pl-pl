---
title: UShort — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343853"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="812c4-102">UShort data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="812c4-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="812c4-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span><span class="sxs-lookup"><span data-stu-id="812c4-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="812c4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="812c4-104">Remarks</span></span>

 <span data-ttu-id="812c4-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span><span class="sxs-lookup"><span data-stu-id="812c4-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="812c4-106">The default value of `UShort` is 0.</span><span class="sxs-lookup"><span data-stu-id="812c4-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="812c4-107">Literal assignments</span><span class="sxs-lookup"><span data-stu-id="812c4-107">Literal assignments</span></span>

<span data-ttu-id="812c4-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span><span class="sxs-lookup"><span data-stu-id="812c4-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="812c4-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span><span class="sxs-lookup"><span data-stu-id="812c4-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="812c4-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span><span class="sxs-lookup"><span data-stu-id="812c4-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="812c4-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span><span class="sxs-lookup"><span data-stu-id="812c4-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="812c4-112">Decimal literals have no prefix.</span><span class="sxs-lookup"><span data-stu-id="812c4-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="812c4-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="812c4-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="812c4-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span><span class="sxs-lookup"><span data-stu-id="812c4-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="812c4-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="812c4-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="812c4-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span><span class="sxs-lookup"><span data-stu-id="812c4-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="812c4-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="812c4-117">Programming tips</span></span>
  
- <span data-ttu-id="812c4-118">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="812c4-118">**Negative Numbers.**</span></span> <span data-ttu-id="812c4-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span><span class="sxs-lookup"><span data-stu-id="812c4-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="812c4-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span><span class="sxs-lookup"><span data-stu-id="812c4-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="812c4-121">**CLS Compliance.**</span><span class="sxs-lookup"><span data-stu-id="812c4-121">**CLS Compliance.**</span></span> <span data-ttu-id="812c4-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span><span class="sxs-lookup"><span data-stu-id="812c4-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="812c4-123">**Widening.**</span><span class="sxs-lookup"><span data-stu-id="812c4-123">**Widening.**</span></span> <span data-ttu-id="812c4-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span><span class="sxs-lookup"><span data-stu-id="812c4-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="812c4-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span><span class="sxs-lookup"><span data-stu-id="812c4-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="812c4-126">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="812c4-126">**Type Characters.**</span></span> <span data-ttu-id="812c4-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span><span class="sxs-lookup"><span data-stu-id="812c4-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="812c4-128">`UShort` has no identifier type character.</span><span class="sxs-lookup"><span data-stu-id="812c4-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="812c4-129">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="812c4-129">**Framework Type.**</span></span> <span data-ttu-id="812c4-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span><span class="sxs-lookup"><span data-stu-id="812c4-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="812c4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="812c4-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="812c4-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="812c4-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="812c4-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="812c4-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="812c4-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="812c4-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="812c4-135">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="812c4-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="812c4-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="812c4-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
