---
title: "Zabezpieczenia komunikatów w ramach kolejkowania komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6e3d87ab31b7a0910b270e81c28985ffe9279d4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="message-security-over-message-queuing"></a>Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
W tym przykładzie pokazano, jak wdrożyć aplikację, która używa WS-Security przy użyciu uwierzytelniania certyfikatu X.509v3 klienta i wymaga uwierzytelniania serwera za pomocą certyfikatu X.509v3 serwera za pośrednictwem usługi MSMQ. Komunikat zabezpieczeń jest czasami więcej pożądane, aby upewnić się, że komunikaty w magazynie usługi MSMQ pozostaną zaszyfrowane i aplikacji, można wykonać uwierzytelniania wiadomości.  
  
 Ten przykład jest oparty na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki. Komunikaty są zaszyfrowana i podpisana.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny. Jeśli kolejka nie jest obecny, będzie utworzyć usługę. Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ. Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.  
  
    1.  Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Rozwiń węzeł **funkcje** kartę.  
  
    3.  Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.  
  
    4.  Sprawdź **transakcyjna** pole.  
  
    5.  Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Upewnij się, że ścieżka zawiera folder zawierający Makecert.exe i FindPrivateKey.exe.  
  
2.  Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Upewnij się, Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu z próbką. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
3.  Uruchom Service.exe z \service\bin.  
  
4.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
5.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Skopiuj pliki pliku Setup.bat, Cleanup.bat i ImportClientCert.bat do komputera usług.  
  
2.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
3.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
4.  Na serwerze, uruchom `setup.bat service`. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
5.  Edytuj service.exe.config usługi, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.  
  
6.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
7.  Na komputerze klienckim, uruchom `setup.bat client`. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi. W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.  Należy również zmienić nazwę certyfikatu usługa jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera usługi (w `findValue` atrybutu w `defaultCertificate` elementu `serviceCertificate` w obszarze `clientCredentials`).  
  
9. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
10. Na komputerze klienckim, uruchom `ImportServiceCert.bat`. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
11. Na serwerze, uruchom `ImportClientCert.bat`, certyfikat klienta zostaną zaimportowane z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
12. Na komputerze, usługi uruchom Service.exe z wiersza polecenia.  
  
13. Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="requirements"></a>Wymagania  
 W tym przykładzie wymaga, aby usługa MSMQ jest zainstalowana i uruchomiona.  
  
## <a name="demonstrates"></a>Demonstracje  
 Klient szyfrowanie wiadomości za pomocą klucza publicznego, usługi i podpisuje wiadomości za pomocą własnego certyfikatu. Usługi, odczytywanie wiadomości z kolejki uwierzytelnianie certyfikatu klienta przy użyciu certyfikatu w magazynie zaufanych osób. Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.  
  
 Ponieważ [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wiadomość jest przenoszona jako ładunek w treści wiadomości MSMQ, treść pozostaną zaszyfrowane w magazynie usługi MSMQ. Chroni to wiadomość od ujawnienia niechcianych wiadomości. Należy pamiętać, że MSMQ sam nie są znane czy komunikat, który jest jego wykonywanie są szyfrowane.  
  
 W przykładzie pokazano, jak wzajemnego uwierzytelniania w komunikacie poziomu może być używany z usługi MSMQ. Certyfikaty są wymieniane poza pasmem. Jest to zawsze w przypadku aplikacji w kolejce, ponieważ usługa i klient musi być uruchomiona w tym samym czasie.  
  
## <a name="description"></a>Opis  
 Przykładowy kod klienta i usługi są takie same jak [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki z jedną różnicą. Kontrakt operacji jest oznaczony za pomocą poziomu ochrony, które sugeruje, że wiadomości muszą być podpisane i zaszyfrowane.  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 Aby upewnić się, że wiadomość jest zabezpieczona przy użyciu wymaganego tokenu do identyfikowania usługi i klienta, App.config zawiera informacji o poświadczeniach.  
  
 Konfiguracja klienta Określa certyfikat usługi do uwierzytelniania usługi. Używa magazynie LocalMachine jako zaufanego magazynu polegać na ważności usługi. Określa również certyfikat klienta, który jest dołączony komunikat dla usługi uwierzytelniania klienta.  
  
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
  
 Należy pamiętać, że tryb zabezpieczeń jest ustawiony na komunikat i że właściwość ClientCredentialType ma wartość Certificate.  
  
 Konfiguracja usługi zawiera zachowanie usługi, które określa poświadczenia używane, gdy usługa uwierzytelnia klienta. Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 W przykładzie pokazano kontrolowanie uwierzytelniania przy użyciu konfiguracji i uzyskiwania tożsamości elementu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym kodzie próbki:  
  
```  
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
  
 Po uruchomieniu kodu usługi Wyświetla identyfikator klienta. Oto przykładowe dane wyjściowe z kodem usługi:  
  
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
  
-   Tworzenie certyfikatu klienta.  
  
     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Podana nazwa klienta jest używany w nazwie podmiotu certyfikatu utworzony. Certyfikat jest przechowywany w `My` przechowywać `CurrentUser` lokalizacji magazynu.  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.  
  
     Certyfikat klienta do serwera TrustedPeople następujący wiersz w kopii pliku wsadowym należy przechowywać, dzięki czemu odpowiednie zaufanie lub decyzje zaufania nie mogą być serwera. Certyfikat zainstalowany w magazynie TrustedPeople, aby być uważany za zaufany przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi, tryb walidacji certyfikatu klienta musi mieć ustawioną `PeerOrChainTrust` lub `PeerTrust` wartość. Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak to zrobić przy użyciu pliku konfiguracji.  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia:  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli instalacyjny plik wsadowy jest uruchamiana z argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowaną nazwą domeny komputera. W przeciwnym razie domyślne localhost  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Następujący wiersz kopiuje certyfikat serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Jeśli używasz innej niż stany USA Angielska wersja programu Microsoft systemu Windows, należy edytować pliku Setup.bat plików i zastąp "Usługa NT AUTHORITY\NETWORK" Nazwa konta użytkownika regionalnych równoważne.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a>Zobacz też
