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
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="d4702-102">UShort — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4702-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="d4702-103">Przechowuje liczby całkowite (2-bajtowe) bez znaku w zakresie od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="d4702-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4702-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4702-104">Remarks</span></span>

 <span data-ttu-id="d4702-105">Użyj `UShort` typ danych, aby zawierać dane binarne zbyt duże dla `Byte`.</span><span class="sxs-lookup"><span data-stu-id="d4702-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="d4702-106">Wartość domyślna `UShort` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="d4702-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="d4702-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="d4702-107">Literal assignments</span></span>

<span data-ttu-id="d4702-108">Można zadeklarować i zainicjować zmienną `UShort`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="d4702-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="d4702-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `UShort` (czyli jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d4702-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="d4702-110">W poniższym przykładzie liczby całkowite równe 65 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do wartości `UShort`.</span><span class="sxs-lookup"><span data-stu-id="d4702-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="d4702-111">Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="d4702-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d4702-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="d4702-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d4702-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d4702-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="d4702-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="d4702-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d4702-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d4702-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d4702-116">Literały numeryczne mogą również zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) `US` lub `us`, aby zauważyć `UShort` typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d4702-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="d4702-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="d4702-117">Programming tips</span></span>
  
- <span data-ttu-id="d4702-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="d4702-118">**Negative Numbers.**</span></span> <span data-ttu-id="d4702-119">Ponieważ `UShort` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="d4702-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d4702-120">Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `UShort`, Visual Basic konwertuje wyrażenie na `Integer` jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="d4702-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="d4702-121">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="d4702-121">**CLS Compliance.**</span></span> <span data-ttu-id="d4702-122">`UShort` typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="d4702-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="d4702-123">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="d4702-123">**Widening.**</span></span> <span data-ttu-id="d4702-124">Typ danych `UShort` poszerza do `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`i `Double`.</span><span class="sxs-lookup"><span data-stu-id="d4702-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d4702-125">Oznacza to, że można skonwertować `UShort` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="d4702-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="d4702-126">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="d4702-126">**Type Characters.**</span></span> <span data-ttu-id="d4702-127">Dołączanie znaków literału `US` do literału wymusza `UShort` do typu danych.</span><span class="sxs-lookup"><span data-stu-id="d4702-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="d4702-128">`UShort` nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="d4702-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="d4702-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="d4702-129">**Framework Type.**</span></span> <span data-ttu-id="d4702-130">Odpowiedni typ w .NET Framework jest strukturą <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4702-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4702-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4702-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="d4702-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="d4702-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="d4702-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="d4702-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d4702-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="d4702-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="d4702-135">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="d4702-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d4702-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="d4702-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
