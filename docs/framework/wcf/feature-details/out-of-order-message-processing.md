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
# <a name="out-of-order-message-processing"></a>Przetwarzanie komunikatów poza kolejnością
Usługi przepływu pracy może zależeć od wiadomości w określonej kolejności. Usługi przepływu pracy zawiera jeden lub więcej <xref:System.ServiceModel.Activities.Receive> działań i każdego <xref:System.ServiceModel.Activities.Receive> działania oczekuje określonego komunikatu. Bez gwarancją dostarczania danego transportu wiadomości wysyłane przez klientów mogą być opóźnione i w związku z tym dostarczane w określonym porządku usługi przepływu pracy nie mogą oczekiwać. Wdrażanie usługi przepływu pracy, który nie wymaga wiadomości wysyłane w określonej kolejności zwykle odbywa się za pomocą działania równoległego. Dla bardziej złożonego protokołu aplikacji przepływu pracy może być bardzo złożone bardzo szybko.  Funkcja przetwarzanie komunikatów poza kolejnością w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pozwala utworzyć przepływ bez wszystkich złożoność zagnieżdżonego działania równoległe. Przetwarzanie komunikatów poza kolejnością jest obsługiwana tylko na kanałów, które obsługują <xref:System.ServiceModel.Channels.ReceiveContext> takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania usługi MSMQ.  
  
## <a name="enabling-out-of-order-message-processing"></a>Włączanie przetwarzanie komunikatów poza kolejnością.  
 Przetwarzanie komunikatów poza kolejnością jest włączane przez ustawienie <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości `true` na WorkflowService. Poniższy przykład przedstawia sposób ustawiania <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości w kodzie.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Można także zastosować `AllowBufferedReceive` atrybutu usługi przepływu pracy w języku XAML, jak pokazano w poniższym przykładzie.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
