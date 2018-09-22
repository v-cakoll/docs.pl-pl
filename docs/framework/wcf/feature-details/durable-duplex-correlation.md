---
title: Niezawodna korelacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 82c052ff87eb8b125dfc64e1567dbd00d255894d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699186"
---
# <a name="durable-duplex-correlation"></a>Niezawodna korelacja dwukierunkowa
Niezawodna korelacja dwukierunkowa, znany także jako wywołanie zwrotne korelacji jest przydatne, gdy usługi przepływu pracy istnieje wymaganie, aby wysłać wywołanie zwrotne do początkowego obiektu wywołującego. W odróżnieniu od dupleks WCF wywołania zwrotnego może się zdarzyć w dowolnym momencie w przyszłości i nie jest związany z tego samego kanału lub trwania kanału. Jedynym wymaganiem jest, że obiekt wywołujący ma aktywny punkt końcowy nasłuchiwać komunikatów wywołania zwrotnego. Dzięki temu dwie usługi przepływu pracy do komunikowania się z konwersacji długotrwałych. Ten temat zawiera omówienie niezawodna korelacja dwukierunkowa.  
  
## <a name="using-durable-duplex-correlation"></a>Za pomocą niezawodna korelacja dwukierunkowa  
 Niezawodna korelacja dwukierunkowa, te dwie usługi korzystać z obsługą kontekstu powiązania, obsługującej dwukierunkowe operacje, takie jak <xref:System.ServiceModel.NetTcpContextBinding> lub <xref:System.ServiceModel.WSHttpContextBinding>. Wywołujący rejestrów usługi <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> dla żądanego powiązania na kliencie <xref:System.ServiceModel.Endpoint>. Usługa odbierająca odbiera tych danych w wywołaniu początkową, a następnie używa go samodzielnie <xref:System.ServiceModel.Endpoint> w <xref:System.ServiceModel.Activities.Send> działania, która wywołuje tę funkcję do wywoływania usługi. W tym przykładzie dwie usługi komunikują się ze sobą. Pierwsza usługa wywołuje metodę dla drugiej usługi, a następnie czeka na odpowiedź. Nazwa metody wywołania zwrotnego wie, drugi usługi, ale punktu końcowego usługi, który implementuje ta metoda nie jest znany w czasie projektowania.  
  
> [!NOTE]
> Niezawodna komunikacja dwukierunkowa może zawierać tylko używane podczas <xref:System.ServiceModel.Channels.AddressingVersion> punktu końcowego jest konfigurowana <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Jeśli nie jest dostępna, a następnie <xref:System.InvalidOperationException> wyjątek z następującym komunikatem: "wiadomość zawiera nagłówek Kontekst wywołania zwrotnego z odwołania do punktu końcowego dla [standard](http://schemas.xmlsoap.org/ws/2004/08/addressing). Kontekst wywołania zwrotnego być przesyłany tylko w przypadku, gdy wersja adresowania mogła być skonfigurowano adresowania "WSAddressing10".
  
 W poniższym przykładzie przepływu pracy jest hostowana usługa, która tworzy wywołanie zwrotne <xref:System.ServiceModel.Endpoint> przy użyciu <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Przepływ pracy, który implementuje ta usługa przepływu pracy inicjuje korelacji wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działania i zawiera odwołania do tego punktu końcowego wywołania zwrotnego, z <xref:System.ServiceModel.Activities.Receive> działanie, które mają związek z <xref:System.ServiceModel.Activities.Send>. Poniższy przykład przedstawia przepływ pracy, który jest zwracany z `GetWF1` metody.  
  
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
  
 Drugi usługi przepływu pracy znajduje się za pomocą powiązania dostarczane przez system, oparte na kontekście.  
  
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
  
 Przepływ pracy, który implementuje ta usługa przepływu pracy rozpoczyna się od <xref:System.ServiceModel.Activities.Receive> działania. Inicjuje działania to otrzymują korelacji wywołania zwrotnego dla tej usługi, opóźnienia w danym okresie czasu, aby zasymulować długotrwała praca, a następnie wywołania do pierwszej usługi przy użyciu tego kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu do usługi. Poniższy przykład przedstawia przepływ pracy, który jest zwracany z wywołania `GetWF2`. Należy pamiętać, że <xref:System.ServiceModel.Activities.Send> działanie ma symbol zastępczy adres `http://www.contoso.com`; rzeczywisty adres używany w czasie wykonywania jest adres podany wywołania zwrotnego.  
  
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
  
 Gdy `StartOrder` metoda jest wywoływana pierwszego przepływu pracy, wyświetlane następujące dane wyjściowe, które przedstawia przepływ wykonania przy użyciu dwóch przepływów pracy.  
  
```Output  
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
  
 W tym przykładzie przepływami pracy jawnie zarządzać za pomocą korelacji <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Powodu pojedynczego korelacji w tych przepływów pracy przykładowej domyślnie <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania mogą być wystarczające.  
  
## <a name="see-also"></a>Zobacz też  
 [Niezawodna komunikacja dwukierunkowa &#91;WF — przykłady&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
