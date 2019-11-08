---
title: <message> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738959"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="69fe4-102">\<komunikat > \<protokołu HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="69fe4-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="69fe4-103">Definiuje ustawienia zabezpieczeń na poziomie wiadomości dla [\<protokołu HttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="69fe4-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
<span data-ttu-id="69fe4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="69fe4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69fe4-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="69fe4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="69fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="69fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="69fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protokół HttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="69fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="69fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="69fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="69fe4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="69fe4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="69fe4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<komunikat >**</span><span class="sxs-lookup"><span data-stu-id="69fe4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69fe4-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="69fe4-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69fe4-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69fe4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="69fe4-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69fe4-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69fe4-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69fe4-114">Attributes</span></span>  
  
|<span data-ttu-id="69fe4-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69fe4-115">Attribute</span></span>|<span data-ttu-id="69fe4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="69fe4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69fe4-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="69fe4-117">algorithmSuite</span></span>|<span data-ttu-id="69fe4-118">Ustawia szyfrowanie komunikatów i algorytmy zawijania kluczy.</span><span class="sxs-lookup"><span data-stu-id="69fe4-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="69fe4-119">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy.</span><span class="sxs-lookup"><span data-stu-id="69fe4-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="69fe4-120">Te algorytmy są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="69fe4-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="69fe4-121">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="69fe4-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="69fe4-122">Powiązania ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="69fe4-122">clientCredentialType</span></span>|<span data-ttu-id="69fe4-123">Określa typ poświadczeń, które mają być używane podczas uwierzytelniania klienta przy użyciu zabezpieczeń opartych na komunikatach.</span><span class="sxs-lookup"><span data-stu-id="69fe4-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="69fe4-124">Wartość domyślna to `UserName`.</span><span class="sxs-lookup"><span data-stu-id="69fe4-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="69fe4-125">clientCredentialtype — atrybut</span><span class="sxs-lookup"><span data-stu-id="69fe4-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="69fe4-126">Wartość</span><span class="sxs-lookup"><span data-stu-id="69fe4-126">Value</span></span>|<span data-ttu-id="69fe4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="69fe4-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="69fe4-128">UserName</span><span class="sxs-lookup"><span data-stu-id="69fe4-128">UserName</span></span>|<span data-ttu-id="69fe4-129">-Wymaga uwierzytelnienia klienta na serwerze przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69fe4-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="69fe4-130">To poświadczenie należy określić przy użyciu <`clientCredentials`> elementu.</span><span class="sxs-lookup"><span data-stu-id="69fe4-130">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="69fe4-131">— Usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu haseł i używania tych kluczy do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="69fe4-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="69fe4-132">W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69fe4-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="69fe4-133">W przypadku `basicHttpBinding`wymaga to skonfigurowania kanału SSL.</span><span class="sxs-lookup"><span data-stu-id="69fe4-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="69fe4-134">Certyfikatu</span><span class="sxs-lookup"><span data-stu-id="69fe4-134">Certificate</span></span>|<span data-ttu-id="69fe4-135">Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="69fe4-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="69fe4-136">Poświadczenia klienta w tym przypadku należy określić przy użyciu <`clientCredentials`> i <`clientCertificate`>.</span><span class="sxs-lookup"><span data-stu-id="69fe4-136">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="69fe4-137">Ponadto w przypadku korzystania z trybu zabezpieczeń wiadomości klient musi być zainicjowany przy użyciu certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="69fe4-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="69fe4-138">Poświadczenia usługi w tym przypadku należy określić przy użyciu klasy <xref:System.ServiceModel.Description.ClientCredentials> lub `ClientCredentials`, a także określić certyfikat usługi przy użyciu elementu > \<serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="69fe4-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69fe4-139">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69fe4-139">Child Elements</span></span>  
 <span data-ttu-id="69fe4-140">Brak</span><span class="sxs-lookup"><span data-stu-id="69fe4-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69fe4-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69fe4-141">Parent Elements</span></span>  
  
|<span data-ttu-id="69fe4-142">Element</span><span class="sxs-lookup"><span data-stu-id="69fe4-142">Element</span></span>|<span data-ttu-id="69fe4-143">Opis</span><span class="sxs-lookup"><span data-stu-id="69fe4-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69fe4-144"><`security`> elementu <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="69fe4-144"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="69fe4-145">Definiuje funkcje zabezpieczeń dla <`netHttpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="69fe4-145">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69fe4-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="69fe4-146">Example</span></span>  
 <span data-ttu-id="69fe4-147">Ten przykład ilustruje sposób implementacji aplikacji, która korzysta z basicHttpBinding i zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="69fe4-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="69fe4-148">W poniższym przykładzie konfiguracji dla usługi definicja punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="69fe4-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="69fe4-149">Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w sekcji `behaviors` pliku konfiguracji w obszarze `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="69fe4-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="69fe4-150">Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również ustawiany w sekcji `behaviors` w elemencie `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="69fe4-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="69fe4-151">W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="69fe4-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
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
      <binding name="Binding1" >
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
  
## <a name="see-also"></a><span data-ttu-id="69fe4-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69fe4-152">See also</span></span>

- [<span data-ttu-id="69fe4-153">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="69fe4-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="69fe4-154">Powiązania</span><span class="sxs-lookup"><span data-stu-id="69fe4-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="69fe4-155">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="69fe4-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="69fe4-156">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="69fe4-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="69fe4-157">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="69fe4-157">\<binding></span></span>](bindings.md)
