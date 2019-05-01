---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797699"
---
# <a name="spatial-functions"></a><span data-ttu-id="da96f-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="da96f-102">Spatial Functions</span></span>
<span data-ttu-id="da96f-103">Istnieje nie literału format dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="da96f-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="da96f-104">Można jednak użyć wywołać za pomocą ciągów w formacie tekstowym dobrze znane funkcje canonical Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="da96f-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="da96f-105">Na przykład poniższe wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="da96f-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="da96f-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> Metody mają przestrzenne canonical metod programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="da96f-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="da96f-107">Kliknij metodę, aby wyświetlić parametry powinien zostać przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="da96f-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
