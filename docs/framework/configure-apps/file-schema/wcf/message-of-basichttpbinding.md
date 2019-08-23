---
title: <message> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 320aca16bde9fc27aa35cad27286d402745e4710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931572"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="b2183-102">\<> komunikatu > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b2183-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="b2183-103">Definiuje ustawienia zabezpieczeń [ \<](basichttpbinding.md)na poziomie wiadomości BasicHttpBinding >.</span><span class="sxs-lookup"><span data-stu-id="b2183-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="b2183-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2183-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2183-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="b2183-105">\<bindings></span></span>  
<span data-ttu-id="b2183-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b2183-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="b2183-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b2183-107">\<binding></span></span>  
<span data-ttu-id="b2183-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b2183-108">\<security></span></span>  
<span data-ttu-id="b2183-109">\<message></span><span class="sxs-lookup"><span data-stu-id="b2183-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2183-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2183-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2183-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b2183-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2183-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b2183-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2183-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b2183-113">Attributes</span></span>  
  
|<span data-ttu-id="b2183-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b2183-114">Attribute</span></span>|<span data-ttu-id="b2183-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b2183-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2183-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="b2183-116">algorithmSuite</span></span>|<span data-ttu-id="b2183-117">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="b2183-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="b2183-118">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy.</span><span class="sxs-lookup"><span data-stu-id="b2183-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="b2183-119">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="b2183-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="b2183-120">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="b2183-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="b2183-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b2183-121">clientCredentialType</span></span>|<span data-ttu-id="b2183-122">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikatach.</span><span class="sxs-lookup"><span data-stu-id="b2183-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="b2183-123">Wartość domyślna to `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b2183-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b2183-124">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="b2183-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b2183-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="b2183-125">Value</span></span>|<span data-ttu-id="b2183-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b2183-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2183-127">UserName</span><span class="sxs-lookup"><span data-stu-id="b2183-127">UserName</span></span>|<span data-ttu-id="b2183-128">-Wymaga uwierzytelnienia klienta na serwerze przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b2183-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="b2183-129">To poświadczenie należy określić przy użyciu [ \<> ClientCredentials](clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b2183-129">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="b2183-130">— Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu haseł i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b2183-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="b2183-131">W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b2183-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="b2183-132">W przypadku `basicHttpBinding`programu wymagane jest skonfigurowanie kanału SSL.</span><span class="sxs-lookup"><span data-stu-id="b2183-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="b2183-133">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="b2183-133">Certificate</span></span>|<span data-ttu-id="b2183-134">Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b2183-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="b2183-135">Poświadczenia klienta w tym przypadku należy określić przy użyciu funkcji [ \<ClientCredentials](clientcredentials.md) [ \<> i ClientCertificate >](clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b2183-135">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="b2183-136">Ponadto w przypadku korzystania z trybu zabezpieczeń wiadomości klient musi być zainicjowany przy użyciu certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="b2183-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="b2183-137">Poświadczenia usługi w tym przypadku należy określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` zachowania elementu, a [ \<](servicecertificate-of-servicecredentials.md)także określić certyfikat usługi przy użyciu > serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="b2183-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2183-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b2183-138">Child Elements</span></span>  
 <span data-ttu-id="b2183-139">Brak</span><span class="sxs-lookup"><span data-stu-id="b2183-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2183-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b2183-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b2183-141">Element</span><span class="sxs-lookup"><span data-stu-id="b2183-141">Element</span></span>|<span data-ttu-id="b2183-142">Opis</span><span class="sxs-lookup"><span data-stu-id="b2183-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2183-143">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b2183-143">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="b2183-144">Definiuje możliwości zabezpieczeń dla [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b2183-144">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2183-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2183-145">Example</span></span>  
 <span data-ttu-id="b2183-146">Ten przykład ilustruje sposób implementacji aplikacji, która korzysta z basicHttpBinding i zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b2183-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="b2183-147">W poniższym przykładzie konfiguracji dla usługi definicja punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="b2183-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="b2183-148">Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w `behaviors` sekcji pliku konfiguracji `serviceCredentials` w obszarze elementu.</span><span class="sxs-lookup"><span data-stu-id="b2183-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="b2183-149">Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również `behaviors` ustawiany w sekcji `clientCertificate` w obszarze elementu.</span><span class="sxs-lookup"><span data-stu-id="b2183-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="b2183-150">W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="b2183-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
    <!-- This configuration defines the SecurityMode as Message and
         the clientCredentialType as Certificate. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
               is in the user's Trusted People store, then it will be trusted without performing a
               validation of the certificate's issuer chain. This setting is used here for convenience so that the
               sample can be run without having to have certificates issued by a certification authority (CA).
               This setting is less secure than the default, ChainTrust. The security implications of this
               setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="b2183-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2183-151">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="b2183-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="b2183-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2183-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b2183-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2183-154">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b2183-154">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2183-155">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="b2183-155">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b2183-156">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b2183-156">\<binding></span></span>](../../../misc/binding.md)
