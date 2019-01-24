---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527084"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="37f8e-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="37f8e-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="37f8e-103">Windows Communication Foundation (WCF) jest zależna od kilka zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="37f8e-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="37f8e-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="37f8e-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="37f8e-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="37f8e-105">Resource</span></span>|<span data-ttu-id="37f8e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="37f8e-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="37f8e-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="37f8e-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="37f8e-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="37f8e-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="37f8e-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="37f8e-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="37f8e-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37f8e-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="37f8e-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="37f8e-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="37f8e-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37f8e-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37f8e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37f8e-113">See also</span></span>
- [<span data-ttu-id="37f8e-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="37f8e-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
