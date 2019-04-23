---
title: Powiązanie HTTP w standardzie WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 550a88552658864e3eedb70463e676ad6f9a2511
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769531"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="162f9-102">Powiązanie HTTP w standardzie WS 2007 Federation</span><span class="sxs-lookup"><span data-stu-id="162f9-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="162f9-103">Ten przykład demonstruje użycie <xref:System.ServiceModel.WS2007FederationHttpBinding>, standard, powiązanie, której można tworzyć scenariuszach obejmujących Federację obsługi wersji 1.3 specyfikację protokołu WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="162f9-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="162f9-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="162f9-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="162f9-105">Przykład składa się z programu klienckiego z konsoli (Client.exe), program usługi tokenu zabezpieczeń opartych na konsoli (Securitytokenservice.exe) i usługa oparta na konsoli programu (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="162f9-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="162f9-106">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji żądanie/nietypizowana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="162f9-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="162f9-107">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (`Add`, `Subtract`, `Multiply`, i `Divide`).</span><span class="sxs-lookup"><span data-stu-id="162f9-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="162f9-108">Klient uzyskuje token zabezpieczający z Usługa tokenu zabezpieczającego (STS) i sprawia, że do usługi w przypadku operacji matematycznych danego żądań synchronicznych.</span><span class="sxs-lookup"><span data-stu-id="162f9-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="162f9-109">Usługa następnie odpowiedzi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="162f9-109">The service then replies with the result.</span></span> <span data-ttu-id="162f9-110">Aktywność klienta jest widoczna w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="162f9-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="162f9-111">Przykład sprawia, że `ICalculator` dostępne za pośrednictwem umowy `ws2007FederationHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="162f9-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="162f9-112">Konfiguracji tego powiązania na kliencie jest wyświetlany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="162f9-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="162f9-113">Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość Określa tryb zabezpieczeń, którym powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="162f9-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="162f9-114">W tym przykładzie `message` zabezpieczeń jest używany, co jest dlaczego [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określona wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="162f9-115">[ \<Issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element wewnątrz [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i powiązanie dla usługi STS, która wystawia token zabezpieczający do klienta, tak aby klient może uwierzytelnianie `ICalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="162f9-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="162f9-116">Konfiguracji tego powiązania usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="162f9-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="162f9-117">Na [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` wartość Określa tryb zabezpieczeń, którym powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="162f9-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="162f9-118">W tym przykładzie `message` zabezpieczeń jest używany, co jest dlaczego [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) jest określona wewnątrz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="162f9-119">[ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementu `ws2007FederationHttpBinding` wewnątrz [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) Określa adres i tożsamości dla punktu końcowego, który może służyć do pobrania metadane dla usługi STS.</span><span class="sxs-lookup"><span data-stu-id="162f9-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="162f9-120">Zachowanie usługi przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="162f9-120">The behavior for the service is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="162f9-121">[ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> umożliwia usłudze określanie ograniczeń na tokeny zezwala na klientów przedstawić podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="162f9-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="162f9-122">Ta konfiguracja Określa, że tokeny podpisane przy użyciu certyfikatu, którego nazwa podmiotu jest CN = usługi STS są akceptowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="162f9-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="162f9-123">Usługi STS sprawia, że jeden punkt końcowy jest dostępny za pomocą standardowych <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="162f9-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="162f9-124">Usługa odpowiada na żądania klientów dotyczące tokenów.</span><span class="sxs-lookup"><span data-stu-id="162f9-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="162f9-125">Jeśli klient jest uwierzytelniany przy użyciu konta Windows, usługę wystawia token, który zawiera nazwę użytkownika klienta jako oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="162f9-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="162f9-126">Jako część tworzenia tokenu usługi STS podpisuje token przy użyciu klucza prywatnego skojarzonego z CN = certyfikatu usługi STS.</span><span class="sxs-lookup"><span data-stu-id="162f9-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="162f9-127">Ponadto tworzy klucz symetryczny i szyfruje za pomocą klucza publicznego skojarzonego z CN = localhost certyfikat.</span><span class="sxs-lookup"><span data-stu-id="162f9-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="162f9-128">Zwracany token do klienta, w STS zwraca klucz symetryczny.</span><span class="sxs-lookup"><span data-stu-id="162f9-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="162f9-129">Klient przedstawia wystawiony token `ICalculator` usług i upoważnienie wie klucz symetryczny, tworząc wiadomości za pomocą tego klucza.</span><span class="sxs-lookup"><span data-stu-id="162f9-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="162f9-130">Po uruchomieniu przykładu, żądania tokenu zabezpieczeń są wyświetlane w oknie konsoli usługi STS.</span><span class="sxs-lookup"><span data-stu-id="162f9-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="162f9-131">Operacja żądania i odpowiedzi są wyświetlane w oknach konsoli klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="162f9-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="162f9-132">Naciśnij klawisz ENTER w żadnym z okna konsoli do zamykania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="162f9-132">Press ENTER in any of the console windows to shut down the application.</span></span>  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="162f9-133">Plik Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera i usługę STS przy użyciu odpowiednich certyfikatów do uruchamiania aplikacji samodzielnie hostowanej.</span><span class="sxs-lookup"><span data-stu-id="162f9-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="162f9-134">Plik wsadowy tworzy dwa certyfikaty w magazynie LocalMachine/TrustedPeople certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="162f9-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="162f9-135">Pierwszy certyfikat ma nazwę podmiotu, CN = usługi STS i jest używany przez usługę STS do podpisywania tokenów zabezpieczających, które generuje dla klienta.</span><span class="sxs-lookup"><span data-stu-id="162f9-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="162f9-136">Drugi certyfikat ma nazwę podmiotu, CN = localhost i jest używany przez usługę STS do szyfrowania klucza w taki sposób, że usługa może odszyfrować.</span><span class="sxs-lookup"><span data-stu-id="162f9-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="162f9-137">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="162f9-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="162f9-138">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="162f9-139">Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom plik Setup.bat jest, aby utworzyć wymagane certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="162f9-139">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="162f9-140">Ten plik wsadowy używa Certmgr.exe i Makecert.exe, które są dystrybuowane za pomocą zestawu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="162f9-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="162f9-141">Należy jednak uruchomić Setup.bat z, w wierszu polecenia programu Visual Studio, aby włączyć skryptów znaleźć te narzędzia.</span><span class="sxs-lookup"><span data-stu-id="162f9-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1. <span data-ttu-id="162f9-142">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="162f9-143">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="162f9-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="162f9-144">Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić Service.exe, Client.exe, i SecurityTokenService.exe z podwyższonym poziomem uprawnień (kliknij prawym przyciskiem myszy pliki, a następnie kliknij przycisk **Uruchom jako administrator**).</span><span class="sxs-lookup"><span data-stu-id="162f9-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="162f9-145">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="162f9-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="162f9-146">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="162f9-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="162f9-147">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="162f9-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="162f9-148">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="162f9-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
