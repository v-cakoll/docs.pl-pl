---
title: "Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0a59788544a32b78e75ac25e787dcbae478451e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="e8e1d-102">Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="e8e1d-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="e8e1d-103">W tym temacie wyjaśniono, jak utworzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wykrywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-103">This topic explains how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span> <span data-ttu-id="e8e1d-104">Jest on oparty na [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) próbki.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-104">It is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="e8e1d-105">Aby skonfigurować istniejącą przykład hosta samodzielnego usługi odnajdywania</span><span class="sxs-lookup"><span data-stu-id="e8e1d-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="e8e1d-106">Otwórz rozwiązanie hosta samodzielnego w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8e1d-106">Open the Self-Host solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="e8e1d-107">Przykładowa zawartość pliku znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="e8e1d-108">Dodaj odwołanie do `System.ServiceModel.Discovery.dll` do projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="e8e1d-109">Zobaczysz komunikat o błędzie informujący o tym, "System.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-109">You may see an error message saying "System.</span></span> <span data-ttu-id="e8e1d-110">ServiceModel.Discovery.dll lub jednej z jego zależności wymaga nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] niż określona w projekcie... "</span><span class="sxs-lookup"><span data-stu-id="e8e1d-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …"</span></span> <span data-ttu-id="e8e1d-111">Jeśli ten komunikat zostanie wyświetlony, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-111">If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="e8e1d-112">W **właściwości projektu** okna, upewnij się, że **platformy docelowej** jest [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8e1d-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="e8e1d-113">Otwórz plik Service.cs i dodaj następujące `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="e8e1d-114">W `Main()` metoda, wewnątrz `using` instrukcji, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="e8e1d-115"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Określa, że usługa jest stosowany do wykrywania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="e8e1d-116">Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> host usługi bezpośrednio po kodzie, który dodaje <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="e8e1d-117">Ten kod określa, czy komunikaty odnajdywania mają być wysyłane do standardowego punktu końcowego odnajdywania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="e8e1d-118">Do tworzenia aplikacji klienckiej, która korzysta z odnajdywania w celu wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="e8e1d-118">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="e8e1d-119">Dodaj nową aplikację konsoli do rozwiązania o nazwie `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="e8e1d-120">Dodaj odwołanie do `System.ServiceModel.dll` i`System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="e8e1d-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="e8e1d-121">Skopiuj pliki GeneratedClient.cs i App.config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="e8e1d-122">Aby to zrobić, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**, wybierz pozycję **kopiowania**, a następnie wybierz **DiscoveryClientApp** projektu, kliknij prawym przyciskiem myszy i wybierz **Wklej**.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="e8e1d-123">Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-123">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="e8e1d-124">Dodaj następujące `using` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="e8e1d-125">Dodaj metody statycznej o nazwie `FindCalculatorServiceAddress()` do `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="e8e1d-126">Ta metoda używa odnajdywania, aby wyszukać `CalculatorService` usługi.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="e8e1d-127">Wewnątrz `FindCalculatorServiceAddress` metody, Utwórz nową <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienia, przekazując <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="e8e1d-128">Ta wartość informuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] który <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy standardowy punkt końcowy odnajdowania UDP powinna być używana do wysyłania i odbierania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-128">This tells [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="e8e1d-129">W następnym wierszu wywołać <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> — metoda i określ <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, którego chcesz wyszukać kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="e8e1d-130">W takim przypadku określ `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="e8e1d-131">Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, sprawdź, czy istnieje co najmniej jedną usługę dopasowywania i zwracać <xref:System.ServiceModel.EndpointAddress> pierwszej usługi dopasowania.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="e8e1d-132">W przeciwnym razie zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-132">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="e8e1d-133">Dodaj metody statycznej o nazwie `InvokeCalculatorService` do `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="e8e1d-134">Ta metoda używa adres punktu końcowego zwrócony z `FindCalculatorServiceAddress` do wywołania tej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="e8e1d-135">Wewnątrz `InvokeCalculatorService` metody, Utwórz wystąpienie `CalculatorServiceClient` klasy.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="e8e1d-136">Ta klasa jest zdefiniowana przez [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) próbki.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-136">This class is defined by the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="e8e1d-137">Został wygenerowany, za pomocą Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="e8e1d-138">W następnym wierszu ustawiony adres punktu końcowego klienta na adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="e8e1d-139">Bezpośrednio po kodzie dla poprzedniego kroku należy wywołać metody ujawnione przez usługę Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="e8e1d-140">Dodaj kod, aby `Main()` metody w `Program` klasy do wywołania `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="e8e1d-141">W następnym wierszu wywołać `InvokeCalculatorService()` i podaj adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="e8e1d-142">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="e8e1d-142">To test the application</span></span>  
  
1.  <span data-ttu-id="e8e1d-143">Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom Service.exe.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="e8e1d-144">Otwórz wiersz polecenia i uruchom Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="e8e1d-145">Dane wyjściowe z service.exe powinien wyglądać następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-145">The output from service.exe should look like the following output.</span></span>  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  <span data-ttu-id="e8e1d-146">Dane wyjściowe z Discoveryclientapp.exe powinien wyglądać następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="e8e1d-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8e1d-147">Example</span></span>  
 <span data-ttu-id="e8e1d-148">Poniżej znajduje się lista kodu dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="e8e1d-149">Ponieważ ten kod jest oparta na [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) przykładowe są wyświetlane tylko te pliki, które są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="e8e1d-149">Because this code is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e8e1d-150">przykład hosta samodzielnego zobacz [instrukcje dotyczące konfigurowania](http://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="e8e1d-150"> the Self-Host sample, see [Setup Instructions](http://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="e8e1d-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8e1d-151">See Also</span></span>  
 [<span data-ttu-id="e8e1d-152">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="e8e1d-152">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="e8e1d-153">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="e8e1d-153">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
