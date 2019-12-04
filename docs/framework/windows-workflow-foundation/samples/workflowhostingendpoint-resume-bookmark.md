---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3b3c7d40a70e797960837c82e2f5a08b2814e17f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710965"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="c12a8-102">Wznowienie zakładki WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="c12a8-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="c12a8-103">W tym przykładzie pokazano, jak można użyć <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do tworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c12a8-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c12a8-104">Przedstawia</span><span class="sxs-lookup"><span data-stu-id="c12a8-104">Demonstrates</span></span>  
 <span data-ttu-id="c12a8-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="c12a8-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c12a8-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="c12a8-106">Discussion</span></span>  
 <span data-ttu-id="c12a8-107">W tym przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, aby utworzyć wystąpienie przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c12a8-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="c12a8-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost>, którego można użyć w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="c12a8-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="c12a8-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c12a8-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="c12a8-110">Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c12a8-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="c12a8-111">W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt zawierający operacje umożliwiające utworzenie przepływu pracy i zwrócenie identyfikatora wystąpienia lub utworzenie wystąpienia o określonym IDENTYFIKATORze.</span><span class="sxs-lookup"><span data-stu-id="c12a8-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="c12a8-112">Przykładowa aplikacja konsolowa tworzy wystąpienie <xref:System.ServiceModel.Activities.WorkflowServiceHost> z podstawową definicją przepływu pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="c12a8-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="c12a8-113">Następnie wywołuje operację `Create` w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c12a8-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c12a8-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="c12a8-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c12a8-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="c12a8-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="c12a8-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="c12a8-116">Run the application.</span></span> <span data-ttu-id="c12a8-117">W konsoli `CreationEndpoint` zostanie wyświetlony komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c12a8-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="c12a8-118">Komunikat "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="c12a8-118">The message "Hello World!"</span></span> <span data-ttu-id="c12a8-119">jest drukowany przez przepływ pracy w przypadku pomyślnego wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="c12a8-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c12a8-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c12a8-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c12a8-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="c12a8-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c12a8-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c12a8-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c12a8-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c12a8-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
