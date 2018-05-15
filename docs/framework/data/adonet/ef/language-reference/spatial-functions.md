---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7b78cbf4dc53ba1bc4148fa0077615e43cc8f9f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="spatial-functions"></a><span data-ttu-id="d3a76-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="d3a76-102">Spatial Functions</span></span>
<span data-ttu-id="d3a76-103">Brak ma literału formatu dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="d3a76-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="d3a76-104">Można jednak użyć kanonicznej funkcji programu Entity Framework wywołać przy użyciu ciągów w formacie Well-Known Text.</span><span class="sxs-lookup"><span data-stu-id="d3a76-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="d3a76-105">Na przykład następujące wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="d3a76-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="d3a76-106">[Metody SpatialEdmFunctions](http://msdn.microsoft.com/library/hh749531.aspx) strona zawiera listę przestrzennych canonical metody Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d3a76-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="d3a76-107">Kliknij metodę zainteresowań, aby zobaczyć, jakie parametry powinien zostać przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d3a76-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
