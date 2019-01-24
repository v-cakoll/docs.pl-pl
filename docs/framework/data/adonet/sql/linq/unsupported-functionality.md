---
title: Nieobsługiwana funkcja
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5022c9011c2aac5b3272e359f991c40236a5673f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686706"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="1dce2-102">Nieobsługiwana funkcja</span><span class="sxs-lookup"><span data-stu-id="1dce2-102">Unsupported Functionality</span></span>
<span data-ttu-id="1dce2-103">W składniku LINQ to SQL tłumaczenie istniejące środowisko uruchomieniowe języka wspólnego (CLR) nie są dostępne następujące funkcje programu SQL i .NET Framework tworzy:</span><span class="sxs-lookup"><span data-stu-id="1dce2-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="1dce2-104">Mimo że `LIKE` nie jest obsługiwany za pośrednictwem bezpośredniego tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="1dce2-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="1dce2-105">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1dce2-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="1dce2-106">LINQ to SQL ma ograniczoną obsługę `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="1dce2-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="1dce2-107">Podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="1dce2-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="1dce2-108">LINQ to SQL ma ograniczoną obsługę `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="1dce2-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="1dce2-109">Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1dce2-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dce2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dce2-110">See also</span></span>
- [<span data-ttu-id="1dce2-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="1dce2-111">Data Types and Functions</span></span>](data-types-and-functions.md)
