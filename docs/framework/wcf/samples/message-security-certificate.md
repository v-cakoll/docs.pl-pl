---
title: Certyfikat zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 92e656f36ae0af851def393575cbb7d418bc4a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183533"
---
# <a name="message-security-certificate"></a>Certyfikat zabezpieczeń komunikatów
W tym przykładzie pokazano, jak zaimplementować aplikację, która używa programu WS-Security z uwierzytelnianiem certyfikatu X.509 v3 dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509 v3 serwera. W tym przykładzie użyto ustawień domyślnych, takich jak, że wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane. Ten przykład jest oparty na [programie WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) i składa się z programu konsoli klienta i biblioteki usług hostowanych przez internetowe usługi informacyjne (IIS). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład pokazuje kontrolowanie uwierzytelniania przy użyciu konfiguracji i jak uzyskać tożsamość wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie.  

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
  
 Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą i jeden punkt końcowy do udostępnienia dokumentu WSDL usługi przy użyciu protokołu WS-MetadataExchange, zdefiniowane przy użyciu pliku konfiguracyjnego (Web.config). Punkt końcowy składa się z adresu, powiązania i umowy. Powiązanie jest skonfigurowane ze standardowym [ \<elementem>wsHttpBinding,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) który domyślnie używa zabezpieczeń wiadomości. W tym `clientCredentialType` przykładzie ustawia atrybut Certyfikat, aby wymagać uwierzytelniania klienta.  
  
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
  
 Zachowanie określa poświadczenia usługi, które są używane, gdy klient uwierzytelnia usługę. Nazwa podmiotu certyfikatu serwera `findValue` jest określona w atrybucie w [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i umowy. Powiązanie klienta jest skonfigurowane przy użyciu odpowiedniego trybu zabezpieczeń i trybu uwierzytelniania. Podczas uruchamiania w scenariuszu między komputerami, upewnij się, że adres punktu końcowego usługi zostanie odpowiednio zmieniony.  
  
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
  
 Implementacja klienta można ustawić certyfikat do użycia, za pośrednictwem pliku konfiguracji lub za pośrednictwem kodu. W poniższym przykładzie pokazano, jak ustawić certyfikat do użycia w pliku konfiguracyjnym.  
  
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
  
 W poniższym przykładzie pokazano, jak wywołać usługę w programie.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup.bat dołączony do przykładów zabezpieczeń wiadomości umożliwia skonfigurowanie klienta i serwera z odpowiednimi certyfikatami do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach. Plik wsadowy można uruchomić w trzech trybach. Aby uruchomić w trybie jednokomunijnym typu **setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio ; dla usługi typu **setup.bat**w trybie serwisowym ; i dla klienta typu **setup.bat klienta**. Użyj trybu klienta i serwera podczas uruchamiania próbki na komputerach. Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu. Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji:  
  
- Tworzenie certyfikatu klienta.  
  
     Następujący wiersz w pliku wsadowym tworzy certyfikat klienta. Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu. Certyfikat jest przechowywany `My` w `CurrentUser` magazynie w lokalizacji sklepu.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Instalowanie certyfikatu klienta w magazynie certyfikatów zaufanych serwera.  
  
     Poniższy wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje dotyczące zaufania lub braku zaufania. Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), należy `PeerOrChainTrust` ustawić `PeerTrust`tryb sprawdzania poprawności certyfikatu klienta lub . Zobacz przykład poprzedniej konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracyjnego.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Zmienna %SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup.bat jest uruchamiany z argumentem usługi (takim jak **usługa setup.bat),**%SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie domyślnie localhost.  
  
- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.  
  
     Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udzielanie uprawnień do klucza prywatnego certyfikatu.  
  
     Następujące wiersze w pliku Setup.bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu ASP.NET procesu roboczego.  
  
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
    > Jeśli używasz wersji systemu Windows w języku niesie poza USA, musisz edytować plik Setup.bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" regionalnym odpowiednikiem.  
  
> [!NOTE]
> Narzędzia używane w tym pliku wsadowym znajdują się w folderze C:\Program Files\Microsoft Visual Studio 8\Common7\tools lub C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. Jeden z tych katalogów musi znajdować się w ścieżce systemowej. Jeśli masz zainstalowany program Visual Studio, najprostszym sposobem, aby uzyskać ten katalog w ścieżce jest otwarcie wiersza polecenia dewelopera dla programu Visual Studio. Kliknij **przycisk Start**, a następnie wybierz pozycję Wszystkie **programy**, **Visual Studio 2012**, **Narzędzia**. Ten wiersz polecenia ma już skonfigurowane odpowiednie ścieżki. W przeciwnym razie należy ręcznie dodać odpowiedni katalog do ścieżki.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog:  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu:  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.  
  
    > [!NOTE]
    > Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio. Wymaga, aby zmienna środowiskowa ścieżki wskazywała katalog, w którym jest zainstalowany pakiet SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia dewelopera dla programu Visual Studio (2010).  
  
2. Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.  
  
3. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Utwórz katalog na komputerze usługowym. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania internetowymi usługami informacyjnymi (IIS).  
  
2. Skopiuj pliki programu serwisowego z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki są kopiowane w podkatalogu \bin. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputer usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze uruchom **usługę setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora. Uruchomienie **pliku setup.bat** z argumentem **usługi** tworzy certyfikat usługi o w pełni kwalifikowanej nazwie domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. Na kliencie uruchom **klienta setup.bat** w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora. Uruchomienie **pliku setup.bat** z argumentem **klienta** tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi. W tym celu można zastąpić hosta lokalnego w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na kliencie uruchom plik ImportServiceCert.bat w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administracyjnymi. Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
12. Na serwerze uruchom plik ImportClientCert.bat w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administracyjnymi. Spowoduje to zaimportowanie certyfikatu klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.  
  
13. Na komputerze klienckim uruchom program Client.exe z okna wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
    > [!NOTE]
    > Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
