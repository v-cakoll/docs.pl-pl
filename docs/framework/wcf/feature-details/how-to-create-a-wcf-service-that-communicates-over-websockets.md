---
title: 'Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: 80c62ddc6630d26c6c178d1eeff8c6df05bf1d00
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051938"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="24ef2-102">Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets</span><span class="sxs-lookup"><span data-stu-id="24ef2-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="24ef2-103">Usługi i klienci WCF mogą używać <xref:System.ServiceModel.NetHttpBinding> powiązania do komunikacji za pośrednictwem obiektów WebSockets.</span><span class="sxs-lookup"><span data-stu-id="24ef2-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="24ef2-104">Usługa WebSockets zostanie użyta, gdy <xref:System.ServiceModel.NetHttpBinding> określi kontrakt usługi definiuje kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="24ef2-105">W tym temacie opisano sposób implementacji usługi WCF i klienta, który używa programu <xref:System.ServiceModel.NetHttpBinding> do komunikacji za pośrednictwem usług WebSockets.</span><span class="sxs-lookup"><span data-stu-id="24ef2-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="24ef2-106">Definiowanie usługi</span><span class="sxs-lookup"><span data-stu-id="24ef2-106">Define the Service</span></span>  
  
1. <span data-ttu-id="24ef2-107">Definiowanie kontraktu wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="24ef2-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="24ef2-108">Ta umowa zostanie wdrożona przez aplikację kliencką, aby umożliwić usłudze wysyłanie komunikatów z powrotem do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="24ef2-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="24ef2-109">Zdefiniuj kontrakt usługi i określ `IStockQuoteCallback` interfejs jako kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="24ef2-110">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="24ef2-110">Implement the service contract.</span></span>  
  
    ```csharp
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
  
     <span data-ttu-id="24ef2-111">Operacja usługi `StartSendingQuotes` jest zaimplementowana jako wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="24ef2-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="24ef2-112">Pobieramy kanał wywołania zwrotnego przy użyciu `OperationContext` i Jeśli kanał jest otwarty, my wywołamy wywołanie asynchroniczne w kanale wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="24ef2-113">Konfigurowanie usługi</span><span class="sxs-lookup"><span data-stu-id="24ef2-113">Configure the service</span></span>  
  
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
  
     <span data-ttu-id="24ef2-114">Plik konfiguracji usługi opiera się na domyślnych punktach końcowych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="24ef2-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="24ef2-115">`<protocolMapping>`Sekcja służy do określenia, że `NetHttpBinding` powinny być używane dla utworzonych domyślnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="24ef2-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="24ef2-116">Definiowanie klienta</span><span class="sxs-lookup"><span data-stu-id="24ef2-116">Define the Client</span></span>  
  
1. <span data-ttu-id="24ef2-117">Zaimplementuj kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="24ef2-118">Operacja kontraktu wywołania zwrotnego jest zaimplementowana jako Metoda asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="24ef2-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="24ef2-119">Zaimplementuj kod klienta.</span><span class="sxs-lookup"><span data-stu-id="24ef2-119">Implement the client code.</span></span>  
  
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
  
         <span data-ttu-id="24ef2-120">Obiekt callbackhandlera jest powtarzana w tym miejscu do przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="24ef2-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="24ef2-121">Aplikacja kliencka tworzy nową metodę InstanceContext i określa implementację interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="24ef2-122">Następnie tworzy wystąpienie klasy proxy, wysyłając odwołanie do nowo utworzonej metody InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="24ef2-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="24ef2-123">Gdy klient wywołuje usługę, usługa wywoła klienta przy użyciu określonego kontraktu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="24ef2-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="24ef2-124">Konfigurowanie klienta</span><span class="sxs-lookup"><span data-stu-id="24ef2-124">Configure the client</span></span>  
  
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
  
         <span data-ttu-id="24ef2-125">Nie ma żadnych specjalnych, które należy wykonać w konfiguracji klienta, wystarczy określić punkt końcowy po stronie klienta przy użyciu `NetHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="24ef2-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24ef2-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="24ef2-126">Example</span></span>  
 <span data-ttu-id="24ef2-127">Poniżej znajduje się kompletny kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="24ef2-127">The following is the complete code used in this topic.</span></span>  
  
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
  
```csharp
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
  
```aspx-csharp
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
<!--App.config -->  
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
  
## <a name="see-also"></a><span data-ttu-id="24ef2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24ef2-128">See also</span></span>

- [<span data-ttu-id="24ef2-129">Operacje synchroniczne i asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="24ef2-129">Synchronous and Asynchronous Operations</span></span>](../synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="24ef2-130">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="24ef2-130">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)
