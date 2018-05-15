---
title: Przetwarzanie komunikatów poza kolejnością
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: a7839b60dbad7919a644c196a1c63f6bc46fb5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="4527f-102">Przetwarzanie komunikatów poza kolejnością</span><span class="sxs-lookup"><span data-stu-id="4527f-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="4527f-103">Usługi przepływu pracy może zależeć od wiadomości w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4527f-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="4527f-104">Usługi przepływu pracy zawiera jeden lub więcej <xref:System.ServiceModel.Activities.Receive> działań i każdego <xref:System.ServiceModel.Activities.Receive> działania oczekuje określonego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4527f-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="4527f-105">Bez gwarancją dostarczania danego transportu wiadomości wysyłane przez klientów mogą być opóźnione i w związku z tym dostarczane w określonym porządku usługi przepływu pracy nie mogą oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="4527f-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="4527f-106">Wdrażanie usługi przepływu pracy, który nie wymaga wiadomości wysyłane w określonej kolejności zwykle odbywa się za pomocą działania równoległego.</span><span class="sxs-lookup"><span data-stu-id="4527f-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="4527f-107">Dla bardziej złożonego protokołu aplikacji przepływu pracy może być bardzo złożone bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="4527f-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="4527f-108">Funkcja w systemie Windows Communication Foundation (WCF) przetwarzania komunikatów poza kolejnością służy do tworzenia przepływ bez wszystkich złożoność zagnieżdżonego działania równoległe.</span><span class="sxs-lookup"><span data-stu-id="4527f-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="4527f-109">Przetwarzanie komunikatów poza kolejnością jest obsługiwana tylko na kanałów, które obsługują <xref:System.ServiceModel.Channels.ReceiveContext> np. powiązania WCF usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4527f-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="4527f-110">Włączanie przetwarzanie komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="4527f-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="4527f-111">Przetwarzanie komunikatów poza kolejnością jest włączane przez ustawienie <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości `true` na WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="4527f-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="4527f-112">Poniższy przykład przedstawia sposób ustawiania <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4527f-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="4527f-113">Można także zastosować `AllowBufferedReceive` atrybutu usługi przepływu pracy w języku XAML, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4527f-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4527f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4527f-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="4527f-115">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4527f-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="4527f-116">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="4527f-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
