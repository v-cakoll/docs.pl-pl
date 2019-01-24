---
title: Przetwarzanie komunikatów poza kolejnością
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7d908be84f22835bea744de74d278689516f3185
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698014"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="4a38e-102">Przetwarzanie komunikatów poza kolejnością</span><span class="sxs-lookup"><span data-stu-id="4a38e-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="4a38e-103">Usługi przepływu pracy może zależeć od wiadomości w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4a38e-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="4a38e-104">Usługi przepływu pracy zawiera jeden lub więcej <xref:System.ServiceModel.Activities.Receive> działań, a każdy <xref:System.ServiceModel.Activities.Receive> działania oczekuje szczegółowy komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="4a38e-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="4a38e-105">Bez gwarancją dostarczania danego transportu komunikatów wysyłanych przez klientów może być opóźniony i w związku z tym dostarczane w określonym porządku usługi przepływu pracy nie może oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="4a38e-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="4a38e-106">Wdrażanie usługi przepływu pracy, które nie wymagają komunikaty wysłane w konkretnym kolejności zwykle odbywa się przy użyciu działania równoległego.</span><span class="sxs-lookup"><span data-stu-id="4a38e-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="4a38e-107">Dla bardziej skomplikowanych protokołu aplikacji przepływ pracy może być bardzo złożone bardzo szybko.</span><span class="sxs-lookup"><span data-stu-id="4a38e-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="4a38e-108">Komunikatów poza kolejnością przetwarzania funkcji w Windows Communication Foundation (WCF) umożliwia tworzenie takich przepływu pracy wszystkich wymaganych złożoności zagnieżdżonych działań równoległych.</span><span class="sxs-lookup"><span data-stu-id="4a38e-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="4a38e-109">Przetwarzanie komunikatów poza kolejnością jest obsługiwane tylko za pośrednictwem kanałów, które obsługują <xref:System.ServiceModel.Channels.ReceiveContext> np. powiązania WCF usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4a38e-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="4a38e-110">Włączanie przetwarzanie komunikatów poza kolejnością</span><span class="sxs-lookup"><span data-stu-id="4a38e-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="4a38e-111">Przetwarzanie komunikatów poza kolejnością jest włączona, ustawiając <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości `true` na WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="4a38e-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="4a38e-112">Poniższy przykład pokazuje, jak ustawić <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4a38e-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="4a38e-113">Można również zastosować `AllowBufferedReceive` atrybutów w usługach XAML przepływu pracy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4a38e-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a38e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a38e-114">See also</span></span>
- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="4a38e-115">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4a38e-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="4a38e-116">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="4a38e-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
