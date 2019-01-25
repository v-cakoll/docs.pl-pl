---
title: Byte — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 8c9787d52667dc026d3fe62ac7f4b3de7e838a93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519791"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="e0c8d-102">Byte — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0c8d-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="e0c8d-103">Przechowuje 8-bitowa (1-bajtowe) liczb całkowitych bez znaku z zakresu wartości z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0c8d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0c8d-104">Remarks</span></span>

<span data-ttu-id="e0c8d-105">Użyj `Byte` typ danych, aby zawierać dane binarne.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="e0c8d-106">Wartość domyślna `Byte` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="e0c8d-107">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="e0c8d-107">Literal assignments</span></span>

<span data-ttu-id="e0c8d-108">Można zadeklarować i zainicjować `Byte` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="e0c8d-109">Jeśli literał typu całkowitego jest poza zakresem `Byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="e0c8d-110">W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `byte` wartości.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="e0c8d-111">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="e0c8d-112">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="e0c8d-113">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="e0c8d-114">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="e0c8d-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e0c8d-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="e0c8d-116">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="e0c8d-116">Programming tips</span></span>

-   <span data-ttu-id="e0c8d-117">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="e0c8d-117">**Negative Numbers.**</span></span> <span data-ttu-id="e0c8d-118">Ponieważ `Byte` jest typ bez znaku, go nie może reprezentować wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="e0c8d-119">Jeśli używasz jednoargumentowego znaku minusa (`-`) operatora na wyrażenie obliczane do typu `Byte`, Visual Basic konwertuje wyrażenie które ma `Short` pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
-   <span data-ttu-id="e0c8d-120">**Konwersje formatu.**</span><span class="sxs-lookup"><span data-stu-id="e0c8d-120">**Format Conversions.**</span></span> <span data-ttu-id="e0c8d-121">W przypadku języka Visual Basic odczytuje lub zapisuje pliki lub wywoływanych przez nią bibliotek DLL, metod i właściwości, może automatycznie konwertować między formatami danych.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="e0c8d-122">Dane binarne przechowywane w `Byte` zmienne i tablice są zachowywane w trakcie takie konwersje formatu.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="e0c8d-123">Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jego zawartość, mogą zostać uszkodzone podczas konwersji między formatami ANSI i Unicode.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

-   <span data-ttu-id="e0c8d-124">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="e0c8d-124">**Widening.**</span></span> <span data-ttu-id="e0c8d-125">`Byte` — Typ danych rozszerza się na `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="e0c8d-126">Oznacza to, że możesz przekonwertować `Byte` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="e0c8d-127">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="e0c8d-127">**Type Characters.**</span></span> <span data-ttu-id="e0c8d-128">`Byte` nie ma znak literalny typu lub znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-128">`Byte` has no literal type character or identifier type character.</span></span>

-   <span data-ttu-id="e0c8d-129">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="e0c8d-129">**Framework Type.**</span></span> <span data-ttu-id="e0c8d-130">Odpowiedni typ w .NET Framework jest <xref:System.Byte?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="e0c8d-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0c8d-131">Example</span></span>

 <span data-ttu-id="e0c8d-132">W poniższym przykładzie `b` jest `Byte` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="e0c8d-133">Instrukcje pokazują zakres zmiennej i stosowania operatory przesunięcia bitowego w odniesieniu do niego.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a><span data-ttu-id="e0c8d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0c8d-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="e0c8d-135">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e0c8d-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="e0c8d-136">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e0c8d-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e0c8d-137">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e0c8d-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="e0c8d-138">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="e0c8d-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
