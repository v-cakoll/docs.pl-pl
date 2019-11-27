---
title: Double, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 347b5c7b7af4c4aafec0f91aca46a8cf640236b9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344018"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="631dc-102">Double — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="631dc-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="631dc-103">Przechowuje podpisane cyfry IEEE 64-bitowe (8-bajtowe) liczby zmiennoprzecinkowe o podwójnej precyzji, które obejmują wartość z-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 dla wartości ujemnych i z 4.94065645841246544 E-324 przez 1.79769313486231570 E + 308 dla wartości dodatnie.</span><span class="sxs-lookup"><span data-stu-id="631dc-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="631dc-104">Numery podwójnej precyzji przechowują przybliżoną liczbę rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="631dc-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="631dc-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="631dc-105">Remarks</span></span>

<span data-ttu-id="631dc-106">Typ danych `Double` zapewnia największą i najmniejszą liczbę możliwych wielkości dla liczby.</span><span class="sxs-lookup"><span data-stu-id="631dc-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="631dc-107">Wartość domyślna `Double` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="631dc-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="631dc-108">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="631dc-108">Programming Tips</span></span>

- <span data-ttu-id="631dc-109">**Dokładne.**</span><span class="sxs-lookup"><span data-stu-id="631dc-109">**Precision.**</span></span> <span data-ttu-id="631dc-110">Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci.</span><span class="sxs-lookup"><span data-stu-id="631dc-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="631dc-111">Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i operator `Mod`.</span><span class="sxs-lookup"><span data-stu-id="631dc-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="631dc-112">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="631dc-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="631dc-113">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="631dc-113">**Trailing Zeros.**</span></span> <span data-ttu-id="631dc-114">Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji końcowych znaków.</span><span class="sxs-lookup"><span data-stu-id="631dc-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="631dc-115">Na przykład nie różnią się od 4,2000 do 4,2.</span><span class="sxs-lookup"><span data-stu-id="631dc-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="631dc-116">W związku z tym końcowe znaki nie są wyświetlane podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="631dc-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="631dc-117">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="631dc-117">**Type Characters.**</span></span> <span data-ttu-id="631dc-118">Dołączanie znaku typu literału `R` do literału wymusza go do `Double` typu danych.</span><span class="sxs-lookup"><span data-stu-id="631dc-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="631dc-119">Na przykład, jeśli po wartości całkowitej następuje `R`, wartość zostanie zmieniona na `Double`.</span><span class="sxs-lookup"><span data-stu-id="631dc-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="631dc-120">Dołączanie znaku typu identyfikatora `#` do dowolnego identyfikatora wymusza `Double`.</span><span class="sxs-lookup"><span data-stu-id="631dc-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="631dc-121">W poniższym przykładzie zmienna `num` jest wpisana jako `Double`:</span><span class="sxs-lookup"><span data-stu-id="631dc-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="631dc-122">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="631dc-122">**Framework Type.**</span></span> <span data-ttu-id="631dc-123">Odpowiedni typ w .NET Framework jest strukturą <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="631dc-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="631dc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="631dc-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="631dc-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="631dc-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="631dc-126">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="631dc-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="631dc-127">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="631dc-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="631dc-128">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="631dc-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="631dc-129">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="631dc-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="631dc-130">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="631dc-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="631dc-131">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="631dc-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="631dc-132">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="631dc-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
