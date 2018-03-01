---
title: "Double — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad0e8082edfb7b7d96b0ca2019da88514e5b3b09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="eb92a-102">Double — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb92a-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="eb92a-103">Blokad podpisany IEEE 64-bitowych (8-bajtowych) podwójnej precyzji liczb zmiennoprzecinkowych, które mają wartość z zakresu od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych i z 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnie.</span><span class="sxs-lookup"><span data-stu-id="eb92a-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="eb92a-104">Liczby o podwójnej precyzji przechowywać zbliżenia liczba rzeczywista.</span><span class="sxs-lookup"><span data-stu-id="eb92a-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb92a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb92a-105">Remarks</span></span>  
 <span data-ttu-id="eb92a-106">`Double` — Typ danych przewiduje liczbą wielkości największych i najmniejsze możliwe.</span><span class="sxs-lookup"><span data-stu-id="eb92a-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="eb92a-107">Wartość domyślna `Double` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="eb92a-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="eb92a-108">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="eb92a-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="eb92a-109">**Precyzja.**</span><span class="sxs-lookup"><span data-stu-id="eb92a-109">**Precision.**</span></span> <span data-ttu-id="eb92a-110">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="eb92a-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="eb92a-111">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="eb92a-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="eb92a-112">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="eb92a-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="eb92a-113">**Końcowe zero.**</span><span class="sxs-lookup"><span data-stu-id="eb92a-113">**Trailing Zeros.**</span></span> <span data-ttu-id="eb92a-114">Typy danych zmiennoprzecinkowych nie mają żadnych reprezentacji wewnętrznej końcowe zero znaków.</span><span class="sxs-lookup"><span data-stu-id="eb92a-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="eb92a-115">Na przykład one rozróżnia 4.2000 i 4.2.</span><span class="sxs-lookup"><span data-stu-id="eb92a-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="eb92a-116">W rezultacie końcowe zero znaki nie są wyświetlane po wyświetleniu lub drukowania wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="eb92a-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="eb92a-117">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="eb92a-117">**Type Characters.**</span></span> <span data-ttu-id="eb92a-118">Znak literalny typu dołączanie `R` do literału wymusza `Double` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="eb92a-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="eb92a-119">Na przykład, jeśli wartość całkowitą następuje `R`, wartość jest zmieniana na `Double`.</span><span class="sxs-lookup"><span data-stu-id="eb92a-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="eb92a-120">Dołączanie znak typu identyfikator `#` dla wszystkich identyfikatorów wymusza `Double`.</span><span class="sxs-lookup"><span data-stu-id="eb92a-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="eb92a-121">W poniższym przykładzie zmienna `num` jest typu `Double`:</span><span class="sxs-lookup"><span data-stu-id="eb92a-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="eb92a-122">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="eb92a-122">**Framework Type.**</span></span> <span data-ttu-id="eb92a-123">Danego typu w programie .NET Framework jest <xref:System.Double?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="eb92a-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb92a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb92a-124">See Also</span></span>  
 <xref:System.Double?displayProperty=nameWithType>  
 [<span data-ttu-id="eb92a-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="eb92a-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="eb92a-126">Decimal — typ danych</span><span class="sxs-lookup"><span data-stu-id="eb92a-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="eb92a-127">Single — typ danych</span><span class="sxs-lookup"><span data-stu-id="eb92a-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="eb92a-128">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="eb92a-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="eb92a-129">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="eb92a-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="eb92a-130">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="eb92a-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="eb92a-131">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="eb92a-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="eb92a-132">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="eb92a-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
