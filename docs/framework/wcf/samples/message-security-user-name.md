---
title: Nazwa użytkownika zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183510"
---
# <a name="message-security-user-name"></a>Nazwa użytkownika zabezpieczeń komunikatów
W tym przykładzie pokazano, jak zaimplementować aplikację, która używa programu WS-Security z uwierzytelnianiem nazwy użytkownika dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509v3 serwera. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane. Domyślnie nazwa użytkownika i hasło dostarczone przez klienta są używane do logowania do prawidłowego konta systemu Windows. Ten przykład jest oparty na [programie WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). Ten przykład składa się z programu konsoli klienta (Client.exe) i biblioteki usług (Service.dll) hostowanych przez internetowe usługi informacyjne (IIS). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie pokazano również:  
  
- Domyślne mapowanie do kont systemu Windows, dzięki czemu można wykonać dodatkową autoryzację.  
  
- Jak uzyskać dostęp do informacji o tożsamości wywołującego z kodu usługi.  
  
 Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą, który jest zdefiniowany przy użyciu pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązania i umowy. Powiązanie jest skonfigurowane ze standardem [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), który domyślnie używa zabezpieczeń wiadomości. W tym przykładzie ustawia standardowy [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do używania uwierzytelniania nazwy użytkownika klienta. Zachowanie określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `findValue` dla nazwy podmiotu, jak atrybut w [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i umowy. Powiązanie klienta jest skonfigurowane `securityMode` `authenticationMode`z odpowiednimi i . Podczas uruchamiania w scenariuszu między komputerami, adres punktu końcowego usługi musi zostać odpowiednio zmieniony.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Implementacja klienta ustawia nazwę użytkownika i hasło do użycia.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup.bat dołączony do przykładów MessageSecurity umożliwia skonfigurowanie serwera z odpowiednim certyfikatem do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach. Plik wsadowy można uruchomić w dwóch trybach. Aby uruchomić plik wsadowy w trybie jednokomputerowym, wpisz `setup.bat` wiersz polecenia. Aby uruchomić go w `setup.bat service`trybie serwisowym typu . Ten tryb jest używany podczas uruchamiania próbki na komputerach. Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.  
  
- Tworzenie certyfikatu serwera  
  
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
  
     Zmienna %SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup.bat jest uruchamiany `setup.bat service`z argumentem usługi (na przykład ) %SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera.  W przeciwnym razie domyślnie localhost.  
  
- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta  
  
     Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Udzielanie uprawnień do klucza prywatnego certyfikatu  
  
     Następujące wiersze w pliku wsadowym Setup.bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu ASP.NET procesu roboczego.  
  
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
    > Jeśli używasz wersji systemu Windows w wersji systemu Windows innej niż amerykańska, `NT AUTHORITY\NETWORK SERVICE` musisz edytować plik Setup.bat i zastąpić nazwę konta regionalnym odpowiednikiem.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajdują się pliki Makecert.exe i FindPrivateKey.exe.  
  
2. Uruchom plik Setup.bat z przykładowego folderu instalacji w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.  
  
    > [!NOTE]
    > Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dewelopera dla programu Visual Studio. Wymaga, aby zmienna środowiskowa ścieżki wskazywała katalog, w którym jest zainstalowany pakiet SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia dewelopera dla programu Visual Studio.  
  
3. Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.
  
4. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Utwórz katalog na komputerze usługowym. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania internetowymi usługami informacyjnymi.  
  
2. Skopiuj pliki programu serwisowego z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki są kopiowane w podkatalogu \bin. Skopiuj również pliki Setup.bat i Cleanup.bat do komputera serwisowego.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze `setup.bat service` uruchom w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj web.config, aby odzwierciedlić nową nazwę certyfikatu (w findValue atrybut w serviceCertificate element), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera`.`  
  
7. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.  
  
9. Na kliencie uruchom plik ImportServiceCert.bat w wierszu polecenia dewelopera dla programu Visual Studio otwarty z uprawnieniami administratora. Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
10. Na komputerze klienckim uruchom program Client.exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
    > [!NOTE]
    > Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
