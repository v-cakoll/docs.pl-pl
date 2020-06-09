---
title: Nazwa użytkownika zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 783969342f007895016ed4183257d6b24188d76c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584730"
---
# <a name="message-security-user-name"></a>Nazwa użytkownika zabezpieczeń komunikatów
Ten przykład pokazuje, jak zaimplementować aplikację, która korzysta z protokołu WS-Security z uwierzytelnianiem nazwy użytkownika dla klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X. 509v3 serwera. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i szyfrowane. Domyślnie nazwa użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowego konta systemu Windows. Ten przykład jest oparty na [WSHttpBinding](wshttpbinding.md). Ten przykład składa się z programu konsolowego klienta (Client. exe) i biblioteki usług (Service. dll) hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład ilustruje również:  
  
- Domyślne mapowanie na konta systemu Windows, aby można było wykonać dodatkową autoryzację.  
  
- Jak uzyskać dostęp do informacji o tożsamości wywołującego z kodu usługi.  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest definiowana przy użyciu pliku konfiguracji Web. config. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane przy użyciu standardu [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , który domyślnie wykorzystuje zabezpieczenia komunikatów. Ten przykład ustawia standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do korzystania z uwierzytelniania nazwy użytkownika klienta. Zachowanie określa, że poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość nazwy podmiotu jak `findValue` atrybut w [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednimi `securityMode` i `authenticationMode` . W przypadku działania w scenariuszu obejmującym wiele komputerów należy odpowiednio zmienić adres punktu końcowego usługi.  
  
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
  
 Implementacja klienta ustawia nazwę użytkownika i hasło, które mają być używane.  

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

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup. bat dołączony do przykładów MessageSecurity umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia hostowanej aplikacji wymagającej zabezpieczeń opartych na certyfikatach. Plik wsadowy można uruchomić w dwóch trybach. Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia. W celu uruchomienia tego typu w trybie usługi `setup.bat service` . Ten tryb jest używany podczas uruchamiania przykładu między komputerami. Aby uzyskać szczegółowe informacje, zobacz procedurę instalacji na końcu tego tematu.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.  
  
- Tworzenie certyfikatu serwera  
  
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
  
     Zmienna% SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup. bat jest uruchamiany z argumentem usługi (np `setup.bat service` .),% server_name% zawiera w pełni kwalifikowaną nazwę domeny komputera.  W przeciwnym razie wartość domyślna to localhost.  
  
- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta  
  
     Poniższy wiersz zawiera kopię certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Przyznawanie uprawnień dla klucza prywatnego certyfikatu  
  
     Następujące wiersze w pliku wsadowym Setup. bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu roboczego ASP.NET.  
  
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
    > Jeśli używasz innej wersji systemu Windows niż w języku angielskim, musisz edytować plik Setup. bat i zamienić `NT AUTHORITY\NETWORK SERVICE` nazwę konta na swój odpowiednik regionalny.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert. exe i FindPrivateKey. exe.  
  
2. Uruchom setup. bat z przykładowego folderu instalacyjnego w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.  
  
    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersz polecenia dla deweloperów dla programu Visual Studio. Wymaga, aby zmienna środowiskowa Path wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w ramach wiersz polecenia dla deweloperów dla programu Visual Studio.  
  
3. Aby sprawdzić dostęp do usługi przy użyciu przeglądarki, wprowadź adres `http://localhost/servicemodelsamples/service.svc` .
  
4. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania Internet Information Services.  
  
2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin. Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze programu uruchom polecenie `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
6. Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie findValue w elemencie serviceCertificate), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera`.`  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
9. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
10. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
    > [!NOTE]
    > Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .  
