---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 99371cc64ca2790bec383b4ab5dca280d4bb9659
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716763"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="80446-102">Program rozpoznawania zakładek dla WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="80446-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="80446-103">W tym przykładzie pokazano, jak można użyć <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do tworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="80446-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="80446-104">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="80446-104">Demonstrates</span></span>  
 <span data-ttu-id="80446-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="80446-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="80446-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="80446-106">Discussion</span></span>  
 <span data-ttu-id="80446-107">Ten przykład używa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do tworzenia wystąpień przepływu pracy hostowanych przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="80446-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="80446-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost>, którego można użyć w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="80446-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="80446-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="80446-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="80446-110">Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="80446-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="80446-111">W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt, który zapewnia operacje tworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym IDENTYFIKATORze.</span><span class="sxs-lookup"><span data-stu-id="80446-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="80446-112">Przykładowa aplikacja konsolowa tworzy wystąpienie <xref:System.ServiceModel.Activities.WorkflowServiceHost> z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="80446-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="80446-113">Następnie wywołuje operację `Create` w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="80446-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80446-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="80446-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="80446-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="80446-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="80446-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="80446-116">Run the application.</span></span> <span data-ttu-id="80446-117">W konsoli `CreationEndpoint` zostanie wyświetlony komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="80446-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="80446-118">Komunikat "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="80446-118">The message "Hello World!"</span></span> <span data-ttu-id="80446-119">jest drukowana przez wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="80446-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="80446-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="80446-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80446-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="80446-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="80446-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80446-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80446-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="80446-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
