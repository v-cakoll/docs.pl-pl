---
title: "Uzyskiwanie dostępu do elementu OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="8c6b0-102">Uzyskiwanie dostępu do elementu OperationContext</span><span class="sxs-lookup"><span data-stu-id="8c6b0-102">Accessing OperationContext</span></span>
<span data-ttu-id="8c6b0-103">W tym przykładzie przedstawiono sposób działania dotyczące komunikatów (<xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.Send>) można użyć z działaniem niestandardowy zakres dostępu do <xref:System.ServiceModel.OperationContext.Current%2A> i dołączyć lub pobrać nagłówek niestandardowy komunikat w wiadomości wychodzące lub przychodzące.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8c6b0-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8c6b0-104">Demonstrates</span></span>  
 <span data-ttu-id="8c6b0-105">Działania, do obsługi komunikatów <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8c6b0-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="8c6b0-106">Discussion</span></span>  
 <span data-ttu-id="8c6b0-107">Ten przykład przedstawia sposób użycia punkty rozszerzeń (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) w działaniach obsługi dostępu do <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="8c6b0-108">Wywołania zwrotne są zarejestrowane w ramach środowiska uruchomieniowego przepływu pracy jako implementacja <xref:System.Activities.IExecutionProperty> która zostaje pobrana przez działania obsługi komunikatów na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="8c6b0-109">Wszystkie działania obsługi komunikatów w tym samym zakresie co <xref:System.Activities.IExecutionProperty> dotyczy implementacji.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="8c6b0-110">W szczególności w przykładzie użyto działania niestandardowy zakres, aby wymusić zachowanie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="8c6b0-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> Jest używana w przepływie pracy klienta do włączenia przepływu pracy <xref:System.Activities.WorkflowApplication.Id%2A> jako wychodzące <xref:System.ServiceModel.Channels.MessageHeader>.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="8c6b0-112">Ten nagłówek jest następnie pobrane przy użyciu usługi <xref:System.ServiceModel.Activities.IReceiveMessageCallback> i wartość nagłówka jest drukowany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8c6b0-113">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="8c6b0-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8c6b0-114">Ten przykład przedstawia usługi przepływu pracy przy użyciu punktów końcowych HTTP.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="8c6b0-115">Można dodać do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL (zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje), uruchamiając program Visual Studio jako Administrator lub, wykonując następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień, aby dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="8c6b0-116">Upewnij się, czy użytkownika domena i nazwa użytkownika są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="8c6b0-117">Po dodaniu listy ACL adresu URL, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="8c6b0-118">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="8c6b0-119">Ustawianie wielu projektów uruchamiania prawym przyciskiem myszy rozwiązanie i wybierając **Ustaw projekty startowe**.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="8c6b0-120">Dodaj **usługi** i **klienta** (w tej kolejności) jako wiele projektów rozruchu.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="8c6b0-121">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-121">Run the application.</span></span> <span data-ttu-id="8c6b0-122">W konsoli klienta zawiera przepływu pracy korzystającego z dwa razy i okno usługi zawiera identyfikator wystąpienia tych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8c6b0-123">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8c6b0-124">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8c6b0-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8c6b0-125">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8c6b0-126">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8c6b0-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
