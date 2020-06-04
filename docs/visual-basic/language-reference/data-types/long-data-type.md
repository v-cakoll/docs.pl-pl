---
title: Long, typ danych
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
ms.openlocfilehash: 7c076cd2198c85560f7c63c69e051697966c9524
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415599"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="7a0d5-102">Long — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a0d5-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="7a0d5-103">Przechowuje podpisaną 64-bitową (8-bajtową) liczbę całkowitą z zakresu od-zakresu od do 9 223 372 036 854 775 807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="7a0d5-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>

## <a name="remarks"></a><span data-ttu-id="7a0d5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a0d5-104">Remarks</span></span>

<span data-ttu-id="7a0d5-105">Użyj `Long` typu danych, aby zawierać liczby całkowite, które są zbyt duże, aby mieściły się w `Integer` typie danych.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>

<span data-ttu-id="7a0d5-106">Wartość domyślna `Long` to 0.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="7a0d5-107">Przypisania literałów</span><span class="sxs-lookup"><span data-stu-id="7a0d5-107">Literal assignments</span></span>

<span data-ttu-id="7a0d5-108">Można zadeklarować i zainicjować `Long` zmienną, przypisując jej literał dziesiętny, literał szesnastkowy, literał ósemkowy lub (Zaczynając od Visual Basic 2017) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="7a0d5-109">Jeśli literał liczby całkowitej znajduje się poza zakresem `Long` (to jest, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większy niż <xref:System.Int64.MaxValue?displayProperty=nameWithType> , wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="7a0d5-110">W poniższym przykładzie liczby całkowite równe 4 294 967 296 są reprezentowane jako literały dziesiętne, szesnastkowe i binarne są przypisywane do `Long` wartości.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]

> [!NOTE]
> <span data-ttu-id="7a0d5-111">Używasz prefiksu `&h` lub `&H` do oznaczenia literału szesnastkowego, prefiksu `&b` lub `&B` do oznaczania literału binarnego oraz prefiksu `&o` lub `&O` do określenia literału ósemkowego.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="7a0d5-112">Literały dziesiętne nie mają prefiksu.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7a0d5-113">Począwszy od Visual Basic 2017, można również użyć znaku podkreślenia, `_` jako separatora cyfr, aby zwiększyć czytelność, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="7a0d5-114">Począwszy od Visual Basic 15,5, można również użyć znaku podkreślenia ( `_` ) jako wiodącego separatora między cyframi prefiksu i szesnastkową, binarną lub ósemkową.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="7a0d5-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="7a0d5-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="7a0d5-116">Literały numeryczne mogą również zawierać `L` [znak typu](../../programming-guide/language-features/data-types/type-characters.md) , aby zauważyć `Long` Typ danych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="7a0d5-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="7a0d5-117">Programming tips</span></span>

- <span data-ttu-id="7a0d5-118">**Zagadnienia dotyczące międzyoperacyjnych.**</span><span class="sxs-lookup"><span data-stu-id="7a0d5-118">**Interop Considerations.**</span></span> <span data-ttu-id="7a0d5-119">Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że `Long` w innych środowiskach ma inną szerokość danych (32 bitów).</span><span class="sxs-lookup"><span data-stu-id="7a0d5-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="7a0d5-120">Jeśli przekazujesz argument 32-bitowy do takiego składnika, zadeklaruj go jako `Integer` zamiast `Long` w nowym kodzie Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>

- <span data-ttu-id="7a0d5-121">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="7a0d5-121">**Widening.**</span></span> <span data-ttu-id="7a0d5-122">`Long`Typ danych poszerza do `Decimal` , `Single` , lub `Double` .</span><span class="sxs-lookup"><span data-stu-id="7a0d5-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="7a0d5-123">Oznacza to, że można przekonwertować `Long` na jeden z tych typów, bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="7a0d5-124">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="7a0d5-124">**Type Characters.**</span></span> <span data-ttu-id="7a0d5-125">Dołączanie znaku typu literału `L` do literału wymusza jego `Long` Typ danych.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="7a0d5-126">Dołączanie znaku typu identyfikatora `&` do dowolnego identyfikatora zmusza go do `Long` .</span><span class="sxs-lookup"><span data-stu-id="7a0d5-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>

- <span data-ttu-id="7a0d5-127">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="7a0d5-127">**Framework Type.**</span></span> <span data-ttu-id="7a0d5-128">Odpowiedni typ w .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="7a0d5-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a0d5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a0d5-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="7a0d5-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7a0d5-130">Data Types</span></span>](index.md)
- [<span data-ttu-id="7a0d5-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="7a0d5-131">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="7a0d5-132">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="7a0d5-132">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="7a0d5-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7a0d5-133">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="7a0d5-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="7a0d5-134">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="7a0d5-135">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="7a0d5-135">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
