---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c64540db555d7cac56dd46c6ffb63ec95ca81f91
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493402"
---
# <a name="udp-activation"></a>Aktywacja UDP
Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. Rozszerza [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki do obsługi aktywacji procesu przy użyciu Windows Process Activation Service (WAS).  
  
 Przykład składa się z trzech głównych części:  
  
-   UDP protokołu aktywator, procesem autonomicznym, która odbiera komunikaty protokołu UDP w imieniu aplikacji, które mają być aktywowany.  
  
-   Klient, który używa niestandardowego transportu UDP do wysyłania wiadomości.  
  
-   Usługa (hostowane w procesie roboczym aktywowany przez WAS), która odbiera komunikaty za pośrednictwem protokołu UDP transportu niestandardowych.  
  
## <a name="udp-protocol-activator"></a>Aktywator protokołu UDP  
 Aktywator protokołu UDP jest mostem między klientem usługi WCF i usługi WCF. Umożliwia przesyłanie danych za pośrednictwem protokołu UDP w warstwie transportowej. Ma dwie główne funkcje:  
  
-   BYŁO odbiornika karty (LA), który współpracuje z WAS do aktywowania procesów w odpowiedzi na wiadomości przychodzące.  
  
-   Odbiornik protokołu UDP, który akceptuje komunikaty protokołu UDP w imieniu aplikacji, które mają być aktywowany.  
  
 Aktywator musi działać jako autonomiczna programu na komputerze z serwerem. Zazwyczaj karty listener WAS (na przykład NetTcpActivator i NetPipeActivator) są implementowane w usługach Windows długoterminowych. Jednak dla prostoty i jasności ten przykład implementuje aktywatora protokołu jako oddzielną aplikację.  
  
### <a name="was-listener-adapter"></a>ZOSTAŁ Adapter odbiornika  
 Adapter odbiornika zostało protokołu UDP został zaimplementowany w `UdpListenerAdapter` klasy. To jest moduł, który wchodzi w interakcję z WAS do wykonywania aktywacji aplikacji dla protokołu UDP. Jest to osiągane przez wywołanie następujące interfejsy API hostem sieci Web:  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 Po wywołaniu początkowo `WebhostRegisterProtocol`, karta odbiornika odbiera wywołania zwrotnego `ApplicationCreated` z WAS dla wszystkich aplikacji zarejestrowanych w pliku applicationHost.config (znajdujący się w % windir%\system32\inetsrv). W tym przykładzie będziemy obsługiwać aplikacje przy użyciu protokołu UDP (identyfikatorem protokołu jako "net.udp"), włączone. Inne implementacje może obsługiwać to inaczej w przypadku takich implementacje odpowiadanie na dynamiczną konfigurację zmian w aplikacji (na przykład aplikacja przejście z wyłączonego na włączony).  
  
 Podczas wywołania zwrotnego `ConfigManagerInitializationCompleted` zostanie odebrana, oznacza to, tym WAS zakończy wszystkie powiadomienia dotyczące inicjowania protokołu. W tej chwili adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.  
  
 Gdy nowe żądanie jest dostępna w aplikacji po raz pierwszy, wywołuje adapter odbiornika `WebhostOpenListenerChannelInstance` do WAS, który rozpoczyna się proces roboczy, jeśli nie jest jeszcze uruchomiona. Następnie są ładowane obsługi protokołu i umożliwić komunikację między kartą odbiornik i aplikacji wirtualnej.  
  
 Adapter odbiornika jest zarejestrowany w %SystemRoot%\System32\inetsrv\ApplicationHost.config w <`listenerAdapters`> sekcji, jako pokazano poniżej:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Odbiornik protokołu  
 Odbiornik protokołu UDP jest modułem wewnątrz aktywatora protokołu, który nasłuchuje w punkcie końcowym protokołu UDP w imieniu aplikacji wirtualnej. Jest zaimplementowana w klasie `UdpSocketListener`. Punkt końcowy jest reprezentowany jako `IPEndpoint` dla której są wyodrębniane numer portu z powiązania protokołu dla witryny.  
  
### <a name="control-service"></a>Usługa sterowania  
 W tym przykładzie używamy usługi WCF do komunikowania się między aktywator i proces roboczy WAS. Usługa, która znajduje się w aktywator nosi nazwę usługi kontroli.  
  
## <a name="protocol-handlers"></a>Programy obsługi protokołu  
 Po wywołania adapter odbiornika `WebhostOpenListenerChannelInstance`, menedżera procesów WAS rozpoczyna się proces roboczy, jeśli nie została uruchomiona. Menedżer aplikacji wewnątrz procesu roboczego ładuje obsługi protokołu procesu (PPH) UDP, z tym żądaniem, w tym `ListenerChannelId`. PPH w wywołaniach włącza `IAdphManager`.`StartAppDomainProtocolListenerChannel` Aby uruchomić UDP AppDomain protokołu obsługi (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informacje jest zarejestrowany w pliku Web.config w następujący sposób:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Specjalnej konfiguracji dla tego przykładu  
 W tym przykładzie można tylko skompilować i uruchomić na Windows Vista, Windows Server 2008 lub Windows 7. Do uruchomienia przykładu, należy najpierw uzyskać wszystkie składniki poprawnie skonfigurowane. Wykonaj następujące kroki, aby zainstalować przykład.  
  
#### <a name="to-set-up-this-sample"></a>Aby skonfigurować w tym przykładzie  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Skompiluj projekt w systemie Windows Vista. Po kompilacji również wykonuje następujące operacje w fazie po kompilacji:  
  
    -   Instaluje powiązania protokołu UDP do lokacji "Domyślna witryna sieci Web".  
  
    -   Tworzy aplikację wirtualną "ServiceModelSamples" wskaż ścieżkę fizyczną: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    -   Umożliwia ona także protokół "net.udp" dla tej aplikacji wirtualnej.  
  
3.  Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe". Kliknij przycisk **instalacji** kartę, zaznacz następujące pola wyboru, a następnie kliknij przycisk **zainstalować** je zainstalować:  
  
    -   Adapter odbiornika protokołu UDP  
  
    -   Programy obsługi protokołu UDP  
  
4.  Kliknij przycisk **aktywacji** kartę aplikacji interfejsu użytkownika "WasNetActivator.exe". Kliknij przycisk **Start** przycisk, aby uruchomić odbiornik karty. Teraz można przystąpić do uruchomienia programu.  
  
    > [!NOTE]
    >  Po zakończeniu tego przykładu, należy uruchomić Cleanup.bat, aby usunąć powiązanie net.udp z "Domyślna witryna sieci Web".  
  
## <a name="sample-usage"></a>Przykładowe zastosowanie  
 Po kompilacji dostępne są cztery różne pliki binarne wygenerowane:  
  
-   Client.exe: Kod klienta. App.config jest kompilowany do pliku konfiguracji klienta Client.exe.config.  
  
-   UDPActivation.dll: Biblioteka, która zawiera wszystkie główne implementacji protokołu UDP.  
  
-   Service.dll: W kodzie usługi. To jest kopiowany do katalogu \bin zestawu ServiceModelSamples pakiecie aplikacji wirtualnej. Plik usługi jest Service.svc i plik konfiguracji jest plik Web.config. Po kompilacji, są kopiowane do następującej lokalizacji: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
-   WasNetActivator: UDP aktywatora program.  
  
-   Upewnij się, że wszystkie wymagane elementy zostały zainstalowane poprawnie. Poniższe kroki pokazują jak do uruchomienia przykładu:  
  
1.  Upewnij się, że zostały uruchomione następujące usługi Windows:  
  
    -   Usługi Windows Process Activation Service (WAS).  
  
    -   Internetowe usługi informacyjne (IIS): W3SVC.  
  
2.  Następnie uruchom aktywator WasNetActivator.exe. W obszarze **aktywacji** karta, jedynym protokołem **UDP**, jest zaznaczony na liście rozwijanej. Kliknij przycisk **Start** przycisk, aby uruchomić aktywatora.  
  
3.  Po rozpoczęciu aktywator może uruchamiać kod klienta, uruchamiając Client.exe z okna poleceń. Poniżej przedstawiono przykładowe dane wyjściowe:  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a>Zobacz też
