---
title: "Moduł weryfikacji certyfikatów X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0717aae2c13c9fa5fcbf0ea47d344cac5675fbea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="x509-certificate-validator"></a>Moduł weryfikacji certyfikatów X.509
W tym przykładzie pokazano, jak do zaimplementowania niestandardowego modułu weryfikacji certyfikatów X.509. Jest to przydatne w sytuacjach, gdy żaden z wbudowanych tryby walidacji certyfikatu X.509 nie jest odpowiednią do wymagań aplikacji. W tym przykładzie pokazano usługi, która ma niestandardowego modułu weryfikacji akceptuje własnym wystawionych certyfikatów. Klient używa takiego certyfikatu do uwierzytelnienia w usłudze.  
  
 Uwaga: ponieważ każda osoba, która może utworzyć certyfikat wystawiony samodzielnie niestandardowego modułu weryfikacji, używane przez usługę jest mniej bezpieczna niż udostępniane przez ChainTrust X509CertificateValidationMode zachowanie domyślne. Ryzyko związane z tym powinien zostać starannie przemyślany, przed użyciem tej logiki sprawdzania poprawności w kodzie produkcyjnym.  
  
 W podsumowaniu przykładzie pokazano, jak:  
  
-   Klient może zostać uwierzytelniony przy użyciu certyfikatu X.509.  
  
-   Serwer sprawdza poprawność poświadczeń klienta przed niestandardowego obiektu X509CertificateValidator.  
  
-   Serwer jest uwierzytelniany przy użyciu certyfikat X.509.  
  
 Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji App.config. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą `wsHttpBinding` który używa domyślnie `WSSecurity` i uwierzytelnianie certyfikatu klienta. Zachowanie usługi Określa tryb niestandardowego sprawdzania poprawności certyfikatów X.509 klienta wraz z typem klasy modułu sprawdzania poprawności. Zachowanie określa również za pomocą elementu serviceCertificate certyfikatu serwera. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).  
  
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
  
 Konfiguracja punktu końcowego klienta składa się z nazwy konfiguracji, adres bezwzględny dla punktu końcowego usługi, powiązanie i kontraktu. Klient powiązanie jest skonfigurowane przy użyciu odpowiedni tryb i komunikat `clientCredentialType`.  
  
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
  
```  
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
  
 W przykładzie użyto niestandardowego obiektu X509CertificateValidator, aby zweryfikować certyfikaty. Próbka implementuje CustomX509CertificateValidator pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Zobacz dokumentację <xref:System.IdentityModel.Selectors.X509CertificateValidator> Aby uzyskać więcej informacji. W tym przykładzie niestandardowego modułu sprawdzania poprawności implementuje metodę sprawdzania poprawności do akceptowania dowolny certyfikat X.509 własnym wystawiony zgodnie z poniższym kodem.  
  
```  
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
  
 Po zaimplementowaniu w kodzie usługi modułu sprawdzania poprawności hosta usługi musi informację o wystąpienia modułu sprawdzania poprawności do użycia. Jest to realizowane przy użyciu następującego kodu.  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 Lub tak samo postąpić w konfiguracji w następujący sposób.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie powinny wywoływać wszystkie metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej przedstawiono krótkie omówienie różne sekcje pliki wsadowe, tak, aby można modyfikować w prawidłowej konfiguracji:  
  
-   Tworzenie certyfikatu serwera:  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Wartość domyślna to localhost.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:  
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Tworzenie certyfikatu klienta:  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat Utwórz certyfikat klienta, który ma być używany. % Zmienna % nazwa_użytkownika Określa nazwę klienta. Ta wartość jest równa "test1", ponieważ jest to nazwa, które wyszukuje kodu klienta. W przypadku zmiany wartości nazwa_użytkownika % należy zmienić odpowiednie wartości w pliku źródłowym Client.cs i skompiluj ponownie klienta.  
  
     Certyfikat jest przechowywany w magazynie My (osobistych) w lokalizacji w magazynie CurrentUser.  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera:  
  
     Następujące wiersze w pliku wsadowym pliku Setup.bat skopiuj certyfikat klienta w magazynie zaufanych osób. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu serwera. Jeśli masz już certyfikatu, który jest ścieżką do katalogu głównego w zaufanym certyfikatem głównym — na przykład certyfikat wystawiony Microsoft — ten krok zapełnianie magazynu certyfikatów na serwerze przy użyciu certyfikatu klienta nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykład w jednym - lub cross-computerconfiguration, użyj poniższych instrukcji.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] otworzyć wiersz polecenia z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!IMPORTANT]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
2.  Uruchom Service.exe z service\bin.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi.  
  
2.  Skopiuj pliki programu usługi z \service\bin do katalogu wirtualnego na komputerze usługi. Także skopiować pliki pliku Setup.bat, Cleanup.bat, GetComputerName.vbs i ImportClientCert.bat na komputerze usługi.  
  
3.  Utwórz katalog na computerfor klienta pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę eksportu computerand certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj Service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera. Również zmienić nazwę komputera w \<usługi > /\<baseAddresses > element na podstawie localhost pełną nazwę komputera usługi.  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, uruchom `setup.bat client` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi. W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze należy uruchomić ImportClientCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora. Certyfikat klienta to importuje z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
13. Na komputerze serwera Uruchom Service.exe z okna wiersza polecenia.  
  
14. Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki. Spowoduje to usunięcie certyfikaty serwera i klienta z magazynu certyfikatów.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
