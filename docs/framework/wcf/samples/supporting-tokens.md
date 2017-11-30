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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf4c153cb3bb0b977b2d1f0438d1b6ac0d46ab43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="supporting-tokens"></a><span data-ttu-id="18019-102">Obsługa tokenów</span><span class="sxs-lookup"><span data-stu-id="18019-102">Supporting Tokens</span></span>
<span data-ttu-id="18019-103">Przykładowe tokenów pomocniczych pokazano, jak dodać dodatkowe tokeny na komunikat, który używa WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18019-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="18019-104">W przykładzie dodano tokenu zabezpieczeń binarnych X.509 oprócz tokenu zabezpieczającego nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18019-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="18019-105">Token jest przekazywany w nagłówku wiadomości WS-Security od klienta do usługi i część komunikatu jest podpisany przy użyciu klucza prywatnego skojarzonego z tokenu zabezpieczającego X.509 potwierdzenie posiadania certyfikatu X.509 do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="18019-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="18019-106">Jest to przydatne w przypadku, gdy jest wymagane są wielu oświadczeń skojarzony z komunikatem uwierzytelniania lub autoryzacji nadawcy.</span><span class="sxs-lookup"><span data-stu-id="18019-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="18019-107">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="18019-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="18019-108">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="18019-108">Demonstrates</span></span>  
 <span data-ttu-id="18019-109">Przedstawia przykład:</span><span class="sxs-lookup"><span data-stu-id="18019-109">The sample demonstrates:</span></span>  
  
-   <span data-ttu-id="18019-110">Jak klient może przekazać tokeny zabezpieczające dodatkowe do usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-110">How a client can pass additional security tokens to a service.</span></span>  
  
-   <span data-ttu-id="18019-111">Jak serwer mają dostęp do oświadczeń skojarzone z tokenów zabezpieczających dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="18019-111">How the server can access claims associated with additional security tokens.</span></span>  
  
-   <span data-ttu-id="18019-112">Jak certyfikat X.509 służy do ochrony klucz symetryczny stosowany do szyfrowania wiadomości i podpis.</span><span class="sxs-lookup"><span data-stu-id="18019-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18019-113">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="18019-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="18019-114">Klient przeprowadza uwierzytelnianie z Token nazwy użytkownika i obsługa tokenu zabezpieczającego X.509</span><span class="sxs-lookup"><span data-stu-id="18019-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>  
 <span data-ttu-id="18019-115">Usługa udostępnia jeden punkt końcowy komunikacji utworzonego programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="18019-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="18019-116">Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="18019-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="18019-117">Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="18019-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="18019-118">W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas transmisji oraz przekazywanie `UserNameToken` wraz z towarzyszące `X509SecurityToken` w nagłówku wiadomości WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18019-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="18019-119">Klucz symetryczny jest używany do szyfrowania treści wiadomości i tokenu zabezpieczającego nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="18019-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="18019-120">Token pomocniczy jest przekazywany jako dodatkowe binarnego tokenu zabezpieczającego w nagłówku wiadomości WS-Security.</span><span class="sxs-lookup"><span data-stu-id="18019-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="18019-121">Autentyczności token pomocniczy jest potwierdza, że po zarejestrowaniu część wiadomości przy użyciu klucza prywatnego skojarzonego z obsługi zabezpieczeń X.509 tokenu.</span><span class="sxs-lookup"><span data-stu-id="18019-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>  
  
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
  
 <span data-ttu-id="18019-122">Zachowanie Określa poświadczenia usługi, które mają być używane uwierzytelnianie klienta, a także informacje o certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="18019-123">W przykładzie użyto `CN=localhost` jako nazwę podmiotu w certyfikacie X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>  
  
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
  
 <span data-ttu-id="18019-124">Usługa kodu:</span><span class="sxs-lookup"><span data-stu-id="18019-124">Service code:</span></span>  
  
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
  
 <span data-ttu-id="18019-125">Punkt końcowy klienta jest skonfigurowany w sposób podobny do punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="18019-126">Klient używa takie same `BindingHelper` klasy w celu utworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="18019-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="18019-127">Pozostała konfiguracja znajduje się w `Client` klasy.</span><span class="sxs-lookup"><span data-stu-id="18019-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="18019-128">Klient ustawia informacje o tokenu zabezpieczającego nazwy użytkownika, token pomocniczy zabezpieczeń X.509 i informacje o certyfikat X.509 usługi w kodzie konfiguracji do kolekcji zachowań klienta punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="18019-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>  
  
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
  
