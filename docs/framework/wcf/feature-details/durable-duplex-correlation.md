---
title: Niezawodna korelacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 5bef3e243afc0ea9a51f474bfed98320134ec043
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491491"
---
# <a name="durable-duplex-correlation"></a>Niezawodna korelacja dwukierunkowa
Niezawodna korelacja dwukierunkowa, znanej także jako wywołania zwrotnego korelacji jest przydatne, gdy usługi przepływu pracy istnieje wymaganie, aby wysłać wywołanie zwrotne do początkowego wywołującego. W odróżnieniu od dupleks WCF wywołania zwrotnego może się zdarzyć w dowolnym momencie w przyszłości i nie jest powiązany ten sam kanał lub trwania kanału. Jedynym wymaganiem jest wywołującego aktywnego punktu końcowego nasłuchiwania dla komunikatu wywołania zwrotnego. Dzięki temu dwie usługi przepływu pracy do komunikacji w konwersacji długotrwałe. Ten temat zawiera omówienie niezawodna korelacja dwukierunkowa.  
  
## <a name="using-durable-duplex-correlation"></a>Przy użyciu niezawodna korelacja dwukierunkowa  
 Niezawodna korelacja dwukierunkowa, te dwie usługi korzystać z obsługą kontekstu powiązania, które obsługuje dwukierunkowe operacje, takie jak <xref:System.ServiceModel.NetTcpContextBinding> lub <xref:System.ServiceModel.WSHttpContextBinding>. Wywołanie rejestrów usługi <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> z powiązaniem żądaną na kliencie ich <xref:System.ServiceModel.Endpoint>. Usługa odbierająca odbiera tych danych w wywołaniu początkowej i używa go samodzielnie <xref:System.ServiceModel.Endpoint> w <xref:System.ServiceModel.Activities.Send> działanie, które wykonuje wywołanie powrót do wywoływania usługi. W tym przykładzie dwie usługi komunikują się ze sobą. Pierwszej usługi wywołuje metodę dla drugiego usługi, a następnie czeka na odpowiedź. Drugi usługi zna nazwę metody wywołania zwrotnego, ale punktu końcowego usługi, który implementuje ta metoda nie jest znany w czasie projektowania.  
  
> [!NOTE]
>  Niezawodna komunikacja dwukierunkowa tylko może być użyta, gdy <xref:System.ServiceModel.Channels.AddressingVersion> punktu końcowego jest skonfigurowany z <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>. Jeśli nie, a następnie <xref:System.InvalidOperationException> wyjątek z następującym komunikatem: "wiadomość zawiera nagłówek kontekstu wywołania zwrotnego z odwołaniem do punktu końcowego dla obiektu AddressingVersion" Addressing200408 (HYPERLINK "http://schemas.xmlsoap.org/ws/2004/08/addressing" http://schemas.xmlsoap.org/ws/2004/08/addressing)". Kontekst wywołania zwrotnego może być przesyłany tylko po skonfigurowaniu właściwości AddressingVersion o wartości "Adresowania WSAddressing10"."  
  
 W poniższym przykładzie usługi przepływu pracy jest hostowana tworzącą wywołanie zwrotne <xref:System.ServiceModel.Endpoint> przy użyciu <xref:System.ServiceModel.WSHttpContextBinding>.  
  
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
  
 Przepływ pracy, który implementuje ta usługa przepływu pracy inicjuje korelację wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działania i odwołuje się do tego punktu końcowego wywołania zwrotnego z <xref:System.ServiceModel.Activities.Receive> działanie, które są powiązane z <xref:System.ServiceModel.Activities.Send>. Poniższy przykład przedstawia przepływ pracy, który jest zwracany z `GetWF1` metody.  
  
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
  
 Drugi usługi przepływu pracy jest hostowany za pomocą powiązania dostarczane przez system, na podstawie kontekstu.  
  
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
  
 Przepływ pracy, który implementuje ta usługa przepływu pracy, który rozpoczyna się od <xref:System.ServiceModel.Activities.Receive> działania. Inicjuje działania to odbierać korelacji wywołania zwrotnego dla tej usługi, opóźnienia w określonym czasie, aby symulować długotrwałe pracy, a następnie wywołania do pierwszej usługi przy użyciu kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu usługi. Poniższy przykład przedstawia przepływ pracy, który jest zwracany po wywołaniu `GetWF2`. Należy pamiętać, że <xref:System.ServiceModel.Activities.Send> działanie ma adres symbolu zastępczego `http://www.contoso.com`; rzeczywisty adres używany w czasie wykonywania jest adres podany wywołania zwrotnego.  
  
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
  
 Gdy `StartOrder` metoda jest wywoływana na pierwszym przepływu pracy, zostanie wyświetlone następujące dane wyjściowe, który wskazuje kierunek wykonywania za pośrednictwem dwóch przepływów pracy.  
  
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
  
 W tym przykładzie przepływami pracy jawnego zarządzania przy użyciu korelacji <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>. Powodu pojedynczego korelacji w przepływach pracy te przykładowe, domyślnie <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania byłaby wystarczające.  
  
## <a name="see-also"></a>Zobacz też  
 [Niezawodna komunikacja dwukierunkowa &#91;WF — przykłady&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
