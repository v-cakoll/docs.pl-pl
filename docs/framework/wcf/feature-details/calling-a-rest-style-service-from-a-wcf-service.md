---
title: Wywoływanie usługi typu REST z poziomu usługi WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 8f520b1f77b9ca41b9fd2b8d51c1b935ab1e0a87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="0f756-102">Wywoływanie usługi typu REST z poziomu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="0f756-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="0f756-103">Podczas wywoływania usługi typu REST z regularne usługi WCF (opartego na protokole SOAP), kontekstu operacji na metodzie usługi (zawierający informacje dotyczące żądania przychodzące) przesłania kontekstu, która powinna być używana przez żądania wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="0f756-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="0f756-104">Powoduje to, że żądania HTTP GET, można zmienić na żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="0f756-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="0f756-105">Aby wymusić usługi WCF do kontekstu prawo do wywoływania usługi typu REST, Utwórz nową <xref:System.ServiceModel.OperationContextScope> i wywołać usługi typu REST z wewnątrz operacji kontekstu zakresu.</span><span class="sxs-lookup"><span data-stu-id="0f756-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="0f756-106">W tym temacie opisano sposób tworzenia prostego przykładu, która ilustruje tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f756-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="0f756-107">Definiowanie kontraktu usługi typu REST</span><span class="sxs-lookup"><span data-stu-id="0f756-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="0f756-108">Zdefiniuj kontrakt usługi typu REST prosty:</span><span class="sxs-lookup"><span data-stu-id="0f756-108">Define a simple  REST-style service contract:</span></span>  
  
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
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="0f756-109">Implementowanie kontraktu usługi typu REST</span><span class="sxs-lookup"><span data-stu-id="0f756-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="0f756-110">Implementowanie kontraktu usługi typu REST:</span><span class="sxs-lookup"><span data-stu-id="0f756-110">Implement the REST-style service contract:</span></span>  
  
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
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="0f756-111">Definiowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="0f756-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="0f756-112">Definiowanie kontraktu usługi WCF, która będzie służyć do wywołania tej usługi typu REST:</span><span class="sxs-lookup"><span data-stu-id="0f756-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
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
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="0f756-113">Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="0f756-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="0f756-114">Implementowanie kontraktu usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="0f756-114">Implement the WCF service contract:</span></span>  
  
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
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="0f756-115">Tworzenie klienta serwera proxy usługi typu REST</span><span class="sxs-lookup"><span data-stu-id="0f756-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="0f756-116">Przy użyciu <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` wdrożenie serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="0f756-116">Using <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implement the client proxy.</span></span> <span data-ttu-id="0f756-117">Dla każdej metody o nazwie nowy <xref:System.ServiceModel.OperationContextScope> są tworzone i używane do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="0f756-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
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
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="0f756-118">Hostowanie i wywołania usług</span><span class="sxs-lookup"><span data-stu-id="0f756-118">Host and call the services</span></span>  
 <span data-ttu-id="0f756-119">Host obie te usługi w aplikacji konsoli, dodawanie wymagane punkty końcowe i zachowania.</span><span class="sxs-lookup"><span data-stu-id="0f756-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="0f756-120">A następnie wywołać regularne usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="0f756-120">And then call the regular WCF service:</span></span>  
  
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
  
## <a name="complete-code-listing"></a><span data-ttu-id="0f756-121">Kompletny kod</span><span class="sxs-lookup"><span data-stu-id="0f756-121">Complete code listing</span></span>  
 <span data-ttu-id="0f756-122">Poniżej znajduje się pełna lista próbki zaimplementowana w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="0f756-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f756-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f756-123">See Also</span></span>  
 [<span data-ttu-id="0f756-124">Instrukcje: tworzenie podstawowej, opartej na protokole HTTP usługi internetowej programu WCF</span><span class="sxs-lookup"><span data-stu-id="0f756-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="0f756-125">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="0f756-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
