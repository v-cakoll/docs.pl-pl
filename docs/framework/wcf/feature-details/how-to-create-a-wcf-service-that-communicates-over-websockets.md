---
title: 'Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: a9b3ae8d8dcac7844e241fa668e1199669d216e6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798404"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="b3959-102">Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets</span><span class="sxs-lookup"><span data-stu-id="b3959-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="b3959-103">Usługi WCF i klienci mogą używać <xref:System.ServiceModel.NetHttpBinding> powiązania do komunikowania się przez protokół WebSockets.</span><span class="sxs-lookup"><span data-stu-id="b3959-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="b3959-104">WebSockets będą używane podczas <xref:System.ServiceModel.NetHttpBinding> określa kontrakt usługi definiuje kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="b3959-105">W tym temacie opisano, jak wdrożyć usługę WCF i klienta, który używa <xref:System.ServiceModel.NetHttpBinding> do komunikowania się przez protokół WebSockets.</span><span class="sxs-lookup"><span data-stu-id="b3959-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="b3959-106">Zdefiniuj usługę</span><span class="sxs-lookup"><span data-stu-id="b3959-106">Define the Service</span></span>  
  
1.  <span data-ttu-id="b3959-107">Zdefiniuj kontrakt wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="b3959-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="b3959-108">Niniejszej Umowy będą realizowane przez aplikację klienta, aby umożliwić usłudze wysyłać komunikaty do klienta.</span><span class="sxs-lookup"><span data-stu-id="b3959-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2.  <span data-ttu-id="b3959-109">Definiowanie kontraktu usługi i określ `IStockQuoteCallback` interfejs jako kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3.  <span data-ttu-id="b3959-110">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="b3959-110">Implement the service contract.</span></span>  
  
    ```  
    public class StockQuoteService : IStockQuoteService  
        {  
            public async Task StartSendingQuotes()  
            {  
                var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
                var random = new Random();  
                double price = 29.00;  
  
                while (((IChannel)callback).State == CommunicationState.Opened)  
                {  
                    await callback.SendQuote("MSFT", price);  
                    price += random.NextDouble();  
                    await Task.Delay(1000);  
                }  
            }  
        }  
    ```  
  
     <span data-ttu-id="b3959-111">Operacja usługi `StartSendingQuotes` jest implementowany jako wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="b3959-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="b3959-112">Możemy pobrać za pomocą kanału zwrotnego `OperationContext` i jeśli kanał jest otwarty, udostępnimy asynchronicznego wywołania w kanale wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4.  <span data-ttu-id="b3959-113">Konfigurowanie usługi</span><span class="sxs-lookup"><span data-stu-id="b3959-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />        
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="b3959-114">Plik konfiguracji usługi opiera się na punktami końcowymi programu WCF na domyślne.</span><span class="sxs-lookup"><span data-stu-id="b3959-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="b3959-115">`<protocolMapping>` Sekcja jest używana do określenia, że `NetHttpBinding` powinny być używane domyślne punkty końcowe utworzone.</span><span class="sxs-lookup"><span data-stu-id="b3959-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="b3959-116">Zdefiniuj klienta</span><span class="sxs-lookup"><span data-stu-id="b3959-116">Define the Client</span></span>  
  
1.  <span data-ttu-id="b3959-117">Zaimplementować kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="b3959-118">Operacja kontrakt wywołania zwrotnego jest implementowany jako metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="b3959-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1.  <span data-ttu-id="b3959-119">Zaimplementuj kod klienta.</span><span class="sxs-lookup"><span data-stu-id="b3959-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();              
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="b3959-120">Obiekt CallbackHandler jest powtarzany tutaj dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="b3959-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="b3959-121">Aplikacja kliencka tworzy nowy obiekt InstanceContext i określa implementację interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="b3959-122">Następnie tworzy wystąpienie klasy serwera proxy, wysyłanie odwołaniem do nowo utworzony obiekt InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="b3959-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="b3959-123">Gdy klient wywołuje usługę, usługa będzie wywoływać klienta przy użyciu określonych kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3959-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2.  <span data-ttu-id="b3959-124">Konfigurowanie klienta</span><span class="sxs-lookup"><span data-stu-id="b3959-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>   
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="b3959-125">Nic specjalnego nie należy wykonać w konfiguracji klienta, wystarczy tylko określić klienta po stronie punktu końcowego za pomocą `NetHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b3959-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3959-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3959-126">Example</span></span>  
 <span data-ttu-id="b3959-127">Oto kompletny kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="b3959-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```  
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  https://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />        
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```  
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();              
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!—App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>   
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3959-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3959-128">See Also</span></span>  
 [<span data-ttu-id="b3959-129">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b3959-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [<span data-ttu-id="b3959-130">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b3959-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
