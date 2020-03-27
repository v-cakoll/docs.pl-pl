---
title: 'Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: bf89c793cbd72a0a3980e6ec8e42c688dcedec26
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344980"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="d0735-102">Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="d0735-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="d0735-103">W tym temacie wyjaśniono, jak sprawić, aby usługa Windows Communication Foundation (WCF) była wykrywalna.</span><span class="sxs-lookup"><span data-stu-id="d0735-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="d0735-104">Jest on oparty na przykładzie [self-host.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)</span><span class="sxs-lookup"><span data-stu-id="d0735-104">It is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="d0735-105">Aby skonfigurować istniejący przykład usługi hosta samodzielnego dla odnajdywania</span><span class="sxs-lookup"><span data-stu-id="d0735-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="d0735-106">Otwórz rozwiązanie self-host w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d0735-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="d0735-107">Przykład znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="d0735-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="d0735-108">Dodaj odwołanie `System.ServiceModel.Discovery.dll` do projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="d0735-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="d0735-109">Może zostać wyświetlony komunikat o błędzie "System.</span><span class="sxs-lookup"><span data-stu-id="d0735-109">You may see an error message saying "System.</span></span> <span data-ttu-id="d0735-110">ServiceModel.Discovery.dll lub jedna z jego zależności wymaga nowszej wersji programu .NET Framework niż określona w projekcie..." Jeśli zostanie wyświetlony ten komunikat, kliknij projekt prawym przyciskiem myszy w Eksploratorze rozwiązań i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d0735-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="d0735-111">W oknie **Właściwości projektu** upewnij się, że [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]jest to **struktura docelowa** .</span><span class="sxs-lookup"><span data-stu-id="d0735-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="d0735-112">Otwórz plik Service.cs i dodaj `using` następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="d0735-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="d0735-113">W `Main()` metodzie wewnątrz `using` instrukcji dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d0735-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());
  
            // ...  
        }  
    }  
    ```  
  
     <span data-ttu-id="d0735-114">Określa, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> że usługa, do których jest stosowana, jest wykrywalna.</span><span class="sxs-lookup"><span data-stu-id="d0735-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="d0735-115">Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a do hosta usługi zaraz <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>po kodzie, który dodaje .</span><span class="sxs-lookup"><span data-stu-id="d0735-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="d0735-116">Ten kod określa, że komunikaty odnajdywania powinny być wysyłane do standardowego punktu końcowego odnajdywania UDP.</span><span class="sxs-lookup"><span data-stu-id="d0735-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="d0735-117">Aby utworzyć aplikację kliencką, która używa odnajdywania do wywoływania usługi</span><span class="sxs-lookup"><span data-stu-id="d0735-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="d0735-118">Dodaj nową aplikację konsoli do `DiscoveryClientApp`rozwiązania o nazwie .</span><span class="sxs-lookup"><span data-stu-id="d0735-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="d0735-119">Dodaj odniesienie `System.ServiceModel.dll` do i`System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="d0735-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="d0735-120">Skopiuj pliki GeneratedClient.cs i App.config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="d0735-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="d0735-121">Aby to zrobić, kliknij prawym przyciskiem myszy pliki w **Eksploratorze rozwiązań**, wybierz **polecenie Kopiuj**, a następnie wybierz projekt **DiscoveryClientApp,** kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.</span><span class="sxs-lookup"><span data-stu-id="d0735-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="d0735-122">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d0735-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="d0735-123">Dodaj następujące instrukcje `using`.</span><span class="sxs-lookup"><span data-stu-id="d0735-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="d0735-124">Dodaj metodę statyczną `FindCalculatorServiceAddress()` wywoływaną `Program` do klasy.</span><span class="sxs-lookup"><span data-stu-id="d0735-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="d0735-125">Ta metoda używa odnajdywania do wyszukiwania `CalculatorService` usługi.</span><span class="sxs-lookup"><span data-stu-id="d0735-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="d0735-126">Wewnątrz `FindCalculatorServiceAddress` metody utwórz <xref:System.ServiceModel.Discovery.DiscoveryClient> nowe wystąpienie, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> przekazując w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="d0735-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="d0735-127">Informuje WCF, <xref:System.ServiceModel.Discovery.DiscoveryClient> że klasa powinna używać standardowego punktu końcowego odnajdywania UDP do wysyłania i odbierania komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="d0735-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="d0735-128">W następnym wierszu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> wywołaj metodę <xref:System.ServiceModel.Discovery.FindCriteria> i określ wystąpienie, które zawiera umowę serwisową, którą chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="d0735-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="d0735-129">W takim przypadku `ICalculator`należy określić .</span><span class="sxs-lookup"><span data-stu-id="d0735-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="d0735-130">Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, sprawdź, czy istnieje co najmniej jedna <xref:System.ServiceModel.EndpointAddress> usługa dopasowania i zwrócić pierwszą usługę dopasowania.</span><span class="sxs-lookup"><span data-stu-id="d0735-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="d0735-131">W `null`przeciwnym razie zwróć .</span><span class="sxs-lookup"><span data-stu-id="d0735-131">Otherwise return `null`.</span></span>  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. <span data-ttu-id="d0735-132">Dodaj metodę statyczną `InvokeCalculatorService` o `Program` nazwie do klasy.</span><span class="sxs-lookup"><span data-stu-id="d0735-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="d0735-133">Ta metoda używa adresu punktu `FindCalculatorServiceAddress` końcowego zwróconego z wywołania usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="d0735-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="d0735-134">Wewnątrz `InvokeCalculatorService` metody utwórz wystąpienie `CalculatorServiceClient` klasy.</span><span class="sxs-lookup"><span data-stu-id="d0735-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="d0735-135">Ta klasa jest zdefiniowana przez [przykład hosta własnego.](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host)</span><span class="sxs-lookup"><span data-stu-id="d0735-135">This class is defined by the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span> <span data-ttu-id="d0735-136">Został wygenerowany przy użyciu pliku Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="d0735-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="d0735-137">W następnym wierszu ustaw adres końcowy klienta na adres punktu `FindCalculatorServiceAddress()`końcowego zwrócony z programu .</span><span class="sxs-lookup"><span data-stu-id="d0735-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="d0735-138">Natychmiast po kod dla poprzedniego kroku, wywołać metody udostępniane przez usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="d0735-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
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
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. <span data-ttu-id="d0735-139">Dodaj kod `Main()` do metody `Program` w `FindCalculatorServiceAddress`klasie, aby wywołać .</span><span class="sxs-lookup"><span data-stu-id="d0735-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="d0735-140">W następnym wierszu `InvokeCalculatorService()` wywołaj i przekaż adres `FindCalculatorServiceAddress()`punktu końcowego zwrócony z .</span><span class="sxs-lookup"><span data-stu-id="d0735-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="d0735-141">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="d0735-141">To test the application</span></span>  
  
