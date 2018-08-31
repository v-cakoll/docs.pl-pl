---
title: SByte — Typ danych (Visual Basic)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ab72b2ac2678640697e3cfab426e5a7d6d889a
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257399"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="2b657-102">SByte — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b657-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="2b657-103">Przechowuje podpisany (8-bitowa 1-bajtowe) liczby całkowite z zakresu wartości od -128 do 127.</span><span class="sxs-lookup"><span data-stu-id="2b657-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b657-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b657-104">Remarks</span></span>

<span data-ttu-id="2b657-105">Użyj `SByte` typu danych, które zawierają wartości całkowitych, które nie wymagają szerokość pełnych danych `Integer` , a nawet szerokość danych w wysokości równej połowie `Short`.</span><span class="sxs-lookup"><span data-stu-id="2b657-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="2b657-106">W niektórych przypadkach może być możliwość pakietu środowiska uruchomieniowego języka wspólnego swoje `SByte` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="2b657-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="2b657-107">Wartość domyślna `SByte` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="2b657-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2b657-108">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="2b657-108">Literal assignments</span></span>
  
<span data-ttu-id="2b657-109">Można zadeklarować i zainicjować `SByte` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="2b657-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="2b657-110">W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `SByte` wartości.</span><span class="sxs-lookup"><span data-stu-id="2b657-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="2b657-111">W tym przykładzie wymaga kompilacji z `/removeintchecks` przełącznika kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2b657-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="2b657-112">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="2b657-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2b657-113">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="2b657-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2b657-114">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="2b657-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="2b657-115">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="2b657-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="2b657-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2b657-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="2b657-117">Jeśli literał liczby całkowitej jest poza zakresem `SByte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2b657-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="2b657-118">Gdy literał liczby całkowitej ma Brak przyrostka [całkowitą](integer-data-type.md) została wywnioskowana.</span><span class="sxs-lookup"><span data-stu-id="2b657-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="2b657-119">Jeśli literał liczby całkowitej jest poza zakresem `Integer` typu [długie](long-data-type.md) została wywnioskowana.</span><span class="sxs-lookup"><span data-stu-id="2b657-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="2b657-120">Oznacza to, że w poprzednich przykładach literały numeryczne `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem z wartością 156, co powoduje przekroczenie <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b657-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2b657-121">Aby pomyślnie skompilować kod tak, który przypisuje niebędący cyfrą dziesiętną liczby całkowitej w celu `SByte`, można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2b657-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="2b657-122">Wyłącz sprawdzanie granic liczby całkowitej przez kompilowanie za pomocą `/removeintchecks` przełącznika kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2b657-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="2b657-123">Użyj [wpisz znak](../../programming-guide\language-features\data-types/type-characters.md) umożliwia jawne zdefiniowanie wartości literału, który chcesz przypisać do `SByte`.</span><span class="sxs-lookup"><span data-stu-id="2b657-123">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="2b657-124">Poniższy przykład przypisuje ujemna literał `Short` wartość `SByte`.</span><span class="sxs-lookup"><span data-stu-id="2b657-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="2b657-125">Należy pamiętać, że dla liczb ujemnych musi być ustawiony bit wyższego rzędu słowo wyższego rzędu literału liczbowego.</span><span class="sxs-lookup"><span data-stu-id="2b657-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="2b657-126">W przypadku naszym przykładzie jest to bit 15 literału `Short` wartość.</span><span class="sxs-lookup"><span data-stu-id="2b657-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="2b657-127">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="2b657-127">Programming tips</span></span>
  
-   <span data-ttu-id="2b657-128">**Zgodność ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="2b657-128">**CLS Compliance.**</span></span> <span data-ttu-id="2b657-129">`SByte` Typem danych nie jest częścią [specyfikacja Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), dzięki czemu kod zgodny ze specyfikacją CLS nie mogą korzystać z składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="2b657-129">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="2b657-130">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="2b657-130">**Widening.**</span></span> <span data-ttu-id="2b657-131">`SByte` — Typ danych rozszerza się na `Short`, `Integer`, `Long`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="2b657-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="2b657-132">Oznacza to, że możesz przekonwertować `SByte` do dowolnego z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="2b657-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="2b657-133">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="2b657-133">**Type Characters.**</span></span> <span data-ttu-id="2b657-134">`SByte` nie ma znak literalny typu lub znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="2b657-134">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="2b657-135">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="2b657-135">**Framework Type.**</span></span> <span data-ttu-id="2b657-136">Odpowiedni typ w .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="2b657-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b657-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b657-137">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="2b657-138">Typy danych</span><span class="sxs-lookup"><span data-stu-id="2b657-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="2b657-139">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="2b657-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2b657-140">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="2b657-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2b657-141">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="2b657-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="2b657-142">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="2b657-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="2b657-143">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="2b657-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="2b657-144">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="2b657-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
