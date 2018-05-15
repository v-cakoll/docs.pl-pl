---
title: Short — Typ danych (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: ef99743828d8d80844486b651178622ff45fd554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="556bb-102">Short — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="556bb-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="556bb-103">Blokad podpisany 16-bitowych liczb całkowitych (2-bajtowych) o wartości od-32 768 do 32 767.</span><span class="sxs-lookup"><span data-stu-id="556bb-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="556bb-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="556bb-104">Remarks</span></span>  
 <span data-ttu-id="556bb-105">Użyj `Short` — typ danych zawierający wartości całkowite, które nie wymagają szerokość pełnych danych `Integer`.</span><span class="sxs-lookup"><span data-stu-id="556bb-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="556bb-106">W niektórych przypadkach można pakietu środowisko uruchomieniowe języka wspólnego programu `Short` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="556bb-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="556bb-107">Wartość domyślna `Short` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="556bb-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="556bb-108">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="556bb-108">Literal assignments</span></span>

<span data-ttu-id="556bb-109">Można zadeklarować i zainicjuj `Short` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="556bb-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="556bb-110">Jeśli liczba całkowita literału jest poza zakresem `Short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="556bb-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="556bb-111">W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `Short` wartości.</span><span class="sxs-lookup"><span data-stu-id="556bb-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="556bb-112">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="556bb-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="556bb-113">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="556bb-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="556bb-114">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="556bb-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="556bb-115">Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="556bb-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="556bb-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="556bb-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="556bb-117">Literały numeryczne mogą również obejmować `S` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Short` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="556bb-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="556bb-118">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="556bb-118">Programming tips</span></span>

-   <span data-ttu-id="556bb-119">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="556bb-119">**Widening.**</span></span> <span data-ttu-id="556bb-120">`Short` Rozszerzenie typu danych do `Integer`, `Long`, `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="556bb-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="556bb-121">Oznacza to, że można przekonwertować `Short` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="556bb-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="556bb-122">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="556bb-122">**Type Characters.**</span></span> <span data-ttu-id="556bb-123">Znak literalny typu dołączanie `S` do literału wymusza `Short` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="556bb-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="556bb-124">`Short` nie ma identyfikatora typu znaku.</span><span class="sxs-lookup"><span data-stu-id="556bb-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="556bb-125">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="556bb-125">**Framework Type.**</span></span> <span data-ttu-id="556bb-126">Danego typu w programie .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="556bb-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556bb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="556bb-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="556bb-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="556bb-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="556bb-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="556bb-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="556bb-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="556bb-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="556bb-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="556bb-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="556bb-132">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="556bb-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="556bb-133">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="556bb-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
