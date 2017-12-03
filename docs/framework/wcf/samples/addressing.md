---
title: Adresowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05fe983832eb3931549bbda5ee7db7c70766cd3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="addressing"></a>Adresowanie
Przykładowe adresowanie przedstawiono różne aspekty i funkcje adresy punktów końcowych. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). W tym przykładzie usługa jest samodzielnie hostowana. Zarówno usługa i klient są aplikacji konsoli. Usługa definiuje wiele punktów końcowych przy użyciu kombinacji adresy punktów końcowych względne i bezwzględne.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracyjny usługi Określa adres bazowy i czterech punktów końcowych. Adres podstawowy jest określona za pomocą elementu add, w obszarze usługi/hosta/baseAddress, jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
  
 Pierwszy definicji punktu końcowego pokazano w poniższych Przykładowa konfiguracja Określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny zgodnie z regułami kompozycji identyfikatora URI.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 W takim przypadku adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/usług.  
  
 Druga definicja punkt końcowy określa również adresem względnym, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres względny "test", jest dołączany do adres podstawowy. Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/service/testowanie oprogramowania.  
  
 Trzeci definicji punktu końcowego określa adresu bezwzględnego, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Adres podstawowy pełni żadnej roli w adresie. Adres rzeczywisty punkt końcowy jest http://localhost:8001/hello/servicemodelsamples.  
  
 Adres punktu końcowego czwarty Określa adres bezwzględny i innego transportu — TCP. Adres podstawowy pełni żadnej roli w adresie. Adres rzeczywisty punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usług.  
  
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
  
 Klient uzyskuje dostęp do co najmniej jeden punktów końcowych cztery usługi, ale wszystkie cztery są zdefiniowane w pliku konfiguracji. Klient wybiera punkt końcowy, podczas tworzenia `CalculatorProxy` obiektu. Zmiana nazwy konfiguracji z `CalculatorEndpoint1` za pośrednictwem `CalculatorEndpoint4`, można wykonywać każdego z punktów końcowych.  
  
 Po uruchomieniu próbki usługi wylicza adres powiązanie nazwy i nazwy kontraktu dla każdego z jego punktów końcowych. Punkt końcowy metadanych programu exchange (MEX) jest tylko inny punkt końcowy z punktu widzenia ServiceHost, jest wyświetlane na liście.  
  
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
  
 Po uruchomieniu klienta operacji żądania i odpowiedzi są wyświetlane w oknach konsoli usługi i klienta. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kodu klienta.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a>Zobacz też
