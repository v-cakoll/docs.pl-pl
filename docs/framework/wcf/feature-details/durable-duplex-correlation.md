---
title: Nietrwała korelacja dupleksu
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: efc647b8a39f419f2165fe355529ba145663b753
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291581"
---
# <a name="durable-duplex-correlation"></a>Nietrwała korelacja dupleksu
Niezależna korelacja dupleksu, nazywana również korelacją wywołania zwrotnego, jest przydatna, gdy usługa przepływu pracy wymaga do wysłania wywołania zwrotnego do początkowego obiektu wywołującego. W przeciwieństwie do funkcji WCF, wywołanie zwrotne może wystąpić w dowolnym momencie w przyszłości i nie jest powiązane z tym samym kanałem lub okresem istnienia kanału. Jedynym wymaganiem jest, że obiekt wywołujący ma aktywny punkt końcowy nasłuchujący wiadomości wywołania zwrotnego. Dzięki temu dwie usługi przepływu pracy mogą komunikować się w długotrwałej konwersacji. Ten temat zawiera omówienie trwałej korelacji dupleksowej.  
  
## <a name="using-durable-duplex-correlation"></a>Używanie trwałej korelacji dupleksowej  
 Aby można było użyć korelacji z trwałą dupleksem, dwie usługi muszą używać powiązania z obsługą kontekstu, które obsługuje operacje dwukierunkowe, takie jak <xref:System.ServiceModel.NetTcpContextBinding> lub <xref:System.ServiceModel.WSHttpContextBinding>. Usługa wywołująca rejestruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> z pożądanym powiązaniem na kliencie <xref:System.ServiceModel.Endpoint>. Usługa odbierająca odbiera te dane w początkowym wywołaniu, a następnie używa go na własne <xref:System.ServiceModel.Endpoint> w działaniu <xref:System.ServiceModel.Activities.Send>, które powoduje wywołanie z powrotem do usługi wywołującej. W tym przykładzie dwie usługi komunikują się ze sobą. Pierwsza usługa wywołuje metodę dla drugiej usługi, a następnie czeka na odpowiedź. Druga usługa zna nazwę metody wywołania zwrotnego, ale punkt końcowy usługi implementującej tę metodę nie jest znany w czasie projektowania.  
  
> [!NOTE]
> Trwały dupleks można używać tylko wtedy, gdy <xref:System.ServiceModel.Channels.AddressingVersion> punktu końcowego jest skonfigurowany z <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Jeśli tak nie jest, zostanie zgłoszony wyjątek <xref:System.InvalidOperationException> z następującym komunikatem: "komunikat zawiera nagłówek kontekstu wywołania zwrotnego z odwołaniem do punktu końcowego dla [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontekst wywołania zwrotnego można przesłać tylko wtedy, gdy AddressingVersion jest skonfigurowany przy użyciu elementu "WSAddressing10".
  
 W poniższym przykładzie jest hostowana usługa przepływu pracy, która tworzy wywołanie zwrotne <xref:System.ServiceModel.Endpoint> przy użyciu <xref:System.ServiceModel.WSHttpContextBinding>.  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 Przepływ pracy implementujący tę usługę przepływu pracy inicjuje korelację wywołania zwrotnego z działaniem <xref:System.ServiceModel.Activities.Send> i odwołuje się do tego punktu końcowego wywołania zwrotnego z działania <xref:System.ServiceModel.Activities.Receive>, które jest skorelowane z <xref:System.ServiceModel.Activities.Send>. Poniższy przykład reprezentuje przepływ pracy, który jest zwracany z metody `GetWF1`.  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")                          
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 Druga usługa przepływu pracy jest hostowana przy użyciu opartego na systemie powiązania.  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 Przepływ pracy implementujący tę usługę przepływu pracy rozpoczyna się od działania <xref:System.ServiceModel.Activities.Receive>. To działanie Receive inicjuje korelację wywołania zwrotnego dla tej usługi, opóźnia przez pewien czas, aby symulować długotrwałą pracę, a następnie wywołuje z powrotem do pierwszej usługi przy użyciu kontekstu wywołania zwrotnego, który został przesłany podczas pierwszego wywołania usługi. Poniższy przykład reprezentuje przepływ pracy, który jest zwracany przez wywołanie `GetWF2`. Należy pamiętać, że działanie <xref:System.ServiceModel.Activities.Send> ma adres zastępczy `http://www.contoso.com`; rzeczywistym adresem używanym w czasie wykonywania jest podany adres zwrotny.  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 Gdy metoda `StartOrder` jest wywoływana w pierwszym przepływie pracy, wyświetlane są następujące dane wyjściowe, które pokazują przepływ wykonywania przez dwa przepływy pracy.  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.   
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 W tym przykładzie oba przepływy pracy jawnie zarządzają korelacją przy użyciu <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Ponieważ w tych przykładowych przepływach pracy istniała tylko jedna korelacja, domyślne zarządzanie <xref:System.ServiceModel.Activities.CorrelationHandle> byłoby wystarczające.
