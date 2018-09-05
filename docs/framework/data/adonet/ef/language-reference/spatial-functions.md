---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559520"
---
# <a name="spatial-functions"></a><span data-ttu-id="26877-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="26877-102">Spatial Functions</span></span>
<span data-ttu-id="26877-103">Istnieje nie literału format dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="26877-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="26877-104">Można jednak użyć wywołać za pomocą ciągów w formacie tekstowym dobrze znane funkcje canonical Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="26877-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="26877-105">Na przykład poniższe wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="26877-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="26877-106">[Metody SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) strona zawiera listę wszystkich metod programu Entity Framework canonical przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="26877-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="26877-107">Kliknij metodę, aby wyświetlić parametry powinien zostać przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="26877-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
