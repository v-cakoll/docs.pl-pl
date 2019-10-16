---
title: Kontrolowanie automatycznego uruchamiania hosta programu WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320625"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="c8acf-102">Kontrolowanie automatycznego uruchamiania hosta programu WCF</span><span class="sxs-lookup"><span data-stu-id="c8acf-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="c8acf-103">Można kontrolować funkcję autouruchamiania hosta usługi Windows Communication Foundation (WCF) (WcfSvcHost. exe) dla projektu biblioteki usług WCF, podczas debugowania innego projektu w tym samym rozwiązaniu programu Visual Studio zawierającym wiele projektów.</span><span class="sxs-lookup"><span data-stu-id="c8acf-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="c8acf-104">Aby to zrobić, kliknij prawym przyciskiem myszy projekt usługi WCF w **Eksplorator rozwiązań**, wybierz polecenie **Właściwości**, a następnie kliknij kartę **Opcje WCF** . **Uruchom hosta usługi WCF podczas debugowania innego projektu w tym samym rozwiązaniu** pole wyboru jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c8acf-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="c8acf-105">Możesz wyczyścić to pole, aby Host usługi WCF dla danego projektu nie był uruchamiany, gdy inny projekt jest debugowany w tym samym rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c8acf-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="c8acf-106">To zachowanie nie ma wpływu na Debugowanie F5 ani Dodaj odwołanie do usługi funkcji dla tego projektu.</span><span class="sxs-lookup"><span data-stu-id="c8acf-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="c8acf-107">Ta opcja jest dostępna dla następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="c8acf-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="c8acf-108">Projekt biblioteki usług WCF.</span><span class="sxs-lookup"><span data-stu-id="c8acf-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="c8acf-109">Projekt biblioteki usługi sekwencyjnego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c8acf-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="c8acf-110">Projekt biblioteki usługi przepływu pracy automatu Stanów.</span><span class="sxs-lookup"><span data-stu-id="c8acf-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="c8acf-111">Projekt biblioteki usługi zespolonej.</span><span class="sxs-lookup"><span data-stu-id="c8acf-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8acf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8acf-112">See also</span></span>

- [<span data-ttu-id="c8acf-113">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="c8acf-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
