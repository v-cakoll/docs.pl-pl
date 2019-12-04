---
title: Podstawowy przykład
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 5d0470fefff86ee3a88fa290be5f349c38ca8276
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716080"
---
# <a name="basic-sample"></a>Podstawowy przykład

Ten przykład pokazuje, jak umożliwić odnajdywanie usługi i wyszukiwanie i wywoływanie usługi wykrywalnej. Ten przykład składa się z dwóch projektów: Service i Client.

> [!NOTE]
> Ten przykład implementuje odnajdywanie w kodzie.  Aby uzyskać przykład, który implementuje odnajdywanie w konfiguracji, zobacz [Konfiguracja](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>NDES

To jest prosta implementacja usługi kalkulatora. Kod związany z odnajdywaniem można znaleźć w `Main`, w którym <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> zostanie dodany do hosta usługi i zostanie dodana <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jak pokazano w poniższym kodzie.

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

Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, standardowy punkt końcowy, rozwiązuje punkt końcowy usługi podczas otwierania klienta. W tym przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi na podstawie kontraktu usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint> domyślnie przeszukiwane jest <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>. Po znalezieniu punktu końcowego usługi klient nawiązuje połączenie z tą usługą względem określonego powiązania.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

Klient definiuje metodę o nazwie `InvokeCalculatorService`, która używa klasy <xref:System.ServiceModel.Discovery.DiscoveryClient> do wyszukiwania usług. <xref:System.ServiceModel.Discovery.DynamicEndpoint> dziedziczy po <xref:System.ServiceModel.Description.ServiceEndpoint>, więc można go przesłać do metody `InvokeCalculatorService`. Przykład używa <xref:System.ServiceModel.Discovery.DynamicEndpoint>, aby utworzyć wystąpienie `CalculatorServiceClient` i wywołuje różne operacje usługi Kalkulator.

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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
