---
title: Przykład punktu końcowego zarządzania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 3d99cbef20895381f5e40ee939e1d94a409f1391
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078397"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="4e0eb-102">Przykład punktu końcowego zarządzania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4e0eb-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="4e0eb-103">Niniejszy przykład pokazuje, jak punkt końcowy kontroli przepływu pracy może służyć do tworzenia i uruchamiania przepływów pracy, lokalnie i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="4e0eb-104">W przykładzie pokazano sposób hostowania punkt końcowy kontroli i zapisać klientów, które wywołują punkt końcowy kontroli, aby utworzyć i uruchomić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="4e0eb-105">Przepływ pracy nie jest usługą.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="4e0eb-106">Po stronie usługi próbki przepływ pracy znajduje się za pomocą elementu WorkflowServiceHost i WorkflowControlEndpoint jest dodawany, dzięki czemu klienci mogą wykonywać operacje kontroli (Wstrzymaj, Start itp.).</span><span class="sxs-lookup"><span data-stu-id="4e0eb-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="4e0eb-107">CreationEndpoint zdefiniowanych przez użytkownika jest także dodawane do Zezwalaj na przepływ pracy, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="4e0eb-108">Usługa następnie używa tych punktów końcowych, aby uruchomić przepływ pracy w stanie wstrzymania i wznowienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="4e0eb-109">Klient wykonuje te same operacje, ale z poziomu kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="4e0eb-110">Aby dowiedzieć się więcej o tych interfejsów, zobacz [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) i [instrukcje: hostowanie przepływu pracy bez usługi w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="4e0eb-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="4e0eb-111">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4e0eb-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="4e0eb-112">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="4e0eb-113">Otwórz rozwiązanie ManagementEndpoint.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e0eb-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="4e0eb-114">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="4e0eb-115">Uruchom aplikację ManagementEndpoint.exe.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="4e0eb-116">Uruchom aplikację Client.exe.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4e0eb-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4e0eb-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4e0eb-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4e0eb-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e0eb-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4e0eb-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`