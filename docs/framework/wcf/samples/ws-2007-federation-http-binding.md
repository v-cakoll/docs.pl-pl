---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183186"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="cad0b-102">Powiązanie HTTP w standardzie WS 2007 Federation</span><span class="sxs-lookup"><span data-stu-id="cad0b-102">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="cad0b-103">W tym przykładzie <xref:System.ServiceModel.WS2007FederationHttpBinding>pokazano użycie , standardowe powiązanie, które można użyć do tworzenia scenariuszy federacyjne, które obsługują wersję 1.3 specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="cad0b-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="cad0b-104">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cad0b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="cad0b-105">Przykład składa się z programu klienckiego opartego na konsoli (*Client.exe*), programu usługi tokenu zabezpieczającego opartego na konsoli *(Securitytokenservice.exe)* i programu usługi opartego na konsoli (*Service.exe*).</span><span class="sxs-lookup"><span data-stu-id="cad0b-105">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="cad0b-106">Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie/odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="cad0b-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="cad0b-107">Kontrakt jest definiowany `ICalculator` przez interfejs, który`Add`udostępnia `Subtract` `Multiply`operacje `Divide`matematyczne ( , , , i ).</span><span class="sxs-lookup"><span data-stu-id="cad0b-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="cad0b-108">Klient uzyskuje token zabezpieczający z usługi tokenu zabezpieczającego (STS) i sprawia, że synchroniczne żądania do usługi dla danej operacji matematycznej.</span><span class="sxs-lookup"><span data-stu-id="cad0b-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="cad0b-109">Następnie usługa odpowiada z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="cad0b-109">The service then replies with the result.</span></span> <span data-ttu-id="cad0b-110">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="cad0b-110">Client activity is visible in the console window.</span></span>

<span data-ttu-id="cad0b-111">Próbka udostępnia `ICalculator` kontrakt przy `ws2007FederationHttpBinding` użyciu elementu.</span><span class="sxs-lookup"><span data-stu-id="cad0b-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="cad0b-112">Konfiguracja tego powiązania na kliencie jest pokazana w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cad0b-112">The configuration of this binding on the client is shown in the following code:</span></span>

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

