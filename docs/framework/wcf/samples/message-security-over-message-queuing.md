---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144438"
---
# <a name="message-security-over-message-queuing"></a>Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
W tym przykładzie pokazano, jak zaimplementować aplikację, która używa usługi WS-Security z uwierzytelnianiem certyfikatu X.509v3 dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509v3 serwera za pośrednictwem usługi MSMQ. Zabezpieczenia wiadomości jest czasami bardziej pożądane, aby upewnić się, że wiadomości w magazynie USŁUGI MSMQ pozostają zaszyfrowane i aplikacja może wykonać własne uwierzytelnianie wiadomości.

 Ten przykład jest oparty na próbce [wiązania transacted MSMQ.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) Wiadomości są szyfrowane i podpisane.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Jeśli usługa jest uruchamiana jako pierwsza, sprawdzi, czy kolejka jest obecna. Jeśli kolejka nie jest obecny, usługa utworzy jeden. Usługę można uruchomić najpierw, aby utworzyć kolejkę, lub utworzyć ją za pośrednictwem Menedżera kolejek usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.

    1. Otwórz Menedżera serwera w programie Visual Studio 2012.

    2. Rozwiń kartę **Funkcje.**

    3. Kliknij prawym przyciskiem myszy **pozycję Kolejki wiadomości prywatnych**i wybierz polecenie **Nowa**, **Kolejka prywatna**.

    4. Zaznacz pole **Transakcyjne.**

    5. Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.

3. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze

1. Upewnij się, że ścieżka zawiera folder zawierający pliki Makecert.exe i FindPrivateKey.exe.

2. Uruchom plik Setup.bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.

    > [!NOTE]
    > Upewnij się, że certyfikaty zostały ściął certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
3. Uruchom program Service.exe z \service\bin.  
  
4. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Skopiuj pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputer usługi.  
  
2. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
3. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
4. Na serwerze `setup.bat service`uruchom program . Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
5. Edytuj service's service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
6. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
7. Na kliencie `setup.bat client`uruchom program . Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
8. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi. W tym celu można zastąpić hosta lokalnego w pełni kwalifikowaną nazwą domeny serwera.  Należy również zmienić nazwę certyfikatu usługi tak, aby była taka sama jak w `findValue` pełni kwalifikowana nazwa domeny komputera usługowego (w atrybucie w `defaultCertificate` elemencie `serviceCertificate` under `clientCredentials`).  
  
9. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
10. Na kliencie `ImportServiceCert.bat`uruchom program . Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
11. Na serwerze `ImportClientCert.bat`uruchom program Uruchom program Ta importuje certyfikat klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.  
  
12. Na komputerze z usługami uruchom program Service.exe z wiersza polecenia.  
  
13. Na komputerze klienckim uruchom program Client.exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
    > [!NOTE]
    > Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Wymagania
 Ten przykład wymaga zainstalowania i uruchomienia usługi MSMQ.

## <a name="demonstrates"></a>Demonstracje
 Klient szyfruje wiadomość przy użyciu klucza publicznego usługi i podpisuje wiadomość przy użyciu własnego certyfikatu. Usługa odczytywania wiadomości z kolejki uwierzytelnia certyfikat klienta z certyfikatem w magazynie zaufanych osób. Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.

 Ponieważ komunikat Fundacji Komunikacji systemu Windows (WCF) jest przenoszony jako ładunek w treści wiadomości MSMQ, treść pozostaje zaszyfrowana w magazynie usługi MSMQ. Zabezpiecza to wiadomość przed niechcianym ujawnieniem wiadomości. Należy zauważyć, że sam program MSMQ nie wie, czy wiadomość, którą nosi, jest szyfrowana.

 W przykładzie pokazano, jak wzajemne uwierzytelnianie na poziomie wiadomości może być używane z usługą MSMQ. Certyfikaty są wymieniane poza pasmem. Jest to zawsze w przypadku aplikacji w kolejce, ponieważ usługa i klient nie muszą być uruchomione w tym samym czasie.

## <a name="description"></a>Opis
 Przykładowy kod klienta i usługi są takie same jak próbka [powiązania usługi Transacted MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) z jedną różnicą. Kontrakt operacyjny jest adnotacjami o poziomie ochrony, co sugeruje, że wiadomość musi być podpisana i zaszyfrowana.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Aby upewnić się, że wiadomość jest zabezpieczona przy użyciu tokenu wymaganego do identyfikowania usługi i klienta, App.config zawiera informacje o poświadczeniach.

 Konfiguracja klienta określa certyfikat usługi do uwierzytelniania usługi. Używa magazynu LocalMachine jako zaufanego magazynu, aby polegać na ważności usługi. Określa również certyfikat klienta, który jest dołączony do komunikatu do uwierzytelniania usługi klienta.

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

 Należy zauważyć, że tryb zabezpieczeń jest ustawiony na Message i ClientCredentialType jest ustawiona na certyfikat.

 Konfiguracja usługi zawiera zachowanie usługi, które określa poświadczenia usługi, które są używane, gdy klient uwierzytelnia usługę. Nazwa podmiotu certyfikatu serwera `findValue` jest określona w atrybucie w [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 W przykładzie pokazano kontrolowanie uwierzytelniania przy użyciu konfiguracji i jak uzyskać tożsamość wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:

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

```console
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

     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu. Certyfikat jest przechowywany `My` w `CurrentUser` magazynie w lokalizacji sklepu.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta w magazynie zaufanych certyfikatów serwera.

     Poniższy wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje dotyczące zaufania lub braku zaufania. Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), `PeerOrChainTrust` należy `PeerTrust` ustawić lub wartość trybu sprawdzania poprawności certyfikatu klienta. Zobacz przykład poprzedniej konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracyjnego.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Tworzenie certyfikatu serwera.

     Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     Zmienna %SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy instalatora jest uruchamiany `setup.bat service`z argumentem usługi (na przykład ) %SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie domyślnie host localhost

- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.

     Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Jeśli używasz wersji systemu Microsoft Windows w wersji innej niż amerykańska, musisz edytować plik Setup.bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" regionalnym odpowiednikiem.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
