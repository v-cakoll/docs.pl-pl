---
title: Korelacja żądań i odpowiedzi
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991136"
---
# <a name="request-reply-correlation"></a>Korelacja żądań i odpowiedzi
Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Paruj, aby zaimplementować dwukierunkowe operacji w usłudze przepływu pracy i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> parą, która wywołuje dwukierunkowe operacji w innej sieci Web Usługa. Podczas wywoływania dwukierunkowe operacji usługi WCF, usługa może być albo tradycyjne imperatywne oparte na kodzie usługi Windows Communication Foundation (WCF) lub może być usługi przepływu pracy. Aby użyć korelacji "żądanie-odpowiedź" powiązanie dwustronne należy użyć, takie jak <xref:System.ServiceModel.BasicHttpBinding>. Czy wywołania Implementowanie dwukierunkowej operacji, kroków inicjowania korelacji są podobne i zostały omówione w tej sekcji.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>W ramach operacji dwukierunkowego z otrzymywać SendReply przy użyciu korelacji  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany do implementowania dwukierunkowe operacji w usłudze przepływu pracy. Środowisko wykonawcze używa korelacji "żądanie-odpowiedź", aby upewnić się, że odpowiedź jest wysyłane do poprawny obiekt wywołujący. Gdy przepływ pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>, co ma miejsce w przypadku usług przepływu pracy, a następnie inicjowanie korelacji domyślne są wystarczające. W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany w ramach przepływu pracy i jest wymagana żadna konfiguracja określonych korelacji.  
  
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
  
### <a name="explicitly-initializing-request-reply-correlation"></a>Jawne inicjowanie korelacji "żądanie-odpowiedź"  
 W przypadku innych operacji dwukierunkowe w sposób równoległy, następnie korelacji powinny być jawnie skonfigurowane. Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> i <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, lub poprzez umieszczenie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>. W tym przykładzie korelacja żądań i odpowiedzi jest konfigurowany na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary.  
  
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
  
 Zamiast konfigurować jawnie korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działanie może być używane. <xref:System.ServiceModel.Activities.CorrelationScope> zapewnia niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> do działań dotyczących komunikatów, które zawiera. W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary znajduje się wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>. Jawne korelacji jest wymagana żadna konfiguracja.  
  
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
  
 Jeśli wymagane są dodatkowe korelacji, a następnie takie grupy można skonfigurować przy użyciu <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwość odpowiednich działań dotyczących komunikatów za pomocą żądaną `CorrelationInitializer` typów.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>Przy użyciu korelacja dwukierunkowa operacji za pomocą wysyłania/ReceiveReply  
 Gdy <xref:System.ServiceModel.Activities.Receive> działania można używać tylko w usłudze przepływu pracy pracujących na <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary mogą być używane w każdym przepływie pracy, należy wywołać metody usługi sieci Web. Jeśli przepływ pracy znajduje się za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost> , a następnie stosuje korelacji domyślnej opisanego w poprzedniej sekcji, ale jeśli nie, następnie korelacji musi być skonfigurowany jawnie za pomocą żądaną <xref:System.ServiceModel.Activities.CorrelationInitializer> i <xref:System.ServiceModel.Activities.CorrelationHandle>, lub za pomocą niejawny Obsługa zarządzania <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Korzystając z **Dodaj odwołanie do usługi** usłudze z operacjami dwukierunkowe są generowane działania tego zawijania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jawnie pair działania wewnętrznie z korelacją żądanie/nietypizowana odpowiedź określona.
