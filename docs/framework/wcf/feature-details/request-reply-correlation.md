---
title: "Korelacja żądań i odpowiedzi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29286950cfef7d8e3e2c453bbdcc307c26e641de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="request-reply-correlation"></a>Korelacja żądań i odpowiedzi
Korelacja żądań i odpowiedzi jest używany z <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary do zaimplementowania dwukierunkowe operacji w usłudze przepływu pracy oraz <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, który wywołuje operację dwukierunkowe w innej sieci Web Usługa. Podczas wywoływania dwukierunkowe operacji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, usługi mogą być albo tradycyjnych imperatywne opartej na kodzie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługę albo mogą być usługi przepływu pracy. Umożliwia powiązanie dwustronne muszą być stosowane, takich jak korelacja żądań i odpowiedzi <xref:System.ServiceModel.BasicHttpBinding>. Wywoływanie lub wykonania operacji dwukierunkowe, kroków inicjowania korelacji są podobne i są przedstawione w tej sekcji.  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>W ramach operacji dwukierunkowe z odbierania SendReply przy użyciu korelacji  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używane do implementowania dwukierunkowe operacji w usłudze przepływu pracy. Środowiska uruchomieniowego używa korelacja żądań i odpowiedzi, aby upewnić się, że odpowiedź jest wysyłane do wywołującego poprawne. Gdy przepływ pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, czyli w przypadku usług przepływu pracy, a następnie inicjowanie domyślnych korelacja jest wystarczająca. W tym scenariuszu <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary jest używany przez przepływ pracy i nie jest wymagana żadna konfiguracja określonych korelacji.  
  
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
 W przypadku innych operacji dwukierunkowe równolegle, następnie korelacji należy jawnie skonfigurować. Można to zrobić, określając <xref:System.ServiceModel.Activities.CorrelationHandle> i <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>, lub umieszczając <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>. W tym przykładzie skonfigurowano korelacja żądań i odpowiedzi na <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary.  
  
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
  
 Zamiast konfigurować jawnie korelacji, <xref:System.ServiceModel.Activities.CorrelationScope> działanie może być używane. <xref:System.ServiceModel.Activities.CorrelationScope>zapewnia niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> do obsługi komunikatów działań, które zawiera. W tym przykładzie <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary znajduje się wewnątrz <xref:System.ServiceModel.Activities.CorrelationScope>. Nie jest wymagana żadna konfiguracja jawne korelacji.  
  
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
  
 Jeśli wymagane są dodatkowe korelacji, można je skonfigurować przy użyciu <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwości odpowiednich działań komunikacji przy użyciu żądaną `CorrelationInitializer` typów.  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>W ramach operacji dwukierunkowe z wysyłania/ReceiveReply przy użyciu korelacji  
 Gdy <xref:System.ServiceModel.Activities.Receive> działania można używać tylko w obsługiwanych przez usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary mogą być używane w każdy przepływ pracy, który należy wywołać metodę dla usługi sieci Web. Jeśli przepływ pracy jest hostowana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost> , a następnie stosuje korelacji domyślne opisane w poprzedniej sekcji, ale jeśli nie, korelacji musi być skonfigurowany albo jawnie za pomocą żądaną <xref:System.ServiceModel.Activities.CorrelationInitializer> i <xref:System.ServiceModel.Activities.CorrelationHandle>, lub za pomocą niejawne Obsługa zarządzania <xref:System.ServiceModel.Activities.CorrelationScope>.  
  
 Korzystając z **Dodaj odwołanie do usługi** na usługi za pomocą operacji dwukierunkowe, są generowane działania tego zawijania <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> jawnie parę działania wewnętrznie o korelacji żądania/odpowiedzi określona.
