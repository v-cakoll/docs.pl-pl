---
title: Liczbowe i operatory porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: e2bdc55cd6c2203bc96d0766e5e53a57294d4d7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554715"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="f0299-102">Liczbowe i operatory porównania</span><span class="sxs-lookup"><span data-stu-id="f0299-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="f0299-103">Operatory arytmetyczne i porównanie działają w oczekiwany sposób w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem sytuacji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f0299-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="f0299-104">SQL nie obsługuje operator modulo na liczby zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="f0299-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="f0299-105">SQL nie obsługuje arytmetyki niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f0299-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="f0299-106">Operatory inkrementacji i dekrementacji spowodować efekty uboczne, gdy będziesz ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym, nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="f0299-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="f0299-107">Operatory obsługiwane</span><span class="sxs-lookup"><span data-stu-id="f0299-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f0299-108">obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="f0299-108">supports the following operators.</span></span>  
  
-   <span data-ttu-id="f0299-109">Podstawowe operatory arytmetyczne:</span><span class="sxs-lookup"><span data-stu-id="f0299-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="f0299-110">`-` (odejmowanie)</span><span class="sxs-lookup"><span data-stu-id="f0299-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="f0299-111">Dzielenie liczby całkowitej w języku Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="f0299-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="f0299-112">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="f0299-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="f0299-113">`-` (negacja Jednoargumentowa)</span><span class="sxs-lookup"><span data-stu-id="f0299-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="f0299-114">Operatory porównania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="f0299-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="f0299-115">Visual Basic `=` i C# `==`</span><span class="sxs-lookup"><span data-stu-id="f0299-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="f0299-116">Visual Basic `<>` i C# `!=`</span><span class="sxs-lookup"><span data-stu-id="f0299-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="f0299-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="f0299-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="f0299-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0299-118">See also</span></span>
- [<span data-ttu-id="f0299-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="f0299-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [<span data-ttu-id="f0299-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f0299-120">C# Operators</span></span>](../../../../../../docs/csharp/language-reference/operators/index.md)
- [<span data-ttu-id="f0299-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="f0299-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
