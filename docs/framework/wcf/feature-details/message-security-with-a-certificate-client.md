---
title: Zabezpieczenia komunikatów z klientem dysponującym certyfikatem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: a027577f5118f9a5b2f3eeaa29ddfde20851a8f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530856"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="a3c68-102">Zabezpieczenia komunikatów z klientem dysponującym certyfikatem</span><span class="sxs-lookup"><span data-stu-id="a3c68-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="a3c68-103">Następujący scenariusz pokazuje klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych używających trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a3c68-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="a3c68-104">Zarówno klient, jak i usługi są uwierzytelniane przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a3c68-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="a3c68-105">Aby uzyskać więcej informacji, zobacz [rozproszone zabezpieczenia aplikacji](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="a3c68-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="a3c68-106">Dla przykładowej aplikacji, zobacz [certyfikat zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a3c68-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="a3c68-107">![Klient z certyfikatem](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="a3c68-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="a3c68-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="a3c68-108">Characteristic</span></span>|<span data-ttu-id="a3c68-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a3c68-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a3c68-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a3c68-110">Security Mode</span></span>|<span data-ttu-id="a3c68-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a3c68-111">Message</span></span>|  
|<span data-ttu-id="a3c68-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="a3c68-112">Interoperability</span></span>|<span data-ttu-id="a3c68-113">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="a3c68-113">WCF only</span></span>|  
|<span data-ttu-id="a3c68-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="a3c68-114">Authentication (Server)</span></span>|<span data-ttu-id="a3c68-115">Za pomocą certyfikatu usługi</span><span class="sxs-lookup"><span data-stu-id="a3c68-115">Using service certificate</span></span>|  
|<span data-ttu-id="a3c68-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="a3c68-116">Authentication (Client)</span></span>|<span data-ttu-id="a3c68-117">Za pomocą certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="a3c68-117">Using client certificate</span></span>|  
|<span data-ttu-id="a3c68-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="a3c68-118">Integrity</span></span>|<span data-ttu-id="a3c68-119">Tak</span><span class="sxs-lookup"><span data-stu-id="a3c68-119">Yes</span></span>|  
|<span data-ttu-id="a3c68-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="a3c68-120">Confidentiality</span></span>|<span data-ttu-id="a3c68-121">Tak</span><span class="sxs-lookup"><span data-stu-id="a3c68-121">Yes</span></span>|  
|<span data-ttu-id="a3c68-122">Transport</span><span class="sxs-lookup"><span data-stu-id="a3c68-122">Transport</span></span>|<span data-ttu-id="a3c68-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="a3c68-123">HTTP</span></span>|  
|<span data-ttu-id="a3c68-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a3c68-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="a3c68-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="a3c68-125">Service</span></span>  
 <span data-ttu-id="a3c68-126">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a3c68-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a3c68-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a3c68-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a3c68-128">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a3c68-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="a3c68-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a3c68-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a3c68-130">Kod</span><span class="sxs-lookup"><span data-stu-id="a3c68-130">Code</span></span>  
 <span data-ttu-id="a3c68-131">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który używa zabezpieczenia komunikatów w celu ustanowienia bezpiecznej kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a3c68-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="a3c68-132">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a3c68-132">Configuration</span></span>  
 <span data-ttu-id="a3c68-133">Następująca konfiguracja można używać zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="a3c68-133">The following configuration can be used instead of the code.</span></span>  
  
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
                  bindingConfiguration="MessageAndCerficiateClient"   
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
  
## <a name="client"></a><span data-ttu-id="a3c68-134">Klient</span><span class="sxs-lookup"><span data-stu-id="a3c68-134">Client</span></span>  
 <span data-ttu-id="a3c68-135">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a3c68-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a3c68-136">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a3c68-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a3c68-137">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="a3c68-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="a3c68-138">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a3c68-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a3c68-139">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="a3c68-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a3c68-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a3c68-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a3c68-141">Kod</span><span class="sxs-lookup"><span data-stu-id="a3c68-141">Code</span></span>  
 <span data-ttu-id="a3c68-142">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="a3c68-142">The following code creates the client.</span></span> <span data-ttu-id="a3c68-143">Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="a3c68-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="a3c68-144">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a3c68-144">Configuration</span></span>  
 <span data-ttu-id="a3c68-145">Następująca konfiguracja Określa certyfikat klienta przy użyciu zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a3c68-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="a3c68-146">Aby uzyskać więcej informacji na temat certyfikatów, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a3c68-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="a3c68-147">Kod używa również <`identity`> elementu, aby określić systemu nazw domen (DNS) tożsamości serwera oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="a3c68-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="a3c68-148">Aby uzyskać więcej informacji o tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a3c68-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3c68-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3c68-149">See also</span></span>
- [<span data-ttu-id="a3c68-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a3c68-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="a3c68-151">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a3c68-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a3c68-152">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="a3c68-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a3c68-153">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="a3c68-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
