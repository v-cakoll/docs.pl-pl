---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100954"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="c8f70-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="c8f70-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="c8f70-103">Windows Communication Foundation (WCF) jest zależna od kilka zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="c8f70-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="c8f70-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="c8f70-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="c8f70-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="c8f70-105">Resource</span></span>|<span data-ttu-id="c8f70-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c8f70-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c8f70-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="c8f70-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="c8f70-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="c8f70-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="c8f70-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="c8f70-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="c8f70-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f70-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="c8f70-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="c8f70-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="c8f70-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8f70-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8f70-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8f70-113">See also</span></span>

- [<span data-ttu-id="c8f70-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="c8f70-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
