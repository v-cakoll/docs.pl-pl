---
title: "UShort — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 958c7c74822d3b5cb311d22977b1b1f8bda04cd7
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="322f1-102">Ushort — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="322f1-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="322f1-103">Blokad 16-bitowych (2-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="322f1-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="322f1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="322f1-104">Remarks</span></span>

 <span data-ttu-id="322f1-105">Użyj `UShort` — typ danych zawierający dane binarne zbyt duży dla `Byte`.</span><span class="sxs-lookup"><span data-stu-id="322f1-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="322f1-106">Wartość domyślna `UShort` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="322f1-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="322f1-107">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="322f1-107">Literal assignments</span></span>

<span data-ttu-id="322f1-108">Można zadeklarować i zainicjuj `UShort` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="322f1-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="322f1-109">Jeśli liczba całkowita literału jest poza zakresem `UShort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="322f1-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="322f1-110">W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `UShort` wartości.</span><span class="sxs-lookup"><span data-stu-id="322f1-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="322f1-111">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="322f1-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="322f1-112">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="322f1-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="322f1-113">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="322f1-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="322f1-114">Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="322f1-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="322f1-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="322f1-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="322f1-116">Literały numeryczne mogą również obejmować `US` lub `us` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `UShort` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="322f1-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="322f1-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="322f1-117">Programming tips</span></span>
  
-   <span data-ttu-id="322f1-118">**Wartości ujemne.**</span><span class="sxs-lookup"><span data-stu-id="322f1-118">**Negative Numbers.**</span></span> <span data-ttu-id="322f1-119">Ponieważ `UShort` jest typu unsigned, nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="322f1-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="322f1-120">Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `UShort`, Visual Basic konwertuje wyrażenie `Integer` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="322f1-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="322f1-121">**Zgodności ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="322f1-121">**CLS Compliance.**</span></span> <span data-ttu-id="322f1-122">`UShort` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="322f1-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="322f1-123">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="322f1-123">**Widening.**</span></span> <span data-ttu-id="322f1-124">`UShort` Rozszerzenie typu danych do `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="322f1-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="322f1-125">Oznacza to, że można przekonwertować `UShort` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="322f1-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="322f1-126">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="322f1-126">**Type Characters.**</span></span> <span data-ttu-id="322f1-127">Znaki literalne dołączanie `US` do literału wymusza `UShort` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="322f1-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="322f1-128">`UShort`nie ma identyfikatora typu znaku.</span><span class="sxs-lookup"><span data-stu-id="322f1-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="322f1-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="322f1-129">**Framework Type.**</span></span> <span data-ttu-id="322f1-130">Danego typu w programie .NET Framework jest <xref:System.UInt16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="322f1-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322f1-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="322f1-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="322f1-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="322f1-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="322f1-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="322f1-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="322f1-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="322f1-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="322f1-135">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="322f1-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="322f1-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="322f1-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
