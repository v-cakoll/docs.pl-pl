---
title: Program rozpoznawania zakładek dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 48053ec7882b2e742b61fdc293b6bc5f8a129ca5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490585"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="2bf16-102">Program rozpoznawania zakładek dla WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="2bf16-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="2bf16-103">W tym przykładzie przedstawiono sposób, w jaki <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> do utworzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf16-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2bf16-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="2bf16-104">Demonstrates</span></span>  
 <span data-ttu-id="2bf16-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="2bf16-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2bf16-106">Dyskusja</span><span class="sxs-lookup"><span data-stu-id="2bf16-106">Discussion</span></span>  
 <span data-ttu-id="2bf16-107">W tym przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> do utworzenia wystąpienia przepływu pracy, hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2bf16-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="2bf16-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> jest punktem rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> mogą służyć w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="2bf16-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="2bf16-109">Tworzenie nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf16-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="2bf16-110">Wznowienie zakładki w wystąpieniu przepływu pracy hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2bf16-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="2bf16-111">Punkt końcowy przykład, który jest dołączony udostępnia kontraktu, który zawiera operacje, aby utworzyć przepływ pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie z określonym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="2bf16-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="2bf16-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia przy użyciu definicji przepływu pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="2bf16-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="2bf16-113">Następnie wywołuje `Create` operacji w punkcie końcowym, aby utworzyć nowe wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf16-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2bf16-114">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2bf16-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2bf16-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="2bf16-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="2bf16-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2bf16-116">Run the application.</span></span> <span data-ttu-id="2bf16-117">`CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy tworzone jest wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf16-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="2bf16-118">Komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2bf16-118">The message "Hello World!"</span></span> <span data-ttu-id="2bf16-119">jest drukowany przez wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bf16-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bf16-120">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2bf16-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bf16-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2bf16-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2bf16-122">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2bf16-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bf16-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2bf16-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
