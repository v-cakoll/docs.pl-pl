---
title: Double — Typ danych (Visual Basic)
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
ms.openlocfilehash: 5d2d84f298b9cf6138e84ef287f6ea9212da2960
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43806127"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="39fbe-102">Double — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39fbe-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="39fbe-103">Przechowuje podpisany IEEE 64-bitowych (8-bajtową) podwójnej precyzji liczb zmiennoprzecinkowych, z zakresu wartości od - 1.79769313486231570E + 308 do - 4.94065645841246544E-324 dla wartości ujemnych i 4.94065645841246544E-324 za pośrednictwem 1.79769313486231570E + 308 do wartości dodatnich.</span><span class="sxs-lookup"><span data-stu-id="39fbe-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="39fbe-104">Liczby o podwójnej precyzji przechowywać przybliżeniem liczbą rzeczywistą.</span><span class="sxs-lookup"><span data-stu-id="39fbe-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39fbe-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39fbe-105">Remarks</span></span>  
 <span data-ttu-id="39fbe-106">`Double` Typu danych stanowi wielkości największą i najmniejszą możliwe podanie liczby.</span><span class="sxs-lookup"><span data-stu-id="39fbe-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="39fbe-107">Wartość domyślna `Double` wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="39fbe-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="39fbe-108">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="39fbe-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="39fbe-109">**Dokładność.**</span><span class="sxs-lookup"><span data-stu-id="39fbe-109">**Precision.**</span></span> <span data-ttu-id="39fbe-110">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="39fbe-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="39fbe-111">Może to spowodować nieoczekiwane wyniki z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="39fbe-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="39fbe-112">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="39fbe-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="39fbe-113">**Końcowe zera.**</span><span class="sxs-lookup"><span data-stu-id="39fbe-113">**Trailing Zeros.**</span></span> <span data-ttu-id="39fbe-114">Typy danych zmiennopozycyjnych nie ma żadnych wewnętrznej reprezentacji końcowe zero znaków.</span><span class="sxs-lookup"><span data-stu-id="39fbe-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="39fbe-115">Na przykład ich nie dokonuje rozróżnienia między 4.2000 i 4.2.</span><span class="sxs-lookup"><span data-stu-id="39fbe-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="39fbe-116">W związku z tym zerowego znakami nie są wyświetlane po wyświetleniu lub drukowania wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="39fbe-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="39fbe-117">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="39fbe-117">**Type Characters.**</span></span> <span data-ttu-id="39fbe-118">Dołączanie znaku typu literał `R` do literału wymusza `Double` typu danych.</span><span class="sxs-lookup"><span data-stu-id="39fbe-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="39fbe-119">Na przykład, jeśli jest poprzedzony wartością całkowitą z zakresu `R`, wartość zostanie zmieniona na `Double`.</span><span class="sxs-lookup"><span data-stu-id="39fbe-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="39fbe-120">Dołączanie znaku typu identyfikator `#` do jakiegokolwiek identyfikatora wymusza `Double`.</span><span class="sxs-lookup"><span data-stu-id="39fbe-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="39fbe-121">W poniższym przykładzie zmienna `num` jest `Double`:</span><span class="sxs-lookup"><span data-stu-id="39fbe-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="39fbe-122">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="39fbe-122">**Framework Type.**</span></span> <span data-ttu-id="39fbe-123">Odpowiedni typ w .NET Framework jest <xref:System.Double?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="39fbe-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39fbe-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39fbe-124">See Also</span></span>  
 <xref:System.Double?displayProperty=nameWithType>  
 [<span data-ttu-id="39fbe-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="39fbe-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="39fbe-126">Decimal, typ danych</span><span class="sxs-lookup"><span data-stu-id="39fbe-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="39fbe-127">Single, typ danych</span><span class="sxs-lookup"><span data-stu-id="39fbe-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="39fbe-128">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="39fbe-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="39fbe-129">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="39fbe-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="39fbe-130">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="39fbe-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="39fbe-131">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="39fbe-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="39fbe-132">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="39fbe-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
