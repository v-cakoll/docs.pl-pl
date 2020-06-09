---
title: Wywoływanie usługi typu REST z poziomu usługi WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: eaa5d08faa335740124fcf698b22d2d324cd2c54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576489"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="26916-102">Wywoływanie usługi typu REST z poziomu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="26916-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="26916-103">Podczas wywoływania usługi w stylu REST przy użyciu zwykłej (opartej na SOAP) usługi WCF, kontekst operacji w metodzie usługi (która zawiera informacje o żądaniu przychodzącym) zastępuje kontekst, który powinien być używany przez żądanie wychodzące.</span><span class="sxs-lookup"><span data-stu-id="26916-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="26916-104">Powoduje to, że żądania HTTP GET zmieniają się na żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="26916-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="26916-105">Aby wymusić użycie przez usługę WCF kontekstu właściwego do wywoływania usługi w stylu REST, Utwórz nową <xref:System.ServiceModel.OperationContextScope> i Wywołaj usługę stylu REST z wewnątrz zakresu kontekstu operacji.</span><span class="sxs-lookup"><span data-stu-id="26916-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="26916-106">W tym temacie opisano sposób tworzenia prostego przykładu, który ilustruje tę technikę.</span><span class="sxs-lookup"><span data-stu-id="26916-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="26916-107">Definiowanie kontraktu usługi w stylu REST</span><span class="sxs-lookup"><span data-stu-id="26916-107">Define the REST-style service contract</span></span>

<span data-ttu-id="26916-108">Definiowanie prostego kontraktu usługi w stylu REST:</span><span class="sxs-lookup"><span data-stu-id="26916-108">Define a simple  REST-style service contract:</span></span>

```csharp
[ServiceContract]
public interface IRestInterface
{
    [OperationContract, WebGet]
    int Add(int x, int y);

    [OperationContract, WebGet]
    string Echo(string input);
}
```

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="26916-109">Implementowanie kontraktu usługi w stylu REST</span><span class="sxs-lookup"><span data-stu-id="26916-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="26916-110">Zaimplementuj kontrakt usługi w stylu REST:</span><span class="sxs-lookup"><span data-stu-id="26916-110">Implement the REST-style service contract:</span></span>

```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }

    public string Echo(string input)
    {
        return input;
    }
}
```

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="26916-111">Definiowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="26916-111">Define the WCF service contract</span></span>

<span data-ttu-id="26916-112">Zdefiniuj kontrakt usługi WCF, który będzie używany do wywoływania usługi w stylu REST:</span><span class="sxs-lookup"><span data-stu-id="26916-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);

    [OperationContract]
    string CallEcho(string input);
}
```

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="26916-113">Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="26916-113">Implement the WCF service contract</span></span>

<span data-ttu-id="26916-114">Zaimplementuj kontrakt usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="26916-114">Implement the WCF service contract:</span></span>

```csharp
public class NormalService : INormalInterface
{
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
    public int CallAdd(int x, int y)
    {
        return client.Add(x, y);
    }

    public string CallEcho(string input)
    {
        return client.Echo(input);
    }
}
```

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="26916-115">Tworzenie serwera proxy klienta dla usługi stylu REST</span><span class="sxs-lookup"><span data-stu-id="26916-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="26916-116">Korzystanie <xref:System.ServiceModel.ClientBase%601> z programu w celu zaimplementowania serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="26916-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="26916-117">Dla każdej wywoływanej metody <xref:System.ServiceModel.OperationContextScope> zostanie utworzony i użyty do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="26916-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```

## <a name="host-and-call-the-services"></a><span data-ttu-id="26916-118">Hostowanie i wywoływanie usług</span><span class="sxs-lookup"><span data-stu-id="26916-118">Host and call the services</span></span>

<span data-ttu-id="26916-119">Hostowanie obu usług w aplikacji konsolowej, Dodawanie wymaganych punktów końcowych i zachowań.</span><span class="sxs-lookup"><span data-stu-id="26916-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="26916-120">A następnie Wywołaj zwykłe usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="26916-120">And then call the regular WCF service:</span></span>

```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```

## <a name="complete-code-listing"></a><span data-ttu-id="26916-121">Kompletna lista kodu</span><span class="sxs-lookup"><span data-stu-id="26916-121">Complete code listing</span></span>

<span data-ttu-id="26916-122">Poniżej znajduje się kompletna lista przykładów zaimplementowanych w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="26916-122">The following is a complete listing of the sample implemented in this topic:</span></span>

```csharp
public class CallingRESTSample
{
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";

    [ServiceContract]
    public interface IRestInterface
    {
        [OperationContract, WebGet]
        int Add(int x, int y);
        [OperationContract, WebGet]
        string Echo(string input);
    }

    [ServiceContract]
    public interface INormalInterface
    {
        [OperationContract]
        int CallAdd(int x, int y);
        [OperationContract]
        string CallEcho(string input);
    }

    public class RestService : IRestInterface
    {
        public int Add(int x, int y)
        {
            return x + y;
        }

        public string Echo(string input)
        {
            return input;
        }
    }

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
    {
        public MyRestClient(string address)
            : base(new WebHttpBinding(), new EndpointAddress(address))
        {
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());
        }

        public int Add(int x, int y)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Add(x, y);
            }
        }

        public string Echo(string input)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Echo(input);
            }
        }
    }

    public class NormalService : INormalInterface
    {
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
        public int CallAdd(int x, int y)
        {
            return client.Add(x, y);
        }

        public string CallEcho(string input)
        {
            return client.Echo(input);
        }
    }

    public static void Main()
    {
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
        restHost.Open();

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
        normalHost.Open();

        Console.WriteLine("Hosts opened");

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
        INormalInterface proxy = factory.CreateChannel();

        Console.WriteLine(proxy.CallAdd(123, 456));
        Console.WriteLine(proxy.CallEcho("Hello world"));
    }
}
```

## <a name="see-also"></a><span data-ttu-id="26916-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26916-123">See also</span></span>

- [<span data-ttu-id="26916-124">Instrukcje: tworzenie podstawowej, opartej na protokole HTTP usługi internetowej programu WCF</span><span class="sxs-lookup"><span data-stu-id="26916-124">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="26916-125">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="26916-125">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
