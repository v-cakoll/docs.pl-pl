---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118992"
---
# <a name="instances"></a><span data-ttu-id="e3829-102">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="e3829-102">Instances</span></span>
<span data-ttu-id="e3829-103">Nazwa komputera: wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3829-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3829-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e3829-104">Description</span></span>  
 <span data-ttu-id="e3829-105">Liczba kontekstów wystąpienia, które zawiera obecnie usługi.</span><span class="sxs-lookup"><span data-stu-id="e3829-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="e3829-106">W większości przypadków, liczbę kontekstów wystąpienia jest taka sama jak liczba wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e3829-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="e3829-107">Jednak poniższe scenariusze są wyjątkiem od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="e3829-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="e3829-108">Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.</span><span class="sxs-lookup"><span data-stu-id="e3829-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="e3829-109">A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3829-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3829-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3829-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
