---
title: "Kanał buforowania, wysyłania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f8a11397fe161edad6f726c1d6df9ed09dad54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="3f004-102">Kanał buforowania, wysyłania</span><span class="sxs-lookup"><span data-stu-id="3f004-102">Channel Caching with Send</span></span>
<span data-ttu-id="3f004-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> , Użytkownicy mogą mieć różne poziomy buforowania, kanał <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendParametersContent> działań.</span><span class="sxs-lookup"><span data-stu-id="3f004-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="3f004-104">Buforowanie na poziomie wystąpienia jest domyślnie włączona i w tym przykładzie przedstawiono następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="3f004-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="3f004-105">Udział <xref:System.ServiceModel.Activities.SendMessageChannelCache> w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f004-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="3f004-106">Wyłącz buforowanie kanału.</span><span class="sxs-lookup"><span data-stu-id="3f004-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="3f004-107">Udział <xref:System.ServiceModel.Activities.SendMessageChannelCache> między wystąpienia przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3f004-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3f004-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="3f004-108">Demonstrates</span></span>  
 <span data-ttu-id="3f004-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache>rozszerzenie, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="3f004-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f004-110">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="3f004-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3f004-111">Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="3f004-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="3f004-112">Uruchom aplikację EchoWorkflowService wygenerowanych w \EchoWorkflowService\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="3f004-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="3f004-113">Uruchom aplikację EchoWorkflowClient wygenerowanych w .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="3f004-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="3f004-114">Klient wywołuje operację Echo usługi i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="3f004-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="3f004-115">Podczas drukowania wyników naciśnij klawisz ENTER, aby zamknąć klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="3f004-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3f004-116">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3f004-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f004-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3f004-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3f004-118">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="3f004-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f004-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3f004-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
