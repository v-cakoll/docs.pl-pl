---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bb6356ba4698cad00d443fdb80b1a45d35e2175
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="47b48-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="47b48-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="47b48-103">Można kontrolować możliwości automatycznego uruchamiania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hosta usługi (WcfSvcHost.exe) dla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu biblioteki usługi, podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierający wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="47b48-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="47b48-104">Aby to zrobić, kliknij prawym przyciskiem myszy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projekt usługi w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="47b48-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="47b48-105">Możesz usunąć zaznaczenie pola, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi dla tego konkretnego projektu nie jest uruchamiane podczas debugowania innego projektu w tym samym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="47b48-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="47b48-106">To zachowanie nie ma wpływu na debugowanie F5 lub funkcji Dodaj odwołanie do usługi dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="47b48-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="47b48-107">Ta opcja jest dostępna w następujących projektach:</span><span class="sxs-lookup"><span data-stu-id="47b48-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="47b48-108"> Projekt biblioteki usługi.</span><span class="sxs-lookup"><span data-stu-id="47b48-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="47b48-109">Projekt biblioteki usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="47b48-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="47b48-110">Projekt biblioteki usługi przepływu pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="47b48-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="47b48-111">Projekt biblioteki usługi zespolonego.</span><span class="sxs-lookup"><span data-stu-id="47b48-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b48-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47b48-112">See Also</span></span>  
 [<span data-ttu-id="47b48-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="47b48-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
