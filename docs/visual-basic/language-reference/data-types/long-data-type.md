---
title: "Long — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cf03afc6b2e77ccca74fc26365fc50110e1f71
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="4d01b-102">Long — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d01b-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="4d01b-103">Blokad podpisane liczby całkowite (8-bajtowych) 64-bitowym z zakresu od-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="4d01b-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d01b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d01b-104">Remarks</span></span>

 <span data-ttu-id="4d01b-105">Użyj `Long` typu danych, aby zawierała liczby całkowite, które są za duże, aby zmieścić ją w `Integer` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="4d01b-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="4d01b-106">Wartość domyślna `Long` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="4d01b-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="4d01b-107">Przydziały literału</span><span class="sxs-lookup"><span data-stu-id="4d01b-107">Literal assignments</span></span> 

<span data-ttu-id="4d01b-108">Można zadeklarować i zainicjuj `Long` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny.</span><span class="sxs-lookup"><span data-stu-id="4d01b-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4d01b-109">Jeśli liczba całkowita literału jest poza zakresem `Long` (to znaczy, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4d01b-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4d01b-110">W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `Long` wartości.</span><span class="sxs-lookup"><span data-stu-id="4d01b-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="4d01b-111">Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału.</span><span class="sxs-lookup"><span data-stu-id="4d01b-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4d01b-112">Literałów dziesiętnych mają nie ma prefiksu.</span><span class="sxs-lookup"><span data-stu-id="4d01b-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4d01b-113">Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="4d01b-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="4d01b-114">Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="4d01b-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4d01b-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4d01b-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4d01b-116">Literały numeryczne mogą również obejmować `L` [znaku typu](../../programming-guide\language-features\data-types/type-characters.md) do oznaczania `Long` typu danych, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4d01b-116">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="4d01b-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="4d01b-117">Programming tips</span></span>

-   <span data-ttu-id="4d01b-118">**Zagadnienia dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="4d01b-118">**Interop Considerations.**</span></span> <span data-ttu-id="4d01b-119">Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework, na przykład obiektów automatyzacji lub COM, należy pamiętać, że `Long` ma szerokość różnych danych (32-bitowy) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="4d01b-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="4d01b-120">Jeśli argument 32-bitowej do tych składników, Zadeklaruj ją jako `Integer` zamiast `Long` w nowy kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4d01b-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="4d01b-121">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="4d01b-121">**Widening.**</span></span> <span data-ttu-id="4d01b-122">`Long` Rozszerzenie typu danych do `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="4d01b-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="4d01b-123">Oznacza to, że można przekonwertować `Long` do dowolnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="4d01b-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="4d01b-124">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="4d01b-124">**Type Characters.**</span></span> <span data-ttu-id="4d01b-125">Znak literalny typu dołączanie `L` do literału wymusza `Long` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="4d01b-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="4d01b-126">Dołączanie znak typu identyfikator `&` dla wszystkich identyfikatorów wymusza `Long`.</span><span class="sxs-lookup"><span data-stu-id="4d01b-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="4d01b-127">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="4d01b-127">**Framework Type.**</span></span> <span data-ttu-id="4d01b-128">Danego typu w programie .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="4d01b-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4d01b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d01b-129">See also</span></span>

<span data-ttu-id="4d01b-130"><xref:System.Int64>[Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4d01b-130"><xref:System.Int64> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="4d01b-131">[Integer — typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="4d01b-131">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="4d01b-132">[Short — typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="4d01b-132">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="4d01b-133">[Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="4d01b-133">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="4d01b-134">[Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="4d01b-134">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="4d01b-135">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="4d01b-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
