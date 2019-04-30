---
title: 'Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 54d838967fcc19501ff7385aba29e8d79025ce70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761549"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF
W tym temacie wyjaśniono, jak stał się wykrywalny usługi Windows Communication Foundation (WCF). Jest on oparty na [hosta samodzielnego](https://go.microsoft.com/fwlink/?LinkId=145523) próbki.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Aby skonfigurować istniejący przykład hosta samodzielnego usługi odnajdywania  
  
1. Otwórz rozwiązanie hosta samodzielnego w programie Visual Studio 2012. Przykład znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Dodaj odwołanie do `System.ServiceModel.Discovery.dll` do projektu usługi. Może zostać wyświetlony komunikat o błędzie informujący o tym, "System. ServiceModel.Discovery.dll lub jednej z jego zależności wymaga nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] niż określona w projekcie... " Jeśli ten komunikat jest wyświetlony, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**. W **właściwości projektu** okna, upewnij się, że **platformę docelową** jest [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3. Otwórz plik Service.cs i Dodaj następujący kod `using` instrukcji.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. W `Main()` metody, wewnątrz `using` instrukcji, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienia hosta usługi.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Określa, że usługa jest stosowany do wykrywalne.  
  
5. Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> host usługi bezpośrednio po kodzie, który dodaje <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Ten kod określa, że komunikaty odnajdywania powinny być przesyłane do standardowy punkt końcowy odnajdywania protokołu UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Aby utworzyć aplikację kliencką, która używa odnajdywania w celu wywołania tej usługi  
  
1. Dodaj nową aplikację konsoli w rozwiązaniu o nazwie `DiscoveryClientApp`.  
  
2. Dodaj odwołanie do `System.ServiceModel.dll` i `System.ServiceModel.Discovery.dll`  
  
3. Skopiuj pliki GeneratedClient.cs i App.config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp. Aby to zrobić, kliknij prawym przyciskiem myszy pliki znajdujące się w **Eksploratora rozwiązań**, wybierz opcję **kopiowania**, a następnie wybierz pozycję **DiscoveryClientApp** projektu, kliknij prawym przyciskiem myszy i wybierz **Wklej**.  
  
4. Otwórz plik Program.cs.  
  
5. Dodaj następujący kod `using` instrukcji.  
  
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
  
     Ta metoda używa odnajdywania, aby wyszukać `CalculatorService` usługi.  
  
7. Wewnątrz `FindCalculatorServiceAddress` metody, Utwórz nową <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienia, przekazując <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do konstruktora.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Oznacza to, WCF, <xref:System.ServiceModel.Discovery.DiscoveryClient> klasa powinna być używana standardowy punkt końcowy odnajdywania protokołu UDP do wysyłania i odbierania komunikatów odnajdywania.  
  
8. W następnym wierszu, należy wywołać <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodę i określić <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia, które zawiera kontrakt usługi, które ma być wyszukiwany. W takim przypadku określić `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, sprawdź, czy istnieje co najmniej jedną usługę dopasowania i powrócić <xref:System.ServiceModel.EndpointAddress> pierwszego dopasowania usługi. W przeciwnym razie zwraca `null`.  
  
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
  
10. Dodaj metodę statyczną o nazwie `InvokeCalculatorService` do `Program` klasy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Ta metoda używa adresu punktu końcowego zwróciło `FindCalculatorServiceAddress` do wywołania kalkulatora.  
  
11. Wewnątrz `InvokeCalculatorService` metody, Utwórz wystąpienie obiektu `CalculatorServiceClient` klasy. Ta klasa jest zdefiniowana przez [hosta samodzielnego](https://go.microsoft.com/fwlink/?LinkId=145523) próbki. Został on wygenerowany przy użyciu Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. W następnym wierszu, ustawić adres punktu końcowego klienta na adres punktu końcowego zwróciło `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Bezpośrednio po kodzie w poprzednim kroku należy wywołać metod udostępnianych przez usługę kalkulatora.  
  
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
  
14. Dodaj kod, aby `Main()` method in Class metoda `Program` klasy, aby wywołać `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. W następnym wierszu, należy wywołać `InvokeCalculatorService()` i przekazać adres punktu końcowego zwróciło `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom Service.exe.  
  
2. Otwórz wiersz polecenia i uruchom Discoveryclientapp.exe.  
  
3. Dane wyjściowe z service.exe powinien wyglądać jak poniższe dane wyjściowe.  
  
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
  
4. Dane wyjściowe z Discoveryclientapp.exe powinien wyglądać jak poniższe dane wyjściowe.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Przykład  
 Oto lista kodu dla tego przykładu. Ponieważ ten kod jest oparty na [hosta samodzielnego](https://go.microsoft.com/fwlink/?LinkId=145523) przykładowe są wyświetlane tylko te pliki, które zostały zmienione. Aby uzyskać więcej informacji na temat przykład hosta samodzielnego zobacz [instrukcje dotyczące konfigurowania](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

## <a name="see-also"></a>Zobacz także

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Model obiektów odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
