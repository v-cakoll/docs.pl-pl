---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143723"
---
# <a name="udp-activation"></a>Aktywacja UDP
Ten przykład jest oparty na [transport: próbka UDP.](../../../../docs/framework/wcf/samples/transport-udp.md) Rozszerza [transport: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) do obsługi aktywacji procesu przy użyciu usługi aktywacji procesu systemu Windows (WAS).  
  
 Próbka składa się z trzech głównych elementów:  
  
- A UDP Protocol Activator, autonomiczny proces, który odbiera wiadomości UDP w imieniu aplikacji, które mają być aktywowane.  
  
- Klient, który używa transportu niestandardowego UDP do wysyłania wiadomości.  
  
- Usługa (hostowana w procesie roboczym aktywowanym przez was), która odbiera wiadomości za pomocą transportu niestandardowego UDP.  
  
## <a name="udp-protocol-activator"></a>Aktywator protokołu UDP  
 Aktywator protokołu UDP jest pomostem między klientem WCF a usługą WCF. Zapewnia komunikację danych za pośrednictwem protokołu UDP w warstwie transportu. Posiada dwie główne funkcje:  
  
- Was Listener Adapter (LA), który współpracuje z WAS, aby aktywować procesy w odpowiedzi na przychodzące wiadomości.  
  
- Odbiornik protokołu UDP, który akceptuje komunikaty UDP w imieniu aplikacji, które mają być aktywowane.  
  
 Aktywator musi być uruchomiony jako program autonomiczny na komputerze serwera. Zwykle karty odbiornika WAS (takie jak NetTcpActivator i NetPipeActivator) są implementowane w długotrwałych usługach systemu Windows. Jednak dla uproszczenia i przejrzystości w tym przykładzie implementuje aktywator protokołu jako autonomiczną aplikację.  
  
### <a name="was-listener-adapter"></a>Adapter odbiornika WAS  
 Adapter odbiornika WAS dla UDP jest `UdpListenerAdapter` zaimplementowana w klasie. Jest to moduł, który współdziała z was do wykonywania aktywacji aplikacji dla protokołu UDP. Osiąga się to poprzez wywołanie następujących interfejsów API usługi Webhost:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Po początkowym wywołaniu `WebhostRegisterProtocol`karta odbiornika `ApplicationCreated` odbiera wywołanie zwrotne z usługi WAS dla wszystkich aplikacji zarejestrowanych w aplikacjiHost.config (znajdującej się w %windir%\system32\inetsrv). W tym przykładzie obsługujemy tylko aplikacje z protokołem UDP (z identyfikatorem protokołu jako "net.udp") włączoną. Inne implementacje mogą obsługiwać to inaczej, jeśli takie implementacje reagują na dynamiczne zmiany konfiguracji aplikacji (na przykład przejście aplikacji z wyłączone do włączone).  
  
 Po odebraniu wywołania zwrotnego `ConfigManagerInitializationCompleted` oznacza, że usługa WAS zakończyła wszystkie powiadomienia dotyczące inicjowania protokołu. W tej chwili karta odbiornika jest gotowa do przetwarzania żądań aktywacji.  
  
 Gdy nowe żądanie pojawia się po raz pierwszy dla `WebhostOpenListenerChannelInstance` aplikacji, karta odbiornika wywołuje do usługi WAS, która uruchamia proces roboczy, jeśli nie jest jeszcze uruchomiona. Następnie są ładowane programy obsługi protokołu i można uruchomić komunikację między kartą odbiornika a aplikacją wirtualną.  
  
 Karta odbiornika jest zarejestrowana w sekcji %SystemRoot%\System32\inetsrv\ApplicationHost.config `listenerAdapters` w sekcji <> w następujący sposób:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Odbiornik protokołu  
 Odbiornik protokołu UDP jest modułem wewnątrz aktywatora protokołu, który nasłuchuje w punkcie końcowym UDP w imieniu aplikacji wirtualnej. Jest on realizowany w `UdpSocketListener`klasie . Punkt końcowy jest reprezentowany jako `IPEndpoint` dla których numer portu jest wyodrębniany z powiązania protokołu dla lokacji.  
  
