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
ms.openlocfilehash: 899554f427ac77ead465752c35e51ca88d045763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415637"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="77e9e-102">Double — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e9e-102">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="77e9e-103">Przechowuje podpisane cyfry IEEE 64-bit (8-bajtowe) liczby zmiennoprzecinkowe podwójnej precyzji, które obejmują wartość z-1.79769313486231570 E + 308 do-4.94065645841246544 E-324 dla wartości ujemnych i od 4.94065645841246544 E-324 do 1.79769313486231570 E + 308 dla wartości dodatnich.</span><span class="sxs-lookup"><span data-stu-id="77e9e-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="77e9e-104">Numery podwójnej precyzji przechowują przybliżoną liczbę rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="77e9e-104">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="77e9e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77e9e-105">Remarks</span></span>

<span data-ttu-id="77e9e-106">`Double`Typ danych zapewnia największą i najmniejszą możliwą liczbę wielkości.</span><span class="sxs-lookup"><span data-stu-id="77e9e-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="77e9e-107">Wartość domyślna `Double` to 0.</span><span class="sxs-lookup"><span data-stu-id="77e9e-107">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="77e9e-108">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="77e9e-108">Programming Tips</span></span>

- <span data-ttu-id="77e9e-109">**Dokładne.**</span><span class="sxs-lookup"><span data-stu-id="77e9e-109">**Precision.**</span></span> <span data-ttu-id="77e9e-110">Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci.</span><span class="sxs-lookup"><span data-stu-id="77e9e-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="77e9e-111">Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównywanie wartości i `Mod` operator.</span><span class="sxs-lookup"><span data-stu-id="77e9e-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="77e9e-112">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="77e9e-112">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="77e9e-113">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="77e9e-113">**Trailing Zeros.**</span></span> <span data-ttu-id="77e9e-114">Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji końcowych znaków.</span><span class="sxs-lookup"><span data-stu-id="77e9e-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="77e9e-115">Na przykład nie różnią się od 4,2000 do 4,2.</span><span class="sxs-lookup"><span data-stu-id="77e9e-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="77e9e-116">W związku z tym końcowe znaki nie są wyświetlane podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="77e9e-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="77e9e-117">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="77e9e-117">**Type Characters.**</span></span> <span data-ttu-id="77e9e-118">Dołączanie znaku typu literału `R` do literału wymusza jego `Double` Typ danych.</span><span class="sxs-lookup"><span data-stu-id="77e9e-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="77e9e-119">Na przykład, jeśli następuje wartość typu Integer `R` , wartość zostanie zmieniona na `Double` .</span><span class="sxs-lookup"><span data-stu-id="77e9e-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="77e9e-120">Dołączanie znaku typu identyfikatora `#` do dowolnego identyfikatora zmusza go do `Double` .</span><span class="sxs-lookup"><span data-stu-id="77e9e-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="77e9e-121">W poniższym przykładzie zmienna `num` jest wpisana jako `Double` :</span><span class="sxs-lookup"><span data-stu-id="77e9e-121">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="77e9e-122">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="77e9e-122">**Framework Type.**</span></span> <span data-ttu-id="77e9e-123">Odpowiedni typ w .NET Framework jest <xref:System.Double?displayProperty=nameWithType> strukturą.</span><span class="sxs-lookup"><span data-stu-id="77e9e-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="77e9e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77e9e-124">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="77e9e-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="77e9e-125">Data Types</span></span>](index.md)
- [<span data-ttu-id="77e9e-126">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="77e9e-126">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="77e9e-127">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="77e9e-127">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="77e9e-128">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="77e9e-128">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="77e9e-129">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="77e9e-129">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="77e9e-130">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="77e9e-130">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="77e9e-131">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="77e9e-131">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="77e9e-132">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="77e9e-132">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
