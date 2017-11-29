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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="4e094-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="4e094-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="4e094-103">zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="4e094-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="4e094-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="4e094-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="4e094-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="4e094-105">Resource</span></span>|<span data-ttu-id="4e094-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4e094-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="4e094-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="4e094-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="4e094-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="4e094-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="4e094-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="4e094-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="4e094-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e094-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="4e094-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="4e094-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="4e094-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e094-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e094-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e094-113">See Also</span></span>  
 [<span data-ttu-id="4e094-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="4e094-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
