---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498647"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="e3cc3-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="e3cc3-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="e3cc3-103">Windows Communication Foundation (WCF) zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji.</span><span class="sxs-lookup"><span data-stu-id="e3cc3-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="e3cc3-104">W poniższej tabeli wymieniono te zasoby.</span><span class="sxs-lookup"><span data-stu-id="e3cc3-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="e3cc3-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="e3cc3-105">Resource</span></span>|<span data-ttu-id="e3cc3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e3cc3-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e3cc3-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="e3cc3-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="e3cc3-108">Wymagany do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="e3cc3-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="e3cc3-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="e3cc3-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="e3cc3-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3cc3-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="e3cc3-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="e3cc3-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="e3cc3-112">Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3cc3-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3cc3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3cc3-113">See Also</span></span>  
 [<span data-ttu-id="e3cc3-114">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="e3cc3-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
