---
title: SByte — Typ danych
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
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400793"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="a2482-102">Typ danych SByte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2482-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="a2482-103">Przechowuje podpisane 8-bitowe (1-bajtowe) liczby całkowite o wartości od -128 do 127.</span><span class="sxs-lookup"><span data-stu-id="a2482-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2482-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2482-104">Remarks</span></span>

<span data-ttu-id="a2482-105">Użyj `SByte` typu danych, aby zawierać wartości całkowite, które nie `Integer` wymagają pełnej szerokości `Short`danych lub nawet połowy szerokości danych .</span><span class="sxs-lookup"><span data-stu-id="a2482-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="a2482-106">W niektórych przypadkach środowisko uruchomieniowe języka `SByte` wspólnego może być w stanie spakować zmienne ściśle razem i zapisać zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="a2482-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="a2482-107">Wartość domyślna `SByte` to 0.</span><span class="sxs-lookup"><span data-stu-id="a2482-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="a2482-108">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="a2482-108">Literal assignments</span></span>

<span data-ttu-id="a2482-109">Można zadeklarować i `SByte` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="a2482-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="a2482-110">W poniższym przykładzie liczby całkowite równe -102, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `SByte` wartości.</span><span class="sxs-lookup"><span data-stu-id="a2482-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="a2482-111">W tym przykładzie wymaga `/removeintchecks` kompilacji z przełącznikiem kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a2482-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="a2482-112">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="a2482-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a2482-113">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="a2482-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a2482-114">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a2482-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="a2482-115">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="a2482-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a2482-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a2482-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="a2482-117">Jeśli litera liczba całkowita znajduje się `SByte` poza zakresem (oznacza <xref:System.SByte.MinValue?displayProperty=nameWithType> to, <xref:System.SByte.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a2482-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="a2482-118">Gdy litera liczba całkowita nie ma sufiksu, [liczba całkowita](integer-data-type.md) jest wywnioskowana.</span><span class="sxs-lookup"><span data-stu-id="a2482-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="a2482-119">Jeśli literał liczby całkowitej znajduje się `Integer` poza zakresem typu, [Long](long-data-type.md) jest wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="a2482-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="a2482-120">Oznacza to, że w poprzednich przykładach literały `0x9A` `0b10011010` liczbowe i są interpretowane jako 32-bitowe podpisane liczby całkowite <xref:System.SByte.MaxValue?displayProperty=nameWithType>o wartości 156, która przekracza .</span><span class="sxs-lookup"><span data-stu-id="a2482-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a2482-121">Aby pomyślnie skompilować kod w ten sposób, który przypisuje `SByte`liczbę całkowitą bez miejsca do przecinka dziesiętnego do , można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a2482-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="a2482-122">Wyłącz sprawdzanie granic liczby całkowitej, `/removeintchecks` kompilując za pomocą przełącznika kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a2482-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="a2482-123">Użyj [znaku tekstowego,](../../programming-guide/language-features/data-types/type-characters.md) aby jawnie zdefiniować wartość literału, którą chcesz przypisać do pliku `SByte`.</span><span class="sxs-lookup"><span data-stu-id="a2482-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="a2482-124">Poniższy przykład przypisuje ujemną `Short` wartość `SByte`literału do pliku .</span><span class="sxs-lookup"><span data-stu-id="a2482-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="a2482-125">Należy zauważyć, że w przypadku liczb ujemnych należy ustawić bit wysokiego rzędu słowa wysokiego rzędu literału liczbowego.</span><span class="sxs-lookup"><span data-stu-id="a2482-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="a2482-126">W przypadku naszego przykładu jest to nieco 15 wartości literału. `Short`</span><span class="sxs-lookup"><span data-stu-id="a2482-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="a2482-127">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="a2482-127">Programming tips</span></span>

- <span data-ttu-id="a2482-128">**Zgodność z CLS.**</span><span class="sxs-lookup"><span data-stu-id="a2482-128">**CLS Compliance.**</span></span> <span data-ttu-id="a2482-129">Typ `SByte` danych nie jest częścią [specyfikacji języka wspólnego](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), więc kod zgodny ze specyfikacją CLS nie może korzystać ze składnika, który go używa.</span><span class="sxs-lookup"><span data-stu-id="a2482-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="a2482-130">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="a2482-130">**Widening.**</span></span> <span data-ttu-id="a2482-131">Typ `SByte` danych rozszerza `Short`się `Integer` `Long`do `Decimal` `Single`, `Double`, , , i .</span><span class="sxs-lookup"><span data-stu-id="a2482-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="a2482-132">Oznacza to, `SByte` że można przekonwertować <xref:System.OverflowException?displayProperty=nameWithType> do dowolnego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="a2482-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="a2482-133">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="a2482-133">**Type Characters.**</span></span> <span data-ttu-id="a2482-134">`SByte`nie ma znaku literału ani znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a2482-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="a2482-135">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="a2482-135">**Framework Type.**</span></span> <span data-ttu-id="a2482-136">Odpowiedni typ w .NET Framework <xref:System.SByte?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="a2482-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2482-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2482-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="a2482-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a2482-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a2482-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="a2482-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a2482-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a2482-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a2482-141">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="a2482-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="a2482-142">Integer — Typ danych</span><span class="sxs-lookup"><span data-stu-id="a2482-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="a2482-143">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="a2482-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="a2482-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="a2482-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
