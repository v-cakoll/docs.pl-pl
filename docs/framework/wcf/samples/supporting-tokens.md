---
title: Obsługa tokenów
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 899c6ecabafb1bd0487b989c6da8963dd07945cf
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304157"
---
# <a name="supporting-tokens"></a>Obsługa tokenów
Przykładowe tokenów pomocniczych pokazuje, jak dodać dodatkowe tokeny na komunikat, który korzysta z protokołu WS-Security. W przykładzie dodano tokenu zabezpieczeń binarnych X.509, oprócz nazwy użytkownika tokenu zabezpieczającego. Token jest przekazywany w nagłówku wiadomości WS-Security od klienta do usługi i część komunikatu jest podpisany przy użyciu klucza prywatnego skojarzonego z tokenem zabezpieczającym X.509 potwierdzenie posiadania certyfikatu X.509 do odbiorcy. Jest to przydatne w przypadku, gdy istnieje wymóg posiadania wielu oświadczeń skojarzonych z wiadomością uwierzytelniania lub autoryzacji nadawcy. Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".

## <a name="demonstrates"></a>Demonstracje
 W przykładzie pokazano:

-   Jak klient może przekazać tokeny zabezpieczające dodatkowe usługi.

-   Jak serwera można uzyskać dostęp do oświadczenia skojarzone z tokenów zabezpieczających dodatkowe.

-   Jak certyfikat X.509 umożliwia ochronę klucz symetryczny, używany do szyfrowania wiadomości i podpis.

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient uwierzytelnia się za pomocą Token nazwy użytkownika i obsłudze Token zabezpieczający X.509
 Usługa udostępnia jeden punkt końcowy do komunikacji utworzonego programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`. W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas przesyłania i przekazać `UserNameToken` wraz z towarzyszące `X509SecurityToken` w nagłówku wiadomości WS-Security. Klucz symetryczny jest używany do szyfrowania treści komunikatu i token zabezpieczający nazwy użytkownika. Token pomocniczy jest przekazywany jako dodatkowy binarnego tokenu zabezpieczającego w nagłówku wiadomości WS-Security. Autentyczności token pomocniczy jest okazały się w, rejestrując część wiadomości przy użyciu klucza prywatnego skojarzonego z pomocniczych zabezpieczeń X.509 tokenu.

```csharp
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

 Zachowanie Określa poświadczenia usługi, które mają być używane do uwierzytelniania klienta, a także informacje o certyfikacie X.509. W przykładzie użyto `CN=localhost` jako nazwę podmiotu w certyfikacie X.509.

```csharp
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

 Kod obsługi:

```csharp
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
            return $"Hello {userName}, {certificateSubjectName}";
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

 Punkt końcowy klienta jest skonfigurowany w sposób podobny do punktu końcowego usługi. Klient używa tych samych `BindingHelper` klasy, aby utworzyć powiązanie. Pozostała konfiguracja zostanie znajduje się w `Client` klasy. Klient ustawia informacje dotyczące tokenu zabezpieczeń nazwę użytkownika, pomocnicze token zabezpieczający X.509 i informacje o certyfikacie X.509 w kodu konfiguracji do kolekcji zachowań punktu końcowego klienta.

```csharp
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

## <a name="displaying-callers-information"></a>Wyświetlanie informacji o wywołującym
 Aby wyświetlić informacje dotyczące obiektu wywołującego, można użyć `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczenia skojarzone z bieżącego obiektu wywołującego. Te oświadczenia są dostarczane automatycznie przez Windows Communication Foundation (WCF) dla każdego tokenu otrzymane w wiadomości.

```csharp
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

## <a name="running-the-sample"></a>Działa aplikacja przykładowa
 Po uruchomieniu przykładu, klienta najpierw monituje o podanie nazwy użytkownika i hasła dla użytkownika nazwa tokenu. Upewnij się zapewnić poprawne wartości dla swojego konta systemu, ponieważ usługi WCF w usłudze mapy wartości podane w token nazwy użytkownika w tożsamości udostępnianej przez system. Po tym klient jest wyświetlany odpowiedź z usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchamiania aplikacji hostowanych Internet Information Services (IIS), która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na maszynach lub działać w przypadku innych obsługiwanych.

 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.

### <a name="creating-the-client-certificate"></a>Tworzenie certyfikatu klienta
 Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany. `%CLIENT_NAME%` Zmienna określa podmiot certyfikatu klienta. Ta próbka używa "client.com" jako nazwę podmiotu.

 Certyfikat jest przechowywany w magazynie użytkownika (osobistych) w obszarze `CurrentUser` lokalizacji magazynu.

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalowanie certyfikatu klienta do Store zaufanego serwera
 Następujący wiersz w pliku wsadowym Setup.bat jest skopiowanie certyfikatu klienta w magazynie zaufanych osób serwera. Ten krok jest wymagany, ponieważ certyfikaty generowaną przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Utworzenie certyfikatu serwera
 Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Domyślnie ten plik wsadowy jest localhost.

 Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine. Certyfikat jest przechowywany w magazynie usług hostowanych przez usługi IIS. Samodzielnie hostowany usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu serwera w lokalizacji magazynu CurrentUser, zastępując ciąg LocalMachine CurrentUser.

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalowanie certyfikatu serwera do zaufanego Store certyfikatu klienta
 Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Umożliwianie dostępu do klucza prywatnego certyfikatu
 Aby włączyć dostęp do klucza prywatnego certyfikatu z usług hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dla klucza prywatnego. Jest to realizowane przez ostatnie kroki skrypt Setup.bat jest.

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

##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1.  Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, użyj poniższych instrukcji.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze

1.  Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia programu Visual Studio 2012 uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.

    > [!NOTE]
    >  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia. Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH. Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu pracy z przykładem. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
2.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
3.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Do uruchomienia przykładu na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na maszynie usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki Setup.bat, Cleanup.bat i ImportClientCert.bat maszyną usługi.  
  
3.  Utwórz katalog na komputerze klienckim na potrzeby plików binarnych klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7.  Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8.  Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora. Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.  
  
9. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi. To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.  
  
10. Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.  
  
11. Na komputerze klienckim należy uruchomić ImportServiceCert.bat. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
12. Na serwerze, uruchom ImportClientCert.bat to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.  
  
13. Na komputerze klienckim należy uruchomić Client.exe z okna wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykłady WCF, które używają certyfikatów na maszynach, pamiętaj wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="see-also"></a>Zobacz także
