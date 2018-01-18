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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="3e15d-102">Numeryczne i operatory porównania</span><span class="sxs-lookup"><span data-stu-id="3e15d-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="3e15d-103">Operatory arytmetyczne i porównanie działać zgodnie z oczekiwaniami w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3e15d-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="3e15d-104">Na liczby zmiennoprzecinkowe SQL nie obsługuje operator modulo.</span><span class="sxs-lookup"><span data-stu-id="3e15d-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="3e15d-105">SQL nie obsługuje arytmetyczne niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="3e15d-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="3e15d-106">Operatory inkrementacji i dekrementacji powodować efekty uboczne, podczas ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym nie obsługują.</span><span class="sxs-lookup"><span data-stu-id="3e15d-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="3e15d-107">Operatory obsługiwane</span><span class="sxs-lookup"><span data-stu-id="3e15d-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="3e15d-108">obsługuje następujące operatory.</span><span class="sxs-lookup"><span data-stu-id="3e15d-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="3e15d-109">Operatory arytmetyczne podstawowe:</span><span class="sxs-lookup"><span data-stu-id="3e15d-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="3e15d-110">`-`(odejmowanie)</span><span class="sxs-lookup"><span data-stu-id="3e15d-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="3e15d-111">Dzielenie liczby całkowitej Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="3e15d-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="3e15d-112">`%`(Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="3e15d-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="3e15d-113">`-`(jednoargumentowy negacji)</span><span class="sxs-lookup"><span data-stu-id="3e15d-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="3e15d-114">Operatory porównania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="3e15d-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="3e15d-115">Visual Basic `=` i C#`==`</span><span class="sxs-lookup"><span data-stu-id="3e15d-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="3e15d-116">Visual Basic `<>` i C#`!=`</span><span class="sxs-lookup"><span data-stu-id="3e15d-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="3e15d-117">Visual Basic`Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="3e15d-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="3e15d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e15d-118">See Also</span></span>  
 [<span data-ttu-id="3e15d-119">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="3e15d-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="3e15d-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3e15d-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="3e15d-121">Operatory</span><span class="sxs-lookup"><span data-stu-id="3e15d-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
