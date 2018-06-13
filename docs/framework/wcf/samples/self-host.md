---
title: Host samodzielny
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: d4fc6c55f0eb528e6ae8d19d733c67d7f7ce135f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502681"
---
# <a name="self-host"></a>Host samodzielny
W tym przykładzie pokazano, jak wdrożyć własny hostowanej usługi w aplikacji konsoli. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Pliku konfiguracji usługi zostało zmienione z pliku Web.config do pliku App.config i zmodyfikować, aby skonfigurować adres podstawowy, który korzysta z hosta. Kod źródłowy usługi został zmodyfikowany w celu wykonania statycznego `Main` funkcji, które tworzy i otwiera hosta usługi, która udostępnia skonfigurowany adres podstawowy. Implementacji usługi został zmodyfikowany w celu zapisywania danych wyjściowych do konsoli dla każdej operacji. Klient został zostały zmodyfikowane, z wyjątkiem konfigurowania adresu właściwego punktu końcowego usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Próbki implementuje statycznej funkcji main utworzyć <xref:System.ServiceModel.ServiceHost> dla danego `CalculatorService` typ, jak pokazano w poniższym kodzie próbki.  
  
```  
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
  
 Gdy usługa jest obsługiwana w Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS), adres podstawowy usługi są udostępniane przez środowisko macierzyste. W przypadku hostowania samoobsługowego należy określić adres podstawowy samodzielnie. Odbywa się przy użyciu `add` element, podrzędny [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podrzędny [ \<hosta >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podrzędny [ \<usługi > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak przedstawiono w następujących Przykładowa konfiguracja.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
