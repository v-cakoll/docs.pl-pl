---
title: Obsługa tokenów
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 9c8ee4b11cd61e51e91c2e116ab3c20448fc1a58
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575046"
---
# <a name="supporting-tokens"></a>Obsługa tokenów
Przykład tokenów pomocniczych pokazuje, jak dodać dodatkowe tokeny do wiadomości, która korzysta z protokołu WS-Security. Przykład dodaje binarny token zabezpieczający X. 509 oprócz tokenu zabezpieczeń nazwy użytkownika. Token jest przesyłany z klienta do usługi, a część wiadomości jest podpisywana przy użyciu klucza prywatnego skojarzonego z tokenem zabezpieczeń X. 509 w celu potwierdzenia posiadania certyfikatu X. 509 do odbiorcy. Jest to przydatne w przypadku, gdy wymagane jest posiadanie wielu oświadczeń skojarzonych z komunikatem w celu uwierzytelnienia lub autoryzacji nadawcy. Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.

## <a name="demonstrates"></a>Demonstracje
 Przykład ilustruje:

- Jak klient może przekazać dodatkowe tokeny zabezpieczające do usługi.

- Jak serwer może uzyskać dostęp do oświadczeń skojarzonych z dodatkowymi tokenami zabezpieczeń.

- Jak certyfikat X. 509 serwera jest używany do ochrony klucza symetrycznego używanego do szyfrowania i podpisywania komunikatów.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Klient uwierzytelnia się za pomocą tokenu username i obsługuje token zabezpieczający X. 509
 Usługa ujawnia pojedynczy punkt końcowy do komunikacji, który jest programowo tworzony przy użyciu `BindingHelper` `EchoServiceHost` klas i. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane z powiązaniem niestandardowym przy użyciu `SymmetricSecurityBindingElement` i `HttpTransportBindingElement` . Ten przykład ustawia `SymmetricSecurityBindingElement` do użycia certyfikatu usługi X. 509 w celu ochrony klucza symetrycznego podczas transmisji i przekazywania `UserNameToken` wraz z obsługą `X509SecurityToken` w nagłówku komunikatu WS-Security. Klucz symetryczny jest używany do szyfrowania treści wiadomości i tokenu zabezpieczeń nazwy użytkownika. Token pomocniczy jest przesyłany jako dodatkowy token zabezpieczający binarny w nagłówku komunikatu WS-Security. Autentyczność tokenu pomocniczego jest udowodniona przez podpisywanie części komunikatu z kluczem prywatnym skojarzonym z pomocniczym tokenem zabezpieczeń X. 509.

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

 Zachowanie określa poświadczenia usługi, które mają być używane do uwierzytelniania klientów, a także informacje na temat certyfikatu usługi Service X. 509. Przykład używa `CN=localhost` jako nazwy podmiotu w certyfikacie X. 509 usługi.

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

 Kod usługi:

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
                // Try to find an X500DistinguishedName claim. This will
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

 Punkt końcowy klienta jest skonfigurowany w podobny sposób do punktu końcowego usługi. Klient używa tej samej `BindingHelper` klasy do utworzenia powiązania. Pozostała część instalacji znajduje się w `Client` klasie. Klient ustawia informacje o tokenie zabezpieczającym nazwa użytkownika, pomocniczym tokenie zabezpieczającym X. 509 oraz informacje o certyfikacie usługi Service X. 509 w kodzie instalacji do kolekcji zachowań punktu końcowego klienta.

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

## <a name="displaying-callers-information"></a>Wyświetlanie informacji o wywołujących
 Aby wyświetlić informacje o wywołującym, można użyć, `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`Zawiera oświadczenia autoryzacji skojarzone z bieżącym obiektem wywołującym. Te oświadczenia są dostarczane automatycznie przez Windows Communication Foundation (WCF) dla każdego tokenu otrzymanego w komunikacie.

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
            //Try to find an X500DistinguishedName claim.
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

## <a name="running-the-sample"></a>Uruchamianie przykładu
 Po uruchomieniu przykładu klient najpierw poprosi o podanie nazwy użytkownika i hasła dla tokenu nazwy użytkownika. Upewnij się, że podano poprawne wartości dla konta systemowego, ponieważ WCF w usłudze mapuje wartości podane w tokenie nazwy użytkownika na tożsamość dostarczoną przez system. Następnie klient wyświetli odpowiedź z usługi. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji
 Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej w programie Internet Information Services (IIS), która wymaga zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na maszynach lub działać w nieobsługiwanym przypadku.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować do uruchamiania w odpowiedniej konfiguracji.

### <a name="creating-the-client-certificate"></a>Tworzenie certyfikatu klienta
 Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat klienta, który ma być używany. `%CLIENT_NAME%`Zmienna określa podmiot certyfikatu klienta. Ten przykład używa "client.com" jako nazwy podmiotu.

 Certyfikat jest przechowywany w magazynie (Personal) w `CurrentUser` lokalizacji magazynu.

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Instalowanie certyfikatu klienta w zaufanym magazynie serwera
 Następujący wiersz w pliku wsadowym Setup. bat kopiuje certyfikat klienta do magazynu osób zaufanych na serwerze. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane dla systemu serwera. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Tworzenie certyfikatu serwera
 Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. `%SERVER_NAME%`Zmienna określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna w tym pliku wsadowym to localhost.

 Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu LocalMachine. Certyfikat jest przechowywany w magazynie LocalMachine dla usług hostowanych przez usługi IIS. W przypadku usług samodzielnych należy zmodyfikować plik wsadowy, aby przechowywać certyfikat serwera w lokalizacji magazynu CurrentUser przez zastąpienie ciągu LocalMachine ciągiem CurrentUser.

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta
 Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Włączanie dostępu do klucza prywatnego certyfikatu
 Aby umożliwić dostęp do klucza prywatnego certyfikatu z usługi hostowanej przez usługi IIS, konto użytkownika, pod którym działa proces hostowany przez usługi IIS, musi mieć przyznane odpowiednie uprawnienia do klucza prywatnego. Jest to realizowane przez ostatnie kroki skryptu Setup. bat.

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze

1. Uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 z uprawnieniami administratora. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.

    > [!NOTE]
    > Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat. Pamiętaj o usunięciu certyfikatów, uruchamiając Oczyść. bat po zakończeniu z przykładem. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
2. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
3. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania Internet Information Services (IIS).  
  
2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na maszynie usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin. Skopiuj także pliki Setup. bat, Oczyść. bat i ImportClientCert. bat do maszyny usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze programu uruchom polecenie `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny maszyny i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
6. Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. Na kliencie Uruchom program `setup.bat client` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora. Uruchomienie `setup.bat` z `client` argumentem tworzy certyfikat klienta o nazwie Client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.  
  
9. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi. Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.  
  
10. Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.  
  
11. Na kliencie Uruchom program ImportServiceCert. bat. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
12. Na serwerze programu Uruchom program ImportClientCert. bat, który importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.  
  
13. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
> [!NOTE]
> Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między maszynami. W przypadku uruchamiania przykładów WCF, które używają certyfikatów między maszynami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .
