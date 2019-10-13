---
title: 'Instrukcje: programowe Dodawanie możliwości odnajdywania do usługi i klienta WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a139eb4a15486be329bc6853ee6b3a3be06b0619
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291568"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="05116-102">Instrukcje: programowe Dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="05116-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="05116-103">W tym temacie wyjaśniono, jak umożliwić odnajdywanie usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="05116-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="05116-104">Jest on oparty [na przykładu samoobsługowego](https://go.microsoft.com/fwlink/?LinkId=145523) .</span><span class="sxs-lookup"><span data-stu-id="05116-104">It is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="05116-105">Aby skonfigurować istniejącą przykładową usługę samoobsługi do odnajdowania</span><span class="sxs-lookup"><span data-stu-id="05116-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="05116-106">Otwórz rozwiązanie własne hosta w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="05116-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="05116-107">Przykład znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="05116-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="05116-108">Dodaj odwołanie do `System.ServiceModel.Discovery.dll` do projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="05116-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="05116-109">Może zostać wyświetlony komunikat o błędzie z informacją "System.</span><span class="sxs-lookup"><span data-stu-id="05116-109">You may see an error message saying "System.</span></span> <span data-ttu-id="05116-110">ServiceModel. Discovery. dll lub jedna z jej zależności wymaga nowszej wersji .NET Framework niż określona w projekcie... " Jeśli zobaczysz ten komunikat, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="05116-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="05116-111">W oknie **właściwości projektu** upewnij się, że **Struktura docelowa** to [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05116-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="05116-112">Otwórz plik Service.cs i Dodaj następującą instrukcję `using`.</span><span class="sxs-lookup"><span data-stu-id="05116-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="05116-113">W metodzie `Main()` w instrukcji `using` Dodaj wystąpienie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> do hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="05116-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="05116-114">@No__t-0 Określa, że usługa, do której zostanie zastosowana, jest wykrywalna.</span><span class="sxs-lookup"><span data-stu-id="05116-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="05116-115">Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do hosta usługi bezpośrednio po kodzie, który dodaje <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="05116-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="05116-116">Ten kod określa, że komunikaty odnajdowania powinny być wysyłane do standardowego punktu końcowego odnajdywania UDP.</span><span class="sxs-lookup"><span data-stu-id="05116-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="05116-117">Aby utworzyć aplikację kliencką, która używa odnajdywania do wywoływania usługi</span><span class="sxs-lookup"><span data-stu-id="05116-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="05116-118">Dodaj nową aplikację konsolową do rozwiązania o nazwie `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="05116-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="05116-119">Dodaj odwołanie do `System.ServiceModel.dll` i `System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="05116-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="05116-120">Skopiuj pliki GeneratedClient.cs i App. config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="05116-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="05116-121">Aby to zrobić, kliknij prawym przyciskiem myszy pliki w **Eksplorator rozwiązań**, wybierz polecenie **Kopiuj**, a następnie wybierz projekt **DiscoveryClientApp** , kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.</span><span class="sxs-lookup"><span data-stu-id="05116-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="05116-122">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="05116-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="05116-123">Dodaj następujące instrukcje `using`.</span><span class="sxs-lookup"><span data-stu-id="05116-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="05116-124">Dodaj metodę statyczną o nazwie `FindCalculatorServiceAddress()` do klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="05116-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="05116-125">Ta metoda używa odnajdywania w celu wyszukania usługi `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="05116-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="05116-126">Wewnątrz metody `FindCalculatorServiceAddress` Utwórz nowe wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient>, przekazując w <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="05116-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="05116-127">Oznacza to, że Klasa <xref:System.ServiceModel.Discovery.DiscoveryClient> powinna używać standardowego punktu końcowego odnajdywania UDP do wysyłania i odbierania komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="05116-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="05116-128">W następnym wierszu Wywołaj metodę <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> i Określ wystąpienie <xref:System.ServiceModel.Discovery.FindCriteria> zawierające kontrakt usługi, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="05116-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="05116-129">W takim przypadku Określ `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="05116-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="05116-130">Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Sprawdź, czy istnieje co najmniej jedna zgodna usługa i zwróć <xref:System.ServiceModel.EndpointAddress> pierwszej zgodnej usługi.</span><span class="sxs-lookup"><span data-stu-id="05116-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="05116-131">W przeciwnym razie Zwróć `null`.</span><span class="sxs-lookup"><span data-stu-id="05116-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="05116-132">Dodaj statyczną metodę o nazwie `InvokeCalculatorService` do klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="05116-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="05116-133">Ta metoda używa adresu punktu końcowego zwróconego z `FindCalculatorServiceAddress` w celu wywołania usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="05116-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="05116-134">Wewnątrz metody `InvokeCalculatorService` Utwórz wystąpienie klasy `CalculatorServiceClient`.</span><span class="sxs-lookup"><span data-stu-id="05116-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="05116-135">Ta klasa jest definiowana przez przykład [samoobsługi](https://go.microsoft.com/fwlink/?LinkId=145523) .</span><span class="sxs-lookup"><span data-stu-id="05116-135">This class is defined by the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="05116-136">Został on wygenerowany przy użyciu Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="05116-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="05116-137">W następnym wierszu Ustaw adres punktu końcowego klienta na adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="05116-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="05116-138">Natychmiast po kodzie dla poprzedniego kroku wywołaj metody udostępniane przez usługę Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="05116-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="05116-139">Dodaj kod do metody `Main()` w klasie `Program`, aby wywołać `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="05116-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="05116-140">W następnym wierszu Wywołaj wartość `InvokeCalculatorService()` i przekaż adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="05116-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="05116-141">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="05116-141">To test the application</span></span>  
  
1. <span data-ttu-id="05116-142">Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom Service. exe.</span><span class="sxs-lookup"><span data-stu-id="05116-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="05116-143">Otwórz wiersz polecenia i uruchom Discoveryclientapp. exe.</span><span class="sxs-lookup"><span data-stu-id="05116-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="05116-144">Dane wyjściowe z usługi Service. exe powinny wyglądać podobnie jak następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="05116-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4. <span data-ttu-id="05116-145">Dane wyjściowe z Discoveryclientapp. exe powinny wyglądać podobnie jak następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="05116-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="05116-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="05116-146">Example</span></span>  
 <span data-ttu-id="05116-147">Poniżej znajduje się lista kodów dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="05116-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="05116-148">Ponieważ ten kod jest oparty na przykładu z [własnym hostem](https://go.microsoft.com/fwlink/?LinkId=145523) , wyświetlane są tylko te pliki, które zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="05116-148">Because this code is based on the [Self-Host](https://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="05116-149">Aby uzyskać więcej informacji na temat przykładu samoobsługowego, zobacz [instrukcje dotyczące instalacji](https://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="05116-149">For more information about the Self-Host sample, see [Setup Instructions](https://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="05116-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05116-150">See also</span></span>

- [<span data-ttu-id="05116-151">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="05116-151">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="05116-152">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="05116-152">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
