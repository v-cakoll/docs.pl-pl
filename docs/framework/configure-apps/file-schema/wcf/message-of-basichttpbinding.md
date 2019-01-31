---
title: <message> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: b954ec770ca0c59dec0b25634ccbc59f086d1a99
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274459"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="cf0de-102">\<komunikat > z \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cf0de-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="cf0de-103">Definiuje ustawienia zabezpieczeń na poziomie komunikatu z [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cf0de-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="cf0de-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf0de-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf0de-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="cf0de-105">\<bindings></span></span>  
<span data-ttu-id="cf0de-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cf0de-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="cf0de-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="cf0de-107">\<binding></span></span>  
<span data-ttu-id="cf0de-108">\<security></span><span class="sxs-lookup"><span data-stu-id="cf0de-108">\<security></span></span>  
<span data-ttu-id="cf0de-109">\<message></span><span class="sxs-lookup"><span data-stu-id="cf0de-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf0de-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf0de-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf0de-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf0de-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf0de-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf0de-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf0de-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf0de-113">Attributes</span></span>  
  
|<span data-ttu-id="cf0de-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf0de-114">Attribute</span></span>|<span data-ttu-id="cf0de-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cf0de-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf0de-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="cf0de-116">algorithmSuite</span></span>|<span data-ttu-id="cf0de-117">Ustawia komunikat algorytmów szyfrowania i zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="cf0de-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="cf0de-118">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, która określa te algorytmy i rozmiary kluczy.</span><span class="sxs-lookup"><span data-stu-id="cf0de-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="cf0de-119">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczenia (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="cf0de-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="cf0de-120">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="cf0de-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="cf0de-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="cf0de-121">clientCredentialType</span></span>|<span data-ttu-id="cf0de-122">Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikat.</span><span class="sxs-lookup"><span data-stu-id="cf0de-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="cf0de-123">Wartość domyślna to `UserName`.</span><span class="sxs-lookup"><span data-stu-id="cf0de-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="cf0de-124">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="cf0de-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="cf0de-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="cf0de-125">Value</span></span>|<span data-ttu-id="cf0de-126">Opis</span><span class="sxs-lookup"><span data-stu-id="cf0de-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf0de-127">UserName</span><span class="sxs-lookup"><span data-stu-id="cf0de-127">UserName</span></span>|<span data-ttu-id="cf0de-128">— Wymagają uwierzytelnienia klienta do serwera przy użyciu poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="cf0de-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="cf0de-129">To poświadczenie musi być określona za pomocą [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="cf0de-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="cf0de-130">-WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu haseł i za pomocą takich klucze dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cf0de-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="cf0de-131">W związku z tym usługi WCF wymusza, czy transport zostać zabezpieczony, korzystając z poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="cf0de-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="cf0de-132">Aby uzyskać `basicHttpBinding`, wymaga to skonfigurowanie kanału SSL.</span><span class="sxs-lookup"><span data-stu-id="cf0de-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="cf0de-133">Certyfikat</span><span class="sxs-lookup"><span data-stu-id="cf0de-133">Certificate</span></span>|<span data-ttu-id="cf0de-134">Wymaga uwierzytelnienia klienta z serwerem przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="cf0de-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="cf0de-135">Poświadczeń klienta w tym przypadku musi być określona za pomocą [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) i [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="cf0de-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="cf0de-136">Ponadto po używających trybu zabezpieczenia wiadomości, klienta musi być obsługiwana za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="cf0de-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="cf0de-137">Poświadczenia usługi w tym przypadku należy także określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` element zachowania i określając usługę certyfikatu, przy użyciu [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="cf0de-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf0de-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf0de-138">Child Elements</span></span>  
 <span data-ttu-id="cf0de-139">Brak</span><span class="sxs-lookup"><span data-stu-id="cf0de-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf0de-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf0de-140">Parent Elements</span></span>  
  
|<span data-ttu-id="cf0de-141">Element</span><span class="sxs-lookup"><span data-stu-id="cf0de-141">Element</span></span>|<span data-ttu-id="cf0de-142">Opis</span><span class="sxs-lookup"><span data-stu-id="cf0de-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf0de-143">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="cf0de-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="cf0de-144">Definiuje funkcje bezpieczeństwa umożliwiające [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cf0de-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cf0de-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf0de-145">Example</span></span>  
 <span data-ttu-id="cf0de-146">Ten przykład demonstruje sposób implementacji aplikacji, która używa zabezpieczenia basicHttpBinding i komunikatu.</span><span class="sxs-lookup"><span data-stu-id="cf0de-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="cf0de-147">W poniższym przykładzie konfiguracji dla usługi określa basicHttpBinding definicji punktu końcowego, a odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="cf0de-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="cf0de-148">Certyfikat używany przez usługę do samodzielnego uwierzytelnienia klienta znajduje się w `behaviors` części pliku konfiguracyjnego obszarze `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="cf0de-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="cf0de-149">Tryb weryfikacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia usługi jest również ustawiona `behaviors` sekcji `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="cf0de-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="cf0de-150">Szczegóły tego samego powiązania i zabezpieczenia są określone w pliku konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="cf0de-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf0de-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf0de-151">See also</span></span>
- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="cf0de-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="cf0de-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cf0de-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="cf0de-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="cf0de-154">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="cf0de-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cf0de-155">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="cf0de-155">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cf0de-156">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="cf0de-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
