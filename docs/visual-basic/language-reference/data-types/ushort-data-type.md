---
title: UShort, typ danych
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
ms.openlocfilehash: ee31156e00059699125fd72a7f091afbb21beab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415482"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="1290e-102">UShort — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1290e-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="1290e-103">Przechowuje liczby całkowite (2-bajtowe) bez znaku w zakresie od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="1290e-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1290e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1290e-104">Remarks</span></span>

 <span data-ttu-id="1290e-105">Użyj `UShort` typu danych, aby zawierać dane binarne za duże `Byte` .</span><span class="sxs-lookup"><span data-stu-id="1290e-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="1290e-106">Wartość domyślna `UShort` to 0.</span><span class="sxs-lookup"><span data-stu-id="1290e-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="1290e-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="1290e-107">Literal assignments</span></span>

<span data-ttu-id="1290e-108">Można zadeklarować i zainicjować `UShort` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="1290e-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="1290e-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `UShort` (to jest, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1290e-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="1290e-110">W poniższym przykładzie liczby całkowite równe 65 034 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `UShort` wartości.</span><span class="sxs-lookup"><span data-stu-id="1290e-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="1290e-111">Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego.</span><span class="sxs-lookup"><span data-stu-id="1290e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="1290e-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="1290e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="1290e-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1290e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="1290e-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="1290e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="1290e-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1290e-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="1290e-116">Literały numeryczne mogą również zawierać `US` `us` [znak](../../programming-guide/language-features/data-types/type-characters.md) lub, aby zauważyć `UShort` Typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1290e-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="1290e-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="1290e-117">Programming tips</span></span>
  
- <span data-ttu-id="1290e-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="1290e-118">**Negative Numbers.**</span></span> <span data-ttu-id="1290e-119">Ponieważ `UShort` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="1290e-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="1290e-120">W przypadku użycia jednoargumentowego operatora minus ( `-` ) w wyrażeniu, którego typem jest typ `UShort` , Visual Basic konwertuje wyrażenie na `Integer` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="1290e-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="1290e-121">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="1290e-121">**CLS Compliance.**</span></span> <span data-ttu-id="1290e-122">`UShort`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="1290e-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="1290e-123">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="1290e-123">**Widening.**</span></span> <span data-ttu-id="1290e-124">`UShort`Typ danych poszerza do,, `Integer` ,,, `UInteger` `Long` `ULong` `Decimal` `Single` , i `Double` .</span><span class="sxs-lookup"><span data-stu-id="1290e-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="1290e-125">Oznacza to, że można dokonać konwersji `UShort` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="1290e-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="1290e-126">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="1290e-126">**Type Characters.**</span></span> <span data-ttu-id="1290e-127">Dołączanie znaków literału `US` do literału wymusza jego do `UShort` typu danych.</span><span class="sxs-lookup"><span data-stu-id="1290e-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="1290e-128">`UShort`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="1290e-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="1290e-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="1290e-129">**Framework Type.**</span></span> <span data-ttu-id="1290e-130">Odpowiedni typ w .NET Framework jest <xref:System.UInt16?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="1290e-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1290e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1290e-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="1290e-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1290e-132">Data Types</span></span>](index.md)
- [<span data-ttu-id="1290e-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="1290e-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1290e-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1290e-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1290e-135">Instrukcje: Wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="1290e-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="1290e-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="1290e-136">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
