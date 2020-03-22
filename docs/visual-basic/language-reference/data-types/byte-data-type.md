---
title: Byte — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400744"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="601f6-102">Typ danych bajtów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="601f6-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="601f6-103">Przechowuje niepodpisane 8-bitowe (1-bajtowe) liczby całkowite o wartości od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="601f6-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="601f6-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="601f6-104">Remarks</span></span>

<span data-ttu-id="601f6-105">Użyj `Byte` typu danych, aby zawierać dane binarne.</span><span class="sxs-lookup"><span data-stu-id="601f6-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="601f6-106">Wartość domyślna `Byte` to 0.</span><span class="sxs-lookup"><span data-stu-id="601f6-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="601f6-107">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="601f6-107">Literal assignments</span></span>

<span data-ttu-id="601f6-108">Można zadeklarować i `Byte` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="601f6-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="601f6-109">Jeśli literał integralny znajduje się `Byte` poza zakresem a (czyli jeśli jest mniejszy <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większy niż), <xref:System.Byte.MaxValue?displayProperty=nameWithType>występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="601f6-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="601f6-110">W poniższym przykładzie liczby całkowite równe 201, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na `byte` wartości.</span><span class="sxs-lookup"><span data-stu-id="601f6-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="601f6-111">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="601f6-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="601f6-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="601f6-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="601f6-113">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="601f6-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="601f6-114">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="601f6-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="601f6-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="601f6-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="601f6-116">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="601f6-116">Programming tips</span></span>

- <span data-ttu-id="601f6-117">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="601f6-117">**Negative Numbers.**</span></span> <span data-ttu-id="601f6-118">Ponieważ `Byte` jest typem niepodpisanym, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="601f6-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="601f6-119">Jeśli w wyrażeniu, które ma być wpisane, użyjesz operatora unary minus (`-`) w wyrażeniu, które ma być wpisane, `Byte`visual basic konwertuje wyrażenie na `Short` pierwsze.</span><span class="sxs-lookup"><span data-stu-id="601f6-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="601f6-120">**Formatowanie konwersji.**</span><span class="sxs-lookup"><span data-stu-id="601f6-120">**Format Conversions.**</span></span> <span data-ttu-id="601f6-121">Gdy program Visual Basic odczytuje lub zapisuje pliki lub gdy wywołuje biblioteki DLL, metody i właściwości, może automatycznie konwertować między formatami danych.</span><span class="sxs-lookup"><span data-stu-id="601f6-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="601f6-122">Dane binarne przechowywane w `Byte` zmiennych i tablicach są zachowywane podczas konwersji formatu.</span><span class="sxs-lookup"><span data-stu-id="601f6-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="601f6-123">Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jej zawartość może być uszkodzona podczas konwersji między formatami ANSI i Unicode.</span><span class="sxs-lookup"><span data-stu-id="601f6-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="601f6-124">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="601f6-124">**Widening.**</span></span> <span data-ttu-id="601f6-125">Typ `Byte` danych rozszerza `Short`się `UShort` `Integer`do `UInteger` `Long`, `ULong` `Decimal`, `Single`, `Double`, , , , , lub .</span><span class="sxs-lookup"><span data-stu-id="601f6-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="601f6-126">Oznacza to, `Byte` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="601f6-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="601f6-127">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="601f6-127">**Type Characters.**</span></span> <span data-ttu-id="601f6-128">`Byte`nie ma znaku literału ani znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="601f6-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="601f6-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="601f6-129">**Framework Type.**</span></span> <span data-ttu-id="601f6-130">Odpowiedni typ w .NET Framework <xref:System.Byte?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="601f6-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="601f6-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="601f6-131">Example</span></span>

 <span data-ttu-id="601f6-132">W poniższym `b` przykładzie `Byte` jest zmienną.</span><span class="sxs-lookup"><span data-stu-id="601f6-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="601f6-133">Instrukcje pokazują zakres zmiennej i zastosowanie operatorów zmiany bitowej do niej.</span><span class="sxs-lookup"><span data-stu-id="601f6-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="601f6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="601f6-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="601f6-135">Typy danych</span><span class="sxs-lookup"><span data-stu-id="601f6-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="601f6-136">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="601f6-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="601f6-137">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="601f6-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="601f6-138">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="601f6-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
