---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652091"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="8359d-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="8359d-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="8359d-103">Podczas debugowania innego projektu w tym samym rozwiązaniu Visual Studio zawierającą wiele projektów, można kontrolować możliwości automatycznego uruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost.exe) w projekcie biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8359d-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="8359d-104">Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksploratora rozwiązań**, wybierz **właściwości**i kliknij przycisk **opcje WCF** kartę. **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF** pole wyboru jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="8359d-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="8359d-105">Można wyczyść pole, tak aby Host usługi WCF dla tego określonego projektu nie jest uruchamiane, gdy inny projekt jest debugowany, w tym samym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="8359d-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="8359d-106">To zachowanie nie ma wpływu na debugowanie F5 lub funkcje Dodaj odwołanie do usługi dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="8359d-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="8359d-107">Ta opcja jest dostępna w następujących projektach:</span><span class="sxs-lookup"><span data-stu-id="8359d-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="8359d-108">Projekt biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8359d-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="8359d-109">Projekt Biblioteka usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8359d-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="8359d-110">Projekt biblioteki usługi przepływu pracy automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="8359d-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="8359d-111">Projekt Biblioteka usługi syndykacji.</span><span class="sxs-lookup"><span data-stu-id="8359d-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8359d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8359d-112">See also</span></span>

- [<span data-ttu-id="8359d-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="8359d-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
