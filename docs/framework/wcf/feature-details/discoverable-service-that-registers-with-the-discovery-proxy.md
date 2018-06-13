---
title: 'Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: e0ceada8f65b98676d160ba096c63bf946a178cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490600"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="1b35d-102">Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="1b35d-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="1b35d-103">Ten temat jest drugi cztery tematach omówiono sposób wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1b35d-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="1b35d-104">W poprzednim temacie [porady: Implementowanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), zaimplementowana serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1b35d-104">In the previous topic, [How to: Implement a Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="1b35d-105">W tym temacie Tworzenie usługi WCF, która wysyła komunikaty anonsów (`Hello` i `Bye`) do odnajdowania serwera proxy, co powoduje rejestrowanie i wyrejestrowywanie się przy użyciu serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="1b35d-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="1b35d-106">Aby zdefiniować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="1b35d-106">To define the service contract</span></span>  
  
1.  <span data-ttu-id="1b35d-107">Dodaj nowy projekt aplikacji konsoli do `DiscoveryProxyExample` rozwiązanie o nazwie `Service`.</span><span class="sxs-lookup"><span data-stu-id="1b35d-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>  
  
2.  <span data-ttu-id="1b35d-108">Dodaj odwołania do następujących zestawów:</span><span class="sxs-lookup"><span data-stu-id="1b35d-108">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="1b35d-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b35d-109">System.ServiceModel</span></span>  
  
    2.  <span data-ttu-id="1b35d-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="1b35d-110">System.ServiceModel.Discovery</span></span>  
  
3.  <span data-ttu-id="1b35d-111">Dodaj nową klasę do projektu o nazwie `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="1b35d-111">Add a new class to the project called `CalculatorService`.</span></span>  
  
4.  <span data-ttu-id="1b35d-112">Dodaj następujące instrukcje using.</span><span class="sxs-lookup"><span data-stu-id="1b35d-112">Add the following using statements.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
5.  <span data-ttu-id="1b35d-113">W ramach CalculatorService.cs definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="1b35d-113">Within CalculatorService.cs, define the service contract.</span></span>  
  
    ```csharp  
    // Define a service contract.  
        [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]  
        public interface ICalculatorService  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
    ```  
  
6.  <span data-ttu-id="1b35d-114">Również w CalculatorService.cs, należy zaimplementować kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="1b35d-114">Also within CalculatorService.cs, implement the service contract.</span></span>  
  
    ```csharp  
    // Service class which implements the service contract.      
        public class CalculatorService : ICalculatorService  
        {  
            public double Add(double n1, double n2)  
            {  
                double result = n1 + n2;  
                Console.WriteLine("Received Add({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Subtract(double n1, double n2)  
            {  
                double result = n1 - n2;  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Multiply(double n1, double n2)  
            {  
                double result = n1 * n2;  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Divide(double n1, double n2)  
            {  
                double result = n1 / n2;  
                Console.WriteLine("Received Divide({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
        }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="1b35d-115">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="1b35d-115">To host the service</span></span>  
  
1.  <span data-ttu-id="1b35d-116">Otwórz plik Program.cs, który został wygenerowany podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="1b35d-116">Open the Program.cs file that was generated when you created the project.</span></span>  
  
2.  <span data-ttu-id="1b35d-117">Dodaj następujące instrukcje using.</span><span class="sxs-lookup"><span data-stu-id="1b35d-117">Add the following using statements.</span></span>  
  
    ```csharp 
    using System;  
    using System.ServiceModel;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Discovery;  
    ```  
  
3.  <span data-ttu-id="1b35d-118">W ramach `Main()` metody, Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="1b35d-118">Within the `Main()` method, add the following code:</span></span>  
  
    ```csharp  
    // Define the base address of the service  
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());  
    // Define the endpoint address where announcement messages will be sent  
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
    // Create the service host  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    try  
    {  
       // Add a service endpoint  
       ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
       // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
       AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
  
       // Create a ServiceDiscoveryBehavior and add the announcement endpoint  
       ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
                    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);  
  
       // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable  
       serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);  
  
       // Start listening for messages  
      serviceHost.Open();  
  
       Console.WriteLine("Calculator Service started at {0}", baseAddress);  
       Console.WriteLine();  
       Console.WriteLine("Press <ENTER> to terminate the service.");  
       Console.WriteLine();  
       Console.ReadLine();  
  
       serviceHost.Close();  
    }  
    catch (CommunicationException e)  
    {  
       Console.WriteLine(e.Message);  
    }  
    catch (TimeoutException e)  
    {  
       Console.WriteLine(e.Message);  
    }     
  
    if (serviceHost.State != CommunicationState.Closed)  
    {  
       Console.WriteLine("Aborting the service...");  
       serviceHost.Abort();  
    }  
    ```  
  
 <span data-ttu-id="1b35d-119">Ukończono wdrażanie wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="1b35d-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="1b35d-120">W dalszym ciągu na [porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="1b35d-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b35d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b35d-121">Example</span></span>  
 <span data-ttu-id="1b35d-122">Jest to pełna lista kod używany w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="1b35d-122">This is the full listing of the code used in this topic.</span></span>  
  
```csharp  
// CalculatorService.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
  
namespace Microsoft.Samples.Discovery  
{  
    // Define a service contract.  
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]  
    public interface ICalculatorService  
    {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
  
    // Service class which implements the service contract.      
    public class CalculatorService : ICalculatorService  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
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
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Program  
    {  
        public static void Main()  
        {  
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());  
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
            try  
            {  
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);  
  
                // Make the service discoverable  
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);  
  
                serviceHost.Open();  
  
                Console.WriteLine("Calculator Service started at {0}", baseAddress);  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to terminate the service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                serviceHost.Close();  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            catch (TimeoutException e)  
            {  
                Console.WriteLine(e.Message);  
            }     
  
            if (serviceHost.State != CommunicationState.Closed)  
            {  
                Console.WriteLine("Aborting the service...");  
                serviceHost.Abort();  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="1b35d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b35d-123">See Also</span></span>  
 [<span data-ttu-id="1b35d-124">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="1b35d-124">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="1b35d-125">Instrukcje: wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="1b35d-125">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="1b35d-126">Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="1b35d-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
