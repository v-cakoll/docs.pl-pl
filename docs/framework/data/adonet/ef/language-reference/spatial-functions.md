---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319301"
---
# <a name="spatial-functions"></a><span data-ttu-id="7c877-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="7c877-102">Spatial Functions</span></span>
<span data-ttu-id="7c877-103">Nie ma formatu literału dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="7c877-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="7c877-104">Można jednak używać kanonicznych funkcji Entity Framework, które są wywoływane za pomocą ciągów w formacie dobrze znanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="7c877-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="7c877-105">Na przykład następujące wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="7c877-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="7c877-106">Metody <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> mają wszystkie jednoEntity Frameworkowe metody kanoniczne.</span><span class="sxs-lookup"><span data-stu-id="7c877-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="7c877-107">Kliknij metodę zainteresowania, aby zobaczyć, jakie parametry mają być przenoszone do funkcji.</span><span class="sxs-lookup"><span data-stu-id="7c877-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
