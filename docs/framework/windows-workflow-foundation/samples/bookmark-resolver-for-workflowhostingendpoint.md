---
title: Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: f8afb804525ecf36127e32441c92f43af70f5099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514947"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="b4fb3-102">Mechanizm rozpoznawania zakładki dla WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="b4fb3-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="b4fb3-103">W przykładzie pokazano, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> można utworzyć wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b4fb3-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="b4fb3-104">Demonstrates</span></span>  
 <span data-ttu-id="b4fb3-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="b4fb3-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b4fb3-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b4fb3-106">Discussion</span></span>  
 <span data-ttu-id="b4fb3-107">W przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b4fb3-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> punkt rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> które mogą być używane w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="b4fb3-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="b4fb3-109">Tworzenie nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="b4fb3-110">Wznawianie zakładki w wystąpieniu przepływu pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="b4fb3-111">Punkt końcowy próbki, który znajduje się przedstawia kontraktu, który udostępnia operacje w celu utworzenia przepływu pracy i zwraca identyfikator wystąpienia lub tworzy wystąpienie z określonym identyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="b4fb3-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia z definicją przepływu pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="b4fb3-113">Następnie wywołuje `Create` operacji na punkt końcowy do utworzenia nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b4fb3-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b4fb3-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b4fb3-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="b4fb3-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-116">Run the application.</span></span> <span data-ttu-id="b4fb3-117">`CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy jest tworzone wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="b4fb3-118">Komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="b4fb3-118">The message "Hello World!"</span></span> <span data-ttu-id="b4fb3-119">wydrukowaniu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4fb3-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b4fb3-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b4fb3-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b4fb3-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4fb3-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b4fb3-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
