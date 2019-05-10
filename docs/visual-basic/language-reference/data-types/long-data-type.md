---
title: Long — Typ danych (Visual Basic)
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
ms.openlocfilehash: 7b4226c83f25807e013823031820d58790bb6db2
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912788"
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="9e99d-102">Long — typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e99d-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="9e99d-103">Przechowuje podpisane liczby całkowite (8-bajtową) 64-bitowym z zakresu od-9,223,372,036,854,775,808 za pośrednictwem 9,223,372,036,854,775,807 (9.2... E + 18).</span><span class="sxs-lookup"><span data-stu-id="9e99d-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e99d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e99d-104">Remarks</span></span>

 <span data-ttu-id="9e99d-105">Użyj `Long` typu danych, aby zawierała liczby całkowite, które są zbyt duże, aby zmieścić ją w `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="9e99d-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="9e99d-106">Wartość domyślna `Long` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="9e99d-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="9e99d-107">Literał przypisania</span><span class="sxs-lookup"><span data-stu-id="9e99d-107">Literal assignments</span></span> 

<span data-ttu-id="9e99d-108">Można zadeklarować i zainicjować `Long` zmiennej przez przypisanie dziesiętna literałem szesnastkowy literał ósemkową literał lub (począwszy od 2017 Visual Basic) literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="9e99d-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="9e99d-109">Jeśli literał liczby całkowitej jest poza zakresem `Long` (to znaczy, jeśli jest mniejszy niż <xref:System.Int64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int64.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9e99d-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="9e99d-110">W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `Long` wartości.</span><span class="sxs-lookup"><span data-stu-id="9e99d-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="9e99d-111">Użyj prefiksu `&h` lub `&H` do oznaczania szesnastkowy literał, prefiks `&b` lub `&B` do oznaczania literału binarnego i prefiksem `&o` lub `&O` do oznaczania ósemkową literału.</span><span class="sxs-lookup"><span data-stu-id="9e99d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="9e99d-112">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="9e99d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="9e99d-113">Począwszy od 2017 Visual Basic umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="9e99d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="9e99d-114">Począwszy od wersji 15.5 programu Visual Basic umożliwia także znaku podkreślenia (`_`) jako wiodący separator między prefiks i cyfr szesnastkowych, binarne lub ósemkowo.</span><span class="sxs-lookup"><span data-stu-id="9e99d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="9e99d-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="9e99d-115">For example:</span></span>

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="9e99d-116">Literały numeryczne mogą również obejmować `L` [wpisz znak](../../programming-guide/language-features/data-types/type-characters.md) do oznaczania `Long` typu danych, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="9e99d-116">Numeric literals can also include the `L` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a><span data-ttu-id="9e99d-117">Porady dotyczące programowania</span><span class="sxs-lookup"><span data-stu-id="9e99d-117">Programming tips</span></span>

- <span data-ttu-id="9e99d-118">**Uwagi dotyczące współdziałania.**</span><span class="sxs-lookup"><span data-stu-id="9e99d-118">**Interop Considerations.**</span></span> <span data-ttu-id="9e99d-119">Jeśli są komunikowanie się ze składnikami programu .NET Framework, na przykład obiektami automatyzacji lub COM, pamiętaj, że `Long` ma różną szerokość danych (32-bitowy) w innych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="9e99d-119">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="9e99d-120">Jeśli przekazujesz 32-bitowy argument do takiego składnika, Zadeklaruj go jako `Integer` zamiast `Long` nowego kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9e99d-120">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="9e99d-121">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="9e99d-121">**Widening.**</span></span> <span data-ttu-id="9e99d-122">`Long` — Typ danych rozszerza się na `Decimal`, `Single`, lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="9e99d-122">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="9e99d-123">Oznacza to, że możesz przekonwertować `Long` do jednej z tych typów, nie powodując <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="9e99d-123">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="9e99d-124">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="9e99d-124">**Type Characters.**</span></span> <span data-ttu-id="9e99d-125">Dołączanie znaku typu literał `L` do literału wymusza `Long` typu danych.</span><span class="sxs-lookup"><span data-stu-id="9e99d-125">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="9e99d-126">Dołączanie znaku typu identyfikator `&` do jakiegokolwiek identyfikatora wymusza `Long`.</span><span class="sxs-lookup"><span data-stu-id="9e99d-126">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
- <span data-ttu-id="9e99d-127">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="9e99d-127">**Framework Type.**</span></span> <span data-ttu-id="9e99d-128">Odpowiedni typ w .NET Framework jest <xref:System.Int64?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="9e99d-128">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="9e99d-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e99d-129">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="9e99d-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9e99d-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="9e99d-131">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="9e99d-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="9e99d-132">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="9e99d-132">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="9e99d-133">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9e99d-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9e99d-134">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9e99d-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="9e99d-135">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="9e99d-135">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
