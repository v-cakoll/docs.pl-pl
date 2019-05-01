---
title: Nieobsługiwana funkcja
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917561"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="74b3f-102">Nieobsługiwana funkcja</span><span class="sxs-lookup"><span data-stu-id="74b3f-102">Unsupported Functionality</span></span>
<span data-ttu-id="74b3f-103">W składniku LINQ to SQL tłumaczenie istniejące środowisko uruchomieniowe języka wspólnego (CLR) nie są dostępne następujące funkcje programu SQL i .NET Framework tworzy:</span><span class="sxs-lookup"><span data-stu-id="74b3f-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="74b3f-104">Mimo że `LIKE` nie jest obsługiwany za pośrednictwem bezpośredniego tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="74b3f-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="74b3f-105">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74b3f-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="74b3f-106">LINQ to SQL ma ograniczoną obsługę `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="74b3f-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="74b3f-107">Podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="74b3f-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="74b3f-108">LINQ to SQL ma ograniczoną obsługę `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="74b3f-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="74b3f-109">Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="74b3f-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b3f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74b3f-110">See also</span></span>

- [<span data-ttu-id="74b3f-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="74b3f-111">Data Types and Functions</span></span>](data-types-and-functions.md)
