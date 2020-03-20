---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: d393a26dd29624765e01b139e818de8a41f73e06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182740"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="0df6d-102">Wznowienie zakładki WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="0df6d-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="0df6d-103">W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pokazano, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jak można używać do tworzenia wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0df6d-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0df6d-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="0df6d-104">Demonstrates</span></span>  
 <span data-ttu-id="0df6d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="0df6d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0df6d-106">Dyskusji</span><span class="sxs-lookup"><span data-stu-id="0df6d-106">Discussion</span></span>  
 <span data-ttu-id="0df6d-107">W tym przykładzie <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> użyto do utworzenia <xref:System.ServiceModel.Activities.WorkflowServiceHost>wystąpienia przepływu pracy hostowanego przy użyciu programu .</span><span class="sxs-lookup"><span data-stu-id="0df6d-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="0df6d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>jest punktem rozszerzalności, który <xref:System.ServiceModel.Activities.WorkflowServiceHost> może być używany w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="0df6d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="0df6d-109">Tworzenie nowych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0df6d-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="0df6d-110">Wznowienie zakładek w wystąpieniu przepływu pracy hostowanym w pliku <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0df6d-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="0df6d-111">Przykładowy punkt końcowy, który jest uwzględniony udostępnia kontrakt, który udostępnia operacje, aby utworzyć przepływ pracy i zwrócić identyfikator wystąpienia lub utworzyć wystąpienie o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="0df6d-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="0df6d-112">Przykładowa aplikacja konsoli <xref:System.ServiceModel.Activities.WorkflowServiceHost> tworzy wystąpienie z podstawową `CreationEndpoint` definicją przepływu pracy i dodaje do hosta.</span><span class="sxs-lookup"><span data-stu-id="0df6d-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="0df6d-113">Następnie wywołuje `Create` operację w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0df6d-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0df6d-114">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="0df6d-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0df6d-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="0df6d-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="0df6d-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="0df6d-116">Run the application.</span></span> <span data-ttu-id="0df6d-117">Konsola `CreationEndpoint` wyświetla komunikat zawierający identyfikator wystąpienia podczas tworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0df6d-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="0df6d-118">Wiadomość "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="0df6d-118">The message "Hello World!"</span></span> <span data-ttu-id="0df6d-119">jest drukowany przez przepływ pracy po pomyślnym wznowieniu zakładki.</span><span class="sxs-lookup"><span data-stu-id="0df6d-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0df6d-120">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0df6d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0df6d-121">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="0df6d-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0df6d-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="0df6d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0df6d-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0df6d-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
