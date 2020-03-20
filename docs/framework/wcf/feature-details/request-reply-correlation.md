---
title: Korelacja żądań i odpowiedzi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184543"
---
# <a name="request-reply-correlation"></a>Korelacja żądań i odpowiedzi
Korelacja żądanie-odpowiedź jest używana <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> z parą w celu zaimplementowania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> operacji dwukierunkowej w usłudze przepływu pracy i z parą, która wywołuje operację dwukierunkową w innej usłudze sieci Web. Podczas wywoływania operacji dwukierunkowej w usłudze WCF usługa może być tradycyjną usługą Fundacji komunikacji systemu Windows (WCF) opartą na kodzie imperatywu lub może być usługą przepływu pracy. Aby użyć korelacji żądanie odpowiedź musi być używany dwukierunkowe powiązanie, takie jak <xref:System.ServiceModel.BasicHttpBinding>. Niezależnie od tego, czy jest wywoływanie lub implementowanie operacji dwukierunkowej, kroki inicjowania korelacji są podobne i są omówione w tej sekcji.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>Korzystanie z korelacji w operacji dwukierunkowej z odbierania/wysyłania  
 <xref:System.ServiceModel.Activities.Receive> / Para <xref:System.ServiceModel.Activities.SendReply> jest używana do implementowania operacji dwukierunkowej w usłudze przepływu pracy. Środowisko wykonawcze używa korelacji żądanie odpowiedź, aby upewnić się, że odpowiedź jest wywoływana do poprawnego wywołującego. Gdy przepływ pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost>obsługiwany przy użyciu , co ma miejsce w przypadku usług przepływu pracy, wystarczy domyślna inicjalizacja korelacji. W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> para jest używana przez przepływ pracy i nie jest wymagana określona konfiguracja korelacji.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Jawnie inicjowanie korelacji żądanie-odpowiedź  
 Jeśli inne operacje dwukierunkowe są równolegle, a następnie korelacji powinny być jawnie skonfigurowane. Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>i , lub <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> umieszczając <xref:System.ServiceModel.Activities.CorrelationScope>wnętrze . W tym przykładzie korelacja żądanie odpowiedź jest <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> skonfigurowany na parze.  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 Zamiast jawnie konfigurowania korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działania mogą być używane. <xref:System.ServiceModel.Activities.CorrelationScope>udostępnia niejawne <xref:System.ServiceModel.Activities.CorrelationHandle> działania obsługi wiadomości, które zawiera. W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> para znajduje <xref:System.ServiceModel.Activities.CorrelationScope>się wewnątrz pliku . Nie jest wymagana jawna konfiguracja korelacji.  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 Jeśli wymagane są dodatkowe korelacje, można je <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> skonfigurować przy użyciu właściwości odpowiednich `CorrelationInitializer` działań obsługi wiadomości przy użyciu żądanych typów.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Korzystanie z korelacji w operacji dwukierunkowej z wyślij/odbierz  
 Podczas <xref:System.ServiceModel.Activities.Receive> gdy działanie może być używane tylko w <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> usłudze <xref:System.ServiceModel.Activities.Send> / przepływu pracy obsługiwanej przez program , a <xref:System.ServiceModel.Activities.ReceiveReply> para może być używana w dowolnym przepływie pracy, który musi wywołać metodę w usłudze sieci Web. Jeśli przepływ pracy jest <xref:System.ServiceModel.Activities.WorkflowServiceHost> obsługiwany przy użyciu, stosuje się domyślną korelację opisaną w poprzedniej sekcji, ale jeśli nie, <xref:System.ServiceModel.Activities.CorrelationInitializer> to <xref:System.ServiceModel.Activities.CorrelationHandle>korelacja musi być skonfigurowana <xref:System.ServiceModel.Activities.CorrelationScope>jawnie przy użyciu żądanego i , lub za pomocą zarządzania niejawnymi uchwytami .  
  
 Podczas korzystania z **add service reference** w usłudze z operacji <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> dwukierunkowych, działania są generowane, które zawijają działanie pary wewnętrznie z żądaniem/odpowiedzi korelacji jawnie określone.
