---
title: "Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a80362f8cb7dce2853472b7f03c3586e33b8578
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="1f0c3-102">Dodawanie odwołania do usługi w rozwiązaniu usprawniającym przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="1f0c3-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="1f0c3-103">Dodawanie odwołania do usługi w aplikacji przepływ pracy działa w sposób nieco inaczej niż regularne aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="1f0c3-104">Po wybraniu Dodaj odwołanie do usługi i podaj adres URL do usługi metadanych jest pobierany i działań niestandardowych są generowane, które umożliwią wywoływanie usługi WCF lub usługi przepływu pracy WCF dodać odwołanie do.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="1f0c3-105">Po dodaniu odwołania do usługi, należy ponownie skompiluj rozwiązanie, więc wygenerowanego działania są tworzone.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="1f0c3-106">Pojawi się one w przyborniku projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="1f0c3-107">Należy jednak pamiętać, że działa tylko w przypadku dodawania odwołania do usługi w ramach rozwiązania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="1f0c3-108">Następujące rzutowania web przedstawiono sposób dodawania odwołania do usługi w innych typów projektów: [wywoływania usługi WCF z przepływu pracy w projekcie sieci Web](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="1f0c3-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="1f0c3-109">Dodawanie dwóch lub więcej odwołań do usługi do usług, które zawierają taką samą nazwę operacji spowoduje, że problem.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="1f0c3-110">Wygenerowany działania wywoła tylko pierwszej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="1f0c3-111">Aby obejść ten problem zmiany nazwy operacji usługi różnią się od siebie lub zmień nazwę konfiguracji punktu końcowego w każdym działaniu wygenerowanego.</span><span class="sxs-lookup"><span data-stu-id="1f0c3-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0c3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f0c3-112">See Also</span></span>  
 [<span data-ttu-id="1f0c3-113">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1f0c3-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="1f0c3-114">Porady: Tworzenie usługi przepływu pracy wywołującej inną usługę przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1f0c3-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="1f0c3-115">Wywołanie usługi WCF z przepływu pracy w projekcie sieci Web</span><span class="sxs-lookup"><span data-stu-id="1f0c3-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
