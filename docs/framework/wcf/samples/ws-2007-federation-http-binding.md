---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 74f21494c08f33a61eb1e1b0a102638cff59a970
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960190"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="ca0b1-102">Powiązanie HTTP w standardzie WS 2007 Federation</span><span class="sxs-lookup"><span data-stu-id="ca0b1-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="ca0b1-103">Ten przykład ilustruje użycie <xref:System.ServiceModel.WS2007FederationHttpBinding>, standardowego powiązania, którego można użyć do kompilowania scenariuszy federacyjnych, które obsługują wersję 1,3 specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="ca0b1-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ca0b1-105">Przykład składa się z programu klienckiego opartego na konsoli (*Client. exe*), programu usługi tokenu zabezpieczającego opartego na konsoli (*SecurityTokenService. exe*) i programu usług opartego na konsoli (*Service. exe*).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="ca0b1-106">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="ca0b1-107">Umowa jest definiowana przez interfejs `ICalculator`, który uwidacznia operacje matematyczne (`Add`, `Subtract`, `Multiply`i `Divide`).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="ca0b1-108">Klient uzyskuje token zabezpieczający z usługi tokenu zabezpieczającego (STS) i wysyła synchroniczne żądania do usługi dla danej operacji matematycznej.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="ca0b1-109">Następnie usługa wysyła odpowiedzi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-109">The service then replies with the result.</span></span> <span data-ttu-id="ca0b1-110">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="ca0b1-111">Przykład umożliwia udostępnienie `ICalculator` kontraktu przy użyciu elementu `ws2007FederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="ca0b1-112">Konfiguracja tego powiązania na kliencie jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ca0b1-112">The configuration of this binding on the client is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="ca0b1-113">Na [> zabezpieczeń\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)wartość `security` określa tryb zabezpieczeń, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="ca0b1-114">W tym przykładzie użyto `message` zabezpieczeń, co oznacza, że [> komunikat\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) został określony w [\<> zabezpieczeń](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="ca0b1-115">[\<wystawca >](../../configure-apps/file-schema/wcf/issuer.md) element wewnątrz [wiadomości\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i powiązanie dla usługi STS, która wystawia token zabezpieczający dla klienta, aby klient mógł uwierzytelnić się w usłudze `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="ca0b1-116">Konfiguracja tego powiązania w usłudze jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ca0b1-116">The configuration of this binding on the service is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="ca0b1-117">Na [> zabezpieczeń\<](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)wartość `security` określa tryb zabezpieczeń, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="ca0b1-118">W tym przykładzie użyto `message` zabezpieczeń, co oznacza, że [> komunikat\<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) został określony w [\<> zabezpieczeń](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="ca0b1-119">[\<issuerMetadata >](../../configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` w [\<komunikat >](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i tożsamość punktu końcowego, którego można użyć do pobrania metadanych dla usługi STS.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="ca0b1-120">Zachowanie usługi jest pokazane w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ca0b1-120">The behavior for the service is shown in the following code:</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
<span data-ttu-id="ca0b1-121">[\<issuedTokenAuthentication >](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określenie ograniczeń dotyczących tokenów, które umożliwiają klientom prezentowanie podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="ca0b1-122">Ta konfiguracja określa, że tokeny podpisane przez certyfikat, którego nazwa podmiotu to CN = STS, są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="ca0b1-123">Usługa STS udostępnia jeden punkt końcowy przy użyciu standardowej <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="ca0b1-124">Usługa odpowiada na żądania od klientów tokenów.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="ca0b1-125">Jeśli klient jest uwierzytelniany przy użyciu konta systemu Windows, usługa wystawia token, który zawiera nazwę użytkownika klienta jako rolę żądania.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="ca0b1-126">W ramach tworzenia tokenu usługa STS podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem usługi STS.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="ca0b1-127">Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN = localhost.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="ca0b1-128">W przypadku zwracania tokenu do klienta usługa STS zwraca również klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="ca0b1-129">Klient przedstawia wystawiony token usłudze `ICalculator` i potwierdza, że zna klucz symetryczny, podpisując komunikat przy użyciu tego klucza.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="ca0b1-130">Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli STS.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="ca0b1-131">Żądania i odpowiedzi operacji są wyświetlane w oknach konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="ca0b1-132">Naciśnij klawisz ENTER w dowolnym systemie Windows Console, aby zamknąć aplikację.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="ca0b1-133">Plik *Setup. bat* dołączony do tego przykładu umożliwia skonfigurowanie serwera i usługi STS z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="ca0b1-134">Plik wsadowy tworzy dwa certyfikaty w magazynie certyfikatów LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="ca0b1-135">Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez usługę STS do podpisywania tokenów zabezpieczających, które wystąpiły dla klienta.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="ca0b1-136">Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez usługę STS do szyfrowania klucza w sposób, w jaki usługa może odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca0b1-137">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="ca0b1-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="ca0b1-138">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ca0b1-139">Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom plik Setup. bat, aby utworzyć wymagane certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="ca0b1-140">Ten plik wsadowy używa *certmgr. exe* i Makecert. exe, które są dystrybuowane z Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="ca0b1-141">Należy jednak uruchomić *Setup. bat* z poziomu wiersza polecenia programu Visual Studio, aby umożliwić skryptowi znalezienie tych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="ca0b1-142">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="ca0b1-143">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="ca0b1-144">W przypadku korzystania z systemu Windows Vista należy uruchomić program *Service. exe*, *Client. exe*i *SecurityTokenService. exe* z podwyższonym poziomem uprawnień (kliknij pliki prawym przyciskiem myszy, a następnie kliknij polecenie **Uruchom jako administrator**).</span><span class="sxs-lookup"><span data-stu-id="ca0b1-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca0b1-145">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ca0b1-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ca0b1-146">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny):</span><span class="sxs-lookup"><span data-stu-id="ca0b1-146">Check for the following (default) directory before continuing:</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> <span data-ttu-id="ca0b1-147">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ca0b1-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca0b1-148">Ten przykład znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ca0b1-148">This sample is located in the following directory:</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
