---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712395"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="7e471-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="7e471-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="7e471-103">Podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierającą wiele projektów, można kontrolować możliwości automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) w projekcie biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7e471-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="7e471-104">Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="7e471-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="7e471-105">Można wyczyść pole, tak aby Host usługi WCF dla tego określonego projektu nie jest uruchamiane, gdy inny projekt jest debugowany, w tym samym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="7e471-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="7e471-106">To zachowanie nie ma wpływu na debugowanie F5 lub funkcje Dodaj odwołanie do usługi dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="7e471-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="7e471-107">Ta opcja jest dostępna w następujących projektach:</span><span class="sxs-lookup"><span data-stu-id="7e471-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="7e471-108">Projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="7e471-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="7e471-109">Projekt Biblioteka usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7e471-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="7e471-110">Projekt biblioteki usługi przepływu pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="7e471-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="7e471-111">Projekt Biblioteka usługi syndykacji.</span><span class="sxs-lookup"><span data-stu-id="7e471-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e471-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e471-112">See also</span></span>
- [<span data-ttu-id="7e471-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7e471-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
