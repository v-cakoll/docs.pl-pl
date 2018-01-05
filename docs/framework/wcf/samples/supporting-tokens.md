---
title: "Obsługa tokenów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea429e16914d737547885b6667fc1d81b23a0f0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-tokens"></a>Obsługa tokenów
Przykładowe tokenów pomocniczych pokazano, jak dodać dodatkowe tokeny na komunikat, który używa WS-Security. W przykładzie dodano tokenu zabezpieczeń binarnych X.509 oprócz tokenu zabezpieczającego nazwy użytkownika. Token jest przekazywany w nagłówku wiadomości WS-Security od klienta do usługi i część komunikatu jest podpisany przy użyciu klucza prywatnego skojarzonego z tokenu zabezpieczającego X.509 potwierdzenie posiadania certyfikatu X.509 do odbiornika. Jest to przydatne w przypadku, gdy jest wymagane są wielu oświadczeń skojarzony z komunikatem uwierzytelniania lub autoryzacji nadawcy. Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przedstawia przykład:  
  
-   Jak klient może przekazać tokeny zabezpieczające dodatkowe do usługi.  
  
-   Jak serwer mają dostęp do oświadczeń skojarzone z tokenów zabezpieczających dodatkowe.  
  
-   Jak certyfikat X.509 służy do ochrony klucz symetryczny stosowany do szyfrowania wiadomości i podpis.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient przeprowadza uwierzytelnianie z Token nazwy użytkownika i obsługa tokenu zabezpieczającego X.509  
 Usługa udostępnia jeden punkt końcowy komunikacji utworzonego programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`. W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas transmisji oraz przekazywanie `UserNameToken` wraz z towarzyszące `X509SecurityToken` w nagłówku wiadomości WS-Security. Klucz symetryczny jest używany do szyfrowania treści wiadomości i tokenu zabezpieczającego nazwy użytkownika. Token pomocniczy jest przekazywany jako dodatkowe binarnego tokenu zabezpieczającego w nagłówku wiadomości WS-Security. Autentyczności token pomocniczy jest potwierdza, że po zarejestrowaniu część wiadomości przy użyciu klucza prywatnego skojarzonego z obsługi zabezpieczeń X.509 tokenu.  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
```  
  
 Zachowanie Określa poświadczenia usługi, które mają być używane uwierzytelnianie klienta, a także informacje o certyfikat X.509 usługi. W przykładzie użyto `CN=localhost` jako nazwę podmiotu w certyfikacie X.509 usługi.  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 Usługa kodu:  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 Punkt końcowy klienta jest skonfigurowany w sposób podobny do punktu końcowego usługi. Klient używa takie same `BindingHelper` klasy w celu utworzenia powiązania. Pozostała konfiguracja znajduje się w `Client` klasy. Klient ustawia informacje o tokenu zabezpieczającego nazwy użytkownika, token pomocniczy zabezpieczeń X.509 i informacje o certyfikat X.509 usługi w kodzie konfiguracji do kolekcji zachowań klienta punktu końcowego.  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## <a name="displaying-callers-information"></a>Informacje o wywołującym wyświetlania  
 Aby wyświetlić informacje o wywołującym, można użyć `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczeń skojarzone z bieżącym obiektem wywołującym. Te oświadczenia są dostarczane automatycznie przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dla każdego tokenu odebranego w wiadomości.  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Po uruchomieniu próbki klienta najpierw monituje o podanie nazwy użytkownika i hasła dla użytkownika nazwa tokenu. Należy podać prawidłowe wartości dla Twojego konta systemowego, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi mapuje wartości podane w token nazwy użytkownika do tożsamości podanej przez system. Następnie klient jest wyświetlany odpowiedź z usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia aplikacji hostowanej Internet Information Services (IIS), która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.  
  
### <a name="creating-the-client-certificate"></a>Tworzenie certyfikatu klienta  
 Następujące wiersze z pliku wsadowego pliku Setup.bat Utwórz certyfikat klienta, który ma być używany. `%CLIENT_NAME%` Zmienna określa podmiot certyfikatu klienta. W przykładzie użyto "client.com" w nazwie podmiotu.  
  
 Certyfikat jest przechowywany w magazynie My (osobistych) w obszarze `CurrentUser` lokalizacji magazynu.  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalowanie certyfikatu klienta do magazynu zaufanego serwera  
 Następujący wiersz w pliku wsadowym pliku Setup.bat kopiuje certyfikat klienta w magazynie zaufanych osób serwera. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu serwera. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a>Utworzenie certyfikatu serwera  
 Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Domyślnie ten plik wsadowy jest localhost.  
  
 Certyfikat jest przechowywany w magazynie LocalMachine lokalizacji w mojej (osobiste). Certyfikat jest przechowywany w magazynie LocalMachine usług hostowanych przez usługi IIS. Hostowanie Samoobsługowe usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu serwera w magazynie CurrentUser lokalizacji, zastępując ciąg LocalMachine CurrentUser.  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalowanie certyfikatu serwera do zaufanego magazynu certyfikatów klienta  
 Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a>Włączanie dostępu do klucza prywatnego certyfikatu  
 Aby włączyć dostęp do klucza prywatnego certyfikatu usługi hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dostępu do klucza prywatnego. Jest to osiągane przez ostatnich kroków w skrypcie pliku Setup.bat.  
  
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
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, użyj poniższych instrukcji.  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
    > [!NOTE]
    >  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia. Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu próbki. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
2.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
3.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia zarządzania usług Internet Information Services (IIS).  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na maszynie usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportClientCert.bat maszynie usługi.  
  
3.  Utwórz katalog na komputerze klienckim na potrzeby plików binarnych klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z nazwą domeny pełni kwalifikowanymi maszyny i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, uruchom `setup.bat client` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora. Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi. W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim należy uruchomić ImportServiceCert.bat. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze, uruchom ImportClientCert.bat to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
13. Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Zobacz też
