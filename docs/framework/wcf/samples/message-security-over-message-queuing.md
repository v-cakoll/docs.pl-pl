---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 039ec21296392321fec40df2cae7383ccb3be6ea
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039344"
---
# <a name="message-security-over-message-queuing"></a>Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
Ten przykład pokazuje, jak zaimplementować aplikację, która korzysta z protokołu WS-Security z uwierzytelnianiem za pomocą certyfikatu X. 509v3 na potrzeby klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X. 509v3 serwera za pośrednictwem usługi MSMQ. Zabezpieczenia komunikatów są czasami bardziej pożądane, aby zapewnić, że komunikaty w magazynie usługi MSMQ pozostają zaszyfrowane, a aplikacja może wykonać własne uwierzytelnianie wiadomości.

 Ten przykład jest oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) . Komunikaty są szyfrowane i podpisane.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie istnieje, usługa utworzy ją. Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżer serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **funkcje** .

    3. Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.

    4. Zaznacz pole **transakcyjne** .

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Upewnij się, że ścieżka zawiera folder zawierający Makecert. exe i FindPrivateKey. exe.

2. Uruchom setup. bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Upewnij się, że certyfikaty są usuwane przez uruchomienie Oczyść. bat po zakończeniu z przykładem. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
3. Uruchom usługę Service. exe z \service\bin.  
  
4. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Skopiuj pliki Setup. bat, Oczyść. bat i ImportClientCert. bat do komputera usługi.  
  
2. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
3. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
4. Na serwerze uruchom `setup.bat service`polecenie. `setup.bat` Uruchomienie`service` z argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
5. Edytuj plik Service. exe. config usługi, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie [ \<w > serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
6. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
7. Na kliencie Uruchom `setup.bat client`polecenie. `setup.bat` Uruchomienie`client` z argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.  Należy również zmienić nazwę certyfikatu usługi tak samo jak w pełni kwalifikowana nazwa domeny komputera usługi ( `findValue` w atrybucie `defaultCertificate` w elemencie `serviceCertificate` w obszarze `clientCredentials`).  
  
9. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
10. Na kliencie Uruchom `ImportServiceCert.bat`polecenie. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
11. Na serwerze programu uruchom `ImportClientCert.bat`program, który importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.  
  
12. Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.  
  
13. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Wymagania
 Ten przykład wymaga, aby usługa MSMQ była zainstalowana i uruchomiona.

## <a name="demonstrates"></a>Demonstracje
 Klient szyfruje komunikat przy użyciu klucza publicznego usługi i podpisuje komunikat przy użyciu własnego certyfikatu. Usługa odczytująca komunikat z kolejki uwierzytelnia certyfikat klienta przy użyciu certyfikatu w magazynie zaufanych osób. Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.

 Ponieważ komunikat Windows Communication Foundation (WCF) jest przenoszony jako ładunek w treści wiadomości MSMQ, treść pozostaje zaszyfrowana w magazynie usługi MSMQ. Dzięki temu wiadomość jest zabezpieczona przed niechcianym ujawnieniem wiadomości. Należy zauważyć, że sama usługa MSMQ nie ma informacji o tym, czy komunikat, który jest na nim przenoszony, jest szyfrowany.

 W przykładzie pokazano, jak uwierzytelnianie obustronne na poziomie komunikatu może być używane z usługą MSMQ. Certyfikaty są wymieniane poza pasmem. Jest to zawsze przypadek z aplikacją umieszczoną w kolejce, ponieważ usługa i klient nie muszą działać w tym samym czasie.

## <a name="description"></a>Opis
 Przykładowy klient i kod usługi są takie same jak [transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) przykładowe z jedną różnicą. Umowa operacji ma adnotację z poziomem ochrony, która sugeruje, że komunikat musi być podpisany i szyfrowany.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Aby upewnić się, że komunikat jest zabezpieczony przy użyciu wymaganego tokenu do identyfikacji usługi i klienta, plik App. config zawiera informacje o poświadczeniu.

 Konfiguracja klienta określa certyfikat usługi do uwierzytelniania usługi. Używa magazynu LocalMachine jako zaufanego magazynu, aby polegać na ważności usługi. Określa również certyfikat klienta, który jest dołączony do wiadomości w celu uwierzytelnienia usługi klienta.

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

 Należy pamiętać, że tryb zabezpieczeń jest ustawiony na komunikat, a obiekt ClientCredentialtype jest ustawiony na wartość Certificate.

 Konfiguracja usługi obejmuje zachowanie usługi, które określa poświadczenia usługi, które są używane podczas uwierzytelniania usługi przez klienta. Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybucie [ \<w > ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 Przykład demonstruje kontrolę uwierzytelniania przy użyciu konfiguracji i sposób uzyskiwania tożsamości obiektu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:

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

 Po uruchomieniu kod usługi wyświetla identyfikację klienta. Poniżej przedstawiono przykładowe dane wyjściowe z kodu usługi:

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

     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu. Certyfikat jest przechowywany w `My` magazynie `CurrentUser` w lokalizacji magazynu.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów na serwerze.

     Następujący wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje zaufania lub braku zaufania. Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być ustawiony na `PeerOrChainTrust` wartość lub. `PeerTrust` Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracji.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Tworzenie certyfikatu serwera.

     Następujące wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Zmienna% nazwa_serwera% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy instalacji jest uruchamiany z argumentem usługi (np `setup.bat service`.),% nazwa_serwera% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie wartość domyślna to localhost

- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.

     Poniższy wiersz zawiera kopię certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Jeśli używasz innego niż U. S. Angielska wersja systemu Microsoft Windows należy edytować plik Setup. bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" własnym odpowiednikiem regionalnym.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
