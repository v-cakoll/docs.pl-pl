---
title: 'Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: c28815d1d208d3e91785a13d95e03c09c0f02ed9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596997"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF
W tym temacie wyjaśniono, jak umożliwić odnajdywanie usługi Windows Communication Foundation (WCF). Jest on oparty [na przykładu samoobsługowego](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) .  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Aby skonfigurować istniejącą przykładową usługę samoobsługi do odnajdowania  
  
1. Otwórz rozwiązanie własne hosta w programie Visual Studio 2012. Przykład znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Dodaj odwołanie do `System.ServiceModel.Discovery.dll` projektu usługi. Może zostać wyświetlony komunikat o błędzie z informacją "System. ServiceModel. Discovery. dll lub jedna z jej zależności wymaga nowszej wersji .NET Framework niż określona w projekcie... " Jeśli zobaczysz ten komunikat, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Właściwości**. W oknie **właściwości projektu** upewnij się, że **Struktura docelowa** to [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .  
  
3. Otwórz plik Service.cs i Dodaj następującą `using` instrukcję.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. W `Main()` metodzie, w `using` instrukcji, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie do hosta usługi.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Określa, że usługa, do której ma zostać zastosowana, jest wykrywalna.  
  
5. Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do hosta usługi bezpośrednio po kodzie, który dodaje <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Ten kod określa, że komunikaty odnajdowania powinny być wysyłane do standardowego punktu końcowego odnajdywania UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Aby utworzyć aplikację kliencką, która używa odnajdywania do wywoływania usługi  
  
1. Dodaj nową aplikację konsolową do rozwiązania o nazwie `DiscoveryClientApp` .  
  
2. Dodaj odwołanie do `System.ServiceModel.dll` i`System.ServiceModel.Discovery.dll`  
  
3. Skopiuj pliki GeneratedClient.cs i App. config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp. Aby to zrobić, kliknij prawym przyciskiem myszy pliki w **Eksplorator rozwiązań**, wybierz polecenie **Kopiuj**, a następnie wybierz projekt **DiscoveryClientApp** , kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.  
  
4. Otwórz Program.cs.  
  
5. Dodaj następujące instrukcje `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Dodaj metodę statyczną o nazwie `FindCalculatorServiceAddress()` do `Program` klasy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Ta metoda używa odnajdywania w celu wyszukania `CalculatorService` usługi.  
  
7. Wewnątrz `FindCalculatorServiceAddress` metody Utwórz nowe <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienie, przekazując <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do konstruktora.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     To mówi WCF, że <xref:System.ServiceModel.Discovery.DiscoveryClient> Klasa powinna używać standardowego punktu końcowego odnajdywania UDP do wysyłania i odbierania komunikatów odnajdywania.  
  
8. W następnym wierszu Wywołaj <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę i określ <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, które zawiera kontrakt usługi, który chcesz wyszukać. W takim przypadku Określ `ICalculator` .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> elementu Sprawdź, czy istnieje co najmniej jedna zgodna usługa i zwraca <xref:System.ServiceModel.EndpointAddress> pierwszą zgodną usługę. W przeciwnym razie zwraca `null` .  
  
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
  
10. Dodaj statyczną metodę o nazwie `InvokeCalculatorService` do `Program` klasy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Ta metoda używa adresu punktu końcowego zwróconego przez program, `FindCalculatorServiceAddress` Aby wywołać usługę Kalkulator.  
  
11. Wewnątrz `InvokeCalculatorService` metody Utwórz wystąpienie `CalculatorServiceClient` klasy. Ta klasa jest definiowana przez przykład [samoobsługi](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) . Został on wygenerowany przy użyciu Svcutil. exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. W następnym wierszu Ustaw adres punktu końcowego klienta na adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Natychmiast po kodzie dla poprzedniego kroku wywołaj metody udostępniane przez usługę Kalkulator.  
  
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
  
14. Dodaj kod do `Main()` metody w klasie, `Program` która ma zostać wywołana `FindCalculatorServiceAddress` .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. W następnym wierszu Wywołaj `InvokeCalculatorService()` i przekaż adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom Service. exe.  
  
2. Otwórz wiersz polecenia i uruchom Discoveryclientapp. exe.  
  
3. Dane wyjściowe z usługi Service. exe powinny wyglądać podobnie jak następujące dane wyjściowe.  
  
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
  
4. Dane wyjściowe z Discoveryclientapp. exe powinny wyglądać podobnie jak następujące dane wyjściowe.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się lista kodów dla tego przykładu. Ponieważ ten kod jest oparty na przykładu z [własnym hostem](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) , wyświetlane są tylko te pliki, które zostały zmienione. Aby uzyskać więcej informacji na temat przykładu samoobsługowego, zobacz [instrukcje dotyczące instalacji](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).  
  
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

## <a name="see-also"></a>Zobacz też

- [Omówienie odnajdywania WCF](wcf-discovery-overview.md)
- [Model obiektów odnajdywania WCF](wcf-discovery-object-model.md)