## <a name="displaying-callers-information"></a><span data-ttu-id="18019-129">Informacje o wywołującym wyświetlania</span><span class="sxs-lookup"><span data-stu-id="18019-129">Displaying Callers' Information</span></span>  
 <span data-ttu-id="18019-130">Aby wyświetlić informacje o wywołującym, można użyć `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="18019-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="18019-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczeń skojarzone z bieżącym obiektem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="18019-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="18019-132">Te oświadczenia są dostarczane automatycznie przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dla każdego tokenu odebranego w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="18019-132">Those claims are supplied automatically by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] for every token received in the message.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="18019-133">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="18019-133">Running the Sample</span></span>  
 <span data-ttu-id="18019-134">Po uruchomieniu próbki klienta najpierw monituje o podanie nazwy użytkownika i hasła dla użytkownika nazwa tokenu.</span><span class="sxs-lookup"><span data-stu-id="18019-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="18019-135">Należy podać prawidłowe wartości dla Twojego konta systemowego, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi mapuje wartości podane w token nazwy użytkownika do tożsamości podanej przez system.</span><span class="sxs-lookup"><span data-stu-id="18019-135">Be sure to provide correct values for your system account, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="18019-136">Następnie klient jest wyświetlany odpowiedź z usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="18019-137">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-137">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="18019-138">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="18019-138">Setup Batch File</span></span>  
 <span data-ttu-id="18019-139">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia aplikacji hostowanej Internet Information Services (IIS), która wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="18019-140">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="18019-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="18019-141">Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="18019-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
### <a name="creating-the-client-certificate"></a><span data-ttu-id="18019-142">Tworzenie certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="18019-142">Creating the Client Certificate</span></span>  
 <span data-ttu-id="18019-143">Następujące wiersze z pliku wsadowego pliku Setup.bat Utwórz certyfikat klienta, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="18019-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="18019-144">`%CLIENT_NAME%` Zmienna określa podmiot certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="18019-145">W przykładzie użyto "client.com" w nazwie podmiotu.</span><span class="sxs-lookup"><span data-stu-id="18019-145">This sample uses "client.com" as the subject name.</span></span>  
  
 <span data-ttu-id="18019-146">Certyfikat jest przechowywany w magazynie My (osobistych) w obszarze `CurrentUser` lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="18019-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="18019-147">Instalowanie certyfikatu klienta do magazynu zaufanego serwera</span><span class="sxs-lookup"><span data-stu-id="18019-147">Installing the Client Certificate into the Server's Trusted Store</span></span>  
 <span data-ttu-id="18019-148">Następujący wiersz w pliku wsadowym pliku Setup.bat kopiuje certyfikat klienta w magazynie zaufanych osób serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="18019-149">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="18019-150">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="18019-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a><span data-ttu-id="18019-151">Utworzenie certyfikatu serwera</span><span class="sxs-lookup"><span data-stu-id="18019-151">Creating the Server Certificate</span></span>  
 <span data-ttu-id="18019-152">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="18019-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="18019-153">`%SERVER_NAME%` Zmiennej określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="18019-154">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="18019-155">Domyślnie ten plik wsadowy jest localhost.</span><span class="sxs-lookup"><span data-stu-id="18019-155">The default in this batch file is localhost.</span></span>  
  
 <span data-ttu-id="18019-156">Certyfikat jest przechowywany w magazynie LocalMachine lokalizacji w mojej (osobiste).</span><span class="sxs-lookup"><span data-stu-id="18019-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="18019-157">Certyfikat jest przechowywany w magazynie LocalMachine usług hostowanych przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="18019-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="18019-158">Hostowanie Samoobsługowe usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu serwera w magazynie CurrentUser lokalizacji, zastępując ciąg LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="18019-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="18019-159">Instalowanie certyfikatu serwera do zaufanego magazynu certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="18019-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>  
 <span data-ttu-id="18019-160">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="18019-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="18019-161">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="18019-162">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="18019-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="18019-163">Włączanie dostępu do klucza prywatnego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="18019-163">Enabling Access to the Certificate's Private Key</span></span>  
 <span data-ttu-id="18019-164">Aby włączyć dostęp do klucza prywatnego certyfikatu usługi hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dostępu do klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="18019-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="18019-165">Jest to osiągane przez ostatnich kroków w skrypcie pliku Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="18019-165">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18019-166">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="18019-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="18019-167">Pamiętaj, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18019-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="18019-168">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18019-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="18019-169">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="18019-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="18019-170">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="18019-170">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="18019-171">Uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="18019-171">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="18019-172">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="18019-172">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18019-173">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="18019-173">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="18019-174">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="18019-174">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="18019-175">Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu próbki.</span><span class="sxs-lookup"><span data-stu-id="18019-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="18019-176">Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="18019-176">Other security samples use the same certificates.</span></span>  
  
2.  <span data-ttu-id="18019-177">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="18019-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="18019-178">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-178">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="18019-179">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="18019-179">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="18019-180">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="18019-180">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="18019-181">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-181">Create a directory on the service machine.</span></span> <span data-ttu-id="18019-182">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia zarządzania usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="18019-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="18019-183">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="18019-184">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="18019-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="18019-185">Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportClientCert.bat maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="18019-186">Utwórz katalog na komputerze klienckim na potrzeby plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="18019-187">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="18019-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="18019-188">Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="18019-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="18019-189">Na serwerze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="18019-189">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="18019-190">Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z nazwą domeny pełni kwalifikowanymi maszyny i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="18019-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="18019-191">Edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="18019-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7.  <span data-ttu-id="18019-192">Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="18019-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="18019-193">Na komputerze klienckim, uruchom `setup.bat client` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="18019-193">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="18019-194">Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="18019-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="18019-195">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="18019-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="18019-196">W tym celu zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="18019-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="18019-197">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="18019-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="18019-198">Na komputerze klienckim należy uruchomić ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="18019-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="18019-199">Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="18019-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="18019-200">Na serwerze, uruchom ImportClientCert.bat to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="18019-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="18019-201">Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="18019-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="18019-202">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="18019-202">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="18019-203">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="18019-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="18019-204">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="18019-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18019-205">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania na komputerach w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="18019-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="18019-206">Jeśli uruchomiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="18019-206">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="18019-207">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="18019-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18019-208">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18019-208">See Also</span></span>
