---
title: '&lt;message&gt; w &lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: be96306b61b3eb6bfb8d3305ccbb05bb3ec4549d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-of-ltnethttpbindinggt"></a><span data-ttu-id="a643d-102">&lt;message&gt; w &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a643d-102">&lt;message&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="a643d-103">Definiuje ustawienia zabezpieczeń na poziomie komunikatu z [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a643d-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="a643d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a643d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a643d-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a643d-105">\<bindings></span></span>  
<span data-ttu-id="a643d-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a643d-106">\<netHttpBinding></span></span>  
<span data-ttu-id="a643d-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a643d-107">\<binding></span></span>  
<span data-ttu-id="a643d-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a643d-108">\<security></span></span>  
<span data-ttu-id="a643d-109">\<message></span><span class="sxs-lookup"><span data-stu-id="a643d-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a643d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a643d-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a643d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a643d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a643d-112">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a643d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a643d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a643d-113">Attributes</span></span>  
  
|<span data-ttu-id="a643d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a643d-114">Attribute</span></span>|<span data-ttu-id="a643d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a643d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a643d-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="a643d-116">algorithmSuite</span></span>|<span data-ttu-id="a643d-117">Ustawia komunikat algorytmów szyfrowania i zawijania klucza.</span><span class="sxs-lookup"><span data-stu-id="a643d-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="a643d-118">Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy.</span><span class="sxs-lookup"><span data-stu-id="a643d-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="a643d-119">Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="a643d-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="a643d-120">Wartość domyślna to `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="a643d-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="a643d-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a643d-121">clientCredentialType</span></span>|<span data-ttu-id="a643d-122">Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta za pomocą zabezpieczenia na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a643d-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="a643d-123">Wartość domyślna to `UserName`.</span><span class="sxs-lookup"><span data-stu-id="a643d-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a643d-124">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="a643d-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a643d-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="a643d-125">Value</span></span>|<span data-ttu-id="a643d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a643d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a643d-127">UserName</span><span class="sxs-lookup"><span data-stu-id="a643d-127">UserName</span></span>|<span data-ttu-id="a643d-128">-Wymaga uwierzytelnienia klienta do serwera o poświadczenie nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a643d-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="a643d-129">To poświadczenie musi być określona za pomocą <`clientCredentials`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a643d-129">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="a643d-130">-WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a643d-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="a643d-131">W związku z tym WCF wymusza, czy transport można zabezpieczyć, korzystając z poświadczeń UserName.</span><span class="sxs-lookup"><span data-stu-id="a643d-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="a643d-132">Aby uzyskać `basicHttpBinding`, wymagane jest skonfigurowanie kanału SSL.</span><span class="sxs-lookup"><span data-stu-id="a643d-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="a643d-133">certyfikat</span><span class="sxs-lookup"><span data-stu-id="a643d-133">Certificate</span></span>|<span data-ttu-id="a643d-134">Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="a643d-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="a643d-135">W takim przypadku poświadczeń klienta należy określić przy użyciu <`clientCredentials`> i <`clientCertificate`>.</span><span class="sxs-lookup"><span data-stu-id="a643d-135">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="a643d-136">Ponadto podczas korzystania z trybu zabezpieczeń wiadomości, klient musi obsługiwane za pomocą certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="a643d-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="a643d-137">Poświadczenia usługi w takim przypadku należy określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` element zachowania i określając usługi certyfikatów przy użyciu \<serviceCertificate > elementu serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="a643d-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a643d-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a643d-138">Child Elements</span></span>  
 <span data-ttu-id="a643d-139">Brak</span><span class="sxs-lookup"><span data-stu-id="a643d-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a643d-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a643d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a643d-141">Element</span><span class="sxs-lookup"><span data-stu-id="a643d-141">Element</span></span>|<span data-ttu-id="a643d-142">Opis</span><span class="sxs-lookup"><span data-stu-id="a643d-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a643d-143"><`security`> elementu <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="a643d-143"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="a643d-144">Definiuje funkcje zabezpieczeń dla <`netHttpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a643d-144">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a643d-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a643d-145">Example</span></span>  
 <span data-ttu-id="a643d-146">W tym przykładzie pokazano, jak wdrożyć aplikację, która używa zabezpieczeń basicHttpBinding i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a643d-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="a643d-147">W poniższym przykładzie konfiguracji dla usługi definicji punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="a643d-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="a643d-148">Certyfikat używany przez usługę do samodzielnego uwierzytelnienia klienta znajduje się w `behaviors` sekcji pliku konfiguracji w obszarze `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="a643d-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="a643d-149">Tryb walidacji, która ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia usługi znajduje się również w `behaviors` w obszarze `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="a643d-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="a643d-150">Szczegóły tego samego powiązania i zabezpieczenia są określone w pliku konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="a643d-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a643d-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a643d-151">See Also</span></span>  
 [<span data-ttu-id="a643d-152">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a643d-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a643d-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a643d-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a643d-154">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a643d-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a643d-155">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a643d-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a643d-156">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a643d-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
