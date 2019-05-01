---
title: Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 8fc8d6d4a63b7a752fb8c26991d904761fdcebdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923071"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="ecbb3-102">Zabezpieczenia komunikatów ze wzajemnymi certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ecbb3-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="ecbb3-103">Następujący scenariusz pokazuje usługi Windows Communication Foundation (WCF), a klient zabezpieczone przy użyciu trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="ecbb3-104">Klient i usługa są uwierzytelniane przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="ecbb3-105">Ten scenariusz jest współpracujący, ponieważ używa ona WS-Security za pomocą tokenu profilu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecbb3-106">W tym scenariuszu nie przeprowadza negocjowanie certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="ecbb3-107">Certyfikatu usługi musi być podana klientowi wyprzedzeniem o wszelkich komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="ecbb3-108">Certyfikat serwera można rozpowszechniać za pomocą aplikacji lub udostępniane w ramach komunikacji poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="ecbb3-109">![Zabezpieczenia ze wzajemnymi certyfikatami wiadomości](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="ecbb3-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="ecbb3-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="ecbb3-110">Characteristic</span></span>|<span data-ttu-id="ecbb3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ecbb3-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ecbb3-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ecbb3-112">Security Mode</span></span>|<span data-ttu-id="ecbb3-113">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ecbb3-113">Message</span></span>|  
|<span data-ttu-id="ecbb3-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ecbb3-114">Interoperability</span></span>|<span data-ttu-id="ecbb3-115">Tak, za pomocą WS-Security i tokenu profilu certyfikatu X.509, zgodne klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="ecbb3-116">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="ecbb3-116">Authentication</span></span>|<span data-ttu-id="ecbb3-117">Wzajemne uwierzytelnianie serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="ecbb3-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="ecbb3-118">Integrity</span></span>|<span data-ttu-id="ecbb3-119">Yes</span><span class="sxs-lookup"><span data-stu-id="ecbb3-119">Yes</span></span>|  
|<span data-ttu-id="ecbb3-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="ecbb3-120">Confidentiality</span></span>|<span data-ttu-id="ecbb3-121">Tak</span><span class="sxs-lookup"><span data-stu-id="ecbb3-121">Yes</span></span>|  
|<span data-ttu-id="ecbb3-122">Transport</span><span class="sxs-lookup"><span data-stu-id="ecbb3-122">Transport</span></span>|<span data-ttu-id="ecbb3-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="ecbb3-123">HTTP</span></span>|  
|<span data-ttu-id="ecbb3-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="ecbb3-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ecbb3-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="ecbb3-125">Service</span></span>  
 <span data-ttu-id="ecbb3-126">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ecbb3-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ecbb3-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="ecbb3-128">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ecbb3-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ecbb3-130">Kod</span><span class="sxs-lookup"><span data-stu-id="ecbb3-130">Code</span></span>  
 <span data-ttu-id="ecbb3-131">Ilustruje poniższy kod tworzy punkt końcowy usługi, która używa zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="ecbb3-132">Usługa wymaga certyfikatów do samodzielnego uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="ecbb3-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ecbb3-133">Configuration</span></span>  
 <span data-ttu-id="ecbb3-134">Następująca konfiguracja może służyć zamiast kodu do tworzenia tej samej usługi.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"   
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ecbb3-135">Klient</span><span class="sxs-lookup"><span data-stu-id="ecbb3-135">Client</span></span>  
 <span data-ttu-id="ecbb3-136">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ecbb3-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ecbb3-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="ecbb3-138">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="ecbb3-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="ecbb3-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ecbb3-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ecbb3-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ecbb3-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ecbb3-142">Kod</span><span class="sxs-lookup"><span data-stu-id="ecbb3-142">Code</span></span>  
 <span data-ttu-id="ecbb3-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-143">The following code creates the client.</span></span> <span data-ttu-id="ecbb3-144">Tryb zabezpieczeń jest ustawiony na komunikat i typu poświadczeń klienta jest ustawiona na certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="ecbb3-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ecbb3-145">Configuration</span></span>  
 <span data-ttu-id="ecbb3-146">Następujące konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="ecbb3-146">The following configures the client.</span></span> <span data-ttu-id="ecbb3-147">Należy określić certyfikat klienta przy użyciu [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="ecbb3-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="ecbb3-148">Ponadto certyfikat usługi jest określony, przy użyciu [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="ecbb3-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecbb3-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecbb3-149">See also</span></span>

- [<span data-ttu-id="ecbb3-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ecbb3-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="ecbb3-151">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="ecbb3-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
- [<span data-ttu-id="ecbb3-152">Instrukcje: Tworzenie i instalowanie certyfikatów tymczasowych programu WCF dla zabezpieczeń transportu podczas programowania</span><span class="sxs-lookup"><span data-stu-id="ecbb3-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
