---
title: "Wznów WorkflowHostingEndpoint zakładki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1179d09d68d8730847776cf98e3996e3e6817753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="2420d-102">Wznów WorkflowHostingEndpoint zakładki</span><span class="sxs-lookup"><span data-stu-id="2420d-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="2420d-103">W przykładzie pokazano, jak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> mogą być używane z <xref:System.ServiceModel.Activities.WorkflowServiceHost> można utworzyć wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2420d-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2420d-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="2420d-104">Demonstrates</span></span>  
 <span data-ttu-id="2420d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="2420d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2420d-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="2420d-106">Discussion</span></span>  
 <span data-ttu-id="2420d-107">W przykładzie użyto <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> można utworzyć wystąpienia przepływu pracy hostowane przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2420d-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="2420d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>punkt rozszerzalności dla <xref:System.ServiceModel.Activities.WorkflowServiceHost> które mogą być używane w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="2420d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="2420d-109">Tworzenie nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2420d-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="2420d-110">Wznawianie zakładki w wystąpieniu przepływu pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2420d-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="2420d-111">Punkt końcowy próbki, który znajduje się przedstawia kontraktu, który udostępnia operacje, aby utworzyć przepływ pracy i zwracać identyfikator wystąpienia lub można utworzyć wystąpienia o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="2420d-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="2420d-112">Przykładowa aplikacja konsolowa tworzy <xref:System.ServiceModel.Activities.WorkflowServiceHost> wystąpienia z definicją podstawowy przepływ pracy i dodaje `CreationEndpoint` do hosta.</span><span class="sxs-lookup"><span data-stu-id="2420d-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="2420d-113">Następnie wywołuje `Create` operacji na punkt końcowy do utworzenia nowego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2420d-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2420d-114">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2420d-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2420d-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="2420d-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="2420d-116">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="2420d-116">Run the application.</span></span> <span data-ttu-id="2420d-117">`CreationEndpoint` Konsoli Pokazuje komunikat, który zawiera identyfikator wystąpienia, gdy jest tworzone wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2420d-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="2420d-118">Komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2420d-118">The message "Hello World!"</span></span> <span data-ttu-id="2420d-119">jest drukowany przez przepływ pracy na pomyślne wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="2420d-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2420d-120">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2420d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2420d-121">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2420d-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2420d-122">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2420d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2420d-123">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2420d-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
