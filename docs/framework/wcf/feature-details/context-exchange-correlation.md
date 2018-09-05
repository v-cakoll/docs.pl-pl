---
title: Korelacja wymiany kontekstu
ms.date: 03/30/2017
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
ms.openlocfilehash: d9de111fa08b4a398bba52bc903ea1fec8c7f298
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519735"
---
# <a name="context-exchange-correlation"></a>Korelacja wymiany kontekstu
Kontekst korelacji opiera się na mechanizm wymiany kontekstu, które są opisane w [specyfikacji protokół wymiany kontekstu .NET](https://go.microsoft.com/fwlink/?LinkId=166059). Kontekst korelacji używa nagłówka dobrze znanych kontekstu lub plik cookie do wiązania wiadomości wystąpienia jest poprawny. Używać kontekstu korelacji, na podstawie kontekstu wiązania takich jak <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, lub <xref:System.ServiceModel.NetTcpContextBinding> należy używać w punkcie końcowym udostępniane <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W tym temacie wyjaśniono, jak za pomocą usług korelacji kontekstu działań dotyczących komunikatów w usłudze przepływu pracy.  
  
## <a name="using-context-correlation"></a>Za pomocą kontekstu korelacji  
 Korelacji kontekstu jest używana, gdy klient musi skierować wielokrotnego wywołania do usługi przepływu pracy, a usługa jest obsługiwana przy użyciu jednej z kontekstu powiązania. Tego rodzaju korelacji jest inicjowany przez <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary w usłudze przepływu pracy. Kontekst jest wysyłane z powrotem do klienta wraz z odpowiedzią, a następnie klient dołącza ten kontekst w kolejnych wywołaniach do usługi.  
  
### <a name="configuring-context-correlation-in-a-workflow-service"></a>Konfigurowanie korelacji kontekstu w usłudze przepływu pracy  
 Kontekst korelacji jest inicjowana za pomocą <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> skojarzony z <xref:System.ServiceModel.Activities.SendReply> działania, który odpowiada na początkowej wiadomości przychodzącej. W poniższym przykładzie <xref:System.ServiceModel.Activities.SendReply> jest skonfigurowany do inicializace korelace kontekstu.  
  
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
>  W tym przykładzie są faktycznie dwa rodzaje korelacji używane: kontekst korelacji i korelacja żądań i odpowiedzi. Korelacja kontekstu jest używana, co wywołania od klientów są kierowane do wystąpienia jest poprawny. Korelacja żądań i odpowiedzi jest używany przez <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań ze sobą w celu wykonania operacji dwukierunkowe formowane przez te działania. W tym przykładzie, tylko korelacji kontekstu jest jawnie skonfigurowany, a <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pary używa korelacji "żądanie-odpowiedź" domyślne, dostarczone przez niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzanie <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Korzystając z **ReceiveAndSendReply** szablon działania w korelacja żądań i odpowiedzi z projektanta przepływu pracy jest jawnie skonfigurowany. Aby uzyskać więcej informacji na temat korelacji "żądanie-odpowiedź" i zarządzania dojście niejawnego korelacji zobacz ["żądanie-odpowiedź"](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md) i [Przegląd korelacji](../../../../docs/framework/wcf/feature-details/correlation-overview.md). Aby uzyskać więcej informacji na temat **ReceiveAndSendReply** szablon działania, zobacz [ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer).  
  
 Kolejne <xref:System.ServiceModel.Activities.Receive> może odwoływać się do działania w usłudze przepływu pracy <xref:System.ServiceModel.Activities.CorrelationHandle> , został zainicjowany przez <xref:System.ServiceModel.Activities.SendReply> w poprzednim przykładzie.  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 Punkt końcowy jest następnie konfigurowana na <xref:System.ServiceModel.Activities.WorkflowServiceHost> do użycia na podstawie kontekstu wiązania, takich jak <xref:System.ServiceModel.BasicHttpContextBinding>.  
  
```xml  
<endpoint  
  contract="IOrderContract"  
  binding = "basicHttpContextBinding"  
  address="http://localhost:8080/OrderService" />  
```  
  
### <a name="configuring-context-correlation-in-a-workflow-client"></a>Konfigurowanie korelacji kontekstu w kliencie przepływu pracy  
 Gdy klient jest inny przepływ pracy, kontekst korelacji musi być skonfigurowany na komputerze klienckim, jak również. W przepływie pracy klienta <xref:System.ServiceModel.Activities.ReceiveReply> z <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> parą, która sprawia, że początkowe wywołanie usługi przepływu pracy musi być skonfigurowany z <xref:System.ServiceModel.Activities.ContextCorrelationInitializer>.  
  
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
  
 Po korelacja jest zainicjowany, kolejne <xref:System.ServiceModel.Activities.Send> działania mogą używać <xref:System.ServiceModel.Activities.CorrelationHandle> do wywołania metody, w tym samym wystąpieniu usługi.  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 Należy pamiętać, że w tych przykładach korelacji kontekstu zostało jawnie skonfigurowane. Jeśli klient przepływu pracy nie jest obsługiwana w <xref:System.ServiceModel.Activities.WorkflowServiceHost>, a następnie korelacji musi być jawnie skonfigurowane, chyba że działania są zawarte w <xref:System.ServiceModel.Activities.CorrelationScope> działania. Aby uzyskać więcej informacji na temat kontekstu korelacji zobacz [NetContextExchangeCorrelation](https://msdn.microsoft.com/library/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) próbki.  
  
 Jeśli klient, który jest wykonywanie wywołań do usługi przepływu pracy nie jest przepływ pracy, następnie go można nadal prowadzić wielokrotnego wywołania tak długo, jak ją jawnie odsyła kontekstu, który jest zwracany z wywołania pierwszej usługi przepływu pracy. Serwery proxy generowany przez dodanie odwołania do usługi w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] przechowywania i przekazać ten kontekst domyślnie.
