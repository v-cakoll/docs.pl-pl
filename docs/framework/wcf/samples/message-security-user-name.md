---
title: Nazwa użytkownika zabezpieczeń komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 947ef3c2120377fe33e0062d1ed508ddda432314
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335332"
---
# <a name="message-security-user-name"></a>Nazwa użytkownika zabezpieczeń komunikatów
Ten przykład demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security przy użyciu uwierzytelniania nazwy użytkownika dla klienta i wymaga uwierzytelnienia serwera za pomocą certyfikatu X.509v3 serwera. Wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane. Domyślnie, nazwa użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowego konta Windows. Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). W tym przykładzie składa się z konsoli programu klienckiego (Client.exe) i Biblioteka usługi (Service.dll) hostowanej przez Internetowe usługi informacyjne (IIS). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Niniejszy przykład pokazuje, również:  
  
-   Domyślne mapowania konta Windows tak, aby autoryzacji dodatkowe, które mogą być wykonywane.  
  
-   Jak uzyskać dostęp do informacji o tożsamości wywołującego z kodem usługi.  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest zdefiniowana za pomocą pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), którego wartość domyślna to korzystanie z zabezpieczeń komunikatów. W tym przykładzie ustawia standard [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do korzystania z uwierzytelniania nazwy użytkownika klienta. Zachowanie Określa, czy poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość w polu Nazwa podmiotu jako `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano odpowiednie `securityMode` i `authenticationMode`. Podczas uruchamiania w przypadku wielu komputerów, można odpowiednio zmienić adres punktu końcowego usługi.  
  
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

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy Setup.bat jest dołączone do przykładów MessageSecurity umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Plik wsadowy może działać w dwóch trybach. Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia. Aby uruchomić je w typ tryb usługi `setup.bat service`. Użyj tego trybu, gdy działa aplikacja przykładowa na komputerach. Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje.  
  
 Poniżej zawiera krótkie omówienie różnych sekcji w plikach wsadowych.  
  
-   Utworzenie certyfikatu serwera  
  
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
  
     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy Setup.bat jest uruchamiany z nieprawidłowym argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera.  W przeciwnym razie wartość domyślna hosta lokalnego.  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta  
  
     Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Przyznawanie uprawnień do klucza prywatnego certyfikatu  
  
     Następujące wiersze w pliku wsadowym Setup.bat upewnij certyfikatu serwera, przechowywane w magazynie LocalMachine dostępny [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces roboczy.  
  
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
    >  Jeśli używasz spoza USA Angielskiej wersji systemu Windows, należy edytować plik Setup.bat jest i Zastąp `NT AUTHORITY\NETWORK SERVICE` nazwa konta ekwiwalent regionalne.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert.exe i FindPrivateKey.exe.  
  
2. Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wiersza polecenia dla deweloperów programu Visual Studio. Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiona w wierszu polecenia dla deweloperów dla programu Visual Studio.  
  
3. Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.
  
4. Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
5. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania Internet Information Services.  
  
2. Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3. Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4. Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w atrybucie findValue w elemencie serviceCertificate), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera`.`  
  
7. Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim uruchom ImportServiceCert.bat w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