1. <span data-ttu-id="d0735-142">Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom plik Service.exe.</span><span class="sxs-lookup"><span data-stu-id="d0735-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="d0735-143">Otwórz wiersz polecenia i uruchom plik Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="d0735-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="d0735-144">Dane wyjściowe z pliku service.exe powinny wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="d0735-144">The output from service.exe should look like the following output.</span></span>  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. <span data-ttu-id="d0735-145">Dane wyjściowe z Discoveryclientapp.exe powinny wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="d0735-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="d0735-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0735-146">Example</span></span>  
 <span data-ttu-id="d0735-147">Poniżej znajduje się lista kodu dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="d0735-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="d0735-148">Ponieważ ten kod jest oparty na przykładzie [self-host,](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) tylko te pliki, które zostały zmienione są wymienione.</span><span class="sxs-lookup"><span data-stu-id="d0735-148">Because this code is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="d0735-149">Aby uzyskać więcej informacji na temat przykładu hosta samodzielnego, zobacz [Instrukcje instalacji](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span><span class="sxs-lookup"><span data-stu-id="d0735-149">For more information about the Self-Host sample, see [Setup Instructions](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
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
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="d0735-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0735-150">See also</span></span>

- [<span data-ttu-id="d0735-151">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="d0735-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="d0735-152">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="d0735-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
