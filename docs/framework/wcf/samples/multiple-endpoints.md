---
title: Wiele punktów końcowych
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: 438c321e44f04060a733b90ccdbf02caba9406c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112713"
---
# <a name="multiple-endpoints"></a>Wiele punktów końcowych
Przykład wiele punktów końcowych pokazuje, jak skonfigurować wiele punktów końcowych usługi oraz jak komunikować się z każdego punktu końcowego z klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Konfiguracja usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe, które obsługują `ICalculator` kontraktu, ale każdy na inny adres za pomocą różnych powiązania. Konfiguracja klienta i kod zostały zmodyfikowane w celu komunikacji zarówno z punktów końcowych usługi.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Plik Web.config usługi została zmodyfikowana, aby zdefiniować dwa punkty końcowe, każda obsługuje takie same `ICalculator` kontraktu, ale pod różnymi adresami przy użyciu różnych powiązania. Pierwszy punkt końcowy jest zdefiniowana na adres bazowy przy użyciu `basicHttpBinding` powiązanie, które nie ma włączoną obsługą zabezpieczeń. Drugi punkt końcowy jest zdefiniowany w {baseaddress} / bezpieczne korzystają `wsHttpBinding` powiązania, który jest domyślnie bezpieczny, za pomocą usługi WS-Security przy użyciu uwierzytelniania Windows.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 Oba punkty końcowe są również skonfigurowane na komputerze klienckim. Te punkty końcowe są podanej nazwy, co obiekt wywołujący może przekazywać nazwę jednostki żądanego punktu końcowego do konstruktora obiektu klienta.  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="basicHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
            address="http://localhost/servicemodelsamples/service.svc/secure"   
            binding="wsHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 Klient używa zarówno punkty końcowe, jak pokazano w poniższym kodzie.  
  
```csharp  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 Po uruchomieniu klienta, interakcji z obu punkty końcowe są wyświetlane.  
  
```  
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
