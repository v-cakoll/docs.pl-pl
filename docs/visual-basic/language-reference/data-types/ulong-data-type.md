---
title: "ULong — Typ danych (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ulong
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc52bfd16541feed599d5445adad7aba04f8e9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="93a52-102">Ulong — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93a52-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="93a52-103">Przechowuje 64-bitowych (8-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 18,446,744,073,709,551,615 (10 razy większa od 1.84 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="93a52-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93a52-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93a52-104">Remarks</span></span>

<span data-ttu-id="93a52-105">Użyj `ULong` — typ danych zawierający dane binarne zbyt duży dla `UInteger`, lub największego możliwego podpisane liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="93a52-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="93a52-106">Wartość domyślna `ULong` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="93a52-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="93a52-107">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="93a52-107">Literal assignments</span></span>

<span data-ttu-id="93a52-108">Można zadeklarować i zainicjuj `ULong` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="93a52-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="93a52-109">Jeśli liczba całkowita literału jest poza zakresem `ULong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="93a52-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="93a52-110">W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `ULong` wartości.</span><span class="sxs-lookup"><span data-stu-id="93a52-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="93a52-111">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="93a52-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="93a52-112">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="93a52-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="93a52-113">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="93a52-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="93a52-114">Literały numeryczne mogą również obejmować `UL` lub `ul` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `ULong` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="93a52-114">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="93a52-115">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="93a52-115">Programming tips</span></span>
  
-   <span data-ttu-id="93a52-116">**Wartości ujemne.**</span><span class="sxs-lookup"><span data-stu-id="93a52-116">**Negative Numbers.**</span></span> <span data-ttu-id="93a52-117">Ponieważ `ULong` jest typu unsigned, nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="93a52-117">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="93a52-118">Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `ULong`, Visual Basic konwertuje wyrażenie `Decimal` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="93a52-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="93a52-119">**Zgodności ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="93a52-119">**CLS Compliance.**</span></span> <span data-ttu-id="93a52-120">`ULong` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="93a52-120">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="93a52-121">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="93a52-121">**Interop Considerations.**</span></span> <span data-ttu-id="93a52-122">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że typy, takich jak `ulong` może mieć szerokość różnych danych (32-bitowy) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="93a52-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="93a52-123">Jeśli argument 32-bitowej do tych składników, Zadeklaruj ją jako `UInteger` zamiast `ULong` w zarządzanym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93a52-123">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="93a52-124">Ponadto automatyzacji nie obsługuje 64-bitowych liczb całkowitych w systemie Windows 95, Windows 98, Windows ME lub Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="93a52-124">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="93a52-125">Nie można przekazać języka Visual Basic `ULong` argument składnika automatyzacji na tych platformach.</span><span class="sxs-lookup"><span data-stu-id="93a52-125">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="93a52-126">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="93a52-126">**Widening.**</span></span> <span data-ttu-id="93a52-127">`ULong` Rozszerzenie typu danych do `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="93a52-127">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="93a52-128">Oznacza to, że można przekonwertować `ULong` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="93a52-128">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="93a52-129">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="93a52-129">**Type Characters.**</span></span> <span data-ttu-id="93a52-130">Znaki literalne dołączanie `UL` do literału wymusza `ULong` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="93a52-130">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="93a52-131">`ULong`nie ma identyfikatora typu znaku.</span><span class="sxs-lookup"><span data-stu-id="93a52-131">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="93a52-132">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="93a52-132">**Framework Type.**</span></span> <span data-ttu-id="93a52-133">Danego typu w programie .NET Framework jest <xref:System.UInt64?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="93a52-133">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a52-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a52-134">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="93a52-135">Typy danych</span><span class="sxs-lookup"><span data-stu-id="93a52-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="93a52-136">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="93a52-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="93a52-137">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="93a52-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="93a52-138">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="93a52-138">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="93a52-139">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="93a52-139">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
