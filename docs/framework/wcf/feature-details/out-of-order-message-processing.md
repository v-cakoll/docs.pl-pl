---
title: Przetwarzanie komunikatów poza kolejnością
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7930f26cf5957158a16d65085267cf1bab2e4504
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598726"
---
# <a name="out-of-order-message-processing"></a>Przetwarzanie komunikatów poza kolejnością
Usługi przepływu pracy mogą zależeć od komunikatów wysyłanych w określonej kolejności. Usługa przepływu pracy zawiera co najmniej jedną <xref:System.ServiceModel.Activities.Receive> czynność, a każde <xref:System.ServiceModel.Activities.Receive> działanie oczekuje określonego komunikatu. Bez określonych gwarancji dostarczania transportowego komunikaty wysyłane przez klientów mogą być opóźnione i w związku z tym dostarczane w kolejności, w której usługa przepływu pracy może się nie spodziewać. Implementacja usługi przepływu pracy, która nie wymaga przesyłania komunikatów w określonej kolejności, zwykle odbywa się przy użyciu działania równoległego. W przypadku bardziej skomplikowanego protokołu aplikacji przepływ pracy staje się bardzo skomplikowany bardzo szybko.  Funkcja przetwarzania komunikatów poza kolejnością w programie Windows Communication Foundation (WCF) umożliwia tworzenie takiego przepływu pracy bez żadnej złożoności zagnieżdżonych działań równoległych. Przetwarzanie komunikatów poza kolejnością jest obsługiwane tylko w przypadku kanałów obsługujących <xref:System.ServiceModel.Channels.ReceiveContext> takie działania jak powiązania MSMQ usługi WCF.  
  
## <a name="enabling-out-of-order-message-processing"></a>Włączanie przetwarzania komunikatów poza kolejnością  
 Przetwarzanie komunikatów poza kolejnością jest włączane przez ustawienie właściwości na <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> `true` obiektu WorkflowService. Poniższy przykład pokazuje, jak ustawić <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Właściwość w kodzie.  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 Można również zastosować `AllowBufferedReceive` atrybut do usługi przepływu pracy w języku XAML, jak pokazano w poniższym przykładzie.  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [Usługi przepływu pracy](workflow-services.md)
- [Kolejki i sesje niezawodne](queues-and-reliable-sessions.md)
