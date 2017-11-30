---
title: Niezawodna korelacja dwukierunkowa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc7a6655467fccf924783fea9110bdaf1b788675
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="5ff75-102">Niezawodna korelacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="5ff75-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="5ff75-103">Niezawodna korelacja dwukierunkowa, znanej także jako wywołania zwrotnego korelacji jest przydatne, gdy usługi przepływu pracy istnieje wymaganie, aby wysłać wywołanie zwrotne do początkowego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5ff75-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="5ff75-104">W odróżnieniu od dupleks WCF wywołania zwrotnego może się zdarzyć w dowolnym momencie w przyszłości i nie jest powiązany ten sam kanał lub trwania kanału. Jedynym wymaganiem jest wywołującego aktywnego punktu końcowego nasłuchiwania dla komunikatu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5ff75-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="5ff75-105">Dzięki temu dwie usługi przepływu pracy do komunikacji w konwersacji długotrwałe.</span><span class="sxs-lookup"><span data-stu-id="5ff75-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="5ff75-106">Ten temat zawiera omówienie niezawodna korelacja dwukierunkowa.</span><span class="sxs-lookup"><span data-stu-id="5ff75-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="5ff75-107">Przy użyciu niezawodna korelacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="5ff75-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="5ff75-108">Niezawodna korelacja dwukierunkowa, te dwie usługi korzystać z obsługą kontekstu powiązania, które obsługuje dwukierunkowe operacje, takie jak <xref:System.ServiceModel.NetTcpContextBinding> lub <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="5ff75-109">Wywołanie rejestrów usługi <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> z powiązaniem żądaną na kliencie ich <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="5ff75-110">Usługa odbierająca odbiera tych danych w wywołaniu początkowej i używa go samodzielnie <xref:System.ServiceModel.Endpoint> w <xref:System.ServiceModel.Activities.Send> działanie, które wykonuje wywołanie powrót do wywoływania usługi.</span><span class="sxs-lookup"><span data-stu-id="5ff75-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="5ff75-111">W tym przykładzie dwie usługi komunikują się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="5ff75-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="5ff75-112">Pierwszej usługi wywołuje metodę dla drugiego usługi, a następnie czeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="5ff75-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="5ff75-113">Drugi usługi zna nazwę metody wywołania zwrotnego, ale punktu końcowego usługi, który implementuje ta metoda nie jest znany w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="5ff75-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ff75-114">Niezawodna komunikacja dwukierunkowa tylko może być użyta, gdy <xref:System.ServiceModel.Channels.AddressingVersion> punktu końcowego jest skonfigurowany z <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="5ff75-115">Jeśli nie, a następnie <xref:System.InvalidOperationException> wyjątek z następującym komunikatem: "wiadomość zawiera nagłówek kontekstu wywołania zwrotnego z odwołaniem do punktu końcowego dla obiektu AddressingVersion" Addressing200408 (HYPERLINK "http://schemas.xmlsoap.org/ws/2004/08/ adresowanie"http://schemas.xmlsoap.org/ws/2004/08/addressing)".</span><span class="sxs-lookup"><span data-stu-id="5ff75-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for AddressingVersion 'Addressing200408 ( HYPERLINK "http://schemas.xmlsoap.org/ws/2004/08/addressing" http://schemas.xmlsoap.org/ws/2004/08/addressing)'.</span></span> <span data-ttu-id="5ff75-116">Kontekst wywołania zwrotnego może być przesyłany tylko po skonfigurowaniu właściwości AddressingVersion o wartości "Adresowania WSAddressing10"."</span><span class="sxs-lookup"><span data-stu-id="5ff75-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'."</span></span>  
  
 <span data-ttu-id="5ff75-117">W poniższym przykładzie usługi przepływu pracy jest hostowana tworzącą wywołanie zwrotne <xref:System.ServiceModel.Endpoint> przy użyciu <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="5ff75-118">Przepływ pracy, który implementuje ta usługa przepływu pracy inicjuje korelację wywołania zwrotnego z jego <xref:System.ServiceModel.Activities.Send> działania i odwołuje się do tego punktu końcowego wywołania zwrotnego z <xref:System.ServiceModel.Activities.Receive> działanie, które są powiązane z <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="5ff75-119">Poniższy przykład przedstawia przepływ pracy, który jest zwracany z `GetWF1` metody.</span><span class="sxs-lookup"><span data-stu-id="5ff75-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="5ff75-120">Drugi usługi przepływu pracy jest hostowany za pomocą powiązania dostarczane przez system, na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5ff75-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="5ff75-121">Przepływ pracy, który implementuje ta usługa przepływu pracy, który rozpoczyna się od <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="5ff75-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="5ff75-122">Inicjuje działania to odbierać korelacji wywołania zwrotnego dla tej usługi, opóźnienia w określonym czasie, aby symulować długotrwałe pracy, a następnie wywołania do pierwszej usługi przy użyciu kontekstu wywołania zwrotnego, który został przekazany w pierwszym wywołaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="5ff75-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="5ff75-123">Poniższy przykład przedstawia przepływ pracy, który jest zwracany po wywołaniu `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="5ff75-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="5ff75-124">Należy pamiętać, że <xref:System.ServiceModel.Activities.Send> działanie ma adres symbolu zastępczego `http://www.contoso.com`; rzeczywisty adres używany w czasie wykonywania jest adres podany wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5ff75-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="5ff75-125">Gdy `StartOrder` metoda jest wywoływana na pierwszym przepływu pracy, zostanie wyświetlone następujące dane wyjściowe, który wskazuje kierunek wykonywania za pośrednictwem dwóch przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="5ff75-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="5ff75-126">W tym przykładzie przepływami pracy jawnego zarządzania przy użyciu korelacji <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="5ff75-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="5ff75-127">Powodu pojedynczego korelacji w przepływach pracy te przykładowe, domyślnie <xref:System.ServiceModel.Activities.CorrelationHandle> zarządzania byłaby wystarczające.</span><span class="sxs-lookup"><span data-stu-id="5ff75-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff75-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ff75-128">See Also</span></span>  
 [<span data-ttu-id="5ff75-129">Niezawodna komunikacja dwukierunkowa &#91; WF — przykłady &#93;</span><span class="sxs-lookup"><span data-stu-id="5ff75-129">Durable Duplex &#91;WF Samples&#93;</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
