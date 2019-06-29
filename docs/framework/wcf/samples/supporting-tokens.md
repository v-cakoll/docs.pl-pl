---
title: Obsługa tokenów
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: fba9a44342da5b064897b3ab81f34fa39498d379
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425453"
---
# <a name="supporting-tokens"></a><span data-ttu-id="ababf-102">Obsługa tokenów</span><span class="sxs-lookup"><span data-stu-id="ababf-102">Supporting Tokens</span></span>
<span data-ttu-id="ababf-103">Przykładowe tokenów pomocniczych pokazuje, jak dodać dodatkowe tokeny na komunikat, który korzysta z protokołu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ababf-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="ababf-104">W przykładzie dodano tokenu zabezpieczeń binarnych X.509, oprócz nazwy użytkownika tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ababf-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="ababf-105">Token jest przekazywany w nagłówku wiadomości WS-Security od klienta do usługi i część komunikatu jest podpisany przy użyciu klucza prywatnego skojarzonego z tokenem zabezpieczającym X.509 potwierdzenie posiadania certyfikatu X.509 do odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="ababf-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="ababf-106">Jest to przydatne w przypadku, gdy istnieje wymóg posiadania wielu oświadczeń skojarzonych z wiadomością uwierzytelniania lub autoryzacji nadawcy.</span><span class="sxs-lookup"><span data-stu-id="ababf-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="ababf-107">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="ababf-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ababf-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="ababf-108">Demonstrates</span></span>
 <span data-ttu-id="ababf-109">W przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="ababf-109">The sample demonstrates:</span></span>

- <span data-ttu-id="ababf-110">Jak klient może przekazać tokeny zabezpieczające dodatkowe usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-110">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="ababf-111">Jak serwera można uzyskać dostęp do oświadczenia skojarzone z tokenów zabezpieczających dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="ababf-111">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="ababf-112">Jak certyfikat X.509 umożliwia ochronę klucz symetryczny, używany do szyfrowania wiadomości i podpis.</span><span class="sxs-lookup"><span data-stu-id="ababf-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
>  <span data-ttu-id="ababf-113">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ababf-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="ababf-114">Klient uwierzytelnia się za pomocą Token nazwy użytkownika i obsłudze Token zabezpieczający X.509</span><span class="sxs-lookup"><span data-stu-id="ababf-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="ababf-115">Usługa udostępnia jeden punkt końcowy do komunikacji utworzonego programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="ababf-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="ababf-116">Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ababf-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ababf-117">Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="ababf-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="ababf-118">W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas przesyłania i przekazać `UserNameToken` wraz z towarzyszące `X509SecurityToken` w nagłówku wiadomości WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ababf-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="ababf-119">Klucz symetryczny jest używany do szyfrowania treści komunikatu i token zabezpieczający nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ababf-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="ababf-120">Token pomocniczy jest przekazywany jako dodatkowy binarnego tokenu zabezpieczającego w nagłówku wiadomości WS-Security.</span><span class="sxs-lookup"><span data-stu-id="ababf-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="ababf-121">Autentyczności token pomocniczy jest okazały się w, rejestrując część wiadomości przy użyciu klucza prywatnego skojarzonego z pomocniczych zabezpieczeń X.509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="ababf-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

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

 <span data-ttu-id="ababf-122">Zachowanie Określa poświadczenia usługi, które mają być używane do uwierzytelniania klienta, a także informacje o certyfikacie X.509.</span><span class="sxs-lookup"><span data-stu-id="ababf-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="ababf-123">W przykładzie użyto `CN=localhost` jako nazwę podmiotu w certyfikacie X.509.</span><span class="sxs-lookup"><span data-stu-id="ababf-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

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

 <span data-ttu-id="ababf-124">Kod obsługi:</span><span class="sxs-lookup"><span data-stu-id="ababf-124">Service code:</span></span>

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

 <span data-ttu-id="ababf-125">Punkt końcowy klienta jest skonfigurowany w sposób podobny do punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="ababf-126">Klient używa tych samych `BindingHelper` klasy, aby utworzyć powiązanie.</span><span class="sxs-lookup"><span data-stu-id="ababf-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="ababf-127">Pozostała konfiguracja zostanie znajduje się w `Client` klasy.</span><span class="sxs-lookup"><span data-stu-id="ababf-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="ababf-128">Klient ustawia informacje dotyczące tokenu zabezpieczeń nazwę użytkownika, pomocnicze token zabezpieczający X.509 i informacje o certyfikacie X.509 w kodu konfiguracji do kolekcji zachowań punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

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

## <a name="displaying-callers-information"></a><span data-ttu-id="ababf-129">Wyświetlanie informacji o wywołującym</span><span class="sxs-lookup"><span data-stu-id="ababf-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="ababf-130">Aby wyświetlić informacje dotyczące obiektu wywołującego, można użyć `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ababf-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="ababf-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczenia skojarzone z bieżącego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ababf-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="ababf-132">Te oświadczenia są dostarczane automatycznie przez Windows Communication Foundation (WCF) dla każdego tokenu otrzymane w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ababf-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

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

