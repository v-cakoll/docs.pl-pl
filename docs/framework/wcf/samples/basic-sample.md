---
title: Podstawowy przykład
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d692b33c84f12976e2d1c263ca9d68475667c2a8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="basic-sample"></a>Podstawowy przykład
W tym przykładzie pokazano, jak sprawiają, że usługa wykrywania urządzeń oraz sposób wyszukiwania i wywołać wykrywalnej usługi. W tym przykładzie składa się z dwóch projektów: usługa i klient.  
  
> [!NOTE]
>  W tym przykładzie implementuje odnajdywania w kodzie.  Dla przykładu, który implementuje odnajdywania w konfiguracji, zobacz [konfiguracji](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Usługa  
 Jest to prosty kalkulator implementacji usługi. Odnajdywanie powiązane kod można znaleźć w `Main` gdzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> zostanie dodany do usługi hosta i <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> zostanie dodany, jak pokazano w poniższym kodzie.  
  
```  
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
 Klient używa <xref:System.ServiceModel.Discovery.DynamicEndpoint> do lokalizowania usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Standardowy punkt końcowy rozpoznaje punktu końcowego usługi, gdy klient jest otwarty. W takim przypadku <xref:System.ServiceModel.Discovery.DynamicEndpoint> szuka usługi oparte na kontrakt usługi. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Przeprowadza wyszukiwanie za pośrednictwem <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> domyślnie. Gdy klient zlokalizuje punkt końcowy usługi, klient łączy się z tej usługi za pośrednictwem określonego powiązania.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Klient definiuje metodę o nazwie `InvokeCalculatorService` używającą <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy wyszukiwania usług. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Dziedziczy <xref:System.ServiceModel.Description.ServiceEndpoint>, więc można go przekazać do `InvokeCalculatorService` metody. W przykładzie następnie użyto <xref:System.ServiceModel.Discovery.DynamicEndpoint> można utworzyć wystąpienia `CalculatorServiceClient` i wywołuje różnych operacji usługi Kalkulator.  
  
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
  
1.  W przykładzie użyto punktów końcowych HTTP i do uruchomienia tego przykładu, muszą zostać dodane odpowiednie listy ACL adresu URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL. Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz Basic.sln i tworzyć przykładowy kod.  
  
3.  Uruchom aplikację service.exe.  
  
4.  Po uruchomieniu usługi, uruchom client.exe.  
  
5.  Sprawdź, czy klient mógł znaleźć usługi bez uprzedniego uzyskania informacji o jego adres.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Zobacz też
