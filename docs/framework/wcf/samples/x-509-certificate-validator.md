---
title: Moduł weryfikacji certyfikatów X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: e54f79046113e5f1a1a1cc065606fd5b706b49ac
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272530"
---
# <a name="x509-certificate-validator"></a>Moduł weryfikacji certyfikatów X.509
Niniejszy przykład pokazuje, jak zaimplementować niestandardowy moduł weryfikacji certyfikatów X.509. Jest to przydatne w przypadkach, gdy żadna z wbudowanych metod walidacji certyfikatu X.509 jest odpowiednia dla wymagań aplikacji. Niniejszy przykład pokazuje usługi, która ma niestandardowy moduł sprawdzania poprawności, który akceptuje własnym wystawionych certyfikatów. Klient używa takiego certyfikatu do uwierzytelnienia w usłudze.  
  
 Uwaga: jak każdy może utworzyć własny wystawionego certyfikatu niestandardowego modułu weryfikacji, używane przez usługę jest mniej bezpieczna niż zachowanie domyślne, dostarczone przez ChainTrust X509CertificateValidationMode. Ryzyko związane z tym powinien zostać starannie przemyślany, przed użyciem tej logiki weryfikacji w kodzie produkcyjnym.  
  
 W podsumowaniu Niniejszy przykład pokazuje, jak:  
  
-   Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.  
  
-   Serwer sprawdza poprawność poświadczeń klienta względem X509CertificateValidator niestandardowych.  
  
-   Serwer jest uwierzytelniany przy użyciu certyfikatu X.509 serwera.  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding` , domyślnie używane są `WSSecurity` i uwierzytelnianie certyfikatu klienta. Zachowanie usługi Określa tryb niestandardowego sprawdzania poprawności certyfikatów X.509 klienta wraz z typu klasy modułu sprawdzania poprawności. Zachowanie określa również certyfikat serwera za pomocą elementu serviceCertificate. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
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
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji adresu bezwzględnego dla punktu końcowego usługi, powiązanie i zamówienia. Klient powiązanie skonfigurowano odpowiedni tryb i wiadomości `clientCredentialType`.  
  
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
  
 Implementacja klienta ustawia certyfikat klienta do użycia.  
  
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
  
 Ta próbka używa niestandardowych X509CertificateValidator do sprawdzania poprawności certyfikatów. Przykład implementuje CustomX509CertificateValidator, pochodzące z <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Zobacz dokumentację na temat <xref:System.IdentityModel.Selectors.X509CertificateValidator> Aby uzyskać więcej informacji. W tym przykładzie niestandardowego modułu sprawdzania poprawności implementuje metodę sprawdzania poprawności, aby zaakceptować certyfikat X.509, wszelkie własnym wystawiony, jak pokazano w poniższym kodzie.  
  
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
  
 Po wdrożeniu modułu sprawdzania poprawności jest w kodzie usługi hosta usługi muszą zostać powiadomieni o wystąpieniu weryfikacji do użycia. Odbywa się przy użyciu następującego kodu.  
  
```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 Lub można zrobić to samo w konfiguracji w następujący sposób.  
  
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
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie należy wywołać wszystkich metod. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.  
  
 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji:  
  
-   Tworzenie certyfikatu serwera:  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Wartość domyślna to hosta lokalnego.  
  
    ```bash  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:  
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```bash  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Tworzenie certyfikatu klienta:  
  
     Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany. % Zmienna % nazwa_użytkownika Określa nazwę klienta. Ta wartość jest równa "test1", ponieważ jest to nazwa, którą wyszukuje kodu klienta. Jeśli zmienisz wartość % nazwa_użytkownika należy zmienić odpowiednie wartości w pliku źródłowym Client.cs i ponownie skompilować klienta.  
  
     Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu CurrentUser.  
  
    ```bash  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera:  
  
     Następujące wiersze w pliku wsadowym Setup.bat skopiuj certyfikat klienta do magazynu osób zaufanych. Ten krok jest wymagany, ponieważ certyfikaty generowaną przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera. Jeśli masz już certyfikat, który jest ścieżką w zaufany certyfikat główny — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów serwera za pomocą certyfikatu klienta nie jest wymagane.  
  
    ```bash  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Do uruchomienia przykładu w jednym — lub cross-computerconfiguration, użyj poniższych instrukcji.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej wewnątrz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia otwartych z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!IMPORTANT]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Ustawić zmiennej środowiskowej PATH, w ramach [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] polecenia wskazuje katalog, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest.  
  
2.  Uruchom Service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi.  
  
2.  Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi. Także skopiować pliki Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat, aby komputer z usługą.  
  
3.  Utwórz katalog na computerfor klienta plików binarnych klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny wywozu computerand certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj Service.exe.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera. Również zmienić nazwę komputera w \<usługi > /\<baseAddresses > element z hostem lokalnym do w pełni kwalifikowanej nazwy komputera usługi.  
  
7.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi. To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze uruchom ImportClientCert.bat w wierszu polecenia programu Visual Studio otwartych z uprawnieniami administratora. To importuje certyfikat klienta z pliku Client.cer, do maszyny lokalnej - TrustedPeople magazynu.  
  
13. Na komputerze serwera uruchomić Service.exe z okna wiersza polecenia.  
  
14. Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa. Spowoduje to usunięcie certyfikaty klienta i serwera z magazynu certyfikatów.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
