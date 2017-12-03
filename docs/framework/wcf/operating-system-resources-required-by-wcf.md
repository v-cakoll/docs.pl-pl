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
ms.openlocfilehash: 31006331f5e8a71bf3f4fb9a68c31cb32d0b6f2b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="3daf9-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="3daf9-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="3daf9-103">zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="3daf9-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="3daf9-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="3daf9-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="3daf9-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="3daf9-105">Resource</span></span>|<span data-ttu-id="3daf9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3daf9-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3daf9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="3daf9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="3daf9-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="3daf9-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="3daf9-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="3daf9-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="3daf9-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3daf9-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="3daf9-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="3daf9-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="3daf9-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3daf9-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3daf9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3daf9-113">See Also</span></span>  
 [<span data-ttu-id="3daf9-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="3daf9-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
