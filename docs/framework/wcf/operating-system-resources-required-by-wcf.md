---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100954"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="c7fd5-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="c7fd5-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="c7fd5-103">Windows Communication Foundation (WCF) jest zależna od kilka zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7fd5-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="c7fd5-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="c7fd5-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="c7fd5-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="c7fd5-105">Resource</span></span>|<span data-ttu-id="c7fd5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7fd5-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c7fd5-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="c7fd5-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="c7fd5-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="c7fd5-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="c7fd5-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="c7fd5-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="c7fd5-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7fd5-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="c7fd5-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="c7fd5-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="c7fd5-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7fd5-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7fd5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7fd5-113">See also</span></span>

- [<span data-ttu-id="c7fd5-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="c7fd5-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
