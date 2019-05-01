---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916399"
---
# <a name="instances"></a><span data-ttu-id="f64d2-102">Wystąpienia</span><span class="sxs-lookup"><span data-stu-id="f64d2-102">Instances</span></span>
<span data-ttu-id="f64d2-103">Nazwa komputera: wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f64d2-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f64d2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f64d2-104">Description</span></span>  
 <span data-ttu-id="f64d2-105">Liczba kontekstów wystąpienia, które zawiera obecnie usługi.</span><span class="sxs-lookup"><span data-stu-id="f64d2-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="f64d2-106">W większości przypadków, liczbę kontekstów wystąpienia jest taka sama jak liczba wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f64d2-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="f64d2-107">Jednak poniższe scenariusze są wyjątkiem od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="f64d2-107">However, the following scenarios are exception to this rule.</span></span>  
  
- <span data-ttu-id="f64d2-108">Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.</span><span class="sxs-lookup"><span data-stu-id="f64d2-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
- <span data-ttu-id="f64d2-109">A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f64d2-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64d2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f64d2-110">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
