---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: e5a8adc73ba08007802eeb3b66de27098c688d84
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044327"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="7b47b-102">Program rozpoznawania zakładek dla WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="7b47b-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="7b47b-103">W tym przykładzie pokazano, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak można użyć programu <xref:System.ServiceModel.Activities.WorkflowServiceHost> z programem w celu utworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b47b-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7b47b-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="7b47b-104">Demonstrates</span></span>  
 <span data-ttu-id="7b47b-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="7b47b-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7b47b-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="7b47b-106">Discussion</span></span>  
 <span data-ttu-id="7b47b-107">Ten przykład używa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do tworzenia wystąpień przepływu pracy hostowanych <xref:System.ServiceModel.Activities.WorkflowServiceHost>za pomocą.</span><span class="sxs-lookup"><span data-stu-id="7b47b-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="7b47b-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozszerzalności, który może być używany w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="7b47b-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="7b47b-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b47b-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="7b47b-110">Wznawianie zakładek w wystąpieniu przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanym w.</span><span class="sxs-lookup"><span data-stu-id="7b47b-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="7b47b-111">W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt, który zapewnia operacje tworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym IDENTYFIKATORze.</span><span class="sxs-lookup"><span data-stu-id="7b47b-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="7b47b-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienie z definicją przepływu pracy i `CreationEndpoint` dodaje do hosta.</span><span class="sxs-lookup"><span data-stu-id="7b47b-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="7b47b-113">Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b47b-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b47b-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="7b47b-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7b47b-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="7b47b-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="7b47b-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="7b47b-116">Run the application.</span></span> <span data-ttu-id="7b47b-117">W `CreationEndpoint` konsoli programu jest wyświetlany komunikat z identyfikatorem wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b47b-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="7b47b-118">Komunikat "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="7b47b-118">The message "Hello World!"</span></span> <span data-ttu-id="7b47b-119">jest drukowana przez wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b47b-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b47b-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7b47b-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b47b-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="7b47b-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7b47b-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7b47b-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b47b-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7b47b-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
