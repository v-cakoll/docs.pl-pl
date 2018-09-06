---
title: ULong — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214243f6a8a87f4e4cc15f31be23275fff00d07d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797978"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="ef5eb-102">Ulong — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef5eb-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="ef5eb-103">Przechowuje 64-bitowych (8-bajtową) liczb całkowitych bez znaku z zakresu od 0 do 18,446,744,073,709,551,615 (10 razy większa od 1.84 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="ef5eb-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef5eb-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef5eb-104">Remarks</span></span>

<span data-ttu-id="ef5eb-105">Użyj `ULong` typ danych, aby zawierać dane binarne, które są zbyt duże, aby `UInteger`, lub największa możliwa niepodpisanych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="ef5eb-106">Wartość domyślna `ULong` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ef5eb-107">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="ef5eb-107">Literal assignments</span></span>

<span data-ttu-id="ef5eb-108">Można zadeklarować i zainicjować `ULong` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ef5eb-109">Jeśli literał liczby całkowitej jest poza zakresem `ULong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ef5eb-110">W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `ULong` wartości.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="ef5eb-111">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ef5eb-112">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ef5eb-113">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="ef5eb-114">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ef5eb-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ef5eb-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ef5eb-116">Literały numeryczne mogą również obejmować `UL` lub `ul` [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `ULong` typu danych, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="ef5eb-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="ef5eb-117">Programming tips</span></span>
  
-   <span data-ttu-id="ef5eb-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-118">**Negative Numbers.**</span></span> <span data-ttu-id="ef5eb-119">Ponieważ `ULong` jest typ bez znaku, go nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="ef5eb-120">Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `ULong`, Visual Basic konwertuje wyrażenie które ma `Decimal` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="ef5eb-121">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-121">**CLS Compliance.**</span></span> <span data-ttu-id="ef5eb-122">`ULong` Typem danych nie jest częścią [specyfikacja Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-122">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="ef5eb-123">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-123">**Interop Considerations.**</span></span> <span data-ttu-id="ef5eb-124">Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, należy pamiętać, takich jak wpisywany `ulong` mogą mieć różną szerokość danych (32-bitowy) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="ef5eb-125">Jeśli przekazujesz 32-bitowy argument do takiego składnika, Zadeklaruj go jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="ef5eb-126">Ponadto usługi Automation nie obsługuje 64-bitowych liczb całkowitych na Windows 95, Windows 98, Windows ME lub Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="ef5eb-127">Nie można przekazać w języku Visual Basic `ULong` argument do składnika usługi Automation na tych platformach.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="ef5eb-128">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-128">**Widening.**</span></span> <span data-ttu-id="ef5eb-129">`ULong` — Typ danych rozszerza się na `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ef5eb-130">Oznacza to, że możesz przekonwertować `ULong` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="ef5eb-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-131">**Type Characters.**</span></span> <span data-ttu-id="ef5eb-132">Dołącza znaki literalne `UL` do literału wymusza `ULong` typu danych.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="ef5eb-133">`ULong` nie ma identyfikatora typ znaku.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-133">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="ef5eb-134">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="ef5eb-134">**Framework Type.**</span></span> <span data-ttu-id="ef5eb-135">Odpowiedni typ w .NET Framework jest <xref:System.UInt64?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="ef5eb-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5eb-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef5eb-136">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="ef5eb-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ef5eb-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="ef5eb-138">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="ef5eb-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ef5eb-139">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ef5eb-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="ef5eb-140">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="ef5eb-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="ef5eb-141">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="ef5eb-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
