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
# <a name="durable-duplex-correlation"></a><span data-ttu-id="295d7-102">Niezawodna korelacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="295d7-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="295d7-103">Trwałej korelacji dupleksu, znany również jako korelacji wywołania zwrotnego, jest przydatne, gdy usługa przepływu pracy ma wymóg, aby wysłać wywołanie zwrotne do początkowego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="295d7-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="295d7-104">W przeciwieństwie do dupleksu WCF wywołanie zwrotne może się zdarzyć w dowolnym momencie w przyszłości i nie jest powiązany z tego samego kanału lub okresu istnienia kanału; jedynym wymaganiem jest, że obiekt wywołujący mają aktywny punkt końcowy nasłuchiwania wiadomości wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="295d7-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="295d7-105">Dzięki temu dwie usługi przepływu pracy do komunikowania się w długotrwałej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="295d7-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="295d7-106">Ten temat zawiera omówienie trwałej korelacji dupleksu.</span><span class="sxs-lookup"><span data-stu-id="295d7-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="295d7-107">Korzystanie z trwałej korelacji dupleksu</span><span class="sxs-lookup"><span data-stu-id="295d7-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="295d7-108">Aby użyć trwałej korelacji dupleksu, dwie usługi muszą używać powiązania kontekstowego, <xref:System.ServiceModel.NetTcpContextBinding> <xref:System.ServiceModel.WSHttpContextBinding>które obsługuje operacje dwukierunkowe, takie jak lub .</span><span class="sxs-lookup"><span data-stu-id="295d7-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="295d7-109">Usługa wywołująca rejestruje <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> z żądanym powiązaniem dla swojego klienta. <xref:System.ServiceModel.Endpoint></span><span class="sxs-lookup"><span data-stu-id="295d7-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="295d7-110">Usługa odbierająca odbiera te dane w wywołaniu początkowym, <xref:System.ServiceModel.Endpoint> a <xref:System.ServiceModel.Activities.Send> następnie używa ich samodzielnie w działaniu, które sprawia, że połączenie z powrotem do usługi wywołującej.</span><span class="sxs-lookup"><span data-stu-id="295d7-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="295d7-111">W tym przykładzie dwie usługi komunikują się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="295d7-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="295d7-112">Pierwsza usługa wywołuje metodę w drugiej usłudze, a następnie czeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="295d7-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="295d7-113">Druga usługa zna nazwę metody wywołania zwrotnego, ale punkt końcowy usługi, która implementuje tę metodę, nie jest znany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="295d7-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="295d7-114">Trwałego dupleksu można <xref:System.ServiceModel.Channels.AddressingVersion> używać tylko wtedy, <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>gdy punkt końcowy jest skonfigurowany z programem .</span><span class="sxs-lookup"><span data-stu-id="295d7-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="295d7-115">Jeśli tak nie jest, wyjątek jest zgłaszany z następującym <xref:System.InvalidOperationException> komunikatem: "Wiadomość zawiera nagłówek kontekstu wywołania zwrotnego z odwołaniem do punktu końcowego [addressingversion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="295d7-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="295d7-116">Kontekst wywołania zwrotnego może być przesyłany tylko wtedy, gdy AddressingVersion jest skonfigurowany z "WSAddressing10".</span><span class="sxs-lookup"><span data-stu-id="295d7-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="295d7-117">W poniższym przykładzie hostowana jest usługa przepływu <xref:System.ServiceModel.Endpoint> pracy, która tworzy wywołanie zwrotne przy użyciu programu <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="295d7-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="295d7-118">Przepływ pracy, który implementuje tę usługę przepływu pracy inicjuje korelację wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działaniem i odwołuje się do tego punktu końcowego wywołania zwrotnego <xref:System.ServiceModel.Activities.Receive> z działania, które koreluje z <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="295d7-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="295d7-119">Poniższy przykład reprezentuje przepływ pracy, `GetWF1` który jest zwracany z metody.</span><span class="sxs-lookup"><span data-stu-id="295d7-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="295d7-120">Druga usługa przepływu pracy jest obsługiwana przy użyciu powiązania opartego na systemie, opartego na kontekście.</span><span class="sxs-lookup"><span data-stu-id="295d7-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="295d7-121">Przepływ pracy, który implementuje tę usługę <xref:System.ServiceModel.Activities.Receive> przepływu pracy rozpoczyna się od działania.</span><span class="sxs-lookup"><span data-stu-id="295d7-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="295d7-122">To działanie odbierania inicjuje korelację wywołania zwrotnego dla tej usługi, opóźnienia przez pewien okres czasu, aby symulować długotrwałą pracę, a następnie wywołania z powrotem do pierwszej usługi przy użyciu kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu do usługi.</span><span class="sxs-lookup"><span data-stu-id="295d7-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="295d7-123">Poniższy przykład przedstawia przepływ pracy, który `GetWF2`jest zwracany z wywołania do .</span><span class="sxs-lookup"><span data-stu-id="295d7-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="295d7-124">Należy zauważyć, że <xref:System.ServiceModel.Activities.Send> działanie ma `http://www.contoso.com`adres zastępczy ; rzeczywisty adres używany w czasie wykonywania jest podany adres wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="295d7-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="295d7-125">Gdy `StartOrder` metoda jest wywoływana w pierwszym przepływie pracy, wyświetlane są następujące dane wyjściowe, który pokazuje przepływ wykonywania za pośrednictwem dwóch przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="295d7-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="295d7-126">W tym przykładzie oba przepływy pracy jawnie <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>zarządzają korelacją przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="295d7-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="295d7-127">Ponieważ w tych przykładowych przepływach pracy istniała tylko <xref:System.ServiceModel.Activities.CorrelationHandle> jedna korelacja, domyślne zarządzanie byłoby wystarczające.</span><span class="sxs-lookup"><span data-stu-id="295d7-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
