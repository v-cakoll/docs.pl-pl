---
title: "Przepływ pracy zarządzania punktu końcowego próbki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d13d1d2af449631f93dd4df29ff41113ffbbfec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="45095-102">Przepływ pracy zarządzania punktu końcowego próbki</span><span class="sxs-lookup"><span data-stu-id="45095-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="45095-103">W tym przykładzie pokazano, jak punkt końcowy kontroli przepływu pracy może służyć do tworzenia i uruchamiania przepływów pracy, zarówno lokalnie, jak i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="45095-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="45095-104">Przykład pokazuje, jak hosta kontrolnego punktu końcowego i zapisu klientów, które wywołują kontrolnego punktu końcowego, aby utworzyć i uruchomić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="45095-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="45095-105">Przepływ pracy nie jest usługą.</span><span class="sxs-lookup"><span data-stu-id="45095-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="45095-106">Po stronie usługi próbki przepływu pracy jest obsługiwana przy użyciu klasy WorkflowServiceHost i obiektu WorkflowControlEndpoint zostanie dodany, dzięki czemu klienci mogą wykonywać operacje kontroli (Wstrzymaj, Start itp.).</span><span class="sxs-lookup"><span data-stu-id="45095-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="45095-107">CreationEndpoint zdefiniowane przez użytkownika jest także dodawane do Zezwalaj przepływu pracy, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="45095-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="45095-108">Usługa następnie używa tych punktów końcowych w celu uruchomienia przepływu pracy w stanie wstrzymania i wznowienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="45095-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="45095-109">Klient wykonuje te same operacje, ale z kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="45095-109">The client performs the same operations but from the client code.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="45095-110">Zobacz te interfejsy, [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) i [porady: hosta z systemem innym niż usługi przepływu pracy w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="45095-110"> these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="45095-111">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="45095-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="45095-112">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="45095-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="45095-113">Otwórz rozwiązanie ManagementEndpoint.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45095-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="45095-114">Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="45095-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="45095-115">Uruchom aplikację ManagementEndpoint.exe.</span><span class="sxs-lookup"><span data-stu-id="45095-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="45095-116">Uruchom aplikację Client.exe.</span><span class="sxs-lookup"><span data-stu-id="45095-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45095-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="45095-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="45095-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="45095-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45095-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="45095-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45095-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="45095-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`  
  
## <a name="see-also"></a><span data-ttu-id="45095-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45095-121">See Also</span></span>
