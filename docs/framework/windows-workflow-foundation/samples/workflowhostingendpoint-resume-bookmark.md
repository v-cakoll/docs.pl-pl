---
title: Wznowienie zakładki WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 3c1a3421c87d18e695790cfb3a1f066600748ce9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619513"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="4d6f4-102">Wznowienie zakładki WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="4d6f4-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="4d6f4-103">W tym przykładzie przedstawiono sposób, w jaki <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do utworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4d6f4-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="4d6f4-104">Demonstrates</span></span>  
 <span data-ttu-id="4d6f4-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="4d6f4-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4d6f4-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="4d6f4-106">Discussion</span></span>  
 <span data-ttu-id="4d6f4-107">W tym przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy, hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="4d6f4-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> mogą służyć w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="4d6f4-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="4d6f4-109">Tworzenie nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="4d6f4-110">Wznowienie zakładki w wystąpieniu przepływu pracy hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="4d6f4-111">Punkt końcowy przykład, który jest dołączony udostępnia kontraktu, który zawiera operacje tworzenia przepływu pracy i zwracają Identyfikatora wystąpienia, aby utworzyć wystąpienie z określonym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="4d6f4-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia z definicją podstawowy przepływ pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="4d6f4-113">Następnie wywołuje `Create` operacji w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d6f4-114">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4d6f4-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4d6f4-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="4d6f4-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-116">Run the application.</span></span> <span data-ttu-id="4d6f4-117">`CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy tworzone jest wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="4d6f4-118">Komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4d6f4-118">The message "Hello World!"</span></span> <span data-ttu-id="4d6f4-119">jest drukowany przez przepływ pracy na pomyślne wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d6f4-120">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d6f4-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4d6f4-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d6f4-122">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d6f4-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d6f4-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
