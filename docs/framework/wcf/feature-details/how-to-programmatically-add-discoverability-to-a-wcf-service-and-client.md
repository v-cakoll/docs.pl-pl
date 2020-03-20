---
title: 'Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: dd96bc168413eef99260a5251e74971aa1309ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184887"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF
W tym temacie wyjaśniono, jak sprawić, aby usługa Windows Communication Foundation (WCF) była wykrywalna. Jest on oparty na przykładzie [self-host.](https://go.microsoft.com/fwlink/?LinkId=145523)  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Aby skonfigurować istniejący przykład usługi hosta samodzielnego dla odnajdywania  
  
1. Otwórz rozwiązanie self-host w programie Visual Studio 2012. Przykład znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Dodaj odwołanie `System.ServiceModel.Discovery.dll` do projektu usługi. Może zostać wyświetlony komunikat o błędzie "System. ServiceModel.Discovery.dll lub jedna z jego zależności wymaga nowszej wersji programu .NET Framework niż określona w projekcie..." Jeśli zostanie wyświetlony ten komunikat, kliknij projekt prawym przyciskiem myszy w Eksploratorze rozwiązań i wybierz polecenie **Właściwości**. W oknie **Właściwości projektu** upewnij się, że [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]jest to **struktura docelowa** .  
  
3. Otwórz plik Service.cs i dodaj `using` następującą instrukcję.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. W `Main()` metodzie wewnątrz `using` instrukcji dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie do hosta usługi.  
  
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
  
     Określa, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> że usługa, do których jest stosowana, jest wykrywalna.  
  
5. Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a do hosta usługi zaraz <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>po kodzie, który dodaje .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Ten kod określa, że komunikaty odnajdywania powinny być wysyłane do standardowego punktu końcowego odnajdywania UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Aby utworzyć aplikację kliencką, która używa odnajdywania do wywoływania usługi  
  
1. Dodaj nową aplikację konsoli do `DiscoveryClientApp`rozwiązania o nazwie .  
  
2. Dodaj odniesienie `System.ServiceModel.dll` do i`System.ServiceModel.Discovery.dll`  
  
3. Skopiuj pliki GeneratedClient.cs i App.config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp. Aby to zrobić, kliknij prawym przyciskiem myszy pliki w **Eksploratorze rozwiązań**, wybierz **polecenie Kopiuj**, a następnie wybierz projekt **DiscoveryClientApp,** kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.  
  
4. Otwórz Program.cs.  
  
5. Dodaj następujące instrukcje `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Dodaj metodę statyczną `FindCalculatorServiceAddress()` wywoływaną `Program` do klasy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Ta metoda używa odnajdywania do wyszukiwania `CalculatorService` usługi.  
  
7. Wewnątrz `FindCalculatorServiceAddress` metody utwórz <xref:System.ServiceModel.Discovery.DiscoveryClient> nowe wystąpienie, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> przekazując w konstruktorze.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Informuje WCF, <xref:System.ServiceModel.Discovery.DiscoveryClient> że klasa powinna używać standardowego punktu końcowego odnajdywania UDP do wysyłania i odbierania komunikatów odnajdywania.  
  
8. W następnym wierszu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> wywołaj metodę <xref:System.ServiceModel.Discovery.FindCriteria> i określ wystąpienie, które zawiera umowę serwisową, którą chcesz wyszukać. W takim przypadku `ICalculator`należy określić .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, sprawdź, czy istnieje co najmniej jedna <xref:System.ServiceModel.EndpointAddress> usługa dopasowania i zwrócić pierwszą usługę dopasowania. W `null`przeciwnym razie zwróć .  
  
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
  
10. Dodaj metodę statyczną `InvokeCalculatorService` o `Program` nazwie do klasy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Ta metoda używa adresu punktu `FindCalculatorServiceAddress` końcowego zwróconego z wywołania usługi kalkulatora.  
  
11. Wewnątrz `InvokeCalculatorService` metody utwórz wystąpienie `CalculatorServiceClient` klasy. Ta klasa jest zdefiniowana przez [przykład hosta własnego.](https://go.microsoft.com/fwlink/?LinkId=145523) Został wygenerowany przy użyciu pliku Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. W następnym wierszu ustaw adres końcowy klienta na adres punktu `FindCalculatorServiceAddress()`końcowego zwrócony z programu .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Natychmiast po kod dla poprzedniego kroku, wywołać metody udostępniane przez usługę kalkulatora.  
  
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
  
14. Dodaj kod `Main()` do metody `Program` w `FindCalculatorServiceAddress`klasie, aby wywołać .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. W następnym wierszu `InvokeCalculatorService()` wywołaj i przekaż adres `FindCalculatorServiceAddress()`punktu końcowego zwrócony z .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom plik Service.exe.  
  
2. Otwórz wiersz polecenia i uruchom plik Discoveryclientapp.exe.  
  
3. Dane wyjściowe z pliku service.exe powinny wyglądać następująco.  
  
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
  
4. Dane wyjściowe z Discoveryclientapp.exe powinny wyglądać następująco.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się lista kodu dla tego przykładu. Ponieważ ten kod jest oparty na przykładzie [self-host,](https://go.microsoft.com/fwlink/?LinkId=145523) tylko te pliki, które zostały zmienione są wymienione. Aby uzyskać więcej informacji na temat przykładu hosta samodzielnego, zobacz [Instrukcje instalacji](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

- [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Model obiektów odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
