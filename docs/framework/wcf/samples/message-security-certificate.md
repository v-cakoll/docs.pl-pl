---
title: Certyfikat zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: ead36beda4a56d779969eea0ed746bfb47891243
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333316"
---
# <a name="message-security-certificate"></a>Certyfikat zabezpieczeń komunikatów
Ten przykład demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security przy użyciu uwierzytelniania certyfikatów X.509 v3 klienta i wymaga uwierzytelnienia serwera za pomocą certyfikat serwera X.509 v3. Ta próbka używa domyślnych ustawień w taki sposób, że wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane. Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) i składa się z programu konsoli klienta i Biblioteka usługi hostowanej przez Internetowe usługi informacyjne (IIS). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano kontroli uwierzytelniania przy użyciu konfiguracji i jak można uzyskać tożsamości elementu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie.  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą i jeden punkt końcowy do udostępniania dokumentu WSDL usługi przy użyciu protokołu WS-MetadataExchange zdefiniowane przy użyciu pliku konfiguracji (Web.config). Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu, którego wartość domyślna to korzystanie z zabezpieczeń komunikatów. W tym przykładzie ustawia `clientCredentialType` atrybutów do certyfikatu, aby wymagać uwierzytelniania klienta.  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
```  
  
 Zachowanie Określa poświadczenia, które są używane, gdy klient uwierzytelnia się usługi. Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) elementu.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
```  
  
 Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano tryb zabezpieczeń odpowiednich i tryb uwierzytelniania. Podczas uruchamiania w przypadku wielu komputerów, upewnij się, odpowiednio zmieniony adres punktu końcowego usługi.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 Implementacja klienta można ustawić certyfikatu do użycia, za pomocą pliku konfiguracji lub za pomocą kodu. Poniższy przykład pokazuje, jak ustawić certyfikat do użycia w pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 Poniższy przykład pokazuje sposób wywołania tej usługi w programie.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup.bat jest dołączone do przykładów zabezpieczenia komunikatów umożliwia konfigurowanie klienta i serwera przy użyciu odpowiednich certyfikatów uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Plik wsadowy mogą być uruchamiane w trzech trybów. Do uruchamiania w trybie pojedynczego komputera typu **setup.bat** w wiersz polecenia dewelopera dla programu Visual Studio; w przypadku typu tryb usługi **setup.bat usługi**; i typ trybu klienta **klienta setup.bat**. Użyj trybu klienta i serwera na komputerach działa aplikacja przykładowa. Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje. Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:  
  
-   Tworzenie certyfikatu klienta.  
  
     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Podana nazwa klienta jest używany w nazwie podmiotu certyfikatu, utworzony. Certyfikat jest przechowywany w `My` przechowywać `CurrentUser` lokalizacji magazynu.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.  
  
     Następujący wiersz w kopii pliku wsadowego certyfikat klienta do serwera TrustedPeople przechowywać tak, aby istotne zaufania lub decyzji dotyczących zaufania nie mogą być serwera. Aby uzyskać certyfikat, który został zainstalowany w magazynie TrustedPeople być uważany za zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być równa `PeerOrChainTrust` lub `PeerTrust`. Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić przy użyciu pliku konfiguracji.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup.bat jest uruchamiany z nieprawidłowym argumentem usługi (takie jak **usługi setup.bat**) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera. W przeciwnym razie wartość domyślna hosta lokalnego.  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Przyznawanie uprawnień do klucza prywatnego certyfikatu.  
  
     Następujące wiersze w plik Setup.bat jest udostępnić certyfikat serwera, przechowywane w magazynie dostępne dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces roboczy.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  Jeśli używasz spoza USA Angielskiej wersji systemu Windows, należy edytować Setup.bat i zastąp nazwę konta "NT AUTHORITY\NETWORK SERVICE" ekwiwalent regionalne.  
  
> [!NOTE]
>  Narzędzia używane w tym pliku wsadowego znajdują się w 8\Common7\tools C:\Program Files\Microsoft Visual Studio lub C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jeden z tych katalogów musi być w ścieżce systemowej. Jeśli masz zainstalowany program Visual Studio, otwórz wiersz polecenia dla deweloperów programu Visual Studio jest najprostszym sposobem, aby uzyskać ten katalog w ścieżce. Kliknij przycisk **Start**, a następnie wybierz pozycję **wszystkie programy**, **programu Visual Studio 2012**, **narzędzia**. Ten wiersz polecenia zawiera odpowiednie ścieżki już skonfigurowane. W przeciwnym razie należy dodać odpowiedni katalog do ścieżki ręcznie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dla deweloperów programu Visual Studio. Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiona w wierszu polecenia dla deweloperów dla programu Visual Studio (2010).  
  
2.  Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputerze usługi.  
  
3.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom **usługi setup.bat** w wierszu polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora. Uruchamianie **setup.bat** z **usługi** argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, należy uruchomić **klienta setup.bat** w wierszu polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora. Uruchamianie **setup.bat** z **klienta** argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi. To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim uruchom ImportServiceCert.bat w wierszu polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze uruchom ImportClientCert.bat w wierszu polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi. To importuje certyfikat klienta z pliku Client.cer, do maszyny lokalnej - TrustedPeople magazynu.  
  
13. Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz także
