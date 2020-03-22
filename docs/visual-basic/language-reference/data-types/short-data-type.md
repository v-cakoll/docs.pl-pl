---
title: Short — typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400730"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="fd4ef-102">Krótki typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd4ef-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="fd4ef-103">Posiada podpisane 16-bitowe (2-bajtowe) liczby całkowite o wartości od -32 768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd4ef-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd4ef-104">Remarks</span></span>  

 <span data-ttu-id="fd4ef-105">Użyj `Short` typu danych, aby zawierać wartości całkowite, które nie `Integer`wymagają pełnej szerokości danych .</span><span class="sxs-lookup"><span data-stu-id="fd4ef-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="fd4ef-106">W niektórych przypadkach środowisko wykonawcze `Short` języka wspólnego można spakować zmienne ściśle razem i zapisać zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="fd4ef-107">Wartość domyślna `Short` to 0.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="fd4ef-108">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="fd4ef-108">Literal assignments</span></span>

<span data-ttu-id="fd4ef-109">Można zadeklarować i `Short` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="fd4ef-110">Jeśli litera liczba całkowita znajduje się `Short` poza zakresem (oznacza <xref:System.Int16.MinValue?displayProperty=nameWithType> to, <xref:System.Int16.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="fd4ef-111">W poniższym przykładzie liczby całkowite równe 1034, które są reprezentowane jako dziesiętne, szesnastkowe i binarne `Short` literały są niejawnie konwertowane z [liczby całkowitej](integer-data-type.md) na wartości.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="fd4ef-112">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fd4ef-113">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fd4ef-114">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="fd4ef-115">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="fd4ef-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="fd4ef-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="fd4ef-117">Literały liczbowe mogą również `S` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) typu `Short` oznaczającego typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="fd4ef-118">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="fd4ef-118">Programming tips</span></span>

- <span data-ttu-id="fd4ef-119">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="fd4ef-119">**Widening.**</span></span> <span data-ttu-id="fd4ef-120">Typ `Short` danych rozszerza `Integer`się `Long` `Decimal`do `Single`, `Double`, , , lub .</span><span class="sxs-lookup"><span data-stu-id="fd4ef-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="fd4ef-121">Oznacza to, `Short` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="fd4ef-122">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="fd4ef-122">**Type Characters.**</span></span> <span data-ttu-id="fd4ef-123">Dołączenie znaku literału `S` do literału wymusza go do `Short` typu danych.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="fd4ef-124">`Short`nie ma znaku typu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="fd4ef-125">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="fd4ef-125">**Framework Type.**</span></span> <span data-ttu-id="fd4ef-126">Odpowiedni typ w .NET Framework <xref:System.Int16?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="fd4ef-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4ef-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd4ef-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="fd4ef-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fd4ef-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="fd4ef-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fd4ef-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="fd4ef-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fd4ef-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="fd4ef-131">Integer — Typ danych</span><span class="sxs-lookup"><span data-stu-id="fd4ef-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="fd4ef-132">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="fd4ef-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="fd4ef-133">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="fd4ef-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
