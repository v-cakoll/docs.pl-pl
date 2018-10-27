---
title: Liczbowe i operatory porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 733c1e494c29f04aa06a4159c3b1dae219f01b44
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180339"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="c84d2-102">Liczbowe i operatory porównania</span><span class="sxs-lookup"><span data-stu-id="c84d2-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="c84d2-103">Operatory arytmetyczne i porównanie działają w oczekiwany sposób w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem sytuacji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c84d2-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="c84d2-104">SQL nie obsługuje operator modulo na liczby zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="c84d2-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="c84d2-105">SQL nie obsługuje arytmetyki niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="c84d2-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="c84d2-106">Operatory inkrementacji i dekrementacji spowodować efekty uboczne, gdy będziesz ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym, nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="c84d2-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="c84d2-107">Operatory obsługiwane</span><span class="sxs-lookup"><span data-stu-id="c84d2-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c84d2-108">obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="c84d2-108">supports the following operators.</span></span>  
  
-   <span data-ttu-id="c84d2-109">Podstawowe operatory arytmetyczne:</span><span class="sxs-lookup"><span data-stu-id="c84d2-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="c84d2-110">`-` (odejmowanie)</span><span class="sxs-lookup"><span data-stu-id="c84d2-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="c84d2-111">Dzielenie liczby całkowitej w języku Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="c84d2-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="c84d2-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="c84d2-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="c84d2-113">`-` (negacja Jednoargumentowa)</span><span class="sxs-lookup"><span data-stu-id="c84d2-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="c84d2-114">Operatory porównania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="c84d2-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="c84d2-115">Visual Basic `=` i C# `==`</span><span class="sxs-lookup"><span data-stu-id="c84d2-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="c84d2-116">Visual Basic `<>` i C# `!=`</span><span class="sxs-lookup"><span data-stu-id="c84d2-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="c84d2-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="c84d2-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="c84d2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c84d2-118">See Also</span></span>  
 [<span data-ttu-id="c84d2-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="c84d2-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="c84d2-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c84d2-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c84d2-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="c84d2-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
