---
title: 'Instrukcje: Wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: 62b41a75-cf40-4c52-a842-a5f1c70e247f
ms.openlocfilehash: 33ee5d2c9206b16b1667abd5f6d6c811ff955969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185385"
---
# <a name="how-to-implement-a-client-application-that-uses-the-discovery-proxy-to-find-a-service"></a><span data-ttu-id="a1091-102">Instrukcje: Wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="a1091-102">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>
<span data-ttu-id="a1091-103">Ten temat jest trzecim z trzech tematów, który omawia sposób implementacji serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="a1091-103">This topic is the third of three topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="a1091-104">W poprzednim temacie [Jak: Implementowanie usługi odnajdywalnej, która rejestruje się za pomocą serwera proxy odnajdowania,](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)zaimplementowano usługę WCF, która rejestruje się za pomocą serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="a1091-104">In the previous topic, [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md), you implemented a WCF service that registers itself with the discovery proxy.</span></span> <span data-ttu-id="a1091-105">W tym temacie należy utworzyć klienta WCF, który używa serwera proxy odnajdywania, aby znaleźć usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="a1091-105">In this topic you create a WCF client that uses the discovery proxy to find the WCF service.</span></span>  
  
### <a name="implement-the-client"></a><span data-ttu-id="a1091-106">Zaimplementuj klienta</span><span class="sxs-lookup"><span data-stu-id="a1091-106">Implement the client</span></span>  
  
1. <span data-ttu-id="a1091-107">Dodaj nowy projekt aplikacji `DiscoveryProxyExample` konsoli `Client`do rozwiązania o nazwie .</span><span class="sxs-lookup"><span data-stu-id="a1091-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Client`.</span></span>  
  
2. <span data-ttu-id="a1091-108">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="a1091-108">Add references to the following assemblies:</span></span>  
  
    1. <span data-ttu-id="a1091-109">System.servicemodel</span><span class="sxs-lookup"><span data-stu-id="a1091-109">System.ServiceModel</span></span>  
  
    2. <span data-ttu-id="a1091-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="a1091-110">System.ServiceModel.Discovery</span></span>  
  
3. <span data-ttu-id="a1091-111">Dodaj GeneratedClient.cs znalezionych u dołu tego tematu do projektu.</span><span class="sxs-lookup"><span data-stu-id="a1091-111">Add the GeneratedClient.cs found at the bottom of this topic to the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1091-112">Ten plik jest zwykle generowany przy użyciu narzędzia, takiego jak Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a1091-112">This file is usually generated using a tool such as Svcutil.exe.</span></span> <span data-ttu-id="a1091-113">Jest to przewidziane w tym temacie, aby uprościć zadanie.</span><span class="sxs-lookup"><span data-stu-id="a1091-113">It is provided in this topic to simplify the task.</span></span>  
  
4. <span data-ttu-id="a1091-114">Otwórz plik Program.cs i dodaj następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="a1091-114">Open the Program.cs file and add the following method.</span></span> <span data-ttu-id="a1091-115">Ta metoda przyjmuje adres punktu końcowego i używa go do zainicjowania klienta usługi (serwera proxy).</span><span class="sxs-lookup"><span data-stu-id="a1091-115">This method takes an endpoint address and uses it to initialize the service client (proxy).</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
        // Create a client  
        CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
        Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
        Console.WriteLine();  

        double value1 = 100.00D;  
        double value2 = 15.99D;  

        // Call the Add service operation.  
        double result = client.Add(value1, value2);  
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  

        // Call the Subtract service operation.  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  

        // Call the Multiply service operation.  
        result = client.Multiply(value1, value2);  
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  

        // Call the Divide service operation.  
        result = client.Divide(value1, value2);  
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
        Console.WriteLine();  

        // Closing the client gracefully closes the connection and cleans up resources  
        client.Close();  
    }  
    ```  
  
5. <span data-ttu-id="a1091-116">Dodaj następujący kod do metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="a1091-116">Add the following code to the `Main` method.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
        Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  

        // Create a DiscoveryClient passing in the discovery endpoint  
        DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  

        Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
        Console.WriteLine();  

        try  
        {  
            // Search for services that implement ICalculatorService
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  

            Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
            Console.WriteLine();  

            // Check to see if endpoints were found, if so then invoke the service.  
            if (findResponse.Endpoints.Count > 0)  
            {  
                InvokeCalculatorService(findResponse.Endpoints[0].Address);  
            }  
        }  
        catch (TargetInvocationException)  
        {  
            Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
        }  

        Console.WriteLine("Press <ENTER> to exit.");  
        Console.ReadLine();  
    }  
    ```  
  
 <span data-ttu-id="a1091-117">Ukończono implementowanie aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="a1091-117">You have completed implementing the client application.</span></span> <span data-ttu-id="a1091-118">Przejdź do [strony Jak: Testowanie serwera proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="a1091-118">Continue on to [How to: Test the Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1091-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1091-119">Example</span></span>  
 <span data-ttu-id="a1091-120">Jest to pełna lista kodów dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a1091-120">This is the full code listing for this topic.</span></span>  
  
```csharp  
// GeneratedClient.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1434  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace Microsoft.Samples.Discovery  
{  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.Samples.Discovery", ConfigurationName = "ICalculatorService")]  
    public interface ICalculatorService  
    {  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Add", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/AddResponse")]  
        double Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Subtract", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/SubtractResponse")]  
        double Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Multiply", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/MultiplyResponse")]  
        double Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Divide", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/DivideResponse")]  
        double Divide(double n1, double n2);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public interface ICalculatorServiceChannel : ICalculatorService, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public partial class CalculatorServiceClient : System.ServiceModel.ClientBase<ICalculatorService>, ICalculatorService  
    {  
  
        public CalculatorServiceClient()  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName) :  
            base(endpointConfigurationName)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, string remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(binding, remoteAddress)  
        {  
        }  
  
        public double Add(double n1, double n2)  
        {  
            return base.Channel.Add(n1, n2);  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            return base.Channel.Subtract(n1, n2);  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            return base.Channel.Multiply(n1, n2);  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            return base.Channel.Divide(n1, n2);  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Reflection;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Client  
    {  
        public static void Main()  
        {  
            // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
  
            DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  
  
            Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
            Console.WriteLine();  
  
            try  
            {  
                // Find ICalculatorService endpoints
                FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  
  
                Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
                Console.WriteLine();  
  
                // Check to see if endpoints were found, if so then invoke the service.  
                if (findResponse.Endpoints.Count > 0)  
                {  
                    InvokeCalculatorService(findResponse.Endpoints[0].Address);  
                }  
            }  
            catch (TargetInvocationException)  
            {  
                Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
            Console.WriteLine();  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            // Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1091-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1091-121">See also</span></span>

- [<span data-ttu-id="a1091-122">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="a1091-122">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="a1091-123">Instrukcje: Wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="a1091-123">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="a1091-124">Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="a1091-124">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
