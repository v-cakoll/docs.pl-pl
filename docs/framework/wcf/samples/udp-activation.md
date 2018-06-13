---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810034"
---
# <a name="udp-activation"></a>Aktywacja UDP
Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. Rozszerza [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki do obsługi aktywacji procesu przy użyciu usługi aktywacji procesów systemu Windows (WAS).  
  
 Przykład obejmuje trzy główne:  
  
-   UDP protokołu aktywatora, proces autonomiczny, który odbiera komunikaty UDP w imieniu aplikacji, które mają być aktywowany.  
  
-   Klient, który używa niestandardowych transportu UDP do wysyłania komunikatów.  
  
-   Usługa (obsługiwanych przez proces roboczy aktywowany przez WAS), która odbiera komunikaty za pomocą niestandardowych transportu UDP.  
  
## <a name="udp-protocol-activator"></a>Aktywator protokołu UDP  
 Aktywator protokół UDP jest mostek między klienta WCF i usługi WCF. Zapewnia komunikację danych za pośrednictwem protokołu UDP w warstwie transportowej. Składa się z dwóch głównych funkcji:  
  
-   ZOSTAŁ odbiornika karty (LA), który współpracuje z WAS do aktywowania procesów w odpowiedzi na wiadomości przychodzących.  
  
-   Odbiornika protokołu UDP, który akceptuje wiadomości UDP w imieniu aplikacji, które mają być aktywowany.  
  
 Aktywator musi działać jako autonomiczny program na komputerze z serwerem. Zwykle WAS odbiornika kart (takie jak usługi NetTcpActivator i NetPipeActivator) zostały wdrożone w długim usług systemu Windows. Jednak dla uproszczenia i przejrzystości, w tym przykładzie implementuje protokół aktywatora jako aplikacja autonomiczna.  
  
### <a name="was-listener-adapter"></a>Adapter odbiornika zostało  
 Adapter odbiornika zostało UDP jest zaimplementowana w `UdpListenerAdapter` klasy. Jest moduł, który współdziała z WAS do wykonywania aktywacji aplikacji dla protokołu UDP. Jest to osiągane przez wywołanie metody Webhost API:  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 Po wywołaniu metody początkowo `WebhostRegisterProtocol`, adapter odbiornika odbiera wywołania zwrotnego `ApplicationCreated` z WAS dla wszystkich aplikacji w zarejestrowany w pliku applicationHost.config (znajdujący się w % windir%\system32\inetsrv). W tym przykładzie mamy tylko obsługi aplikacji przy użyciu protokołu UDP (o identyfikatorze protokołu jako "net.udp") włączone. Implementacje mogą obsługiwać to inaczej, jeśli takie implementacje reagowania na zmiany konfiguracji dynamicznej dla aplikacji (na przykład aplikacji przejście wyłączonego na włączony).  
  
 Podczas wywołania zwrotnego `ConfigManagerInitializationCompleted` zostanie odebrana, oznacza to, że WAS zakończył wszystkie powiadomienia do inicjowania protokołu. W tej chwili adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.  
  
 Gdy nowe żądanie w aplikacji po raz pierwszy, wywołuje adapter odbiornika `WebhostOpenListenerChannelInstance` do WAS, który rozpoczyna się proces roboczy, jeśli nie jest jeszcze uruchomiona. Następnie obsług protokołu są ładowane i umożliwić komunikację między adapter odbiornika i aplikacji wirtualnej.  
  
 Adapter odbiornika jest zarejestrowany w %SystemRoot%\System32\inetsrv\ApplicationHost.config w <`listenerAdapters`> sekcji jako następujące czynności:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Protokół odbiornika  
 Protokół UDP odbiornika jest modułem wewnątrz aktywatora protokołu, która nasłuchuje na punkt końcowy protokołu UDP w imieniu aplikacji wirtualnej. Jest zaimplementowana w klasie `UdpSocketListener`. Punkt końcowy jest reprezentowany jako `IPEndpoint` dla którego numer portu jest wyodrębniana z powiązania protokołu dla tej lokacji.  
  
### <a name="control-service"></a>Sterowanie  
 W tym przykładzie używamy WCF do komunikacji między aktywatora i proces roboczy WAS. Usługa, która znajduje się w aktywatora nosi nazwę usługi kontroli.  
  
## <a name="protocol-handlers"></a>Programy obsługi protokołu  
 Po wywołania adapter odbiornika `WebhostOpenListenerChannelInstance`, Menedżer procesu WAS uruchamia proces roboczy, jeśli nie jest uruchomiona. Menedżer aplikacji wewnątrz proces roboczy ładuje obsługi protokołu procesu (PPH) UDP, z żądaniem w tym `ListenerChannelId`. PPH w wywołaniach włącza `IAdphManager`.`StartAppDomainProtocolListenerChannel` Aby uruchomić program obsługi protokołu domeny aplikacji UDP (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informacje jest zarejestrowany w pliku Web.config:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Specjalnych ustawień dla tego przykładu  
 W tym przykładzie można tylko wbudowane i uruchomić w systemie Windows Vista, Windows Server 2008 lub Windows 7. Aby uruchomić próbki, należy najpierw pobrać wszystkie składniki są nieprawidłowo skonfigurowane. Wykonaj następujące kroki, aby zainstalować przykład.  
  
#### <a name="to-set-up-this-sample"></a>Aby skonfigurować ten przykład  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Skompiluj projekt w systemie Windows Vista. Po kompilacji również wykonuje następujące operacje w fazie mające miejsce po kompilacji:  
  
    -   Instaluje powiązania protokołu UDP do witryny "Default Web Site".  
  
    -   Tworzy aplikację wirtualną "ServiceModelSamples" wskaż ścieżkę fizyczną: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    -   Umożliwia również protokół "net.udp" dla tej aplikacji wirtualnej.  
  
3.  Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe". Kliknij przycisk **Instalator** karcie, sprawdź poniższe pola wyboru, a następnie kliknij przycisk **zainstalować** ich instalowania:  
  
    -   Adapter odbiornika protokołu UDP  
  
    -   Programy obsługi protokołu UDP  
  
4.  Kliknij przycisk **aktywacji** na karcie aplikacja interfejsu użytkownika "WasNetActivator.exe". Kliknij przycisk **Start** przycisk, aby uruchomić adapter odbiornika. Teraz można przystąpić do uruchomienia programu.  
  
    > [!NOTE]
    >  Po zakończeniu tej próbki, należy uruchomić Cleanup.bat usunąć powiązania net.udp z "Default Web Site".  
  
## <a name="sample-usage"></a>Przykładowe zastosowanie  
 Po kompilacji istnieją cztery różne pliki binarne wygenerowane:  
  
-   Client.exe: Kod klienta. App.config jest skompilowany w pliku konfiguracji klienta Client.exe.config.  
  
-   UDPActivation.dll: Biblioteka, która zawiera wszystkie główne implementacje protokołu UDP.  
  
-   Service.dll: Kodzie usługi. To jest kopiowana do katalogu \bin ServiceModelSamples aplikacji wirtualnej. Plik usługi jest Service.svc i plik konfiguracji jest pliku Web.config. Po kompilacji, są kopiowane do następującej lokalizacji: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
-   WasNetActivator: UDP aktywatora program.  
  
-   Upewnij się, że wszystkie wymagane elementy zostały zainstalowane poprawnie. Poniższe kroki przedstawiają sposób uruchamiania próbki:  
  
1.  Upewnij się, że zostały uruchomione następujące usługi systemu Windows:  
  
    -   Usługa aktywacji procesów systemu Windows (WAS).  
  
    -   Internetowe usługi informacyjne (IIS): W3SVC.  
  
2.  Następnie uruchom aktywatora WasNetActivator.exe. W obszarze **aktywacji** kartę, jedynym protokołem **UDP**, jest zaznaczona na liście rozwijanej. Kliknij przycisk **Start** przycisk, aby uruchomić aktywatora.  
  
3.  Po rozpoczęciu aktywatora kod klienta można uruchomić, uruchamiając Client.exe z okna poleceń. Oto przykładowe dane wyjściowe:  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a>Zobacz też
