---
title: Wywoływanie usługi typu REST z poziomu usługi WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: be9f15d35ec00ba91a06abf5a0a413b59452270b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184247"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="05614-102">Wywoływanie usługi typu REST z poziomu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="05614-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="05614-103">Podczas wywoływania usługi typu REST z regularnych usługi WCF (w oparciu o protokół SOAP), kontekst operacji dla metody usługi, (który zawiera informacje dotyczące żądania przychodzące) zastępuje kontekstu, który powinien być używany przez żądania wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="05614-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="05614-104">Powoduje to, że żądania HTTP GET przejść do żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="05614-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="05614-105">Aby wymusić uruchomienia usługi WCF do użycia w kontekście wywoływanie usługi typu REST, Utwórz nowy <xref:System.ServiceModel.OperationContextScope> i wywoływanie usługi typu REST z wewnątrz zakresu kontekstu operacji.</span><span class="sxs-lookup"><span data-stu-id="05614-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="05614-106">W tym temacie opisano sposób tworzenia prostych przykładowych, który ilustruje tej techniki.</span><span class="sxs-lookup"><span data-stu-id="05614-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="05614-107">Definiowanie kontraktu usługi opartego na interfejsie REST</span><span class="sxs-lookup"><span data-stu-id="05614-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="05614-108">Definiowanie prostych opartego na interfejsie REST kontraktu usługi:</span><span class="sxs-lookup"><span data-stu-id="05614-108">Define a simple  REST-style service contract:</span></span>  
  
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
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="05614-109">Implementowanie kontraktu usługi opartego na interfejsie REST</span><span class="sxs-lookup"><span data-stu-id="05614-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="05614-110">Implementowanie kontraktu usługi typu REST:</span><span class="sxs-lookup"><span data-stu-id="05614-110">Implement the REST-style service contract:</span></span>  
  
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
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="05614-111">Definiowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="05614-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="05614-112">Definiowanie kontraktu usługi WCF, która będzie służyć do wywołania usługi typu REST:</span><span class="sxs-lookup"><span data-stu-id="05614-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
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
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="05614-113">Implementowanie kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="05614-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="05614-114">Implementowanie kontraktu usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="05614-114">Implement the WCF service contract:</span></span>  
  
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
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="05614-115">Utwórz serwer proxy klienta dla usługi opartego na interfejsie REST</span><span class="sxs-lookup"><span data-stu-id="05614-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="05614-116">Za pomocą <xref:System.ServiceModel.ClientBase%601> wdrożyć serwer proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="05614-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="05614-117">Dla każdej metody o nazwie nową <xref:System.ServiceModel.OperationContextScope> są tworzone i używane do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="05614-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
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
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="05614-118">Hostowanie i wywołania usług</span><span class="sxs-lookup"><span data-stu-id="05614-118">Host and call the services</span></span>  
 <span data-ttu-id="05614-119">Hostowanie obie te usługi w aplikacji konsolowej, dodając wymagane punkty końcowe i zachowania.</span><span class="sxs-lookup"><span data-stu-id="05614-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="05614-120">A następnie wywołać regularne usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="05614-120">And then call the regular WCF service:</span></span>  
  
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
  
## <a name="complete-code-listing"></a><span data-ttu-id="05614-121">Kompletna lista kodu</span><span class="sxs-lookup"><span data-stu-id="05614-121">Complete code listing</span></span>  
 <span data-ttu-id="05614-122">Poniżej przedstawiono pełną listę przykładowych zaimplementowane w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="05614-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05614-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05614-123">See Also</span></span>  
 [<span data-ttu-id="05614-124">Instrukcje: tworzenie podstawowej, opartej na protokole HTTP usługi internetowej programu WCF</span><span class="sxs-lookup"><span data-stu-id="05614-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="05614-125">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="05614-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
