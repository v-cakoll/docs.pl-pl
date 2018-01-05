---
title: "Przetwarzanie komunikatów poza kolejnością"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19ab5afbc1eb13a3126e94a040d51204fea131a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="8a145-102">Przetwarzanie komunikatów poza kolejnością</span><span class="sxs-lookup"><span data-stu-id="8a145-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="8a145-103">Usługi przepływu pracy może zależeć od wiadomości w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8a145-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="8a145-104">Usługi przepływu pracy zawiera jeden lub więcej <xref:System.ServiceModel.Activities.Receive> działań i każdego <xref:System.ServiceModel.Activities.Receive> działania oczekuje określonego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8a145-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="8a145-105">Bez gwarancją dostarczania danego transportu wiadomości wysyłane przez klientów mogą być opóźnione i w związku z tym dostarczane w określonym porządku usługi przepływu pracy nie mogą oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="8a145-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="8a145-106">Wdrażanie usługi przepływu pracy, który nie wymaga wiadomości wysyłane w określonej kolejności zwykle odbywa się za pomocą działania równoległego.</span><span class="sxs-lookup"><span data-stu-id="8a145-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="8a145-107">Dla bardziej złożonego protokołu aplikacji przepływu pracy może być bardzo złożone bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="8a145-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="8a145-108">Funkcja przetwarzanie komunikatów poza kolejnością w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pozwala utworzyć przepływ bez wszystkich złożoność zagnieżdżonego działania równoległe.</span><span class="sxs-lookup"><span data-stu-id="8a145-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="8a145-109">Przetwarzanie komunikatów poza kolejnością jest obsługiwana tylko na kanałów, które obsługują <xref:System.ServiceModel.Channels.ReceiveContext> takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8a145-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="8a145-110">Włączanie przetwarzanie komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="8a145-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="8a145-111">Przetwarzanie komunikatów poza kolejnością jest włączane przez ustawienie <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości `true` na WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="8a145-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="8a145-112">Poniższy przykład przedstawia sposób ustawiania <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8a145-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="8a145-113">Można także zastosować `AllowBufferedReceive` atrybutu usługi przepływu pracy w języku XAML, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8a145-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a145-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a145-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="8a145-115">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8a145-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="8a145-116">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="8a145-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
