---
title: Integer — Typ danych (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1846153375b19b773fedaf056a009f28ab94a4d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591732"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="06a14-102">Integer — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06a14-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="06a14-103">Przechowuje 32-bitowe (4-bajtowe) liczby całkowite ze znakiem z zakresu wartości od -2 147 483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="06a14-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06a14-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06a14-104">Remarks</span></span>
 <span data-ttu-id="06a14-105">`Integer` — Typ danych zapewnia optymalną wydajność w 32-bitowego procesora.</span><span class="sxs-lookup"><span data-stu-id="06a14-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="06a14-106">Inne typy całkowitoliczbowe wolniej wczytują się z pamięci i są w niej zapisywane.</span><span class="sxs-lookup"><span data-stu-id="06a14-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="06a14-107">Wartość domyślna `Integer` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="06a14-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="06a14-108">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="06a14-108">Literal assignments</span></span>

<span data-ttu-id="06a14-109">Można zadeklarować i zainicjuj `Integer` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="06a14-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="06a14-110">Jeśli liczba całkowita literału jest poza zakresem `Integer` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06a14-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="06a14-111">W poniższym przykładzie liczb całkowitych równa 16,342, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `Integer` wartości.</span><span class="sxs-lookup"><span data-stu-id="06a14-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="06a14-112">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="06a14-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="06a14-113">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="06a14-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="06a14-114">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="06a14-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="06a14-115">Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="06a14-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="06a14-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="06a14-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="06a14-117">Literały numeryczne mogą również obejmować `I` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Integer` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="06a14-117">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="06a14-118">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="06a14-118">Programming tips</span></span>

-   <span data-ttu-id="06a14-119">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="06a14-119">**Interop Considerations.**</span></span> <span data-ttu-id="06a14-120">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, takich jak obiekty automatyzacji lub COM, należy pamiętać, że `Integer` ma szerokość różnych danych (16 bitów) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="06a14-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="06a14-121">Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `Short` zamiast `Integer` w nowy kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="06a14-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="06a14-122">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="06a14-122">**Widening.**</span></span> <span data-ttu-id="06a14-123">`Integer` Rozszerzenie typu danych do `Long`, `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a14-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="06a14-124">Oznacza to, że można przekonwertować `Integer` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="06a14-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="06a14-125">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="06a14-125">**Type Characters.**</span></span> <span data-ttu-id="06a14-126">Znak literalny typu dołączanie `I` do literału wymusza `Integer` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="06a14-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="06a14-127">Dołączanie znak typu identyfikator `%` dla wszystkich identyfikatorów wymusza `Integer`.</span><span class="sxs-lookup"><span data-stu-id="06a14-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="06a14-128">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="06a14-128">**Framework Type.**</span></span> <span data-ttu-id="06a14-129">Danego typu w programie .NET Framework jest <xref:System.Int32?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="06a14-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="06a14-130">Zakres</span><span class="sxs-lookup"><span data-stu-id="06a14-130">Range</span></span>

<span data-ttu-id="06a14-131">Jeśli spróbujesz ustawić zmienną typu całkowitoliczbowego na liczbę spoza zakresu dla tego typu, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="06a14-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="06a14-132">Jeśli spróbujesz ustawić ją na ułamek, liczba jest zaokrąglana w górę lub w dół do najbliższej wartości liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="06a14-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="06a14-133">Jeśli liczba jest jednakowo blisko dwóch wartości całkowitych, wartość jest zaokrąglana do najbliższej parzystej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="06a14-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="06a14-134">To zachowanie minimalizuje błędy zaokrągleń, które powstają w wyniku konsekwentnego zaokrąglania wartości punktu środkowego w jednym kierunku.</span><span class="sxs-lookup"><span data-stu-id="06a14-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="06a14-135">W poniższym kodzie pokazano przykłady zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="06a14-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="06a14-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06a14-136">See also</span></span>

<xref:System.Int32?displayProperty=nameWithType>   
 [<span data-ttu-id="06a14-137">Typy danych</span><span class="sxs-lookup"><span data-stu-id="06a14-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="06a14-138">Long, typ danych</span><span class="sxs-lookup"><span data-stu-id="06a14-138">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="06a14-139">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="06a14-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="06a14-140">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="06a14-140">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="06a14-141">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="06a14-141">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="06a14-142">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="06a14-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
