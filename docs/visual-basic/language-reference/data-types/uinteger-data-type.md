---
title: UInteger — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1c734578abd55270dd6feb9060d02691a6aaf8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591341"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="fe468-102">UInteger — Typ danych</span><span class="sxs-lookup"><span data-stu-id="fe468-102">UInteger data type</span></span>

<span data-ttu-id="fe468-103">Blokad 32-bitowe (4-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="fe468-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe468-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe468-104">Remarks</span></span>

 <span data-ttu-id="fe468-105">`UInteger` — Typ danych zapewnia największą wartość bez znaku w najbardziej efektywny szerokość danych.</span><span class="sxs-lookup"><span data-stu-id="fe468-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="fe468-106">Wartość domyślna `UInteger` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="fe468-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="fe468-107">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="fe468-107">Literal assignments</span></span>

<span data-ttu-id="fe468-108">Można zadeklarować i zainicjuj `UInteger` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="fe468-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="fe468-109">Jeśli liczba całkowita literału jest poza zakresem `UInteger` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fe468-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="fe468-110">W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `UInteger` wartości.</span><span class="sxs-lookup"><span data-stu-id="fe468-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="fe468-111">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="fe468-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fe468-112">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="fe468-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fe468-113">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="fe468-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="fe468-114">Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="fe468-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="fe468-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe468-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="fe468-116">Literały numeryczne mogą również obejmować `UI` lub `ui` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `UInteger` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe468-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="fe468-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="fe468-117">Programming tips</span></span>

 <span data-ttu-id="fe468-118">`UInteger` i `Integer` typy danych zapewnić optymalną wydajność na 32-bitowego procesora, ponieważ mniejszych typów całkowitych (`UShort`, `Short`, `Byte`, i `SByte`), nawet jeśli korzystają z mniej bits zająć więcej czasu Ładowanie, przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="fe468-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="fe468-119">**Wartości ujemne.**</span><span class="sxs-lookup"><span data-stu-id="fe468-119">**Negative Numbers.**</span></span> <span data-ttu-id="fe468-120">Ponieważ `UInteger` jest typu unsigned, nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="fe468-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="fe468-121">Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `UInteger`, Visual Basic konwertuje wyrażenie `Long` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="fe468-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="fe468-122">**Zgodności ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="fe468-122">**CLS Compliance.**</span></span> <span data-ttu-id="fe468-123">`UInteger` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="fe468-123">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="fe468-124">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="fe468-124">**Interop Considerations.**</span></span> <span data-ttu-id="fe468-125">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy, takich jak `uint` może mieć szerokość różnych danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="fe468-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="fe468-126">Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fe468-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="fe468-127">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="fe468-127">**Widening.**</span></span> <span data-ttu-id="fe468-128">`UInteger` Rozszerzenie typu danych do `Long`, `ULong`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="fe468-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="fe468-129">Oznacza to, że można przekonwertować `UInteger` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="fe468-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="fe468-130">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="fe468-130">**Type Characters.**</span></span> <span data-ttu-id="fe468-131">Znaki literalne dołączanie `UI` do literału wymusza `UInteger` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="fe468-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="fe468-132">`UInteger` nie ma identyfikatora typu znaku.</span><span class="sxs-lookup"><span data-stu-id="fe468-132">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="fe468-133">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="fe468-133">**Framework Type.**</span></span> <span data-ttu-id="fe468-134">Danego typu w programie .NET Framework jest <xref:System.UInt32?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="fe468-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe468-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe468-135">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="fe468-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fe468-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="fe468-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fe468-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fe468-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fe468-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="fe468-139">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="fe468-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="fe468-140">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="fe468-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
