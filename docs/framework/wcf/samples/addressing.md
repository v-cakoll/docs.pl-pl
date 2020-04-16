---
title: Adresowanie
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 55bb30ba3df80e41986b1337f8732dd8ad3231ff
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463768"
---
# <a name="addressing"></a>Adresowanie
Przykład Adresowania pokazuje różne aspekty i funkcje adresów końcowych. Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest hostowana samodzielnie. Zarówno usługa, jak i klient są aplikacjami konsoli. Usługa definiuje wiele punktów końcowych przy użyciu kombinacji względnych i bezwzględnych adresów końcowych.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi określa adres podstawowy i cztery punkty końcowe. Adres podstawowy jest określony przy użyciu elementu add, w obszarze service/host/baseAddresses, jak pokazano w poniższej konfiguracji przykładowej.  
  
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
  
 Pierwsza definicja punktu końcowego pokazana w poniższej przykładowej konfiguracji określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu bazowego i adresu względnego zgodnie z regułami składu identyfikatora URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service`końcowego to .
  
 Druga definicja punktu końcowego określa również adres względny, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres względny ,,test", jest dołączany do adresu podstawowego. Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service/test`końcowego to .
  
 Trzecia definicja punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres podstawowy nie odgrywa żadnej roli w adresie. Rzeczywisty adres punktu `http://localhost:8001/hello/servicemodelsamples`końcowego to .
  
 Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP. Adres podstawowy nie odgrywa żadnej roli w adresie. Rzeczywisty adres punktu `net.tcp://localhost:9000/servicemodelsamples/service`końcowego to .
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Klient uzyskuje dostęp tylko do jednego z czterech punktów końcowych usługi, ale wszystkie cztery są zdefiniowane w pliku konfiguracji. Klient wybiera punkt końcowy podczas tworzenia `CalculatorProxy` obiektu. Zmieniając nazwę konfiguracji `CalculatorEndpoint1` z `CalculatorEndpoint4`za pośrednictwem , można wykonywać każdy z punktów końcowych.  
  
 Po uruchomieniu próbki usługa wylicza adres, nazwa powiązania i nazwę kontraktu dla każdego z jego punktów końcowych. Punkt końcowy wymiany metadanych (MEX) jest tylko inny punkt końcowy z punktu widzenia ServiceHost, więc pojawia się na liście.  
  
```console  
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
  
 Po uruchomieniu klienta żądania operacji i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Jeśli używasz Svcutil.exe do ponownego wygenerowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
