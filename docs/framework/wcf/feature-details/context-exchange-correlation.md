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
ms.workload: dotnet
ms.openlocfilehash: ee22feab20e2c96f3e708a277f9048f739213520
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="context-exchange-correlation"></a>Korelacja wymiany kontekstu
Kontekst korelacji jest oparta na mechanizm wymiany kontekstu opisanego w [Specyfikacja protokół wymiany kontekstu .NET](http://go.microsoft.com/fwlink/?LinkId=166059). Kontekst korelacji używa nagłówka kontekstu dobrze znanego lub plik cookie powiązać wiadomości na prawidłowe wystąpienie. Umożliwia korelacji kontekstu, na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, lub <xref:System.ServiceModel.NetTcpContextBinding> musi być używany w określony punkt końcowy do <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W tym temacie wyjaśniono, jak używać kontekstu korelacji z działaniami obsługi komunikatów w usłudze przepływu pracy.  
  
## <a name="using-context-correlation"></a>Przy użyciu kontekstu korelacji  
 Korelacji kontekstu jest używana, gdy klient musi wywołań powtarzanego do usługi przepływu pracy i usługa jest obsługiwana przy użyciu jednej z kontekstu powiązania. Ten typ korelacji jest inicjowany przez <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary w usłudze przepływu pracy. Kontekst jest wysyłane do klienta wraz z odpowiedź, a następnie klient dołącza ten kontekst dla kolejnych wywołań do usługi.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Konfigurowanie korelacji kontekstu w usłudze przepływu pracy  
 Kontekst korelacji została zainicjowana przy użyciu <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> skojarzony z <xref:System.ServiceModel.Activities.SendReply> działania, która odpowiada na komunikat przychodzący początkowej. W poniższym przykładzie <xref:System.ServiceModel.Activities.SendReply> jest skonfigurowany do inicjować korelację kontekstu.  
  
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
>  W tym przykładzie są faktycznie dwa rodzaje korelacji używany: kontekst korelacji i korelacja żądań i odpowiedzi. Korelacji kontekstu jest używana i połączeń od klientów są kierowane do prawidłowe wystąpienie. Korelacja żądań i odpowiedzi jest używany przez <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań ze sobą w celu wykonania operacji dwukierunkowe formowane przez te działania. W tym przykładzie tylko korelacji kontekstu jest jawnie skonfigurowany, a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary używa korelacja żądań i odpowiedzi domyślne, dostarczone przez niejawne <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Korzystając z **ReceiveAndSendReply** jawnie skonfigurowano szablon działania w korelacja żądań i odpowiedzi z projektanta przepływów pracy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Korelacja żądań i odpowiedzi i zarządzanie dojścia korelacji niejawne, zobacz [żądanie-odpowiedź](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) i [Przegląd korelacji](../../../../docs/framework/wcf/feature-details/correlation-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]**ReceiveAndSendReply** szablon działania, zobacz [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Kolejne <xref:System.ServiceModel.Activities.Receive> działania w usłudze przepływu pracy można odwoływać się <xref:System.ServiceModel.Activities.CorrelationHandle> który został zainicjowany przez <xref:System.ServiceModel.Activities.SendReply> w poprzednim przykładzie.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Punkt końcowy jest następnie konfigurowana na <xref:System.ServiceModel.Activities.WorkflowServiceHost> do użycia na podstawie kontekstu powiązania, takich jak <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Konfigurowanie korelacji kontekstu w kliencie przepływu pracy  
 Gdy klient jest innego przepływu pracy, kontekst korelacji musi być skonfigurowany na komputerze klienckim, a także. W przepływie pracy klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pary, która sprawia, że początkowe wywołanie usługi przepływu pracy musi być skonfigurowany z <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
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
  
 Po korelacji jest zainicjowana, kolejne <xref:System.ServiceModel.Activities.Send> działania mogą używać <xref:System.ServiceModel.Activities.CorrelationHandle> do wywoływania metod dla tego samego wystąpienia usługi.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Należy pamiętać, że w tych przykładach, jawnie skonfigurowane korelacji kontekstu. Jeśli przepływ pracy klienta nie jest obsługiwany w <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a następnie korelacji musi być jawnie skonfigurowany, chyba że działania są zawarte w <xref:System.ServiceModel.Activities.CorrelationScope> działania. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontekst korelacji, zobacz [NetContextExchangeCorrelation](http://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) próbki.  
  
 Jeśli klient, który jest wykonywania wywołań do usługi przepływu pracy nie jest przepływ pracy, następnie go można nadal prowadzić powtarzane wywołania tak długo, jak ją jawnie odsyła kontekście, który zostanie zwrócony w pierwszym wywołaniu usługi przepływu pracy. Serwery proxy generowany przez dodanie odwołania do usługi w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] przechowywania i przekaż tego kontekstu domyślnie.
