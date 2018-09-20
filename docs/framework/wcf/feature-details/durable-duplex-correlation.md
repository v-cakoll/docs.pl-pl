---
title: Niezawodna korelacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 82c052ff87eb8b125dfc64e1567dbd00d255894d
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323785"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="737bb-102">Niezawodna korelacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="737bb-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="737bb-103">Niezawodna korelacja dwukierunkowa, znany także jako wywołanie zwrotne korelacji jest przydatne, gdy usługi przepływu pracy istnieje wymaganie, aby wysłać wywołanie zwrotne do początkowego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="737bb-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="737bb-104">W odróżnieniu od dupleks WCF wywołania zwrotnego może się zdarzyć w dowolnym momencie w przyszłości i nie jest związany z tego samego kanału lub trwania kanału. Jedynym wymaganiem jest, że obiekt wywołujący ma aktywny punkt końcowy nasłuchiwać komunikatów wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="737bb-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="737bb-105">Dzięki temu dwie usługi przepływu pracy do komunikowania się z konwersacji długotrwałych.</span><span class="sxs-lookup"><span data-stu-id="737bb-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="737bb-106">Ten temat zawiera omówienie niezawodna korelacja dwukierunkowa.</span><span class="sxs-lookup"><span data-stu-id="737bb-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="737bb-107">Za pomocą niezawodna korelacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="737bb-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="737bb-108">Niezawodna korelacja dwukierunkowa, te dwie usługi korzystać z obsługą kontekstu powiązania, obsługującej dwukierunkowe operacje, takie jak <xref:System.ServiceModel.NetTcpContextBinding> lub <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="737bb-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="737bb-109">Wywołujący rejestrów usługi <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> dla żądanego powiązania na kliencie <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="737bb-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="737bb-110">Usługa odbierająca odbiera tych danych w wywołaniu początkową, a następnie używa go samodzielnie <xref:System.ServiceModel.Endpoint> w <xref:System.ServiceModel.Activities.Send> działania, która wywołuje tę funkcję do wywoływania usługi.</span><span class="sxs-lookup"><span data-stu-id="737bb-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="737bb-111">W tym przykładzie dwie usługi komunikują się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="737bb-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="737bb-112">Pierwsza usługa wywołuje metodę dla drugiej usługi, a następnie czeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="737bb-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="737bb-113">Nazwa metody wywołania zwrotnego wie, drugi usługi, ale punktu końcowego usługi, który implementuje ta metoda nie jest znany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="737bb-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="737bb-114">Niezawodna komunikacja dwukierunkowa może zawierać tylko używane podczas <xref:System.ServiceModel.Channels.AddressingVersion> punktu końcowego jest konfigurowana <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="737bb-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="737bb-115">Jeśli nie jest dostępna, a następnie <xref:System.InvalidOperationException> wyjątek z następującym komunikatem: "wiadomość zawiera nagłówek Kontekst wywołania zwrotnego z odwołania do punktu końcowego dla [standard](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="737bb-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="737bb-116">Kontekst wywołania zwrotnego być przesyłany tylko w przypadku, gdy wersja adresowania mogła być skonfigurowano adresowania "WSAddressing10".</span><span class="sxs-lookup"><span data-stu-id="737bb-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="737bb-117">W poniższym przykładzie przepływu pracy jest hostowana usługa, która tworzy wywołanie zwrotne <xref:System.ServiceModel.Endpoint> przy użyciu <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="737bb-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="737bb-118">Przepływ pracy, który implementuje ta usługa przepływu pracy inicjuje korelacji wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działania i zawiera odwołania do tego punktu końcowego wywołania zwrotnego, z <xref:System.ServiceModel.Activities.Receive> działanie, które mają związek z <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="737bb-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="737bb-119">Poniższy przykład przedstawia przepływ pracy, który jest zwracany z `GetWF1` metody.</span><span class="sxs-lookup"><span data-stu-id="737bb-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="737bb-120">Drugi usługi przepływu pracy znajduje się za pomocą powiązania dostarczane przez system, oparte na kontekście.</span><span class="sxs-lookup"><span data-stu-id="737bb-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="737bb-121">Przepływ pracy, który implementuje ta usługa przepływu pracy rozpoczyna się od <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="737bb-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="737bb-122">Inicjuje działania to otrzymują korelacji wywołania zwrotnego dla tej usługi, opóźnienia w danym okresie czasu, aby zasymulować długotrwała praca, a następnie wywołania do pierwszej usługi przy użyciu tego kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu do usługi.</span><span class="sxs-lookup"><span data-stu-id="737bb-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="737bb-123">Poniższy przykład przedstawia przepływ pracy, który jest zwracany z wywołania `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="737bb-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="737bb-124">Należy pamiętać, że <xref:System.ServiceModel.Activities.Send> działanie ma symbol zastępczy adres `http://www.contoso.com`; rzeczywisty adres używany w czasie wykonywania jest adres podany wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="737bb-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="737bb-125">Gdy `StartOrder` metoda jest wywoływana pierwszego przepływu pracy, wyświetlane następujące dane wyjściowe, które przedstawia przepływ wykonania przy użyciu dwóch przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="737bb-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="737bb-126">W tym przykładzie przepływami pracy jawnie zarządzać za pomocą korelacji <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="737bb-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="737bb-127">Powodu pojedynczego korelacji w tych przepływów pracy przykładowej domyślnie <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania mogą być wystarczające.</span><span class="sxs-lookup"><span data-stu-id="737bb-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737bb-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="737bb-128">See Also</span></span>  
 [<span data-ttu-id="737bb-129">Niezawodna komunikacja dwukierunkowa &#91;WF — przykłady&#93;</span><span class="sxs-lookup"><span data-stu-id="737bb-129">Durable Duplex &#91;WF Samples&#93;</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
