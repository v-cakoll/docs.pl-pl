---
title: Numeryczne i operatory porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a1ce13225d72b4286982434d52998a1913814abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="8f758-102">Numeryczne i operatory porównania</span><span class="sxs-lookup"><span data-stu-id="8f758-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="8f758-103">Operatory arytmetyczne i porównanie działać zgodnie z oczekiwaniami w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f758-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="8f758-104">Na liczby zmiennoprzecinkowe SQL nie obsługuje operator modulo.</span><span class="sxs-lookup"><span data-stu-id="8f758-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="8f758-105">SQL nie obsługuje arytmetyczne niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="8f758-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="8f758-106">Operatory inkrementacji i dekrementacji powodować efekty uboczne, podczas ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="8f758-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="8f758-107">Operatory obsługiwane</span><span class="sxs-lookup"><span data-stu-id="8f758-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8f758-108"> obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="8f758-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="8f758-109">Operatory arytmetyczne podstawowe:</span><span class="sxs-lookup"><span data-stu-id="8f758-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="8f758-110">`-` (odejmowanie)</span><span class="sxs-lookup"><span data-stu-id="8f758-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="8f758-111">Dzielenie liczby całkowitej Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="8f758-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="8f758-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="8f758-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="8f758-113">`-` (jednoargumentowy negacji)</span><span class="sxs-lookup"><span data-stu-id="8f758-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="8f758-114">Operatory porównania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="8f758-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="8f758-115">Visual Basic `=` i C# `==`</span><span class="sxs-lookup"><span data-stu-id="8f758-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="8f758-116">Visual Basic `<>` i C# `!=`</span><span class="sxs-lookup"><span data-stu-id="8f758-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="8f758-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="8f758-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="8f758-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f758-118">See Also</span></span>  
 [<span data-ttu-id="8f758-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="8f758-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="8f758-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8f758-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="8f758-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="8f758-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
