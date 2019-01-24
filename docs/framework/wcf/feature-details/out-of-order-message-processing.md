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
# <a name="out-of-order-message-processing"></a>Przetwarzanie komunikatów poza kolejnością
Usługi przepływu pracy może zależeć od wiadomości w określonej kolejności. Usługi przepływu pracy zawiera jeden lub więcej <xref:System.ServiceModel.Activities.Receive> działań, a każdy <xref:System.ServiceModel.Activities.Receive> działania oczekuje szczegółowy komunikat o błędzie. Bez gwarancją dostarczania danego transportu komunikatów wysyłanych przez klientów może być opóźniony i w związku z tym dostarczane w określonym porządku usługi przepływu pracy nie może oczekiwać. Wdrażanie usługi przepływu pracy, które nie wymagają komunikaty wysłane w konkretnym kolejności zwykle odbywa się przy użyciu działania równoległego. Dla bardziej skomplikowanych protokołu aplikacji przepływ pracy może być bardzo złożone bardzo szybko.  Komunikatów poza kolejnością przetwarzania funkcji w Windows Communication Foundation (WCF) umożliwia tworzenie takich przepływu pracy wszystkich wymaganych złożoności zagnieżdżonych działań równoległych. Przetwarzanie komunikatów poza kolejnością jest obsługiwane tylko za pośrednictwem kanałów, które obsługują <xref:System.ServiceModel.Channels.ReceiveContext> np. powiązania WCF usługi MSMQ.  
  
## <a name="enabling-out-of-order-message-processing"></a>Włączanie przetwarzanie komunikatów poza kolejnością  
 Przetwarzanie komunikatów poza kolejnością jest włączona, ustawiając <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości `true` na WorkflowService. Poniższy przykład pokazuje, jak ustawić <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> właściwości w kodzie.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Można również zastosować `AllowBufferedReceive` atrybutów w usługach XAML przepływu pracy, jak pokazano w poniższym przykładzie.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.ReceiveContext>
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
