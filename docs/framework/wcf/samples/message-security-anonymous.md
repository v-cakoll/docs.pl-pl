---
title: Zabezpieczenia komunikatów z anonimowością
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 95101b8ec4f5a7fc60d0233ab6685b5c6851b44e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584990"
---
# <a name="message-security-anonymous"></a>Zabezpieczenia komunikatów z anonimowością
Anonimowy przykład zabezpieczeń wiadomości demonstruje sposób implementacji aplikacji Windows Communication Foundation (WCF), która korzysta z zabezpieczeń na poziomie komunikatów bez uwierzytelniania klienta, ale wymaga uwierzytelniania serwera przy użyciu certyfikatu X. 509 serwera. Wszystkie komunikaty aplikacji między klientem a serwerem są podpisane i szyfrowane. Ten przykład jest oparty na przykładzie [WSHttpBinding](wshttpbinding.md) . Ten przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Ten przykład dodaje nową operację do interfejsu kalkulatora, który zwraca, `True` Jeśli klient nie został uwierzytelniony.

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

 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji (Web. config). Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane z `wsHttpBinding` powiązaniem. Domyślny tryb zabezpieczeń dla `wsHttpBinding` powiązania to `Message` . `clientCredentialType`Atrybut jest ustawiony na `None` .

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

 Poświadczenia, które mają być używane na potrzeby uwierzytelniania usługi, są określone w [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) . Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak wartość określona dla `findValue` atrybutu, jak pokazano w poniższym przykładowym kodzie.

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

 Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Tryb zabezpieczeń klienta dla `wsHttpBinding` powiązania to `Message` . `clientCredentialType`Atrybut jest ustawiony na `None` .

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

 Przykład ustawia <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> uwierzytelniania certyfikatu usługi. Jest to wykonywane w pliku App. config klienta w `behaviors` sekcji. Oznacza to, że jeśli certyfikat znajduje się w magazynie zaufanych osób użytkownika, jest on zaufany bez sprawdzania poprawności łańcucha wystawcy certyfikatu. To ustawienie jest używane w tym miejscu dla wygody, aby można było uruchomić przykład bez certyfikatów wystawionych przez urząd certyfikacji. To ustawienie jest mniej bezpieczne niż domyślne, ChainTrust. Należy uważnie rozważyć implikacje zabezpieczeń tego ustawienia przed użyciem `PeerOrChainTrust` w kodzie produkcyjnym.

 Implementacja klienta dodaje wywołanie do `IsCallerAnonymous` metody i w przeciwnym razie nie różni się od próbki [WSHttpBinding](wshttpbinding.md) .

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

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Plik wsadowy Setup. bat dołączony do anonimowego przykładu zabezpieczeń wiadomości umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia hostowanej aplikacji wymagającej zabezpieczeń opartych na certyfikatach. Plik wsadowy można uruchomić w dwóch trybach. Aby uruchomić plik wsadowy w trybie pojedynczego komputera, wpisz `setup.bat` w wierszu polecenia. Aby uruchomić go w trybie usługi, wpisz polecenie `setup.bat service` . Tego trybu należy używać w przypadku uruchamiania przykładu między komputerami. Aby uzyskać szczegółowe informacje, zobacz procedurę instalacji na końcu tego tematu.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych:

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

     Zmienna% SERVER_NAME% określa nazwę serwera. Certyfikat jest przechowywany w magazynie LocalMachine. Jeśli plik wsadowy instalacji jest uruchamiany z argumentem usługi (np `setup.bat service` .),% server_name% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie wartość domyślna to localhost.

- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.

     Poniższy wiersz zawiera kopię certyfikatu serwera w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Przyznawanie uprawnień dla klucza prywatnego certyfikatu.

     Następujące wiersze w pliku wsadowym Setup. bat sprawiają, że certyfikat serwera przechowywany w magazynie LocalMachine jest dostępny dla konta procesu roboczego ASP.NET.

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
> Jeśli używasz innej wersji systemu Windows niż w języku angielskim, musisz edytować plik Setup. bat i zamienić `NT AUTHORITY\NETWORK SERVICE` nazwę konta na swój odpowiednik regionalny.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Upewnij się, że ścieżka zawiera folder, w którym znajdują się Makecert. exe i FindPrivateKey. exe.

2. Uruchom setup. bat z przykładowego folderu instalacyjnego w wiersz polecenia dla deweloperów dla programu Visual Studio Uruchom z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy instalacji został zaprojektowany do uruchamiania z wiersz polecenia dla deweloperów dla programu Visual Studio. Wymaga, aby zmienna środowiskowa Path wskazywała katalog, w którym zainstalowano zestaw SDK. Ta zmienna środowiskowa jest ustawiana automatycznie w ramach wiersz polecenia dla deweloperów dla programu Visual Studio.  
  
3. Aby sprawdzić dostęp do usługi przy użyciu przeglądarki, wprowadź adres `http://localhost/servicemodelsamples/service.svc` .  
  
4. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
5. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania Internet Information Services (IIS).  
  
2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin. Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze programu uruchom polecenie `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
6. Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
9. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
10. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
> [!NOTE]
> Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`
