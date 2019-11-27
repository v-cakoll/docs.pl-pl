---
title: Single, typ danych
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343916"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="1e260-102">Single — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e260-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="1e260-103">Przechowuje podpisane cyfry IEEE 32-bit (4-bajtowe) liczby zmiennoprzecinkowe o pojedynczej precyzji w zakresie wartości od-3.4028235 E + 38 do-1.401298 E-45 dla wartości ujemnych i od 1.401298 E-45 przez 3.4028235 E + 38 dla wartości dodatnich.</span><span class="sxs-lookup"><span data-stu-id="1e260-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="1e260-104">Liczby o pojedynczej precyzji przechowują przybliżoną liczbę rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="1e260-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e260-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e260-105">Remarks</span></span>  

 <span data-ttu-id="1e260-106">Użyj `Single` typ danych, aby zawierać wartości zmiennoprzecinkowe, które nie wymagają pełnej szerokości danych `Double`.</span><span class="sxs-lookup"><span data-stu-id="1e260-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="1e260-107">W niektórych przypadkach środowisko uruchomieniowe języka wspólnego może być w stanie spakować zmienne `Single` blisko siebie i zaoszczędzić użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="1e260-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="1e260-108">Wartość domyślna `Single` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="1e260-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="1e260-109">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="1e260-109">Programming Tips</span></span>  
  
- <span data-ttu-id="1e260-110">**Dokładne.**</span><span class="sxs-lookup"><span data-stu-id="1e260-110">**Precision.**</span></span> <span data-ttu-id="1e260-111">Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają dokładną reprezentację w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1e260-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="1e260-112">Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównanie wartości i operator `Mod`.</span><span class="sxs-lookup"><span data-stu-id="1e260-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="1e260-113">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="1e260-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="1e260-114">**Rozszerzającą.**</span><span class="sxs-lookup"><span data-stu-id="1e260-114">**Widening.**</span></span> <span data-ttu-id="1e260-115">Typ danych `Single` poszerza do `Double`.</span><span class="sxs-lookup"><span data-stu-id="1e260-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="1e260-116">Oznacza to, że można skonwertować `Single` na `Double` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="1e260-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="1e260-117">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="1e260-117">**Trailing Zeros.**</span></span> <span data-ttu-id="1e260-118">Zmiennoprzecinkowe typy danych nie mają żadnej wewnętrznej reprezentacji znaków kończących 0.</span><span class="sxs-lookup"><span data-stu-id="1e260-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="1e260-119">Na przykład nie różnią się od 4,2000 do 4,2.</span><span class="sxs-lookup"><span data-stu-id="1e260-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="1e260-120">W związku z tym po wyświetleniu lub wydrukowaniu wartości zmiennoprzecinkowych nie są wyświetlane znaki końcowe 0.</span><span class="sxs-lookup"><span data-stu-id="1e260-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="1e260-121">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="1e260-121">**Type Characters.**</span></span> <span data-ttu-id="1e260-122">Dołączanie znaku typu literału `F` do literału wymusza go do `Single` typu danych.</span><span class="sxs-lookup"><span data-stu-id="1e260-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="1e260-123">Dołączanie znaku typu identyfikatora `!` do dowolnego identyfikatora wymusza `Single`.</span><span class="sxs-lookup"><span data-stu-id="1e260-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="1e260-124">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="1e260-124">**Framework Type.**</span></span> <span data-ttu-id="1e260-125">Odpowiedni typ w .NET Framework jest strukturą <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1e260-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e260-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e260-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="1e260-127">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1e260-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="1e260-128">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="1e260-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="1e260-129">Double, typ danych</span><span class="sxs-lookup"><span data-stu-id="1e260-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="1e260-130">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="1e260-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="1e260-131">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1e260-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="1e260-132">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="1e260-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="1e260-133">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="1e260-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
