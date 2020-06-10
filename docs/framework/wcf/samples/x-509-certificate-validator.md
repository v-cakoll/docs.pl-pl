---
title: Moduł weryfikacji certyfikatów X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 32d99b93ef014967aa04bc70f73fbd2ebcfe2c60
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594832"
---
# <a name="x509-certificate-validator"></a>Moduł weryfikacji certyfikatów X.509

Ten przykład pokazuje, jak zaimplementować niestandardowy moduł sprawdzania poprawności certyfikatu X. 509. Jest to przydatne w przypadkach, gdy żaden z wbudowanych trybów weryfikacji certyfikatu X. 509 nie jest odpowiedni dla wymagań aplikacji. Ten przykład pokazuje usługę, która ma niestandardowy moduł sprawdzania poprawności akceptujący certyfikaty wystawione automatycznie. Klient używa takiego certyfikatu do uwierzytelniania w usłudze.

Uwaga: ponieważ każdy może utworzyć certyfikat z własnym wystawiony, niestandardowy moduł sprawdzania poprawności używany przez usługę jest mniej bezpieczny niż domyślne zachowanie udostępniane przez ChainTrust X509CertificateValidationMode. Należy uważnie rozważyć implikacje zabezpieczeń przed użyciem tej logiki walidacji w kodzie produkcyjnym.

W podsumowaniu ten przykład pokazuje, jak:

- Klienta można uwierzytelnić przy użyciu certyfikatu X. 509.

- Serwer sprawdza poprawność poświadczeń klienta względem niestandardowego X509CertificateValidator.

- Serwer jest uwierzytelniany przy użyciu certyfikatu X. 509 serwera.

Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji App. config. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane ze standardem `wsHttpBinding` , który jest domyślnie używany do `WSSecurity` uwierzytelniania certyfikatu klienta. Zachowanie usługi określa niestandardowy tryb weryfikacji certyfikatów X. 509 klienta oraz typ klasy modułu sprawdzania poprawności. Zachowanie określa również certyfikat serwera przy użyciu elementu serviceCertificate. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak `findValue` w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu. Powiązanie klienta jest skonfigurowane z odpowiednim trybem i komunikatem `clientCredentialType` .

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

Implementacja klienta ustawia używany certyfikat klienta.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

Ten przykład używa niestandardowego X509CertificateValidator do weryfikowania certyfikatów. Przykład implementuje CustomX509CertificateValidator, pochodzące od <xref:System.IdentityModel.Selectors.X509CertificateValidator> . <xref:System.IdentityModel.Selectors.X509CertificateValidator>Aby uzyskać więcej informacji, zobacz dokumentację. Ten konkretny niestandardowy przykład modułu sprawdzania poprawności implementuje metodę Validate, aby akceptować dowolny certyfikat X. 509, który został wystawiony jako przedstawiony w poniższym kodzie.

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 Po wdrożeniu modułu sprawdzania poprawności w kodzie usługi Host usługi musi zostać poinformowany o wystąpieniu modułu sprawdzania poprawności, które ma być używane. Jest to realizowane przy użyciu następującego kodu.

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 Można też wykonać tę czynność w konfiguracji w następujący sposób.

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient powinien pomyślnie wywołać wszystkie metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji

Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.

Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji:

- Tworzenie certyfikatu serwera:

     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. Zmienna% SERVER_NAME% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna to localhost.

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:

     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Tworzenie certyfikatu klienta:

     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat klienta, który ma być używany. Zmienna% USER_NAME% określa nazwę klienta. Ta wartość jest ustawiona na "test1", ponieważ jest to nazwa, której szuka kod klienta. W przypadku zmiany wartości% USER_NAME% należy zmienić odpowiadającą jej wartość w pliku źródłowym Client.cs i skompilować ponownie klienta.

     Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu CurrentUser.

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów serwera:

     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat klienta do magazynu osób zaufanych. Ten krok jest wymagany, ponieważ system serwera nie ufa certyfikatom wygenerowanym przez Makecert. exe. Jeśli masz już certyfikat, który został odblokowany w zaufanym certyfikacie głównym — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów serwera z certyfikatem klienta nie jest wymagany.

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 otwartym z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!IMPORTANT]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.

2. Uruchom usługę Service. exe z service\bin.

3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.

4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach

1. Utwórz katalog na komputerze usługi.

2. Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi. Skopiuj także pliki Setup. bat, Oczyść. bat, getcomputers. vbs i ImportClientCert. bat do komputera usługi.

3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.

4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.

5. Na serwerze programu uruchom polecenie `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.

6. Edytuj plik Service. exe. config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Zmień również nazwę komputera w \<service> / \<baseAddresses> elemencie z localhost na w pełni kwalifikowaną nazwę komputera usługi.

7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.

8. Na kliencie Uruchom program `setup.bat client` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `client` argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.

9. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.

10. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.

11. Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.

12. Na serwerze programu Uruchom program ImportClientCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Spowoduje to zaimportowanie certyfikatu klienta z pliku. cer klienta do magazynu LocalMachine-TrustedPeople.

13. Na komputerze serwera Uruchom polecenie Service. exe w oknie wiersza polecenia.

14. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie

1. Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu. Spowoduje to usunięcie certyfikatów serwera i klienta z magazynu certyfikatów.

> [!NOTE]
> Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .
