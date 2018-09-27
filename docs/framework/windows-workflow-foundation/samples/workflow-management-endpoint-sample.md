---
title: Przykład punktu końcowego zarządzania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 398ace1c198f0db0268c44083ccc98c5ba2d2c7f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399128"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="d8e4e-102">Przykład punktu końcowego zarządzania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d8e4e-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="d8e4e-103">Niniejszy przykład pokazuje, jak punkt końcowy kontroli przepływu pracy może służyć do tworzenia i uruchamiania przepływów pracy, lokalnie i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="d8e4e-104">W przykładzie pokazano sposób hostowania punkt końcowy kontroli i zapisać klientów, które wywołują punkt końcowy kontroli, aby utworzyć i uruchomić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="d8e4e-105">Przepływ pracy nie jest usługą.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="d8e4e-106">Po stronie usługi próbki przepływ pracy znajduje się za pomocą elementu WorkflowServiceHost i WorkflowControlEndpoint jest dodawany, dzięki czemu klienci mogą wykonywać operacje kontroli (Wstrzymaj, Start itp.).</span><span class="sxs-lookup"><span data-stu-id="d8e4e-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="d8e4e-107">CreationEndpoint zdefiniowanych przez użytkownika jest także dodawane do Zezwalaj na przepływ pracy, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="d8e4e-108">Usługa następnie używa tych punktów końcowych, aby uruchomić przepływ pracy w stanie wstrzymania i wznowienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="d8e4e-109">Klient wykonuje te same operacje, ale z poziomu kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="d8e4e-110">Aby dowiedzieć się więcej o tych interfejsów, zobacz [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="d8e4e-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="d8e4e-111">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d8e4e-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="d8e4e-112">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="d8e4e-113">Otwórz rozwiązanie ManagementEndpoint.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8e4e-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="d8e4e-114">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="d8e4e-115">Uruchom aplikację ManagementEndpoint.exe.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="d8e4e-116">Uruchom aplikację Client.exe.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8e4e-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d8e4e-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d8e4e-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d8e4e-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8e4e-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d8e4e-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`