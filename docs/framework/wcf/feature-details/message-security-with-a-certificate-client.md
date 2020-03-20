---
title: Zabezpieczenia komunikatów z klientem dysponującym certyfikatem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 3660877194931c2be5b9b1c9aa54e2595701697f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184656"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="1acfb-102">Zabezpieczenia komunikatów z klientem dysponującym certyfikatem</span><span class="sxs-lookup"><span data-stu-id="1acfb-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="1acfb-103">W poniższym scenariuszu przedstawiono klienta i usługę Windows Communication Foundation (WCF) zabezpieczoną przy użyciu trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1acfb-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="1acfb-104">Zarówno klient, jak i usługa są uwierzytelnione za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1acfb-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="1acfb-105">Aby uzyskać więcej informacji, zobacz [Zabezpieczenia aplikacji rozproszonych](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="1acfb-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Zrzut ekranu przedstawiający klienta z certyfikatem.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="1acfb-107">Aby zapoznać się z przykładową aplikacją, zobacz [Certyfikat zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1acfb-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="1acfb-108">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="1acfb-108">Characteristic</span></span>|<span data-ttu-id="1acfb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1acfb-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1acfb-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1acfb-110">Security Mode</span></span>|<span data-ttu-id="1acfb-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1acfb-111">Message</span></span>|  
|<span data-ttu-id="1acfb-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="1acfb-112">Interoperability</span></span>|<span data-ttu-id="1acfb-113">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="1acfb-113">WCF only</span></span>|  
|<span data-ttu-id="1acfb-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="1acfb-114">Authentication (Server)</span></span>|<span data-ttu-id="1acfb-115">Korzystanie z certyfikatu usługi</span><span class="sxs-lookup"><span data-stu-id="1acfb-115">Using service certificate</span></span>|  
|<span data-ttu-id="1acfb-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="1acfb-116">Authentication (Client)</span></span>|<span data-ttu-id="1acfb-117">Korzystanie z certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="1acfb-117">Using client certificate</span></span>|  
|<span data-ttu-id="1acfb-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="1acfb-118">Integrity</span></span>|<span data-ttu-id="1acfb-119">Tak</span><span class="sxs-lookup"><span data-stu-id="1acfb-119">Yes</span></span>|  
|<span data-ttu-id="1acfb-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="1acfb-120">Confidentiality</span></span>|<span data-ttu-id="1acfb-121">Tak</span><span class="sxs-lookup"><span data-stu-id="1acfb-121">Yes</span></span>|  
|<span data-ttu-id="1acfb-122">Transport</span><span class="sxs-lookup"><span data-stu-id="1acfb-122">Transport</span></span>|<span data-ttu-id="1acfb-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="1acfb-123">HTTP</span></span>|  
|<span data-ttu-id="1acfb-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="1acfb-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="1acfb-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="1acfb-125">Service</span></span>  
 <span data-ttu-id="1acfb-126">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="1acfb-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1acfb-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1acfb-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="1acfb-128">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1acfb-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="1acfb-129">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1acfb-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1acfb-130">Code</span><span class="sxs-lookup"><span data-stu-id="1acfb-130">Code</span></span>  
 <span data-ttu-id="1acfb-131">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa zabezpieczeń wiadomości w celu ustanowienia bezpiecznego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1acfb-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="1acfb-132">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="1acfb-132">Configuration</span></span>  
 <span data-ttu-id="1acfb-133">Zamiast kodu można użyć następującej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1acfb-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="1acfb-134">Klient</span><span class="sxs-lookup"><span data-stu-id="1acfb-134">Client</span></span>  
 <span data-ttu-id="1acfb-135">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="1acfb-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1acfb-136">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="1acfb-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="1acfb-137">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="1acfb-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="1acfb-138">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="1acfb-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="1acfb-139">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="1acfb-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="1acfb-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1acfb-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="1acfb-141">Code</span><span class="sxs-lookup"><span data-stu-id="1acfb-141">Code</span></span>  
 <span data-ttu-id="1acfb-142">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="1acfb-142">The following code creates the client.</span></span> <span data-ttu-id="1acfb-143">Powiązanie jest zabezpieczeń trybu wiadomości, a typ `Certificate`poświadczeń klienta jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="1acfb-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="1acfb-144">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="1acfb-144">Configuration</span></span>  
 <span data-ttu-id="1acfb-145">Następująca konfiguracja określa certyfikat klienta przy użyciu zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1acfb-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="1acfb-146">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1acfb-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="1acfb-147">Kod używa również <`identity`> element, aby określić system nazw domen (DNS) oczekiwanej tożsamości serwera.</span><span class="sxs-lookup"><span data-stu-id="1acfb-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="1acfb-148">Aby uzyskać więcej informacji na temat tożsamości, zobacz [Tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1acfb-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1acfb-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1acfb-149">See also</span></span>

- [<span data-ttu-id="1acfb-150">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1acfb-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="1acfb-151">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="1acfb-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1acfb-152">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="1acfb-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="1acfb-153">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1acfb-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
