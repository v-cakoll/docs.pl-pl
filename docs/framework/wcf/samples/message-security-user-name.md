---
title: "Nazwa użytkownika zabezpieczeń komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3d0c5278cf1860a89ea6a1c3ed33b45ed3c48e92
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="message-security-user-name"></a>Nazwa użytkownika zabezpieczeń komunikatów
W tym przykładzie pokazano, jak wdrożyć aplikację, która używa WS-Security przy użyciu uwierzytelniania nazwa użytkownika dla klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X.509v3 serwera. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i zaszyfrowane. Domyślnie nazwa użytkownika i hasło podane przez klienta są używane do logowania się do prawidłowe konto systemu Windows. Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md). W tym przykładzie składa się z konsoli programu klienckiego (Client.exe) i biblioteki usługi (Service.dll) hostowanej przez Internetowe usługi informacyjne (IIS). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie przedstawiono również:  
  
-   Domyślne mapowanie do kont systemu Windows, dzięki czemu można wykonać dodatkowe autoryzacji.  
  
-   Jak uzyskać dostępu do informacji o tożsamości obiektu wywołującego z kodem usługi.  
  
 Usługa udostępnia jeden punkt końcowy do komunikowania się z usługą, która jest definiowana za pomocą pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), która domyślnie korzysta z zabezpieczeń wiadomości. W tym przykładzie ustawia standardowego [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) uwierzytelniania nazwa użytkownika klienta. Zachowanie Określa, czy poświadczenia użytkownika mają być używane do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość w polu Nazwa podmiotu jako `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu. Klient powiązanie jest skonfigurowany z użyciem odpowiednich `securityMode` i `authenticationMode`. Podczas uruchamiania w scenariuszu między komputerami, należy odpowiednio zmienić adres punktu końcowego usługi.  
  
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
  
```  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy pliku Setup.bat dołączonego przykłady MessageSecurity umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Plik wsadowy może działać w dwóch trybach. Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia. Aby uruchomić go w typ tryb usługi `setup.bat service`. Ten tryb jest używany podczas uruchamiania próbki na komputerach. Zapoznaj się z procedurą instalacji na końcu tego tematu, aby uzyskać szczegółowe informacje.  
  
 Poniżej znajdują się krótki przegląd różnych sekcji pliki wsadowe.  
  
-   Utworzenie certyfikatu serwera  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy pliku Setup.bat jest uruchamiana z argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowaną nazwą domeny komputera.  W przeciwnym razie domyślnie localhost.  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta  
  
     Następujący wiersz kopiuje certyfikat serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Przyznawanie uprawnień do klucza prywatnego certyfikatu  
  
     Następujące wiersze w pliku wsadowym pliku Setup.bat upewnij przechowywany w magazynie LocalMachine dostępne dla certyfikatu serwera [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konta procesu roboczego.  
  
    ```  
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
    >  Jeśli używasz innej niż stany USA Angielska wersja systemu Windows, należy edytować plik pliku Setup.bat i Zastąp `NT AUTHORITY\NETWORK SERVICE` nazwę konta z Twojej regionalnych równoważne.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert.exe i FindPrivateKey.exe.  
  
2.  Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio wiersz polecenia. Wymaga, aby zmiennej środowiskowej path punktu do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiana w Visual Studio wiersz polecenia.  
  
3.  Sprawdź dostęp do usługi przy użyciu przeglądarki, wprowadzając adres http://localhost/servicemodelsamples/service.svc.  
  
4.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
5.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia administracyjnego internetowych usług informacyjnych.  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie findValue w elemencie serviceCertificate), która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera`.`  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
9. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
    > [!NOTE]
    >  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
