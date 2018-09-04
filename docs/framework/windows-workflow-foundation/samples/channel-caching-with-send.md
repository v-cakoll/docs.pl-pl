---
title: Buforowanie kanału z wysyłaniem
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503818"
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="a9e9f-102">Buforowanie kanału z wysyłaniem</span><span class="sxs-lookup"><span data-stu-id="a9e9f-102">Channel Caching with Send</span></span>
<span data-ttu-id="a9e9f-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Użytkownicy mogą mieć różne poziomy buforowania kanału <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendParametersContent> działań.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="a9e9f-104">Buforowanie poziomie wystąpienia jest domyślnie włączona, a w tym przykładzie przedstawiono następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a9e9f-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="a9e9f-105">Udostępnij <xref:System.ServiceModel.Activities.SendMessageChannelCache> w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="a9e9f-106">Wyłącz buforowanie kanału.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="a9e9f-107">Udostępnij <xref:System.ServiceModel.Activities.SendMessageChannelCache> wśród wystąpień przepływu pracy w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a9e9f-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="a9e9f-108">Demonstrates</span></span>  
 <span data-ttu-id="a9e9f-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> rozszerzenie <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> i <xref:System.ServiceModel.Activities.SendReply> działań.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9e9f-110">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a9e9f-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a9e9f-111">Załaduj projekt rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="a9e9f-112">Uruchom aplikację EchoWorkflowService wygenerowane w \EchoWorkflowService\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="a9e9f-113">Uruchom aplikację EchoWorkflowClient wygenerowane w .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="a9e9f-114">Klient wywołuje działanie usługi Echo i drukuje wyniki.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="a9e9f-115">Podczas drukowania wyniki naciśnij klawisz ENTER, aby zamknąć klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9e9f-116">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9e9f-117">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a9e9f-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9e9f-118">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9e9f-119">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a9e9f-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
