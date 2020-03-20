---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 113e6e52214d482dcd733bbd07ef2aab9f1b8c3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142813"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="5966d-102">Program rozpoznawania zakładek dla WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="5966d-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="5966d-103">W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pokazano, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jak można używać do tworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5966d-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5966d-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="5966d-104">Demonstrates</span></span>  
 <span data-ttu-id="5966d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="5966d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5966d-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="5966d-106">Discussion</span></span>  
 <span data-ttu-id="5966d-107">W tym przykładzie użyto do <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> utworzenia <xref:System.ServiceModel.Activities.WorkflowServiceHost>wystąpień przepływu pracy hostowanych przy użyciu programu .</span><span class="sxs-lookup"><span data-stu-id="5966d-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="5966d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem rozszerzalności, który <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być używany w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="5966d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="5966d-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5966d-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="5966d-110">Wznowienie zakładek w wystąpieniu przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanym w pliku .</span><span class="sxs-lookup"><span data-stu-id="5966d-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="5966d-111">Przykładowy punkt końcowy, który jest uwzględniony udostępnia kontrakt, który udostępnia operacje w celu utworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="5966d-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="5966d-112">Przykładowa aplikacja konsoli <xref:System.ServiceModel.Activities.WorkflowServiceHost> tworzy wystąpienie z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="5966d-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="5966d-113">Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5966d-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5966d-114">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="5966d-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5966d-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5966d-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="5966d-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5966d-116">Run the application.</span></span> <span data-ttu-id="5966d-117">Konsola `CreationEndpoint` wyświetla komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5966d-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="5966d-118">Wiadomość "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5966d-118">The message "Hello World!"</span></span> <span data-ttu-id="5966d-119">jest drukowany przez wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5966d-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5966d-120">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5966d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5966d-121">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="5966d-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5966d-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5966d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5966d-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5966d-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
