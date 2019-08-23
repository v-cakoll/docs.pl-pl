---
title: Adresowanie
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 290c4648c0904135d11ad3d62280a30cd25bcbe5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945238"
---
# <a name="addressing"></a>Adresowanie
Przykład Addressing ilustruje różne aspekty i funkcje adresów punktów końcowych. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest samodzielna. Zarówno usługa, jak i klient są aplikacjami konsolowymi. Usługa definiuje wiele punktów końcowych przy użyciu kombinacji względnych i bezwzględnych adresów punktów końcowych.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi określa adres podstawowy i cztery punkty końcowe. Adres podstawowy jest określany przy użyciu elementu Add, w obszarze Service/Host/baseAddresses, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 Definicja pierwszego punktu końcowego pokazana w poniższej konfiguracji przykładowej określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adresu względnego, zgodnie z regułami kompozycji identyfikatora URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service`.
  
 Druga definicja punktu końcowego określa adres względny, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres względny "test" jest dołączany do adresu podstawowego. Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service/test`.
  
 Definicja trzeciego punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres podstawowy nie pełni żadnej roli w adresie. Rzeczywisty adres punktu końcowego to `http://localhost:8001/hello/servicemodelsamples`.
  
 Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP. Adres podstawowy nie pełni żadnej roli w adresie. Rzeczywisty adres punktu końcowego to `net.tcp://localhost:9000/servicemodelsamples/service`.
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 Klient uzyskuje dostęp tylko do jednego z czterech punktów końcowych usługi, ale wszystkie cztery są zdefiniowane w pliku konfiguracji. Klient wybiera punkt końcowy podczas tworzenia `CalculatorProxy` obiektu. Zmieniając nazwę konfiguracji z na `CalculatorEndpoint1` `CalculatorEndpoint4`, można wykonać każdy z punktów końcowych.  
  
 Po uruchomieniu przykładu usługa wylicza adres, nazwę powiązania i nazwę kontraktu dla każdego z punktów końcowych. Punkt końcowy wymiany metadanych (MEX) jest tylko innym punktem końcowym w perspektywie hosta ServiceHost, aby został wyświetlony na liście.  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 Po uruchomieniu klienta żądania operacji i odpowiedzi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
