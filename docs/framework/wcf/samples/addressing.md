---
title: Adresowanie
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: a59c3b354404169c2baadd4ab8c2702728d9a891
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767984"
---
# <a name="addressing"></a>Adresowanie
W przykładzie adresowanie pokazano różne aspekty i funkcje adresy punktów końcowych. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest samodzielnie hostowana. Usługi i klienta są aplikacji konsoli. Usługa definiuje wiele punktów końcowych przy użyciu kombinacji adresy punktów końcowych względnych i bezwzględnych.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi Określa adres bazowy i czterech punktów końcowych. Adres podstawowy jest określony, przy użyciu elementu Dodawanie, w ramach hosta/service/baseAddresses, jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
 Pierwszy definicji punktu końcowego pokazano w poniższym Przykładowa konfiguracja Określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny, zgodnie z regułami kompozycji identyfikatora URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taka sama jak adres podstawowy. Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service`.
  
 Drugi definicji punktu końcowego określa również adres względny, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres względny "test", jest dołączana do podstawowego adresu. Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service/test`.
  
 Trzeci definicji punktu końcowego określa adresem bezwzględnym, jak pokazano w poniższym Przykładowa konfiguracja.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres podstawowy odgrywa żadnej roli w adresie. Adres istniejący punkt końcowy jest `http://localhost:8001/hello/servicemodelsamples`.
  
 Adres punktu końcowego czwarty określa adresem bezwzględnym i innego transportu — TCP. Adres podstawowy odgrywa żadnej roli w adresie. Adres istniejący punkt końcowy jest `net.tcp://localhost:9000/servicemodelsamples/service`.
  
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
  
 Klient uzyskuje dostęp do tylko jednej z czterech końcowych, ale wszystkie cztery są zdefiniowane w pliku konfiguracji. Klient wybierze punkt końcowy, podczas tworzenia `CalculatorProxy` obiektu. Zmieniając nazwę konfiguracji z `CalculatorEndpoint1` za pośrednictwem `CalculatorEndpoint4`, można wykonywać każdego z punktów końcowych.  
  
 Po uruchomieniu przykładu, usługa wylicza adres powiązania nazwy i nazwy kontraktu dla każdego z jego punktów końcowych. Punkt końcowy metadanych programu exchange (MEX) jest po prostu innego punktu końcowego z punktu widzenia ServiceHost, więc pojawia się na liście.  
  
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
  
 Po uruchomieniu klienta, operacji żądań i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
