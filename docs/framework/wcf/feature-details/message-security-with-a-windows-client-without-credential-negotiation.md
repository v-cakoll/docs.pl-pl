---
title: "Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 943e3f32334bbf5746d3730f34371793bbd2754c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="5a8cc-102">Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń</span><span class="sxs-lookup"><span data-stu-id="5a8cc-102">Message Security with a Windows Client without Credential Negotiation</span></span>
<span data-ttu-id="5a8cc-103">Poniżej przedstawiono scenariusz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta i usługi zabezpieczonej przez protokół Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="5a8cc-104">Zarówno usługa, jak i klienta znajdują się w tej samej domenie lub domenach zaufanych.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-104">Both the service and the client are in the same domain or trusted domains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a8cc-105">Różnica między tym scenariuszu i [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) jest, że w tym scenariuszu nie negocjuje poświadczenie usługi z usługą przed wysłaniem wiadomości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="5a8cc-106">Ponadto ponieważ wymaga to protokół Kerberos, ten scenariusz wymaga środowiska domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>  
  
 <span data-ttu-id="5a8cc-107">![Zabezpieczenia bez negocjowania poświadczeń wiadomości](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="5a8cc-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>  
  
|<span data-ttu-id="5a8cc-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="5a8cc-108">Characteristic</span></span>|<span data-ttu-id="5a8cc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8cc-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5a8cc-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5a8cc-110">Security Mode</span></span>|<span data-ttu-id="5a8cc-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="5a8cc-111">Message</span></span>|  
|<span data-ttu-id="5a8cc-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5a8cc-112">Interoperability</span></span>|<span data-ttu-id="5a8cc-113">Tak, WS-Security klientom zgodne profilu token protokołu Kerberos</span><span class="sxs-lookup"><span data-stu-id="5a8cc-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|  
|<span data-ttu-id="5a8cc-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="5a8cc-114">Authentication (Server)</span></span>|<span data-ttu-id="5a8cc-115">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="5a8cc-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="5a8cc-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="5a8cc-116">Authentication (Client)</span></span>|<span data-ttu-id="5a8cc-117">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="5a8cc-117">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="5a8cc-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="5a8cc-118">Integrity</span></span>|<span data-ttu-id="5a8cc-119">Tak</span><span class="sxs-lookup"><span data-stu-id="5a8cc-119">Yes</span></span>|  
|<span data-ttu-id="5a8cc-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="5a8cc-120">Confidentiality</span></span>|<span data-ttu-id="5a8cc-121">Tak</span><span class="sxs-lookup"><span data-stu-id="5a8cc-121">Yes</span></span>|  
|<span data-ttu-id="5a8cc-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="5a8cc-122">Transport</span></span>|<span data-ttu-id="5a8cc-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5a8cc-123">HTTP</span></span>|  
|<span data-ttu-id="5a8cc-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="5a8cc-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5a8cc-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="5a8cc-125">Service</span></span>  
 <span data-ttu-id="5a8cc-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5a8cc-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5a8cc-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5a8cc-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5a8cc-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5a8cc-130">Kod</span><span class="sxs-lookup"><span data-stu-id="5a8cc-130">Code</span></span>  
 <span data-ttu-id="5a8cc-131">Poniższy kod tworzy punkt końcowy usługi, który korzysta z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="5a8cc-132">Kod wyłącza negocjowania poświadczeń usługi i ustanowienia token kontekstu zabezpieczeń (SCT).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a8cc-133">Aby użyć typu poświadczeń systemu Windows bez negocjowania, konto użytkownika usługi musi mieć dostęp do nazwy głównej usługi (SPN), która jest zarejestrowana do domeny usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="5a8cc-134">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="5a8cc-134">You can do this in two ways:</span></span>  
  
1.  <span data-ttu-id="5a8cc-135">Użyj `NetworkService` lub `LocalSystem` konto uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="5a8cc-136">Ponieważ te konta ma dostęp do komputera, nazwę SPN, który zostanie nawiązane, gdy komputer jest dołączany domeny usługi Active Directory [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie generuje prawidłowego elementu SPN w punkt końcowy usługi w metadanych usługi (usługi sieci Web Język opisu lub WSDL).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>  
  
2.  <span data-ttu-id="5a8cc-137">Użyj dowolnego konta domeny usługi Active Directory do uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="5a8cc-138">W takim przypadku należy ustanowić nazwę SPN dla tego konta domeny.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="5a8cc-139">Jednym ze sposobów realizacji tego jest narzędzie Narzędzie Setspn.exe.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="5a8cc-140">Po utworzeniu nazwy SPN dla konta usługi należy skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do opublikowania tej nazwy SPN do obsługi klientów za pośrednictwem jego metadanych (WSDL).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-140">Once the SPN is created for the service's account, configure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="5a8cc-141">Odbywa się przez ustawienie tożsamość punktu końcowego dla dostępnego punktu końcowego, albo jeśli pliku konfiguracji aplikacji lub kodu.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="5a8cc-142">Poniższy przykład publikuje tożsamość programowo.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-142">The following example publishes the identity programmatically.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5a8cc-143">Nazwy SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-143"> SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5a8cc-144">Tożsamość punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-144"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a><span data-ttu-id="5a8cc-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5a8cc-145">Configuration</span></span>  
 <span data-ttu-id="5a8cc-146">Następującej konfiguracji można zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-146">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="5a8cc-147">Klient</span><span class="sxs-lookup"><span data-stu-id="5a8cc-147">Client</span></span>  
 <span data-ttu-id="5a8cc-148">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5a8cc-149">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5a8cc-149">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5a8cc-150">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-150">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5a8cc-151">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5a8cc-152">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5a8cc-153">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5a8cc-153">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5a8cc-154">Kod</span><span class="sxs-lookup"><span data-stu-id="5a8cc-154">Code</span></span>  
 <span data-ttu-id="5a8cc-155">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-155">The following code configures the client.</span></span> <span data-ttu-id="5a8cc-156">Tryb zabezpieczeń jest ustawiony na komunikat, a ustawiono typ poświadczeń klienta Windows.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="5a8cc-157">Należy pamiętać, że <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwości są ustawione na `false`.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a8cc-158">Aby użyć typu poświadczeń systemu Windows bez negocjowania, klient musi być skonfigurowany przed rozpoczęciem komunikacji z usługą nazwa SPN konta usługi.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="5a8cc-159">Klient używa nazwy SPN, aby uzyskać token protokołu Kerberos do uwierzytelniania i zabezpieczania komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="5a8cc-160">Poniższy przykład przedstawia sposób konfigurowania klienta z usługi SPN.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="5a8cc-161">Jeśli używasz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klienta, nazwę usługi SPN będzie automatycznie propagowane do klienta z metadanych usługi (WSDL), jeśli zawiera metadanych usługi te informacje.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5a8cc-162">jak skonfigurować usługę, aby uwzględnić jego nazwę SPN w metadanych usługi, zobacz sekcję "Usługa" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-162"> how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>  
>   
>  <span data-ttu-id="5a8cc-163">Aby uzyskać więcej informacji na temat nazw SPN, protokołu Kerberos i usługi Active Directory, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="5a8cc-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5a8cc-164">Tożsamość punktu końcowego, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-164"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a><span data-ttu-id="5a8cc-165">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5a8cc-165">Configuration</span></span>  
 <span data-ttu-id="5a8cc-166">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-166">The following code configures the client.</span></span> <span data-ttu-id="5a8cc-167">Należy pamiętać, że [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element musi mieć ustawiony odpowiadające usługi SPN w zarejestrowany dla konta usługi w domenie usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5a8cc-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a8cc-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a8cc-168">See Also</span></span>  
 [<span data-ttu-id="5a8cc-169">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5a8cc-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="5a8cc-170">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="5a8cc-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5a8cc-171">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="5a8cc-171">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
