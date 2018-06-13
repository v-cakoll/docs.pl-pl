---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473045"
---
# <a name="instances"></a><span data-ttu-id="6380c-102">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="6380c-102">Instances</span></span>
<span data-ttu-id="6380c-103">Nazwa licznika: wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6380c-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6380c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6380c-104">Description</span></span>  
 <span data-ttu-id="6380c-105">Liczba kontekstów wystąpienia, które zawiera obecnie usługi.</span><span class="sxs-lookup"><span data-stu-id="6380c-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="6380c-106">W większości przypadków, liczba konteksty wystąpienia jest taka sama jak liczba wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6380c-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="6380c-107">Jednak poniższe scenariusze są wyjątkiem od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="6380c-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="6380c-108">Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.</span><span class="sxs-lookup"><span data-stu-id="6380c-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="6380c-109">A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6380c-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6380c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6380c-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
