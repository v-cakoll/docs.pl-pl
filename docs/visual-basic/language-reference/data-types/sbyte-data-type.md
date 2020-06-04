---
title: SByte, typ danych
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e7d45c74056ce5b6aa66674c99e48b5ab60015f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415573"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="b19d0-102">Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b19d0-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="b19d0-103">Przechowuje 8-bitową liczbę całkowitą ze znakiem, która ma wartość z zakresu od-128 do 127.</span><span class="sxs-lookup"><span data-stu-id="b19d0-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="b19d0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b19d0-104">Remarks</span></span>

<span data-ttu-id="b19d0-105">Użyj `SByte` typu danych, aby zawierać wartości całkowite, które nie wymagają pełnej szerokości danych, `Integer` a nawet połówkowej szerokości danych `Short` .</span><span class="sxs-lookup"><span data-stu-id="b19d0-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="b19d0-106">W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może mieć ścisłe spakowanie `SByte` zmiennych i oszczędność zużycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="b19d0-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="b19d0-107">Wartość domyślna `SByte` to 0.</span><span class="sxs-lookup"><span data-stu-id="b19d0-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="b19d0-108">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="b19d0-108">Literal assignments</span></span>

<span data-ttu-id="b19d0-109">Można zadeklarować i zainicjować `SByte` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="b19d0-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="b19d0-110">W poniższym przykładzie liczby całkowite równe-102 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `SByte` wartości.</span><span class="sxs-lookup"><span data-stu-id="b19d0-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="b19d0-111">Ten przykład wymaga skompilowania z `/removeintchecks` przełącznikiem kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b19d0-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="b19d0-112">Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego.</span><span class="sxs-lookup"><span data-stu-id="b19d0-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b19d0-113">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b19d0-114">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b19d0-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="b19d0-115">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="b19d0-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b19d0-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b19d0-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="b19d0-117">Jeśli literał liczby całkowitej znajduje się poza zakresem `SByte` (to jest, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.SByte.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b19d0-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="b19d0-118">Gdy literał typu Integer nie ma sufiksu, zostanie wywnioskowana [Liczba całkowita](integer-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="b19d0-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="b19d0-119">Jeśli literał liczby całkowitej jest poza zakresem `Integer` typu, jest wywnioskowana wartość [Long](long-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="b19d0-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="b19d0-120">Oznacza to, że w poprzednich przykładach literały liczbowe `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem o wartości 156, które przekraczają <xref:System.SByte.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b19d0-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b19d0-121">Aby pomyślnie skompilować kod, który przypisuje niedziesiętną liczbę całkowitą do `SByte` , można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b19d0-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="b19d0-122">Wyłącz sprawdzanie granic liczby całkowitej przez skompilowanie z `/removeintchecks` przełącznikiem kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b19d0-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="b19d0-123">Użyj [znaku typu](../../programming-guide/language-features/data-types/type-characters.md) , aby jawnie zdefiniować wartość literału, która ma zostać przypisana do `SByte` .</span><span class="sxs-lookup"><span data-stu-id="b19d0-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="b19d0-124">Poniższy przykład przypisuje ujemną wartość literału `Short` do `SByte` .</span><span class="sxs-lookup"><span data-stu-id="b19d0-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="b19d0-125">Należy pamiętać, że w przypadku liczb ujemnych należy ustawić dużą kolejność wyrazów o wysokiej kolejności w literale numerycznym.</span><span class="sxs-lookup"><span data-stu-id="b19d0-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="b19d0-126">W przypadku naszego przykładu jest to bit 15 wartości literału `Short` .</span><span class="sxs-lookup"><span data-stu-id="b19d0-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="b19d0-127">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="b19d0-127">Programming tips</span></span>

- <span data-ttu-id="b19d0-128">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="b19d0-128">**CLS Compliance.**</span></span> <span data-ttu-id="b19d0-129">`SByte`Typ danych nie jest częścią [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może używać składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="b19d0-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="b19d0-130">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="b19d0-130">**Widening.**</span></span> <span data-ttu-id="b19d0-131">`SByte`Typ danych poszerza do `Short` ,,, `Integer` , `Long` `Decimal` `Single` , i `Double` .</span><span class="sxs-lookup"><span data-stu-id="b19d0-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b19d0-132">Oznacza to, że można dokonać konwersji `SByte` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="b19d0-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="b19d0-133">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="b19d0-133">**Type Characters.**</span></span> <span data-ttu-id="b19d0-134">`SByte`nie ma znaku typu literału lub znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="b19d0-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="b19d0-135">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="b19d0-135">**Framework Type.**</span></span> <span data-ttu-id="b19d0-136">Odpowiedni typ w .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="b19d0-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="b19d0-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b19d0-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="b19d0-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="b19d0-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="b19d0-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="b19d0-139">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="b19d0-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="b19d0-140">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="b19d0-141">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="b19d0-141">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="b19d0-142">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="b19d0-142">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="b19d0-143">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="b19d0-143">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="b19d0-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="b19d0-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
