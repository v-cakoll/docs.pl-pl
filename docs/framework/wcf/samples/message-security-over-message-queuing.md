---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 50f1e8f3a31b58306265b107016a979835f18ad9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664846"
---
# <a name="message-security-over-message-queuing"></a>Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
Ten przykład demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security przy użyciu uwierzytelniania certyfikatu X.509v3 dla klienta i wymaga uwierzytelnienia serwera za pomocą certyfikatu X.509v3 serwera za pośrednictwem usługi MSMQ. Komunikat zabezpieczeń jest czasem korzystniejsze, aby upewnić się, że komunikaty w magazynie usługi MSMQ pozostają zaszyfrowane i aplikacji można wykonać swoje własne uwierzytelniania wiadomości.

 Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. Komunikaty są szyfrowane i podpisany.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.

    1. Otwórz Menedżera serwera w programie Visual Studio 2012.

    2. Rozwiń **funkcji** kartę.

    3. Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.

    4. Sprawdź **transakcyjna** pole.

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Upewnij się, że ścieżka zawiera folder, który zawiera Makecert.exe i FindPrivateKey.exe.

2. Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    >  Upewnij się, usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu dla próbki. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
3. Uruchom Service.exe z \service\bin.  
  
4. Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
5. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1. Skopiuj pliki Setup.bat, Cleanup.bat i ImportClientCert.bat komputer usługi.  
  
2. Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
3. Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
4. Na serwerze, uruchom `setup.bat service`. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
5. Edytuj service.exe.config usługi, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
6. Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
7. Na komputerze klienckim, należy uruchomić `setup.bat client`. Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
8. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi. To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.  Należy także zmienić nazwę certyfikatu usługi, aby być taka sama jak w pełni kwalifikowana nazwa domeny komputera usługi (w `findValue` atrybutu w `defaultCertificate` elementu `serviceCertificate` w obszarze `clientCredentials`).  
  
9. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
10. Na komputerze klienckim, należy uruchomić `ImportServiceCert.bat`. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
11. Na serwerze, uruchom `ImportClientCert.bat`, to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
12. Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.  
  
13. Na komputerze klienckim należy uruchomić Client.exe w wierszu polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
- Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Wymagania
 Ten przykładowy skrypt wymaga, że usługa MSMQ jest zainstalowana i uruchomiona.

## <a name="demonstrates"></a>Demonstracje
 Klient szyfruje wiadomości przy użyciu klucza publicznego usługi i zarejestruje komunikat przy użyciu własnego certyfikatu. Usługi, odczytywanie wiadomości z kolejki uwierzytelnianie certyfikatu klienta przy użyciu certyfikatu w magazynie zaufanych osób. Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.

 Ponieważ komunikat usług Windows Communication Foundation (WCF) jest przenoszone jako ładunek w treści wiadomości usługi MSMQ, treść pozostają zaszyfrowane w magazynie usługi MSMQ. W ten sposób wiadomości przed ujawnieniem niechciane wiadomości. Zwróć uwagę, że usługi MSMQ, sama nie świadomość tego, czy komunikat go prowadzi są szyfrowane.

 W przykładzie pokazano sposób wzajemnego uwierzytelniania wglądu do wiadomości poziom może być używany z usługi MSMQ. Certyfikaty są wymieniane poza pasmem. Jest to zawsze w przypadku aplikacji umieszczonych w kolejce, ponieważ usługa i klient nie ma być uruchomiona w tym samym czasie.

## <a name="description"></a>Opis
 Przykładowy kod klienta i usługi są takie same jak [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki z jedną różnicą. Kontrakt operacji jest oznaczony za pomocą poziom ochrony, co sugeruje, że wiadomości muszą być podpisane i szyfrowane.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Aby upewnić się, że wiadomość jest zabezpieczona przy użyciu tokenu wymagany do identyfikowania usługi i klienta, App.config zawiera informacji o poświadczeniach.

 Konfiguracja klienta Określa certyfikat usługi do uwierzytelniania usługi. Użyto jej magazynie jako zaufany magazyn do zależą od ważności usługi. Określa również certyfikat klienta, który jest dołączony komunikat do usługi uwierzytelniania klienta.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 Należy zauważyć, że tryb zabezpieczeń jest ustawiony na komunikat i ClientCredentialType jest ustawiony na certyfikatu.

 Konfiguracja usługi zawiera zachowanie usługi, który określa poświadczenia, które są używane, gdy klient uwierzytelnia się usługi. Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 W przykładzie pokazano kontroli uwierzytelniania za pomocą konfiguracji i jak można uzyskać tożsamości elementu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 Po uruchomieniu kodu usługi Wyświetla identyfikator klienta. Poniżej przedstawiono przykładowe dane wyjściowe z kodem usługi:

```
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a>Komentarze

- Tworzenie certyfikatu klienta.

     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Podana nazwa klienta jest używany w nazwie podmiotu certyfikatu, utworzony. Certyfikat jest przechowywany w `My` przechowywać `CurrentUser` lokalizacji magazynu.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.

     Następujący wiersz w kopii pliku wsadowego certyfikat klienta do serwera TrustedPeople przechowywać tak, aby istotne zaufania lub decyzji dotyczących zaufania nie mogą być serwera. Certyfikat zainstalowany w magazynie TrustedPeople, aby być uważany za zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być równa `PeerOrChainTrust` lub `PeerTrust` wartość. Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić przy użyciu pliku konfiguracji.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Tworzenie certyfikatu serwera.

     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli instalacyjny plik wsadowy jest uruchamiany z nieprawidłowym argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera. W przeciwnym razie jego wartość domyślna to hosta lokalnego

- Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.

     Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Jeśli używasz spoza USA Wersja programu Microsoft Windows, należy edytować Setup.bat i zastąp nazwę konta "NT AUTHORITY\NETWORK SERVICE" ekwiwalent regionalne w języku angielskim.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
