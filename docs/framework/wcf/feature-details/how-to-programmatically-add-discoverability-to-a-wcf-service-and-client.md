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
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Instrukcje: Programowe dodawanie możliwości odnajdywania do usługi i klienta WCF
W tym temacie wyjaśniono, jak utworzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wykrywalny usługi. Jest on oparty na [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) próbki.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Aby skonfigurować istniejącą przykład hosta samodzielnego usługi odnajdywania  
  
1.  Otwórz rozwiązanie hosta samodzielnego w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Przykładowa zawartość pliku znajduje się w katalogu TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2.  Dodaj odwołanie do `System.ServiceModel.Discovery.dll` do projektu usługi. Zobaczysz komunikat o błędzie informujący o tym, "System. ServiceModel.Discovery.dll lub jednej z jego zależności wymaga nowszej wersji [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] niż określona w projekcie... " Jeśli ten komunikat zostanie wyświetlony, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz pozycję **właściwości**. W **właściwości projektu** okna, upewnij się, że **platformy docelowej** jest [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Otwórz plik Service.cs i dodaj następujące `using` instrukcji.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  W `Main()` metoda, wewnątrz `using` instrukcji, Dodaj <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie hosta usługi.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Określa, że usługa jest stosowany do wykrywania urządzeń.  
  
5.  Dodaj <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> host usługi bezpośrednio po kodzie, który dodaje <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Ten kod określa, czy komunikaty odnajdywania mają być wysyłane do standardowego punktu końcowego odnajdywania protokołu UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Do tworzenia aplikacji klienckiej, która korzysta z odnajdywania w celu wywołania tej usługi  
  
1.  Dodaj nową aplikację konsoli do rozwiązania o nazwie `DiscoveryClientApp`.  
  
2.  Dodaj odwołanie do `System.ServiceModel.dll` i`System.ServiceModel.Discovery.dll`  
  
3.  Skopiuj pliki GeneratedClient.cs i App.config z istniejącego projektu klienta do nowego projektu DiscoveryClientApp. Aby to zrobić, kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań**, wybierz pozycję **kopiowania**, a następnie wybierz **DiscoveryClientApp** projektu, kliknij prawym przyciskiem myszy i wybierz **Wklej**.  
  
4.  Otwórz plik Program.cs.  
  
5.  Dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Dodaj metody statycznej o nazwie `FindCalculatorServiceAddress()` do `Program` klasy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Ta metoda używa odnajdywania, aby wyszukać `CalculatorService` usługi.  
  
7.  Wewnątrz `FindCalculatorServiceAddress` metody, Utwórz nową <xref:System.ServiceModel.Discovery.DiscoveryClient> wystąpienia, przekazując <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do konstruktora.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Ta wartość informuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] który <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy standardowy punkt końcowy odnajdowania UDP powinna być używana do wysyłania i odbierania wiadomości odnajdywania.  
  
8.  W następnym wierszu wywołać <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> — metoda i określ <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienie, którego chcesz wyszukać kontraktu usługi. W takim przypadku określ `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po wywołaniu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, sprawdź, czy istnieje co najmniej jedną usługę dopasowywania i zwracać <xref:System.ServiceModel.EndpointAddress> pierwszej usługi dopasowania. W przeciwnym razie zwraca `null`.  
  
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
  
10. Dodaj metody statycznej o nazwie `InvokeCalculatorService` do `Program` klasy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Ta metoda używa adres punktu końcowego zwrócony z `FindCalculatorServiceAddress` do wywołania tej usługi Kalkulator.  
  
11. Wewnątrz `InvokeCalculatorService` metody, Utwórz wystąpienie `CalculatorServiceClient` klasy. Ta klasa jest zdefiniowana przez [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) próbki. Został wygenerowany, za pomocą Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. W następnym wierszu ustawiony adres punktu końcowego klienta na adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Bezpośrednio po kodzie dla poprzedniego kroku należy wywołać metody ujawnione przez usługę Kalkulator.  
  
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
  
14. Dodaj kod, aby `Main()` metody w `Program` klasy do wywołania `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. W następnym wierszu wywołać `InvokeCalculatorService()` i podaj adres punktu końcowego zwrócony z `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i uruchom Service.exe.  
  
2.  Otwórz wiersz polecenia i uruchom Discoveryclientapp.exe.  
  
3.  Dane wyjściowe z service.exe powinien wyglądać następujące dane wyjściowe.  
  
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
  
4.  Dane wyjściowe z Discoveryclientapp.exe powinien wyglądać następujące dane wyjściowe.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się lista kodu dla tego przykładu. Ponieważ ten kod jest oparta na [hosta samodzielnego](http://go.microsoft.com/fwlink/?LinkId=145523) przykładowe są wyświetlane tylko te pliki, które są zmieniane. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]przykład hosta samodzielnego zobacz [instrukcje dotyczące konfigurowania](http://go.microsoft.com/fwlink/?LinkId=145522).  
  
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
 [Omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Model obiektów odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