### <a name="control-service"></a>Usługa sterowania  
 W tym przykładzie używamy WCF do komunikowania się między aktywatorem a procesem roboczym WAS. Usługa, która znajduje się w aktywatorze jest nazywany Control Service.  
  
## <a name="protocol-handlers"></a>Programy obsługi protokołów  
 Po wywołaniu `WebhostOpenListenerChannelInstance`karty odbiornika menedżer procesów WAS uruchamia proces roboczy, jeśli nie został uruchomiony. Menedżer aplikacji wewnątrz procesu roboczego następnie ładuje program obsługi protokołu procesu UDP (PPH) z żądaniem tego `ListenerChannelId`. PPH z kolei `IAdphManager`wywołuje .`StartAppDomainProtocolListenerChannel` , aby uruchomić program obsługi protokołu UDP AppDomain Protocol (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informacje są rejestrowane w witrynie Web.config w następujący sposób:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Specjalna konfiguracja dla tego przykładu  
 Ten przykład można zbudować i uruchomić tylko w systemach Windows Vista, Windows Server 2008 lub Windows 7. Aby uruchomić próbkę, należy najpierw poprawnie skonfigurować wszystkie składniki. Aby zainstalować próbkę, należy wykonać następujące kroki.  
  
#### <a name="to-set-up-this-sample"></a>Aby skonfigurować tę próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Tworzenie projektu w systemie Windows Vista. Po kompilacji wykonuje również następujące operacje w fazie po kompilacji:  
  
    - Instaluje powiązanie UDP z witryną "Domyślna witryna sieci Web".  
  
    - Tworzy aplikację wirtualną "ServiceModelSamples", aby wskazać ścieżkę fizyczną: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Umożliwia również protokół "net.udp" dla tej wirtualnej aplikacji.  
  
3. Uruchom aplikację interfejsu użytkownika "WasNetActivator.exe". Kliknij kartę **Ustawienia,** zaznacz następujące pola wyboru, a następnie kliknij pozycję **Zainstaluj,** aby je zainstalować:  
  
    - Adapter odbiornika UDP  
  
    - Programy obsługi protokołów UDP  
  
4. Kliknij kartę **Aktywacja** aplikacji interfejsu użytkownika "WasNetActivator.exe". Kliknij przycisk **Start,** aby uruchomić kartę odbiornika. Teraz możesz przystąpić do uruchomienia programu.  
  
    > [!NOTE]
    > Po zakończeniu pracy z tym przykładem należy uruchomić plik Cleanup.bat, aby usunąć powiązanie net.udp z "Domyślnej witryny sieci Web".  
  
## <a name="sample-usage"></a>Przykładowe użycie  
 Po kompilacji, istnieją cztery różne pliki binarne generowane:  
  
- Client.exe: Kod klienta. Plik App.config jest kompilowany do pliku konfiguracyjnego klienta Client.exe.config.  
  
- UDPActivation.dll: biblioteka, która zawiera wszystkie główne implementacje UDP.  
  
- Service.dll: Kod usługi. Jest to kopiowane do katalogu \bin wirtualnej aplikacji ServiceModelSamples. Plik usługi to Service.svc, a plik konfiguracyjny to Web.config. Po kompilacji są one kopiowane do następującej lokalizacji: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: program aktywatora UDP.  
  
- Upewnij się, że wszystkie wymagane elementy są prawidłowo zainstalowane. Poniższe kroki pokazują, jak uruchomić przykład:  
  
1. Upewnij się, że uruchomiono następujące usługi systemu Windows:  
  
    - Usługa aktywacji procesów systemu Windows (WAS).  
  
    - Internetowe usługi informacyjne (IIS): W3SVC.  
  
2. Następnie uruchom aktywator, WasNetActivator.exe. Na karcie **Aktywacja** na liście rozwijanej wybrano jedyny protokół **UDP.** Kliknij przycisk **Start,** aby uruchomić aktywator.  
  
3. Po uruchomieniu aktywatora można uruchomić kod klienta, uruchamiając client.exe z okna polecenia. Poniżej przedstawiono dane wyjściowe próbki:  
  
    ```console  
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
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
