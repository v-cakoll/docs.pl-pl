---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202092"
---
# <a name="spatial-functions"></a><span data-ttu-id="531ee-102">Funkcje przestrzenne</span><span class="sxs-lookup"><span data-stu-id="531ee-102">Spatial Functions</span></span>
<span data-ttu-id="531ee-103">Istnieje nie literału format dla typów przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="531ee-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="531ee-104">Można jednak użyć wywołać za pomocą ciągów w formacie tekstowym dobrze znane funkcje canonical Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="531ee-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="531ee-105">Na przykład poniższe wywołanie funkcji tworzy punkt geometrii:</span><span class="sxs-lookup"><span data-stu-id="531ee-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="531ee-106">[Metody SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) strona zawiera listę wszystkich metod programu Entity Framework canonical przestrzennych.</span><span class="sxs-lookup"><span data-stu-id="531ee-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="531ee-107">Kliknij metodę, aby wyświetlić parametry powinien zostać przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="531ee-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
