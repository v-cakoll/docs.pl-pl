---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318946"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="b9dec-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="b9dec-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="b9dec-103">Windows Communication Foundation (WCF) zależy od kilku zasobów dostarczonych przez system operacyjny do działania.</span><span class="sxs-lookup"><span data-stu-id="b9dec-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="b9dec-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="b9dec-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="b9dec-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="b9dec-105">Resource</span></span>|<span data-ttu-id="b9dec-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b9dec-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b9dec-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="b9dec-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="b9dec-108">Wymagane do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="b9dec-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="b9dec-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="b9dec-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="b9dec-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9dec-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="b9dec-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="b9dec-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="b9dec-112">Wymagane, jeśli chcesz używać aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9dec-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9dec-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9dec-113">See also</span></span>

- [<span data-ttu-id="b9dec-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="b9dec-114">System Requirements</span></span>](wcf-system-requirements.md)
