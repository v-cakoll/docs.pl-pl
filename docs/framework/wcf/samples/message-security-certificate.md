---
title: Certyfikat zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 3382aeb59f3500f9371f39cc892bce5fac65791f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714804"
---
# <a name="message-security-certificate"></a>Certyfikat zabezpieczeń komunikatów
Ten przykład pokazuje, jak zaimplementować aplikację, która korzysta z protokołu WS-Security z uwierzytelnianiem certyfikatu X. 509 v3 dla klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X. 509 v3 serwera. Ten przykład używa ustawień domyślnych, takich jak wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i szyfrowane. Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) i składa się z programu konsolowego klienta oraz biblioteki usług hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład demonstruje kontrolę uwierzytelniania przy użyciu konfiguracji i sposób uzyskiwania tożsamości obiektu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie.  

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
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą i jeden punkt końcowy do udostępnienia dokumentu WSDL usługi przy użyciu protokołu WS-MetadataExchange zdefiniowanego przy użyciu pliku konfiguracji (Web. config). Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane przy użyciu standardowego [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu, który domyślnie używa zabezpieczeń komunikatów. Ten przykład ustawia atrybut `clientCredentialType` na certyfikat, aby wymagać uwierzytelnienia klienta.  
  
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
  
 Zachowanie określa poświadczenia usługi, które są używane podczas uwierzytelniania usługi przez klienta. Nazwa podmiotu certyfikatu serwera jest określona w atrybucie `findValue` w elemencie [\<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) .  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednim trybem zabezpieczeń i trybem uwierzytelniania. W przypadku działania w scenariuszu między komputerami upewnij się, że adres punktu końcowego usługi został odpowiednio zmieniony.  
  
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
  
 Implementacja klienta może ustawić certyfikat do użycia w pliku konfiguracji lub za pomocą kodu. Poniższy przykład pokazuje, jak ustawić certyfikat do użycia w pliku konfiguracji.  
  
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
  
 Poniższy przykład pokazuje, jak wywołać usługę w programie.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup. bat dołączony do przykładów zabezpieczeń wiadomości umożliwia skonfigurowanie klienta i serwera przy użyciu odpowiednich certyfikatów do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach. Plik wsadowy można uruchomić w trzech trybach. Do uruchamiania w trybie jednego komputera wpisz **Setup. bat** w wiersz polecenia dla deweloperów dla programu Visual Studio; w przypadku typu usługi **Setup. bat usługa**; i w przypadku trybu klienta **Setup. bat Client**. Użyj trybu klienta i serwera podczas uruchamiania przykładu między komputerami. Aby uzyskać szczegółowe informacje, zobacz procedurę instalacji na końcu tego tematu. Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować do uruchamiania w odpowiedniej konfiguracji:  
  
- Tworzenie certyfikatu klienta.  
  
     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu. Certyfikat jest przechowywany w magazynie `My` w lokalizacji magazynu `CurrentUser`.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów serwera.  
  
     Następujący wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje zaufania lub braku zaufania. Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być ustawiony na `PeerOrChainTrust` lub `PeerTrust`. Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracji.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- Tworzenie certyfikatu serwera.  
  
     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Zmienna% SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup. bat jest uruchamiany przy użyciu argumentu usługi (np **. usługi Setup. bat**),% server_name% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie wartość domyślna to localhost.  
  
- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.  
  
     Poniższy wiersz zawiera kopię certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Przyznawanie uprawnień dla klucza prywatnego certyfikatu.  
  
     Następujące wiersze w pliku Setup. bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu roboczego ASP.NET.  
  
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
    > W przypadku korzystania z systemu Windows w wersji innej niż w języku angielskim, należy edytować plik Setup. bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" własnym odpowiednikiem regionalnym.  
  
> [!NOTE]
> Narzędzia używane w tym pliku wsadowym znajdują się w folderze C:\Program Files\Microsoft Visual Studio 8 \ Common7\tools lub C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jeden z tych katalogów musi znajdować się w ścieżce systemowej. Jeśli masz zainstalowany program Visual Studio, najprostszym sposobem pobrania tego katalogu w ścieżce jest otwarcie wiersz polecenia dla deweloperów dla programu Visual Studio. Kliknij przycisk **Start**, a następnie wybierz pozycję **Wszystkie programy**, **Visual Studio 2012**, **Narzędzia**. Ten wiersz polecenia ma już skonfigurowane odpowiednie ścieżki. W przeciwnym razie musisz ręcznie dodać odpowiedni katalog do swojej ścieżki.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny):  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu:  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.  
  
    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersz polecenia dla deweloperów dla programu Visual Studio. Wymaga, aby zmienna środowiskowa Path wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w ramach wiersz polecenia dla deweloperów dla programu Visual Studio (2010).  
  
2. Aby sprawdzić dostęp do usługi przy użyciu przeglądarki, wprowadź adres `http://localhost/servicemodelsamples/service.svc`.  
  
3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania Internet Information Services (IIS).  
  
2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin. Skopiuj także pliki Setup. bat, Oczyść. bat i ImportClientCert. bat do komputera usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze uruchom **usługę Setup. bat** w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora. Uruchomienie pliku **Setup. bat** przy użyciu argumentu **usługi** powoduje utworzenie certyfikatu usługi z w pełni kwalifikowaną nazwą domeny komputera i wyeksportowanie certyfikatu usługi do plik o nazwie Service. cer.  
  
6. Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie `findValue` w [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. Na kliencie Uruchom program **Setup. bat Client** w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora. Uruchomienie pliku **Setup. bat** z argumentem **Client** powoduje utworzenie certyfikatu klienta o nazwie Client.com i wyeksportowanie certyfikatu klienta programu na plik o nazwie Client. cer.  
  
9. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.  
  
10. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
11. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
12. Na serwerze programu Uruchom program ImportClientCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi. Spowoduje to zaimportowanie certyfikatu klienta z pliku. cer klienta do magazynu LocalMachine-TrustedPeople.  
  
13. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
