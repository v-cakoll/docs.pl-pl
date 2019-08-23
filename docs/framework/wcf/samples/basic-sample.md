---
title: Podstawowy przykład
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: d227b3ac64108901b8280ac7887adc30b0fab13e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915449"
---
# <a name="basic-sample"></a>Podstawowy przykład
Ten przykład pokazuje, jak umożliwić odnajdywanie usługi i wyszukiwanie i wywoływanie usługi wykrywalnej. Ten przykład składa się z dwóch projektów: Service i Client.

> [!NOTE]
> Ten przykład implementuje odnajdywanie w kodzie.  Aby uzyskać przykład, który implementuje odnajdywanie w konfiguracji, zobacz [Konfiguracja](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Usługa  
 To jest prosta implementacja usługi kalkulatora. Kod powiązany z odnajdywaniem można znaleźć w `Main` <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> miejscu, w którym jest dodawany do hosta usługi i <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> jest dodawany, jak pokazano w poniższym kodzie.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Klient  
 Klient używa programu <xref:System.ServiceModel.Discovery.DynamicEndpoint> w celu zlokalizowania usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint>Standardowy punkt końcowy rozwiązuje punkt końcowy usługi podczas otwierania klienta. W tym przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi na podstawie kontraktu usługi. Domyślnie wykonuje wyszukiwanie w przeszukiwaniu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Po znalezieniu punktu końcowego usługi klient nawiązuje połączenie z tą usługą względem określonego powiązania.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Klient definiuje metodę o nazwie `InvokeCalculatorService` , która <xref:System.ServiceModel.Discovery.DiscoveryClient> używa klasy do wyszukiwania usług. Dziedziczy z <xref:System.ServiceModel.Description.ServiceEndpoint>, więc`InvokeCalculatorService` można go przesłać do metody. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Ten przykład używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do tworzenia `CalculatorServiceClient` wystąpienia i wywołuje różne operacje usługi Kalkulator.  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
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
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](https://go.microsoft.com/fwlink/?LinkId=70353). Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL. Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Za pomocą programu Visual Studio 2012 Otwórz podstawową. sln i skompiluj przykład.  
  
3. Uruchom aplikację Service. exe.  
  
4. Po uruchomieniu usługi Uruchom program Client. exe.  
  
5. Zwróć uwagę, że klient mógł znaleźć usługę bez znajomości jej adresu.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
