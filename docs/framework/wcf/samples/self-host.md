---
title: Host samodzielny
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 26a2cc6e7e4a023915f2e63009aa1570528cedf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964572"
---
# <a name="self-host"></a>Host samodzielny
Ten przykład pokazuje, jak wdrożyć usługę samoobsługową w aplikacji konsolowej. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Zmieniono nazwę pliku konfiguracji usługi z Web. config na App. config i zmodyfikowano, aby skonfigurować adres podstawowy używany przez hosta. Kod źródłowy usługi został zmodyfikowany w celu zaimplementowania funkcji `Main` statycznej, która tworzy i otwiera hosta usługi, który udostępnia skonfigurowany adres podstawowy. Implementacja usługi została zmodyfikowana w celu zapisania danych wyjściowych w konsoli dla każdej operacji. Klient został niezmodyfikowany, z wyjątkiem konfigurowania poprawnego adresu punktu końcowego usługi.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład implementuje statyczną funkcję Main, aby utworzyć <xref:System.ServiceModel.ServiceHost> dla danego `CalculatorService` typu, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 Gdy usługa jest hostowana w usłudze Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS), adres podstawowy usługi jest dostarczany przez środowisko hostingu. W przypadku samodzielnego udostępniania należy samodzielnie określić adres podstawowy. Odbywa się to za pomocą `add` elementu, elementu [ \<podrzędnego baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu podrzędnego [ \<> hosta](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), elementu podrzędnego > usługi, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
