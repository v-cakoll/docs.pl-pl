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
ms.openlocfilehash: 7cdbd5fb192fd5cc1be6260dcdcdb1f30cf3f865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400695"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="279f7-102">Typ danych UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279f7-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="279f7-103">Przechowuje niepodpisane 16-bitowe (2-bajtowe) liczby całkowite o wartości od 0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="279f7-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="279f7-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="279f7-104">Remarks</span></span>

 <span data-ttu-id="279f7-105">Użyj `UShort` typu danych, aby zawierać `Byte`dane binarne zbyt duże dla .</span><span class="sxs-lookup"><span data-stu-id="279f7-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="279f7-106">Wartość domyślna `UShort` to 0.</span><span class="sxs-lookup"><span data-stu-id="279f7-106">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="279f7-107">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="279f7-107">Literal assignments</span></span>

<span data-ttu-id="279f7-108">Można zadeklarować i `UShort` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="279f7-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="279f7-109">Jeśli litera liczba całkowita znajduje się `UShort` poza zakresem (oznacza <xref:System.UInt16.MinValue?displayProperty=nameWithType> to, <xref:System.UInt16.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="279f7-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="279f7-110">W poniższym przykładzie liczby całkowite równe 65 034, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisywane do `UShort` wartości.</span><span class="sxs-lookup"><span data-stu-id="279f7-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="279f7-111">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="279f7-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="279f7-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="279f7-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="279f7-113">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="279f7-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="279f7-114">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="279f7-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="279f7-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="279f7-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="279f7-116">Literały liczbowe mogą również `US` `us` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) lub `UShort` typ oznaczania typu danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="279f7-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="279f7-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="279f7-117">Programming tips</span></span>
  
- <span data-ttu-id="279f7-118">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="279f7-118">**Negative Numbers.**</span></span> <span data-ttu-id="279f7-119">Ponieważ `UShort` jest typem niepodpisanym, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="279f7-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="279f7-120">Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `UShort`visual basic konwertuje wyrażenie na `Integer` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="279f7-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="279f7-121">**Zgodność z CLS.**</span><span class="sxs-lookup"><span data-stu-id="279f7-121">**CLS Compliance.**</span></span> <span data-ttu-id="279f7-122">Typ `UShort` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="279f7-122">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="279f7-123">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="279f7-123">**Widening.**</span></span> <span data-ttu-id="279f7-124">Typ `UShort` danych rozszerza `Integer`się `UInteger` `Long`do `ULong` `Decimal`, `Single`, `Double`, , , i .</span><span class="sxs-lookup"><span data-stu-id="279f7-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="279f7-125">Oznacza to, `UShort` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="279f7-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="279f7-126">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="279f7-126">**Type Characters.**</span></span> <span data-ttu-id="279f7-127">Dołączenie znaków `US` typu literału do literału `UShort` wymusza go do typu danych.</span><span class="sxs-lookup"><span data-stu-id="279f7-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="279f7-128">`UShort`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="279f7-128">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="279f7-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="279f7-129">**Framework Type.**</span></span> <span data-ttu-id="279f7-130">Odpowiedni typ w .NET Framework <xref:System.UInt16?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="279f7-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279f7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="279f7-131">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="279f7-132">Typy danych</span><span class="sxs-lookup"><span data-stu-id="279f7-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="279f7-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="279f7-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="279f7-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="279f7-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="279f7-135">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="279f7-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="279f7-136">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="279f7-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
