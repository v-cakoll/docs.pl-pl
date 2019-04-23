---
title: Podstawowy przykład
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 1ceee6dd11b59ab9b43797ca8b1fd80c232fc8ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976420"
---
# <a name="basic-sample"></a>Podstawowy przykład
Niniejszy przykład pokazuje, jak usługa stał się wykrywalny i jak wyszukiwanie i wywoływać odnajdywanej usługi. W tym przykładzie składa się z dwóch projektów: usługi i klienta.

> [!NOTE]
>  W tym przykładzie implementuje odnajdywania w kodzie.  Dla przykładu, który implementuje odnajdywania w konfiguracji, zobacz [konfiguracji](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Usługa  
 Jest to implementacja usługi prosty kalkulator. Odnajdywanie związane z kodem znajduje się w `Main` gdzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> jest dodawany do hosta usługi i <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> jest dodawany, jak pokazano w poniższym kodzie.  
  
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
 Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Standardowy punkt końcowy jest rozpoznawany jako punkt końcowy usługi po otwarciu klienta. W tym przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi, w oparciu kontraktu usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Przeprowadza wyszukiwanie ciągu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> domyślnie. Gdy klient zlokalizuje punkt końcowy usługi, klient łączy się z tej usługi za pośrednictwem określonego powiązania.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Klient definiuje metodę o nazwie `InvokeCalculatorService` , który używa <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy w celu wyszukiwania usług. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Dziedziczy <xref:System.ServiceModel.Description.ServiceEndpoint>, dzięki czemu mogą być przekazywane do `InvokeCalculatorService` metody. Następnie w przykładzie <xref:System.ServiceModel.Discovery.DynamicEndpoint> do utworzenia wystąpienia `CalculatorServiceClient` i wywołuje różne operacje usługi kalkulatora.  
  
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
  
1. W tym przykładzie użyto punktów końcowych HTTP i aby uruchomić ten przykład, muszą zostać dodane odpowiednie listy ACL adresu URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Za pomocą programu Visual Studio 2012, otwórz Basic.sln i stworzyć próbkę.  
  
3. Uruchom aplikację service.exe.  
  
4. Po uruchomieniu usługi, uruchom client.exe.  
  
5. Sprawdź, czy klient mógł znaleźć tę usługę, nie wiedząc o tym adresu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
