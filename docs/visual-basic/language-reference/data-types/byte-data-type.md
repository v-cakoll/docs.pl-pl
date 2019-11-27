---
title: Byte, typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 347d7e7d0f09e089886bc81bd0be659deaca9b46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344075"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="09a5f-102">Byte — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09a5f-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="09a5f-103">Zawiera 8-bitowe (1-bajtowe) liczby całkowite bez znaku, który ma wartość z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="09a5f-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="09a5f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09a5f-104">Remarks</span></span>

<span data-ttu-id="09a5f-105">Użyj typu danych `Byte`, aby zawierać dane binarne.</span><span class="sxs-lookup"><span data-stu-id="09a5f-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="09a5f-106">Wartość domyślna `Byte` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="09a5f-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="09a5f-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="09a5f-107">Literal assignments</span></span>

<span data-ttu-id="09a5f-108">Można zadeklarować i zainicjować zmienną `Byte`, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="09a5f-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="09a5f-109">Jeśli literał całkowity znajduje się poza zakresem `Byte` (czyli jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="09a5f-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="09a5f-110">W poniższym przykładzie liczby całkowite równe 201, które są reprezentowane jako dziesiętne, szesnastkowe i literały binarne, są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na wartości `byte`.</span><span class="sxs-lookup"><span data-stu-id="09a5f-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="09a5f-111">Możesz użyć prefiksu `&h` lub `&H` do określenia literału szesnastkowego, prefiksu `&b` lub `&B`, aby zauważyć literał binarny, a prefiks `&o` lub `&O`, aby zauważyć literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="09a5f-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="09a5f-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="09a5f-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="09a5f-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_`, jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09a5f-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="09a5f-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia (`_`) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="09a5f-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="09a5f-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="09a5f-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="09a5f-116">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="09a5f-116">Programming tips</span></span>

- <span data-ttu-id="09a5f-117">**Liczby ujemne.**</span><span class="sxs-lookup"><span data-stu-id="09a5f-117">**Negative Numbers.**</span></span> <span data-ttu-id="09a5f-118">Ponieważ `Byte` jest typem bez znaku, nie może reprezentować liczby ujemnej.</span><span class="sxs-lookup"><span data-stu-id="09a5f-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="09a5f-119">Jeśli używasz operatora jednoargumentowego minus (`-`) w wyrażeniu, które oblicza `Byte`, Visual Basic konwertuje wyrażenie na `Short` jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="09a5f-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="09a5f-120">**Konwersje formatu.**</span><span class="sxs-lookup"><span data-stu-id="09a5f-120">**Format Conversions.**</span></span> <span data-ttu-id="09a5f-121">Gdy Visual Basic odczytuje lub zapisuje pliki, lub gdy wywołuje biblioteki DLL, metody i właściwości, można automatycznie konwertować między formatami danych.</span><span class="sxs-lookup"><span data-stu-id="09a5f-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="09a5f-122">Dane binarne przechowywane w zmiennych `Byte` i tablicach są zachowywane podczas konwersji tego formatu.</span><span class="sxs-lookup"><span data-stu-id="09a5f-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="09a5f-123">Nie należy używać zmiennej `String` dla danych binarnych, ponieważ jej zawartość może być uszkodzona podczas konwersji między formatami ANSI i Unicode.</span><span class="sxs-lookup"><span data-stu-id="09a5f-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="09a5f-124">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="09a5f-124">**Widening.**</span></span> <span data-ttu-id="09a5f-125">Typ danych `Byte` poszerza do `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="09a5f-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="09a5f-126">Oznacza to, że można skonwertować `Byte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="09a5f-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="09a5f-127">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="09a5f-127">**Type Characters.**</span></span> <span data-ttu-id="09a5f-128">`Byte` nie ma znaku typu literału lub typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="09a5f-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="09a5f-129">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="09a5f-129">**Framework Type.**</span></span> <span data-ttu-id="09a5f-130">Odpowiedni typ w .NET Framework jest strukturą <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09a5f-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="09a5f-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="09a5f-131">Example</span></span>

 <span data-ttu-id="09a5f-132">W poniższym przykładzie `b` jest zmienną `Byte`.</span><span class="sxs-lookup"><span data-stu-id="09a5f-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="09a5f-133">Instrukcje przedstawiają zakres zmiennej i zastosowano do niej operatory przesunięcia bitowego.</span><span class="sxs-lookup"><span data-stu-id="09a5f-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="09a5f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09a5f-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="09a5f-135">Typy danych</span><span class="sxs-lookup"><span data-stu-id="09a5f-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="09a5f-136">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="09a5f-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="09a5f-137">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="09a5f-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="09a5f-138">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="09a5f-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
