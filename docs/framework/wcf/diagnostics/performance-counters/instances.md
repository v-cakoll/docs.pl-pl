---
title: "Wystąpienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="4fed2-102">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="4fed2-102">Instances</span></span>
<span data-ttu-id="4fed2-103">Nazwa licznika: wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4fed2-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4fed2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="4fed2-104">Description</span></span>  
 <span data-ttu-id="4fed2-105">Liczba kontekstów wystąpienia, które zawiera obecnie usługi.</span><span class="sxs-lookup"><span data-stu-id="4fed2-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="4fed2-106">W większości przypadków, liczba konteksty wystąpienia jest taka sama jak liczba wystąpień.</span><span class="sxs-lookup"><span data-stu-id="4fed2-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="4fed2-107">Jednak poniższe scenariusze są wyjątkiem od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="4fed2-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="4fed2-108">Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.</span><span class="sxs-lookup"><span data-stu-id="4fed2-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="4fed2-109">A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4fed2-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fed2-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fed2-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
