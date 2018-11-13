---
title: UShort — Typ danych (Visual Basic)
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
ms.openlocfilehash: a3d60747400d570a3e5a930377e9be9c0aca4f35
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982714"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="5b878-102">Ushort — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b878-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="5b878-103">Przechowuje 16-bitowych (2-bajtowych) liczb całkowitych bez znaku z zakresu od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="5b878-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b878-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b878-104">Remarks</span></span>

 <span data-ttu-id="5b878-105">Użyj `UShort` typ danych, aby zawierać dane binarne, które są zbyt duże, aby `Byte`.</span><span class="sxs-lookup"><span data-stu-id="5b878-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="5b878-106">Wartość domyślna `UShort` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="5b878-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="5b878-107">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="5b878-107">Literal assignments</span></span>

<span data-ttu-id="5b878-108">Można zadeklarować i zainicjować `UShort` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="5b878-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="5b878-109">Jeśli literał liczby całkowitej jest poza zakresem `UShort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5b878-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="5b878-110">W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `UShort` wartości.</span><span class="sxs-lookup"><span data-stu-id="5b878-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="5b878-111">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="5b878-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="5b878-112">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="5b878-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="5b878-113">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="5b878-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="5b878-114">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="5b878-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="5b878-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5b878-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="5b878-116">Literały numeryczne mogą również obejmować `US` lub `us` [wpisz znak](../../programming-guide/language-features/data-types/type-characters.md) do oznaczania `UShort` typu danych, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="5b878-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="5b878-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="5b878-117">Programming tips</span></span>
  
-   <span data-ttu-id="5b878-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="5b878-118">**Negative Numbers.**</span></span> <span data-ttu-id="5b878-119">Ponieważ `UShort` jest typ bez znaku, go nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="5b878-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="5b878-120">Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `UShort`, Visual Basic konwertuje wyrażenie które ma `Integer` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="5b878-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="5b878-121">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="5b878-121">**CLS Compliance.**</span></span> <span data-ttu-id="5b878-122">`UShort` Typem danych nie jest częścią [specyfikacja Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="5b878-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="5b878-123">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="5b878-123">**Widening.**</span></span> <span data-ttu-id="5b878-124">`UShort` — Typ danych rozszerza się na `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="5b878-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="5b878-125">Oznacza to, że możesz przekonwertować `UShort` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="5b878-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="5b878-126">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="5b878-126">**Type Characters.**</span></span> <span data-ttu-id="5b878-127">Dołącza znaki literalne `US` do literału wymusza `UShort` typu danych.</span><span class="sxs-lookup"><span data-stu-id="5b878-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="5b878-128">`UShort` nie ma identyfikatora typ znaku.</span><span class="sxs-lookup"><span data-stu-id="5b878-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="5b878-129">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="5b878-129">**Framework Type.**</span></span> <span data-ttu-id="5b878-130">Odpowiedni typ w .NET Framework jest <xref:System.UInt16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="5b878-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b878-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b878-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="5b878-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5b878-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="5b878-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5b878-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="5b878-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="5b878-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="5b878-135">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="5b878-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="5b878-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="5b878-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
