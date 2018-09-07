---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061692"
---
# <a name="spatial-functions"></a><span data-ttu-id="eeac8-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="eeac8-102">Spatial Functions</span></span>
<span data-ttu-id="eeac8-103">Istnieje nie literału format dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="eeac8-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="eeac8-104">Można jednak użyć wywołać za pomocą ciągów w formacie tekstowym dobrze znane funkcje canonical Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="eeac8-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="eeac8-105">Na przykład poniższe wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="eeac8-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="eeac8-106">[Metody SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) strona zawiera listę wszystkich metod programu Entity Framework canonical przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="eeac8-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="eeac8-107">Kliknij metodę, aby wyświetlić parametry powinien zostać przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="eeac8-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