## <a name="running-the-sample"></a><span data-ttu-id="ababf-133">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="ababf-133">Running the Sample</span></span>
 <span data-ttu-id="ababf-134">Po uruchomieniu przykładu, klienta najpierw monituje o podanie nazwy użytkownika i hasła dla użytkownika nazwa tokenu.</span><span class="sxs-lookup"><span data-stu-id="ababf-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="ababf-135">Upewnij się zapewnić poprawne wartości dla swojego konta systemu, ponieważ usługi WCF w usłudze mapy wartości podane w token nazwy użytkownika w tożsamości udostępnianej przez system.</span><span class="sxs-lookup"><span data-stu-id="ababf-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="ababf-136">Po tym klient jest wyświetlany odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="ababf-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="ababf-138">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="ababf-138">Setup Batch File</span></span>
 <span data-ttu-id="ababf-139">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchamiania aplikacji hostowanych Internet Information Services (IIS), która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="ababf-140">Ten plik wsadowy muszą zostać zmodyfikowane, działają na maszynach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="ababf-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="ababf-141">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ababf-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="ababf-142">Tworzenie certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="ababf-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="ababf-143">Następujące wiersze z pliku wsadowego Setup.bat utworzenia certyfikatu klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ababf-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="ababf-144">`%CLIENT_NAME%` Zmienna określa podmiot certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="ababf-145">Ta próbka używa "client.com" jako nazwę podmiotu.</span><span class="sxs-lookup"><span data-stu-id="ababf-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="ababf-146">Certyfikat jest przechowywany w magazynie użytkownika (osobistych) w obszarze `CurrentUser` lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="ababf-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="ababf-147">Instalowanie certyfikatu klienta do Store zaufanego serwera</span><span class="sxs-lookup"><span data-stu-id="ababf-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="ababf-148">Następujący wiersz w pliku wsadowym Setup.bat jest skopiowanie certyfikatu klienta w magazynie zaufanych osób serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="ababf-149">Ten krok jest wymagany, ponieważ certyfikaty generowaną przez Makecert.exe nie niejawnie cieszą się zaufaniem systemu serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="ababf-150">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ababf-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="ababf-151">Utworzenie certyfikatu serwera</span><span class="sxs-lookup"><span data-stu-id="ababf-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="ababf-152">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ababf-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="ababf-153">`%SERVER_NAME%` Zmienna Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="ababf-154">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="ababf-155">Domyślnie ten plik wsadowy jest localhost.</span><span class="sxs-lookup"><span data-stu-id="ababf-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="ababf-156">Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ababf-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="ababf-157">Certyfikat jest przechowywany w magazynie usług hostowanych przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="ababf-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="ababf-158">Samodzielnie hostowany usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu serwera w lokalizacji magazynu CurrentUser, zastępując ciąg LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="ababf-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="ababf-159">Instalowanie certyfikatu serwera do zaufanego Store certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="ababf-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="ababf-160">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="ababf-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ababf-161">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ababf-162">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ababf-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="ababf-163">Umożliwianie dostępu do klucza prywatnego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="ababf-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="ababf-164">Aby włączyć dostęp do klucza prywatnego certyfikatu z usług hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dla klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="ababf-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="ababf-165">Jest to realizowane przez ostatnie kroki skrypt Setup.bat jest.</span><span class="sxs-lookup"><span data-stu-id="ababf-165">This is accomplished by last steps in the Setup.bat script.</span></span>

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

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ababf-166">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="ababf-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ababf-167">Pamiętaj, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ababf-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ababf-168">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ababf-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="ababf-169">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ababf-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ababf-170">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="ababf-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="ababf-171">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia programu Visual Studio 2012 uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="ababf-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="ababf-172">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="ababf-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ababf-173">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="ababf-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="ababf-174">Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="ababf-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="ababf-175">Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu pracy z przykładem.</span><span class="sxs-lookup"><span data-stu-id="ababf-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="ababf-176">Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ababf-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="ababf-177">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ababf-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ababf-178">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="ababf-179">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ababf-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="ababf-180">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="ababf-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="ababf-181">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-181">Create a directory on the service machine.</span></span> <span data-ttu-id="ababf-182">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ababf-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="ababf-183">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="ababf-184">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="ababf-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="ababf-185">Także skopiować pliki Setup.bat, Cleanup.bat i ImportClientCert.bat maszyną usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="ababf-186">Utwórz katalog na komputerze klienckim na potrzeby plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="ababf-187">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="ababf-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="ababf-188">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="ababf-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="ababf-189">Na serwerze, uruchom `setup.bat service` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="ababf-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ababf-190">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="ababf-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="ababf-191">Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="ababf-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="ababf-192">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="ababf-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="ababf-193">Na komputerze klienckim, należy uruchomić `setup.bat client` w wierszu polecenia dla deweloperów programu Visual Studio otwartych z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="ababf-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="ababf-194">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="ababf-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="ababf-195">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="ababf-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="ababf-196">To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="ababf-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="ababf-197">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="ababf-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="ababf-198">Na komputerze klienckim należy uruchomić ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="ababf-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="ababf-199">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="ababf-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="ababf-200">Na serwerze, uruchom ImportClientCert.bat to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="ababf-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="ababf-201">Na komputerze klienckim należy uruchomić Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ababf-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="ababf-202">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ababf-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ababf-203">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="ababf-203">To clean up after the sample</span></span>  
  
- <span data-ttu-id="ababf-204">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="ababf-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ababf-205">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="ababf-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="ababf-206">Po uruchomieniu przykłady WCF, które używają certyfikatów na maszynach, pamiętaj wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="ababf-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ababf-207">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="ababf-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
