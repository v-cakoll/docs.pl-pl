---
title: Aktywacja UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 0f5d07e65abc0b29989834aff496f7c27ea557b5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715805"
---
# <a name="udp-activation"></a>Aktywacja UDP
Ten przykład jest oparty na [transportie: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) . Rozszerza [transport: przykład UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w celu obsługi aktywacji procesu przy użyciu usługi aktywacji procesów systemu Windows (was).  
  
 Przykład składa się z trzech głównych elementów:  
  
- Aktywator protokołu UDP, autonomiczny proces odbierający komunikaty UDP w imieniu aplikacji, które mają zostać aktywowane.  
  
- Klient korzystający z transportu niestandardowego UDP do wysyłania komunikatów.  
  
- Usługa (hostowana w procesie roboczym aktywowana przez usługę WAS), która odbiera komunikaty za pośrednictwem transportu niestandardowego protokołu UDP.  
  
## <a name="udp-protocol-activator"></a>Aktywator protokołu UDP  
 Aktywator protokołu UDP jest mostkiem między klientem programu WCF a usługą WCF. Zapewnia ona komunikację z danymi za pomocą protokołu UDP w warstwie transportowej. Ma dwie główne funkcje:  
  
- Adapter odbiornika (LA), który współpracuje z programem, można aktywować procesy w odpowiedzi na komunikaty przychodzące.  
  
- Odbiornik protokołu UDP, który akceptuje komunikaty UDP w imieniu aplikacji, które mają zostać aktywowane.  
  
 Aktywator musi być uruchomiony jako program autonomiczny na komputerze serwera. Zazwyczaj były to karty odbiornika (takie jak NetTcpActivator i NetPipeActivator), które są implementowane w długotrwałych usługach systemu Windows. Jednak w przypadku uproszczenia i przejrzystości ten przykład implementuje aktywatora protokołu jako autonomiczną aplikację.  
  
### <a name="was-listener-adapter"></a>Adapter odbiornika  
 Adapter odbiornika dla UDP został zaimplementowany w klasie `UdpListenerAdapter`. Jest to moduł, który współdziała z programem, aby przeprowadzić aktywację aplikacji dla protokołu UDP. Jest to osiągane przez wywołanie następujących interfejsów API webhost:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Po pierwszym wywołaniu `WebhostRegisterProtocol`Adapter odbiornika odbiera wywołanie zwrotne `ApplicationCreated` od były przeznaczone dla wszystkich aplikacji zarejestrowanych w pliku applicationHost. config (znajdującym się w%windir%\system32\inetsrv). W tym przykładzie obsługujemy tylko aplikacje z protokołem UDP (z identyfikatorem protokołu "net. UDP"). Inne implementacje mogą być obsługiwane inaczej, jeśli takie implementacje odpowiadają na dynamiczne zmiany konfiguracji aplikacji (np. przejście aplikacji z wyłączone na włączone).  
  
 Po odebraniu `ConfigManagerInitializationCompleted` wywołania zwrotnego wskazuje, że został zakończony wszystkie powiadomienia dotyczące inicjowania protokołu. W tej chwili Adapter odbiornika jest gotowy do przetwarzania żądań aktywacji.  
  
 Gdy nowe żądanie jest uruchamiane po raz pierwszy dla aplikacji, Adapter odbiornika wywołuje `WebhostOpenListenerChannelInstance`, co uruchamia proces roboczy, jeśli nie został jeszcze uruchomiony. Następnie programy obsługi protokołów są ładowane, a komunikacja między kartą odbiornika i aplikacją wirtualną może zostać uruchomiona.  
  
 Karta odbiornika jest zarejestrowana w%SystemRoot%\System32\inetsrv\ApplicationHost.config w sekcji <`listenerAdapters`> w następujący sposób:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Odbiornik protokołu  
 Odbiornik protokołu UDP jest modułem w ramach aktywatora protokołu, który nasłuchuje w punkcie końcowym UDP w imieniu aplikacji wirtualnej. Jest zaimplementowana w klasie `UdpSocketListener`. Punkt końcowy jest reprezentowany jako `IPEndpoint`, dla którego jest wyodrębniany numer portu z powiązania protokołu dla lokacji.  
  
### <a name="control-service"></a>Usługa sterowania  
 W tym przykładzie używamy funkcji WCF do komunikacji między aktywatorem a procesem roboczym. Usługa, która znajduje się w aktywatora, nazywa się usługą kontroli.  
  
## <a name="protocol-handlers"></a>Programy obsługi protokołów  
 Gdy Adapter odbiornika wywoła `WebhostOpenListenerChannelInstance`, Menedżer przetworzenia przetwarza proces roboczy, jeśli nie został uruchomiony. Menedżer aplikacji wewnątrz procesu roboczego ładuje program obsługi protokołu UDP (PPH) żądania dla tego `ListenerChannelId`. PPH w programie włącza wywołania `IAdphManager`.`StartAppDomainProtocolListenerChannel` Aby uruchomić procedurę obsługi protokołu UDP AppDomain (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 Informacje są rejestrowane w pliku Web. config w następujący sposób:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Specjalna instalacja dla tego przykładu  
 Ten przykład może być zbudowany i uruchamiany tylko w systemie Windows Vista, Windows Server 2008 lub Windows 7. Aby uruchomić przykład, należy najpierw pobrać wszystkie składniki skonfigurowane prawidłowo. Wykonaj poniższe kroki, aby zainstalować przykład.  
  
#### <a name="to-set-up-this-sample"></a>Aby skonfigurować ten przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Skompiluj projekt w systemie Windows Vista. Po kompilacji wykonuje także następujące operacje w fazie po kompilacji:  
  
    - Instaluje powiązanie UDP z witryną "Default Web Site".  
  
    - Tworzy aplikację wirtualną "ServiceModelSamples" w celu wskazywania ścieżki fizycznej: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Włącza również protokół "net. UDP" dla tej aplikacji wirtualnej.  
  
3. Uruchom aplikację interfejsu użytkownika "WasNetActivator. exe". Kliknij kartę **Instalator** , zaznacz następujące pola wyboru, a następnie kliknij przycisk **Instaluj** , aby je zainstalować:  
  
    - Adapter odbiornika UDP  
  
    - Procedury obsługi protokołu UDP  
  
4. Kliknij kartę **Aktywacja** aplikacji interfejsu użytkownika "WasNetActivator. exe". Kliknij przycisk **Uruchom** , aby uruchomić Adapter odbiornika. Teraz można przystąpić do uruchamiania programu.  
  
    > [!NOTE]
    > Po zakończeniu pracy z tym przykładem należy uruchomić polecenie Oczyść. bat, aby usunąć powiązanie net. UDP z "domyślnej witryny sieci Web".  
  
## <a name="sample-usage"></a>Przykładowe użycie  
 Po kompilacji są generowane cztery różne pliki binarne:  
  
- Client. exe: kod klienta. Plik App. config jest kompilowany do pliku konfiguracji klienta Client. exe. config.  
  
- UDPActivation. dll: Biblioteka, która zawiera wszystkie główne implementacje protokołu UDP.  
  
- Service. dll: kod usługi. Jest on kopiowany do katalogu \Bin aplikacji wirtualnej ServiceModelSamples. Plik usługi to Service. svc, a plik konfiguracji to Web. config. Po kompilacji są one kopiowane do następującej lokalizacji:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: program aktywatora UDP.  
  
- Upewnij się, że wszystkie wymagane elementy są poprawnie zainstalowane. Poniższe kroki pokazują, jak uruchomić przykład:  
  
1. Upewnij się, że następujące usługi systemu Windows zostały uruchomione:  
  
    - Usługa aktywacji procesów systemu Windows (WAS).  
  
    - Internet Information Services (IIS): W3SVC.  
  
2. Następnie uruchom aktywatora, WasNetActivator. exe. Na karcie **Aktywacja** na liście rozwijanej jest wybierany tylko protokół **UDP**. Kliknij przycisk **Uruchom** , aby uruchomić aktywatora.  
  
3. Po uruchomieniu aktywatora można uruchomić kod klienta, uruchamiając program Client. exe z okna polecenia. Oto przykładowe dane wyjściowe:  
  
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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
