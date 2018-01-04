---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="7d1f6-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="7d1f6-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="7d1f6-103">Można kontrolować możliwości automatycznego uruchamiania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hosta usługi (WcfSvcHost.exe) dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu biblioteki usługi, podczas debugowania innego projektu w tym samym [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] rozwiązanie zawierające wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="7d1f6-104">Aby to zrobić, kliknij prawym przyciskiem myszy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt usługi w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="7d1f6-105">Możesz usunąć zaznaczenie pola, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi dla tego konkretnego projektu nie jest uruchamiane podczas debugowania innego projektu w tym samym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="7d1f6-106">To zachowanie nie ma wpływu na debugowanie F5 lub funkcji Dodaj odwołanie do usługi dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="7d1f6-107">Ta opcja jest dostępna w następujących projektach:</span><span class="sxs-lookup"><span data-stu-id="7d1f6-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="7d1f6-108">Projekt biblioteki usługi.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="7d1f6-109">Projekt biblioteki usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="7d1f6-110">Projekt biblioteki usługi przepływu pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="7d1f6-111">Projekt biblioteki usługi zespolonego.</span><span class="sxs-lookup"><span data-stu-id="7d1f6-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1f6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d1f6-112">See Also</span></span>  
 [<span data-ttu-id="7d1f6-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7d1f6-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
