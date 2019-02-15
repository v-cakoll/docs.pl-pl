---
title: Zabezpieczenia komunikatów z anonimowością
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 2cb1834414b402f8840a9dfa1ee9e2497cea7af5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304248"
---
# <a name="message-security-anonymous"></a>Zabezpieczenia komunikatów z anonimowością
Komunikat zabezpieczeń anonimowe przykład demonstruje sposób implementacji aplikacji Windows Communication Foundation (WCF) korzystającą zabezpieczenia na poziomie komunikatu bez uwierzytelniania klienta, ale, która wymaga uwierzytelnienia serwera za pomocą serwera X.509 certyfikat. Wszystkie komunikaty aplikacji między klientem i serwerem są podpisane i szyfrowane. Ten przykład jest oparty na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) próbki. W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

 Ten przykład dodaje nową operację do interfejsu Kalkulator, która zwraca `True` Jeśli klient nie został uwierzytelniony.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config). Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu `wsHttpBinding` powiązania. Domyślny tryb zabezpieczeń `wsHttpBinding` powiązanie jest `Message`. `clientCredentialType` Ma ustawioną wartość atrybutu `None`.

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Poświadczenia, które mają być używane do uwierzytelniania usługi są określone w [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako wartość określona dla `findValue` atrybutu, jak pokazano w poniższym przykładowym kodzie.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
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
```

 Konfiguracja punktu końcowego klienta składa się z adresem bezwzględnym dla punktu końcowego usługi, powiązanie i zamówienia. Tryb zabezpieczeń klienta dla `wsHttpBinding` powiązanie jest `Message`. `clientCredentialType` Ma ustawioną wartość atrybutu `None`.

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Przykładowe zestawy <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> do uwierzytelniania certyfikatu usługi. Jest to realizowane w pliku App.config klienta `behaviors` sekcji. Oznacza to, że jeśli certyfikat znajduje się w magazynie zaufanych osób użytkownika, jest zaufany bez przeprowadzania weryfikacji łańcucha wystawcy certyfikatu. To ustawienie jest używane w tym miejscu dla wygody, tak, aby próbki mogą być uruchamiane bez konieczności używania certyfikatów, wystawiony przez urząd certyfikacji (CA). To ustawienie jest mniej bezpieczne niż domyślna, ChainTrust. Ryzyko związane z tego ustawienia, które powinien zostać starannie przemyślany przed użyciem `PeerOrChainTrust` w kodzie produkcyjnym.

 Implementacji klienta dodaje wywołanie `IsCallerAnonymous` metody a w przeciwnym razie nie różni się od [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) próbki.

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Plik wsadowy Setup.bat jest dołączone do przykładowy komunikat zabezpieczeń anonimowe umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach. Plik wsadowy może działać w dwóch trybach. Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia. Aby uruchomić go w trybie usługi, wpisz `setup.bat service`. Użyj tego trybu, gdy działa aplikacja przykładowa na komputerach. Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje.

 Poniżej zawiera krótkie omówienie różnych sekcji plików usługi batch:

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

     % Zmienna % nazwa_serwera Określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli instalacyjny plik wsadowy jest uruchamiany z nieprawidłowym argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera. W przeciwnym razie wartość domyślna hosta lokalnego.

-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.

     Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Przyznawanie uprawnień do klucza prywatnego certyfikatu.

     Następujące wiersze w pliku wsadowym Setup.bat upewnij certyfikatu serwera, przechowywane w magazynie LocalMachine dostępny [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces roboczy.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  Jeśli używasz spoza USA Angielskiej wersji systemu Windows, należy edytować plik Setup.bat jest i Zastąp `NT AUTHORITY\NETWORK SERVICE` nazwa konta ekwiwalent regionalne.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1.  Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert.exe i FindPrivateKey.exe.

2.  Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia dla deweloperów programu Visual Studio uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    > Instalacyjny plik wsadowy jest przeznaczony do uruchamiania z wiersza polecenia dla deweloperów programu Visual Studio. Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK. Ta zmienna środowiskowa jest automatycznie ustawiona w wierszu polecenia dla deweloperów dla programu Visual Studio.  
  
3.  Sprawdź dostęp do usługi za pomocą przeglądarki, wprowadzając adres `http://localhost/servicemodelsamples/service.svc`.  
  
4.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
5.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim uruchom ImportServiceCert.bat w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`

## <a name="see-also"></a>Zobacz także
