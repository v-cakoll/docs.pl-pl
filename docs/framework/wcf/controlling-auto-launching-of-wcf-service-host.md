---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="bfb4e-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="bfb4e-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="bfb4e-103">Podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierający wiele projektów, można kontrolować możliwość automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) dla projektu biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="bfb4e-104">Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="bfb4e-105">Dlatego, że Host usługi WCF dla tego konkretnego projektu nie jest uruchamiane podczas debugowania innego projektu w tym samym rozwiązaniu można wyczyść to pole.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="bfb4e-106">To zachowanie nie ma wpływu na debugowanie F5 lub funkcji Dodaj odwołanie do usługi dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="bfb4e-107">Ta opcja jest dostępna w następujących projektach:</span><span class="sxs-lookup"><span data-stu-id="bfb4e-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="bfb4e-108">Projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="bfb4e-109">Projekt biblioteki usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="bfb4e-110">Projekt biblioteki usługi przepływu pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="bfb4e-111">Projekt biblioteki usługi zespolonego.</span><span class="sxs-lookup"><span data-stu-id="bfb4e-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb4e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfb4e-112">See Also</span></span>  
 [<span data-ttu-id="bfb4e-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="bfb4e-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
