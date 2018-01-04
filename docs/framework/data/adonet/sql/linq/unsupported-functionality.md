---
title: "Nieobsługiwanych funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-functionality"></a><span data-ttu-id="5335f-102">Nieobsługiwanych funkcji</span><span class="sxs-lookup"><span data-stu-id="5335f-102">Unsupported Functionality</span></span>
<span data-ttu-id="5335f-103">W składniku LINQ to SQL nie są dostępne następujące funkcje SQL tłumaczenia istniejące środowisko uruchomieniowe języka wspólnego (CLR) i tworzy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5335f-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="5335f-104">Mimo że `LIKE` nie jest obsługiwana przez bezpośrednie tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="5335f-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="5335f-105">Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5335f-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="5335f-106">LINQ do SQL ma ograniczoną obsługę `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="5335f-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="5335f-107">Istnieje podobne funkcje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.</span><span class="sxs-lookup"><span data-stu-id="5335f-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="5335f-108">LINQ do SQL ma ograniczoną obsługę `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="5335f-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="5335f-109">Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5335f-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5335f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5335f-110">See Also</span></span>  
 [<span data-ttu-id="5335f-111">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="5335f-111">Data Types and Functions</span></span>](data-types-and-functions.md)
