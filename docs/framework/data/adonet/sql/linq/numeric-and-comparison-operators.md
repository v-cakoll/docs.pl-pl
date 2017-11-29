---
title: "Numeryczne i operatory porównania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="e7b6f-102">Numeryczne i operatory porównania</span><span class="sxs-lookup"><span data-stu-id="e7b6f-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="e7b6f-103">Operatory arytmetyczne i porównanie działać zgodnie z oczekiwaniami w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e7b6f-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="e7b6f-104">Na liczby zmiennoprzecinkowe SQL nie obsługuje operator modulo.</span><span class="sxs-lookup"><span data-stu-id="e7b6f-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="e7b6f-105">SQL nie obsługuje arytmetyczne niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="e7b6f-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="e7b6f-106">Operatory inkrementacji i dekrementacji powodować efekty uboczne, podczas ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="e7b6f-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="e7b6f-107">Operatory obsługiwane</span><span class="sxs-lookup"><span data-stu-id="e7b6f-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e7b6f-108">obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="e7b6f-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="e7b6f-109">Operatory arytmetyczne podstawowe:</span><span class="sxs-lookup"><span data-stu-id="e7b6f-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="e7b6f-110">`-`(odejmowanie)</span><span class="sxs-lookup"><span data-stu-id="e7b6f-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="e7b6f-111">Dzielenie liczby całkowitej Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="e7b6f-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="e7b6f-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="e7b6f-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="e7b6f-113">`-`(jednoargumentowy negacji)</span><span class="sxs-lookup"><span data-stu-id="e7b6f-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="e7b6f-114">Operatory porównania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="e7b6f-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="e7b6f-115">Visual Basic `=` i C#`==`</span><span class="sxs-lookup"><span data-stu-id="e7b6f-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="e7b6f-116">Visual Basic `<>` i C#`!=`</span><span class="sxs-lookup"><span data-stu-id="e7b6f-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="e7b6f-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="e7b6f-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="e7b6f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7b6f-118">See Also</span></span>  
 [<span data-ttu-id="e7b6f-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="e7b6f-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="e7b6f-120">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="e7b6f-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="e7b6f-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="e7b6f-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
