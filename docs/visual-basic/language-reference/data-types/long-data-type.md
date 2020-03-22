---
title: Long — Typ danych
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
ms.openlocfilehash: 16d7409c802e97b1f33474d810134db4d9f0ad6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400814"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="41b9e-102">Długi typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41b9e-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="41b9e-103">Posiada podpisane 64-bitowe (8-bajtowe) liczby całkowite o wartości od -9 223 372 036 854 775 808 do 9 223 372 036 854 775 807 (9,2...E+18).</span><span class="sxs-lookup"><span data-stu-id="41b9e-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="41b9e-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41b9e-104">Remarks</span></span>

<span data-ttu-id="41b9e-105">Użyj `Long` typu danych, aby zawierać liczby całkowite, które są `Integer` zbyt duże, aby zmieścić się w typie danych.</span><span class="sxs-lookup"><span data-stu-id="41b9e-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="41b9e-106">Wartość domyślna `Long` to 0.</span><span class="sxs-lookup"><span data-stu-id="41b9e-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="41b9e-107">Przydziały dosłowne</span><span class="sxs-lookup"><span data-stu-id="41b9e-107">Literal assignments</span></span>

<span data-ttu-id="41b9e-108">Można zadeklarować i `Long` zainicjować zmienną, przypisując jej literał dziesiętny, szesnastkowy literał, literał ósemkowy lub (zaczynając od języka Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="41b9e-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="41b9e-109">Jeśli litera liczba całkowita znajduje się `Long` poza zakresem (oznacza <xref:System.Int64.MinValue?displayProperty=nameWithType> to, <xref:System.Int64.MaxValue?displayProperty=nameWithType>że jest mniejsza lub większa niż , występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="41b9e-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="41b9e-110">W poniższym przykładzie liczby całkowite równe 4,294,967,296, które są reprezentowane jako dziesiętne, szesnastkowe i binarne literały są przypisane do `Long` wartości.</span><span class="sxs-lookup"><span data-stu-id="41b9e-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="41b9e-111">Prefiksu `&h` lub `&H` oznaczasz szesnastkowy literał, `&b` `&B` prefiks lub oznacza literał binarny i prefiks `&o` lub `&O` oznacza literał ósemkowy.</span><span class="sxs-lookup"><span data-stu-id="41b9e-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="41b9e-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="41b9e-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="41b9e-113">Począwszy od języka Visual Basic 2017, `_`można również użyć znaku podkreślenia, jako separatora cyfry, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41b9e-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="41b9e-114">Począwszy od języka Visual Basic 15.5,`_`można również użyć znaku podkreślenia ( ) jako interełownika wiodącego między prefiksem a cyframi szesnastkowymi, binarnymi lub ósemkowymi.</span><span class="sxs-lookup"><span data-stu-id="41b9e-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="41b9e-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="41b9e-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="41b9e-116">Literały liczbowe mogą również `L` zawierać [znak](../../programming-guide/language-features/data-types/type-characters.md) typu `Long` oznaczającego typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41b9e-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="41b9e-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="41b9e-117">Programming tips</span></span>

- <span data-ttu-id="41b9e-118">**Zagadnienia międzyoperacyjne.**</span><span class="sxs-lookup"><span data-stu-id="41b9e-118">**Interop Considerations.**</span></span> <span data-ttu-id="41b9e-119">Jeśli łączysz się ze składnikami nieuznawane dla programu .NET Framework, `Long` na przykład automatyzacji lub COM obiektów, należy pamiętać, że ma inną szerokość danych (32 bity) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="41b9e-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="41b9e-120">Jeśli przekazujesz 32-bitowy argument do takiego składnika, zadeklaruj go jako `Integer` zamiast `Long` w nowym kodzie języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41b9e-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="41b9e-121">**Poszerzenie.**</span><span class="sxs-lookup"><span data-stu-id="41b9e-121">**Widening.**</span></span> <span data-ttu-id="41b9e-122">Typ `Long` danych rozszerza `Decimal`się `Single`do `Double`, lub .</span><span class="sxs-lookup"><span data-stu-id="41b9e-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="41b9e-123">Oznacza to, `Long` że można przekonwertować do <xref:System.OverflowException?displayProperty=nameWithType> jednego z tych typów bez napotkania błędu.</span><span class="sxs-lookup"><span data-stu-id="41b9e-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="41b9e-124">**Wpisz znaki.**</span><span class="sxs-lookup"><span data-stu-id="41b9e-124">**Type Characters.**</span></span> <span data-ttu-id="41b9e-125">Dołączenie znaku literału `L` do literału wymusza go do `Long` typu danych.</span><span class="sxs-lookup"><span data-stu-id="41b9e-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="41b9e-126">Dołączenie znaku `&` typu identyfikatora do dowolnego identyfikatora wymusza jego `Long`</span><span class="sxs-lookup"><span data-stu-id="41b9e-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="41b9e-127">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="41b9e-127">**Framework Type.**</span></span> <span data-ttu-id="41b9e-128">Odpowiedni typ w .NET Framework <xref:System.Int64?displayProperty=nameWithType> jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="41b9e-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="41b9e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41b9e-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="41b9e-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="41b9e-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="41b9e-131">Integer — Typ danych</span><span class="sxs-lookup"><span data-stu-id="41b9e-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="41b9e-132">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="41b9e-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="41b9e-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="41b9e-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="41b9e-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="41b9e-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="41b9e-135">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="41b9e-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