<span data-ttu-id="cad0b-113">W [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` wartość określa, który tryb zabezpieczeń ma być używany.</span><span class="sxs-lookup"><span data-stu-id="cad0b-113">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="cad0b-114">W tym `message` przykładzie jest używany zabezpieczeń, dlatego [ \<komunikat>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cad0b-114">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="cad0b-115">[ \<Wystawca>](../../configure-apps/file-schema/wcf/issuer.md) element wewnątrz [ \<komunikatu>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i powiązanie dla STS, który wystawia token zabezpieczający do klienta, dzięki czemu klient może uwierzytelnić się w `ICalculator` usłudze.</span><span class="sxs-lookup"><span data-stu-id="cad0b-115">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="cad0b-116">Konfiguracja tego powiązania w usłudze jest wyświetlana w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cad0b-116">The configuration of this binding on the service is shown in the following code:</span></span>

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

<span data-ttu-id="cad0b-117">W [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` wartość określa, który tryb zabezpieczeń ma być używany.</span><span class="sxs-lookup"><span data-stu-id="cad0b-117">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="cad0b-118">W tym `message` przykładzie jest używany zabezpieczeń, dlatego [ \<komunikat>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określony wewnątrz [ \<>zabezpieczeń ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cad0b-118">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="cad0b-119">[ \<IssuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element `ws2007FederationHttpBinding` wewnątrz [ \<komunikatu>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) określa adres i tożsamość punktu końcowego, który może służyć do pobierania metadanych dla STS.</span><span class="sxs-lookup"><span data-stu-id="cad0b-119">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="cad0b-120">Zachowanie usługi jest pokazane w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="cad0b-120">The behavior for the service is shown in the following code:</span></span>

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
  
<span data-ttu-id="cad0b-121">[ \<IssuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określenie ograniczeń tokenów, które umożliwia klientom prezentowanie podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="cad0b-121">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="cad0b-122">Ta konfiguracja określa, że tokeny podpisane certyfikatem, którego nazwa podmiotu jest CN = STS są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="cad0b-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="cad0b-123">STS udostępnia pojedynczy punkt końcowy <xref:System.ServiceModel.WS2007HttpBinding>przy użyciu standardowego .</span><span class="sxs-lookup"><span data-stu-id="cad0b-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="cad0b-124">Usługa odpowiada na żądania od klientów tokenów.</span><span class="sxs-lookup"><span data-stu-id="cad0b-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="cad0b-125">Jeśli klient jest uwierzytelniony przy użyciu konta systemu Windows, usługa wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="cad0b-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="cad0b-126">W ramach tworzenia tokenu STS podpisuje token przy użyciu klucza prywatnego skojarzonego z certyfikatem CN=STS.</span><span class="sxs-lookup"><span data-stu-id="cad0b-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="cad0b-127">Ponadto tworzy klucz symetryczny i szyfruje go przy użyciu klucza publicznego skojarzonego z certyfikatem CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="cad0b-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="cad0b-128">W powrocie tokenu do klienta STS zwraca również klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="cad0b-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="cad0b-129">Klient przedstawia wystawiony token do `ICalculator` usługi i udowadnia, że zna klucz symetryczny, podpisując wiadomość za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="cad0b-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="cad0b-130">Po uruchomieniu przykładu żądanie tokenu zabezpieczającego jest wyświetlane w oknie konsoli STS.</span><span class="sxs-lookup"><span data-stu-id="cad0b-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="cad0b-131">Żądania i odpowiedzi operacji są wyświetlane w oknach konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="cad0b-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="cad0b-132">Naciśnij klawisz ENTER w dowolnym okienku konsoli, aby wyłączyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="cad0b-132">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="cad0b-133">Plik *Setup.bat* dołączony do tego przykładu umożliwia skonfigurowanie serwera i systemu STS z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="cad0b-133">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="cad0b-134">Plik wsadowy tworzy dwa certyfikaty w magazynie certyfikatów LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="cad0b-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="cad0b-135">Pierwszy certyfikat ma nazwę podmiotu CN = STS i jest używany przez STS do podpisywania tokenów zabezpieczających, które wystawia klientowi.</span><span class="sxs-lookup"><span data-stu-id="cad0b-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="cad0b-136">Drugi certyfikat ma nazwę podmiotu CN = localhost i jest używany przez STS do szyfrowania klucza w sposób, który usługa może odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="cad0b-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cad0b-137">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="cad0b-137">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="cad0b-138">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cad0b-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="cad0b-139">Otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat, aby utworzyć wymagane certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="cad0b-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="cad0b-140">Ten plik wsadowy używa *programów Certmgr.exe* i Makecert.exe, które są dystrybuowane za pomocą programu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="cad0b-140">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="cad0b-141">Jednak należy uruchomić *Setup.bat* z poziomu wiersza polecenia programu Visual Studio, aby włączyć skrypt, aby znaleźć te narzędzia.</span><span class="sxs-lookup"><span data-stu-id="cad0b-141">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="cad0b-142">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cad0b-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="cad0b-143">Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, postępuj zgodnie z instrukcjami w [przypadku uruchamiania przykładów fundacji komunikacji systemu Windows](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cad0b-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="cad0b-144">Jeśli używasz systemu Windows Vista, należy uruchomić *program Service.exe*, *Client.exe*i *SecurityTokenService.exe* z podwyższonymi uprawnieniami (kliknij prawym przyciskiem myszy pliki, a następnie kliknij polecenie **Uruchom jako administrator**).</span><span class="sxs-lookup"><span data-stu-id="cad0b-144">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cad0b-145">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cad0b-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cad0b-146">Przed kontynuowaniem sprawdź następujący (domyślny) katalog:</span><span class="sxs-lookup"><span data-stu-id="cad0b-146">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cad0b-147">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="cad0b-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cad0b-148">Ten przykład znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cad0b-148">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
