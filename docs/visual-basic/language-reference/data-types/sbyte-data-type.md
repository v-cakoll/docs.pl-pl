---
title: "SByte — Typ danych (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="fafc1-102">SByte — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fafc1-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="fafc1-103">Blokad podpisany 8-bitowych liczb całkowitych (1-bajtowy), które wartości w wartość z zakresu od -128 do 127.</span><span class="sxs-lookup"><span data-stu-id="fafc1-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fafc1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fafc1-104">Remarks</span></span>

<span data-ttu-id="fafc1-105">Użyj `SByte` — typ danych zawierający wartości całkowite, które nie wymagają szerokość pełnych danych `Integer` , a nawet szerokość połowa danych `Short`.</span><span class="sxs-lookup"><span data-stu-id="fafc1-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="fafc1-106">W niektórych przypadkach może mieć możliwość pakietu środowisko uruchomieniowe języka wspólnego programu `SByte` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="fafc1-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="fafc1-107">Wartość domyślna `SByte` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="fafc1-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="fafc1-108">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="fafc1-108">Literal assignments</span></span>
  
<span data-ttu-id="fafc1-109">Można zadeklarować i zainicjuj `SByte` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="fafc1-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="fafc1-110">W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `SByte` wartości.</span><span class="sxs-lookup"><span data-stu-id="fafc1-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="fafc1-111">W tym przykładzie wymaga, aby skompilować z `/removeintchecks` przełącznika kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fafc1-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="fafc1-112">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="fafc1-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="fafc1-113">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="fafc1-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="fafc1-114">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="fafc1-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="fafc1-115">Jeśli liczba całkowita literału jest poza zakresem `SByte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fafc1-115">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="fafc1-116">Gdy całkowitą literału ma nie sufiks [całkowitą](integer-data-type.md) jest wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="fafc1-116">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="fafc1-117">Jeśli liczba całkowita literału jest poza zakresem `Integer` typu [długi](long-data-type.md) jest wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="fafc1-117">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="fafc1-118">To oznacza, że w poprzednich przykładach, literałach numerycznych `0x9A` i `0b10011010` będą interpretowane jako 32-bitowych liczb całkowitych ze znakiem z wartością 156, którego rozmiar przekracza <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fafc1-118">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fafc1-119">Aby pomyślnie skompilować kod podobny do tego, który przypisuje podawać liczby całkowitej w celu `SByte`, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="fafc1-119">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="fafc1-120">Wyłącz sprawdzanie granic całkowitych przez kompilowania przy użyciu `/removeintchecks` przełącznika kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fafc1-120">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="fafc1-121">Użyj [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) Aby jawnie określić wartość literału, który ma zostać przypisany do `SByte`.</span><span class="sxs-lookup"><span data-stu-id="fafc1-121">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="fafc1-122">W poniższym przykładzie przypisano ujemna literał `Short` do wartości `SByte`.</span><span class="sxs-lookup"><span data-stu-id="fafc1-122">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="fafc1-123">Należy zauważyć, że dla wartości ujemne, musi mieć ustawiony bit znaczących wyrazu znaczących literał liczbowy.</span><span class="sxs-lookup"><span data-stu-id="fafc1-123">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="fafc1-124">W przypadku naszym przykładzie jest to bit 15 literał `Short` wartość.</span><span class="sxs-lookup"><span data-stu-id="fafc1-124">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="fafc1-125">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="fafc1-125">Programming tips</span></span>
  
-   <span data-ttu-id="fafc1-126">**Zgodności ze specyfikacją CLS.**</span><span class="sxs-lookup"><span data-stu-id="fafc1-126">**CLS Compliance.**</span></span> <span data-ttu-id="fafc1-127">`SByte` Typem danych nie jest częścią [specyfikacja języka wspólnego](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik, który korzysta z niego.</span><span class="sxs-lookup"><span data-stu-id="fafc1-127">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="fafc1-128">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="fafc1-128">**Widening.**</span></span> <span data-ttu-id="fafc1-129">`SByte` Rozszerzenie typu danych do `Short`, `Integer`, `Long`, `Decimal`, `Single`, i `Double`.</span><span class="sxs-lookup"><span data-stu-id="fafc1-129">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="fafc1-130">Oznacza to, że można przekonwertować `SByte` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="fafc1-130">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="fafc1-131">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="fafc1-131">**Type Characters.**</span></span> <span data-ttu-id="fafc1-132">`SByte`nie ma znak literalny typu ani znak typu identyfikator.</span><span class="sxs-lookup"><span data-stu-id="fafc1-132">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="fafc1-133">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="fafc1-133">**Framework Type.**</span></span> <span data-ttu-id="fafc1-134">Danego typu w programie .NET Framework jest <xref:System.SByte?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="fafc1-134">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fafc1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fafc1-135">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="fafc1-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fafc1-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="fafc1-137">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fafc1-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fafc1-138">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fafc1-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="fafc1-139">Short — typ danych</span><span class="sxs-lookup"><span data-stu-id="fafc1-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="fafc1-140">Integer — typ danych</span><span class="sxs-lookup"><span data-stu-id="fafc1-140">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="fafc1-141">Long — typ danych</span><span class="sxs-lookup"><span data-stu-id="fafc1-141">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="fafc1-142">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="fafc1-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
