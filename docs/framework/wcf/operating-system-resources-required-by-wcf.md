---
title: "Zasoby systemu operacyjnego wymagane przez architekturę WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fde00011a7fffde4c4c75f9605758971b42627f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="f788b-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="f788b-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="f788b-103">zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="f788b-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="f788b-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="f788b-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="f788b-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="f788b-105">Resource</span></span>|<span data-ttu-id="f788b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f788b-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f788b-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="f788b-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="f788b-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="f788b-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="f788b-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="f788b-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="f788b-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f788b-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="f788b-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="f788b-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="f788b-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f788b-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f788b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f788b-113">See Also</span></span>  
 [<span data-ttu-id="f788b-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="f788b-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
