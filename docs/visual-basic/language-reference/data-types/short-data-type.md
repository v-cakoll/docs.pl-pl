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
ms.openlocfilehash: eb218a9b72208b13700ebd18dbf588066839203d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492921"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="ca657-102">Short — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca657-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="ca657-103">Przechowuje podpisany 16-bitowych liczb całkowitych (2-bajtowych), z zakresu wartości od-32 768 za pośrednictwem 32 767 znaków.</span><span class="sxs-lookup"><span data-stu-id="ca657-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca657-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca657-104">Remarks</span></span>  
 <span data-ttu-id="ca657-105">Użyj `Short` typu danych, które zawierają wartości całkowitych, które nie wymagają szerokość pełnych danych `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ca657-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="ca657-106">W niektórych przypadkach można pakietu środowiska uruchomieniowego języka wspólnego swoje `Short` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="ca657-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="ca657-107">Wartość domyślna `Short` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="ca657-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="ca657-108">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="ca657-108">Literal assignments</span></span>

<span data-ttu-id="ca657-109">Można zadeklarować i zainicjować `Short` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="ca657-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="ca657-110">Jeśli literał liczby całkowitej jest poza zakresem `Short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ca657-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="ca657-111">W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `Short` wartości.</span><span class="sxs-lookup"><span data-stu-id="ca657-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="ca657-112">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="ca657-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ca657-113">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="ca657-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ca657-114">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="ca657-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="ca657-115">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="ca657-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ca657-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ca657-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ca657-117">Literały numeryczne mogą również obejmować `S` [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Short` typu danych, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="ca657-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="ca657-118">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="ca657-118">Programming tips</span></span>

-   <span data-ttu-id="ca657-119">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="ca657-119">**Widening.**</span></span> <span data-ttu-id="ca657-120">`Short` — Typ danych rozszerza się na `Integer`, `Long`, `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="ca657-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="ca657-121">Oznacza to, że możesz przekonwertować `Short` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="ca657-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="ca657-122">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="ca657-122">**Type Characters.**</span></span> <span data-ttu-id="ca657-123">Dołączanie znaku typu literał `S` do literału wymusza `Short` typu danych.</span><span class="sxs-lookup"><span data-stu-id="ca657-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="ca657-124">`Short` nie ma identyfikatora typ znaku.</span><span class="sxs-lookup"><span data-stu-id="ca657-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="ca657-125">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="ca657-125">**Framework Type.**</span></span> <span data-ttu-id="ca657-126">Odpowiedni typ w .NET Framework jest <xref:System.Int16?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="ca657-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca657-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca657-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="ca657-128">Typy danych</span><span class="sxs-lookup"><span data-stu-id="ca657-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="ca657-129">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="ca657-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ca657-130">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ca657-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="ca657-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="ca657-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="ca657-132">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="ca657-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="ca657-133">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="ca657-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
