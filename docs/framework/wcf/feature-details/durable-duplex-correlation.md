---
title: Niezawodna korelacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: bb73cef5190a0b146e713ef1adae24219dc2eed8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185174"
---
# <a name="durable-duplex-correlation"></a>Niezawodna korelacja dwukierunkowa
Trwałej korelacji dupleksu, znany również jako korelacji wywołania zwrotnego, jest przydatne, gdy usługa przepływu pracy ma wymóg, aby wysłać wywołanie zwrotne do początkowego obiektu wywołującego. W przeciwieństwie do dupleksu WCF wywołanie zwrotne może się zdarzyć w dowolnym momencie w przyszłości i nie jest powiązany z tego samego kanału lub okresu istnienia kanału; jedynym wymaganiem jest, że obiekt wywołujący mają aktywny punkt końcowy nasłuchiwania wiadomości wywołania zwrotnego. Dzięki temu dwie usługi przepływu pracy do komunikowania się w długotrwałej konwersacji. Ten temat zawiera omówienie trwałej korelacji dupleksu.  
  
## <a name="using-durable-duplex-correlation"></a>Korzystanie z trwałej korelacji dupleksu  
 Aby użyć trwałej korelacji dupleksu, dwie usługi muszą używać powiązania kontekstowego, <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding>które obsługuje operacje dwukierunkowe, takie jak lub . Usługa wywołująca rejestruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> z żądanym powiązaniem dla swojego klienta. <xref:System.ServiceModel.Endpoint> Usługa odbierająca odbiera te dane w wywołaniu początkowym, <xref:System.ServiceModel.Endpoint> a <xref:System.ServiceModel.Activities.Send> następnie używa ich samodzielnie w działaniu, które sprawia, że połączenie z powrotem do usługi wywołującej. W tym przykładzie dwie usługi komunikują się ze sobą. Pierwsza usługa wywołuje metodę w drugiej usłudze, a następnie czeka na odpowiedź. Druga usługa zna nazwę metody wywołania zwrotnego, ale punkt końcowy usługi, która implementuje tę metodę, nie jest znany w czasie projektowania.  
  
> [!NOTE]
> Trwałego dupleksu można <xref:System.ServiceModel.Channels.AddressingVersion> używać tylko wtedy, <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>gdy punkt końcowy jest skonfigurowany z programem . Jeśli tak nie jest, wyjątek jest zgłaszany z następującym <xref:System.InvalidOperationException> komunikatem: "Wiadomość zawiera nagłówek kontekstu wywołania zwrotnego z odwołaniem do punktu końcowego [addressingversion](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontekst wywołania zwrotnego może być przesyłany tylko wtedy, gdy AddressingVersion jest skonfigurowany z "WSAddressing10".
  
 W poniższym przykładzie hostowana jest usługa przepływu <xref:System.ServiceModel.Endpoint> pracy, która tworzy wywołanie zwrotne przy użyciu programu <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Przepływ pracy, który implementuje tę usługę przepływu pracy inicjuje korelację wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działaniem i odwołuje się do tego punktu końcowego wywołania zwrotnego <xref:System.ServiceModel.Activities.Receive> z działania, które koreluje z <xref:System.ServiceModel.Activities.Send>. Poniższy przykład reprezentuje przepływ pracy, `GetWF1` który jest zwracany z metody.  
  
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
  
 Druga usługa przepływu pracy jest obsługiwana przy użyciu powiązania opartego na systemie, opartego na kontekście.  
  
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
  
 Przepływ pracy, który implementuje tę usługę <xref:System.ServiceModel.Activities.Receive> przepływu pracy rozpoczyna się od działania. To działanie odbierania inicjuje korelację wywołania zwrotnego dla tej usługi, opóźnienia przez pewien okres czasu, aby symulować długotrwałą pracę, a następnie wywołania z powrotem do pierwszej usługi przy użyciu kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu do usługi. Poniższy przykład przedstawia przepływ pracy, który `GetWF2`jest zwracany z wywołania do . Należy zauważyć, że <xref:System.ServiceModel.Activities.Send> działanie ma `http://www.contoso.com`adres zastępczy ; rzeczywisty adres używany w czasie wykonywania jest podany adres wywołania zwrotnego.  
  
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
  
 Gdy `StartOrder` metoda jest wywoływana w pierwszym przepływie pracy, wyświetlane są następujące dane wyjściowe, który pokazuje przepływ wykonywania za pośrednictwem dwóch przepływów pracy.  
  
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
  
 W tym przykładzie oba przepływy pracy jawnie <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>zarządzają korelacją przy użyciu pliku . Ponieważ w tych przykładowych przepływach pracy istniała tylko <xref:System.ServiceModel.Activities.CorrelationHandle> jedna korelacja, domyślne zarządzanie byłoby wystarczające.
