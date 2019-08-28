---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 83065a0034303dcbc83f846ba455f71e954fdb54
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037764"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="464e5-102">Wznowienie zakładki WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="464e5-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="464e5-103">W tym przykładzie pokazano, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jak można użyć programu <xref:System.ServiceModel.Activities.WorkflowServiceHost> z programem w celu utworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="464e5-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="464e5-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="464e5-104">Demonstrates</span></span>  
 <span data-ttu-id="464e5-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="464e5-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="464e5-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="464e5-106">Discussion</span></span>  
 <span data-ttu-id="464e5-107">W <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> tym przykładzie użyto do utworzenia wystąpienia przepływu pracy hostowanego <xref:System.ServiceModel.Activities.WorkflowServiceHost>za pomocą.</span><span class="sxs-lookup"><span data-stu-id="464e5-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="464e5-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem <xref:System.ServiceModel.Activities.WorkflowServiceHost> rozszerzalności, który może być używany w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="464e5-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="464e5-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="464e5-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="464e5-110">Wznawianie zakładek w wystąpieniu przepływu pracy hostowanym w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="464e5-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="464e5-111">W dołączonym przykładowym punkcie końcowym jest udostępniany kontrakt zawierający operacje umożliwiające utworzenie przepływu pracy i zwrócenie identyfikatora wystąpienia lub utworzenie wystąpienia o określonym IDENTYFIKATORze.</span><span class="sxs-lookup"><span data-stu-id="464e5-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="464e5-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienie z podstawową definicją przepływu pracy i `CreationEndpoint` dodaje do hosta.</span><span class="sxs-lookup"><span data-stu-id="464e5-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="464e5-113">Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="464e5-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="464e5-114">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="464e5-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="464e5-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="464e5-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="464e5-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="464e5-116">Run the application.</span></span> <span data-ttu-id="464e5-117">W `CreationEndpoint` konsoli programu jest wyświetlany komunikat z identyfikatorem wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="464e5-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="464e5-118">Komunikat "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="464e5-118">The message "Hello World!"</span></span> <span data-ttu-id="464e5-119">jest drukowany przez przepływ pracy w przypadku pomyślnego wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="464e5-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="464e5-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="464e5-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="464e5-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="464e5-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="464e5-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="464e5-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="464e5-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="464e5-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
