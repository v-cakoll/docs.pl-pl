---
title: Korelacja wymiany kontekstu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18f6501d2c5a97f7f267321e9cf0b06737afa5bd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="context-exchange-correlation"></a><span data-ttu-id="450d8-102">Korelacja wymiany kontekstu</span><span class="sxs-lookup"><span data-stu-id="450d8-102">Context Exchange Correlation</span></span>
<span data-ttu-id="450d8-103">Kontekst korelacji jest oparta na mechanizm wymiany kontekstu opisanego w [Specyfikacja protokół wymiany kontekstu .NET](http://go.microsoft.com/fwlink/?LinkId=166059).</span><span class="sxs-lookup"><span data-stu-id="450d8-103">Context correlation is based on the context exchange mechanism described in the [.NET Context Exchange Protocol Specification](http://go.microsoft.com/fwlink/?LinkId=166059).</span></span> <span data-ttu-id="450d8-104">Kontekst korelacji używa nagłówka kontekstu dobrze znanego lub plik cookie powiązać wiadomości na prawidłowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="450d8-104">Context correlation uses a well-known context header or cookie to relate messages to the correct instance.</span></span> <span data-ttu-id="450d8-105">Umożliwia korelacji kontekstu, na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, lub <xref:System.ServiceModel.NetTcpContextBinding> musi być używany w określony punkt końcowy do <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="450d8-105">To use context correlation, a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, or <xref:System.ServiceModel.NetTcpContextBinding> must be used on the endpoint provided to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="450d8-106">W tym temacie wyjaśniono, jak używać kontekstu korelacji z działaniami obsługi komunikatów w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="450d8-106">This topic explains how to use context correlation with messaging activities in a workflow service.</span></span>  
  
## <a name="using-context-correlation"></a><span data-ttu-id="450d8-107">Przy użyciu kontekstu korelacji</span><span class="sxs-lookup"><span data-stu-id="450d8-107">Using Context Correlation</span></span>  
 <span data-ttu-id="450d8-108">Korelacji kontekstu jest używana, gdy klient musi wywołań powtarzanego do usługi przepływu pracy i usługa jest obsługiwana przy użyciu jednej z kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="450d8-108">Context correlation is used when a client must make repeated calls into a workflow service and the service is hosted using one of the context bindings.</span></span> <span data-ttu-id="450d8-109">Ten typ korelacji jest inicjowany przez <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="450d8-109">This type of correlation is initialized by a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair in the workflow service.</span></span> <span data-ttu-id="450d8-110">Kontekst jest wysyłane do klienta wraz z odpowiedź, a następnie klient dołącza ten kontekst dla kolejnych wywołań do usługi.</span><span class="sxs-lookup"><span data-stu-id="450d8-110">The context is sent back to the client together with the reply, and then the client attaches this context on subsequent calls to the service.</span></span>  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a><span data-ttu-id="450d8-111">Konfigurowanie korelacji kontekstu w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="450d8-111">Configuring Context Correlation in a Workflow Service</span></span>  
 <span data-ttu-id="450d8-112">Kontekst korelacji została zainicjowana przy użyciu <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> skojarzony z <xref:System.ServiceModel.Activities.SendReply> działania, która odpowiada na komunikat przychodzący początkowej.</span><span class="sxs-lookup"><span data-stu-id="450d8-112">Context correlation is initialized by using a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> that is associated with the <xref:System.ServiceModel.Activities.SendReply> activity that replies to the initial incoming message.</span></span> <span data-ttu-id="450d8-113">W poniższym przykładzie <xref:System.ServiceModel.Activities.SendReply> jest skonfigurowany do inicjować korelację kontekstu.</span><span class="sxs-lookup"><span data-stu-id="450d8-113">In the following example, the <xref:System.ServiceModel.Activities.SendReply> is configured to initialize a context correlation.</span></span>  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  <span data-ttu-id="450d8-114">W tym przykładzie są faktycznie dwa rodzaje korelacji używany: kontekst korelacji i korelacja żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="450d8-114">In this example, there are actually two types of correlation being used: context correlation and request-reply correlation.</span></span> <span data-ttu-id="450d8-115">Korelacji kontekstu jest używana i połączeń od klientów są kierowane do prawidłowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="450d8-115">The context correlation is used so that calls from clients are routed to the correct instance.</span></span> <span data-ttu-id="450d8-116">Korelacja żądań i odpowiedzi jest używany przez <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań ze sobą w celu wykonania operacji dwukierunkowe formowane przez te działania.</span><span class="sxs-lookup"><span data-stu-id="450d8-116">The request-reply correlation is used by the <xref:System.ServiceModel.Activities.Receive> and the <xref:System.ServiceModel.Activities.SendReply> activities together to implement the two-way operation modeled by these activities.</span></span> <span data-ttu-id="450d8-117">W tym przykładzie tylko korelacji kontekstu jest jawnie skonfigurowany, a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary używa korelacja żądań i odpowiedzi domyślne, dostarczone przez niejawne <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="450d8-117">In this example, only the context correlation is explicitly configured, and the <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair is using the default request-reply correlation that is provided by the implicit <xref:System.ServiceModel.Activities.CorrelationHandle> management of <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="450d8-118">Korzystając z **ReceiveAndSendReply** jawnie skonfigurowano szablon działania w korelacja żądań i odpowiedzi z projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="450d8-118">When using the **ReceiveAndSendReply** activity template in the workflow designer, request-reply correlation is explicitly configured.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="450d8-119">Korelacja żądań i odpowiedzi i zarządzanie dojścia korelacji niejawne, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) i [Przegląd korelacji](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="450d8-119"> request-reply correlation and implicit correlation handle management, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) and [Correlation Overview](../../../../docs/framework/wcf/feature-details/correlation-overview.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="450d8-120">**ReceiveAndSendReply** szablon działania, zobacz [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span><span class="sxs-lookup"><span data-stu-id="450d8-120"> the **ReceiveAndSendReply** activity template, see [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).</span></span>  
  
 <span data-ttu-id="450d8-121">Kolejne <xref:System.ServiceModel.Activities.Receive> działania w usłudze przepływu pracy można odwoływać się <xref:System.ServiceModel.Activities.CorrelationHandle> który został zainicjowany przez <xref:System.ServiceModel.Activities.SendReply> w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="450d8-121">Subsequent <xref:System.ServiceModel.Activities.Receive> activities in the workflow service can reference the <xref:System.ServiceModel.Activities.CorrelationHandle> that was initialized by the <xref:System.ServiceModel.Activities.SendReply> in the previous example.</span></span>  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 <span data-ttu-id="450d8-122">Punkt końcowy jest następnie konfigurowana na <xref:System.ServiceModel.Activities.WorkflowServiceHost> do użycia na podstawie kontekstu powiązania, takich jak <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="450d8-122">The endpoint is then configured on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> to use a context-based binding, such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span>  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a><span data-ttu-id="450d8-123">Konfigurowanie korelacji kontekstu w kliencie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="450d8-123">Configuring Context Correlation in a Workflow Client</span></span>  
 <span data-ttu-id="450d8-124">Gdy klient jest innego przepływu pracy, kontekst korelacji musi być skonfigurowany na komputerze klienckim, a także.</span><span class="sxs-lookup"><span data-stu-id="450d8-124">When the client is another workflow, context correlation must be configured on the client as well.</span></span> <span data-ttu-id="450d8-125">W przepływie pracy klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, która sprawia, że początkowe wywołanie usługi przepływu pracy musi być skonfigurowany z <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="450d8-125">On the client workflow, the <xref:System.ServiceModel.Activities.ReceiveReply> of the <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that makes the initial call to the workflow service must be configured with a <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 <span data-ttu-id="450d8-126">Po korelacji jest zainicjowana, kolejne <xref:System.ServiceModel.Activities.Send> działania mogą używać <xref:System.ServiceModel.Activities.CorrelationHandle> do wywoływania metod dla tego samego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="450d8-126">After the correlation is initialized, subsequent <xref:System.ServiceModel.Activities.Send> activities can use the <xref:System.ServiceModel.Activities.CorrelationHandle> to invoke methods on the same service instance.</span></span>  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 <span data-ttu-id="450d8-127">Należy pamiętać, że w tych przykładach, jawnie skonfigurowane korelacji kontekstu.</span><span class="sxs-lookup"><span data-stu-id="450d8-127">Note that in these examples, the context correlation has been explicitly configured.</span></span> <span data-ttu-id="450d8-128">Jeśli przepływ pracy klienta nie jest obsługiwany w <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a następnie korelacji musi być jawnie skonfigurowany, chyba że działania są zawarte w <xref:System.ServiceModel.Activities.CorrelationScope> działania.</span><span class="sxs-lookup"><span data-stu-id="450d8-128">If the client workflow is not also hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, then correlation must be explicitly configured, unless the activities are contained within a <xref:System.ServiceModel.Activities.CorrelationScope> activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="450d8-129">kontekst korelacji, zobacz [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) próbki.</span><span class="sxs-lookup"><span data-stu-id="450d8-129"> context correlation, see the [NetContextExchangeCorrelation](http://msdn.microsoft.com/en-us/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) sample.</span></span>  
  
 <span data-ttu-id="450d8-130">Jeśli klient, który jest wykonywania wywołań do usługi przepływu pracy nie jest przepływ pracy, następnie go można nadal prowadzić powtarzane wywołania tak długo, jak ją jawnie odsyła kontekście, który zostanie zwrócony w pierwszym wywołaniu usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="450d8-130">If the client that is making calls to the workflow service is not a workflow, then it can still make repeated calls as long as it explicitly passes back the context that is returned from the first call to the workflow service.</span></span> <span data-ttu-id="450d8-131">Serwery proxy generowany przez dodanie odwołania do usługi w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] przechowywania i przekaż tego kontekstu domyślnie.</span><span class="sxs-lookup"><span data-stu-id="450d8-131">Proxies generated by adding a service reference in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] store and pass this context by default.</span></span>
