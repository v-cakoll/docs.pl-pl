---
title: <message> dla <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: bce80d96b1bcec0d580f2de3fe88d5fd6ad0a3b5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400263"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="e2e3b-102">\<> komunikatu > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e2e3b-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="e2e3b-103">Definiuje ustawienia zabezpieczeń [ \<](basichttpbinding.md)na poziomie wiadomości BasicHttpBinding >.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="e2e3b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2e3b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2e3b-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e2e3b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e2e3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e2e3b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e2e3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e2e3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="e2e3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="e2e3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e2e3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e2e3b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="e2e3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> komunikatu**</span><span class="sxs-lookup"><span data-stu-id="e2e3b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e3b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2e3b-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2e3b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e2e3b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e2e3b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2e3b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2e3b-114">Attributes</span></span>  
  
|<span data-ttu-id="e2e3b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e2e3b-115">Attribute</span></span>|<span data-ttu-id="e2e3b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e2e3b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2e3b-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e2e3b-117">algorithmSuite</span></span>|<span data-ttu-id="e2e3b-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e2e3b-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="e2e3b-120">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="e2e3b-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="e2e3b-121">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="e2e3b-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e2e3b-122">clientCredentialType</span></span>|<span data-ttu-id="e2e3b-123">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikatach.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="e2e3b-124">Wartość domyślna to `UserName`.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e2e3b-125">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="e2e3b-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e2e3b-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="e2e3b-126">Value</span></span>|<span data-ttu-id="e2e3b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e2e3b-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2e3b-128">UserName</span><span class="sxs-lookup"><span data-stu-id="e2e3b-128">UserName</span></span>|<span data-ttu-id="e2e3b-129">-Wymaga uwierzytelnienia klienta na serwerze przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="e2e3b-130">To poświadczenie należy określić przy użyciu [ \<> ClientCredentials](clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e2e3b-130">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="e2e3b-131">— Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu haseł i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="e2e3b-132">W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="e2e3b-133">W przypadku `basicHttpBinding`programu wymagane jest skonfigurowanie kanału SSL.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="e2e3b-134">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e2e3b-134">Certificate</span></span>|<span data-ttu-id="e2e3b-135">Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="e2e3b-136">Poświadczenia klienta w tym przypadku należy określić przy użyciu funkcji [ \<ClientCredentials](clientcredentials.md) [ \<> i ClientCertificate >](clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e2e3b-136">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="e2e3b-137">Ponadto w przypadku korzystania z trybu zabezpieczeń wiadomości klient musi być zainicjowany przy użyciu certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="e2e3b-138">Poświadczenia usługi w tym przypadku należy określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` zachowania elementu, a [ \<](servicecertificate-of-servicecredentials.md)także określić certyfikat usługi przy użyciu > serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2e3b-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2e3b-139">Child Elements</span></span>  
 <span data-ttu-id="e2e3b-140">Brak</span><span class="sxs-lookup"><span data-stu-id="e2e3b-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2e3b-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2e3b-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e2e3b-142">Element</span><span class="sxs-lookup"><span data-stu-id="e2e3b-142">Element</span></span>|<span data-ttu-id="e2e3b-143">Opis</span><span class="sxs-lookup"><span data-stu-id="e2e3b-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2e3b-144">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e2e3b-144">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="e2e3b-145">Definiuje możliwości zabezpieczeń dla [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e2e3b-145">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2e3b-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2e3b-146">Example</span></span>  
 <span data-ttu-id="e2e3b-147">Ten przykład ilustruje sposób implementacji aplikacji, która korzysta z basicHttpBinding i zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="e2e3b-148">W poniższym przykładzie konfiguracji dla usługi definicja punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="e2e3b-149">Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w `behaviors` sekcji pliku konfiguracji `serviceCredentials` w obszarze elementu.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="e2e3b-150">Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również `behaviors` ustawiany w sekcji `clientCertificate` w obszarze elementu.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="e2e3b-151">W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="e2e3b-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2e3b-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2e3b-152">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="e2e3b-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="e2e3b-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e2e3b-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e2e3b-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e2e3b-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e2e3b-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e2e3b-156">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e2e3b-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e2e3b-157">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e2e3b-157">\<binding></span></span>](../../../misc/binding.md)
