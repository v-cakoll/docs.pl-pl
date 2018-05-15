---
title: Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1407593bf90b28a1890a8c18564b31d0aa67e0cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="c9e4f-102">Zabezpieczenia komunikatów ze wzajemnymi certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c9e4f-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="c9e4f-103">Poniższy scenariusz zawiera usługi Windows Communication Foundation (WCF) i klienta zabezpieczony używających trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="c9e4f-104">Klient i usługa są uwierzytelniane za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="c9e4f-105">Ten scenariusz jest współdziałanie, ponieważ używa WS-Security z profilem tokenu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9e4f-106">W tym scenariuszu nie przeprowadza negocjowanie certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="c9e4f-107">Należy podać certyfikat usługi do klienta z wyprzedzeniem wszelkie komunikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="c9e4f-108">Certyfikat serwera można rozpowszechnianej za pomocą aplikacji lub podane w komunikacie poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="c9e4f-109">![Zabezpieczenia ze wzajemnymi certyfikatami wiadomości](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="c9e4f-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="c9e4f-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="c9e4f-110">Characteristic</span></span>|<span data-ttu-id="c9e4f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c9e4f-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c9e4f-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c9e4f-112">Security Mode</span></span>|<span data-ttu-id="c9e4f-113">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c9e4f-113">Message</span></span>|  
|<span data-ttu-id="c9e4f-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c9e4f-114">Interoperability</span></span>|<span data-ttu-id="c9e4f-115">Tak, z WS-Security i klientów zgodne tokenu profilu certyfikatu X.509 i usług.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="c9e4f-116">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="c9e4f-116">Authentication</span></span>|<span data-ttu-id="c9e4f-117">Wzajemne uwierzytelnianie serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="c9e4f-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="c9e4f-118">Integrity</span></span>|<span data-ttu-id="c9e4f-119">Tak</span><span class="sxs-lookup"><span data-stu-id="c9e4f-119">Yes</span></span>|  
|<span data-ttu-id="c9e4f-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="c9e4f-120">Confidentiality</span></span>|<span data-ttu-id="c9e4f-121">Tak</span><span class="sxs-lookup"><span data-stu-id="c9e4f-121">Yes</span></span>|  
|<span data-ttu-id="c9e4f-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="c9e4f-122">Transport</span></span>|<span data-ttu-id="c9e4f-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="c9e4f-123">HTTP</span></span>|  
|<span data-ttu-id="c9e4f-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="c9e4f-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c9e4f-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="c9e4f-125">Service</span></span>  
 <span data-ttu-id="c9e4f-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c9e4f-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c9e4f-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c9e4f-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="c9e4f-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c9e4f-130">Kod</span><span class="sxs-lookup"><span data-stu-id="c9e4f-130">Code</span></span>  
 <span data-ttu-id="c9e4f-131">W poniższym kodzie tworzy punkt końcowy usługi, który korzysta z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="c9e4f-132">Usługa wymaga certyfikatu do samodzielnego uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="c9e4f-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c9e4f-133">Configuration</span></span>  
 <span data-ttu-id="c9e4f-134">Następującej konfiguracji można zamiast kodu do utworzenia tej samej usługi.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="c9e4f-135">Klient</span><span class="sxs-lookup"><span data-stu-id="c9e4f-135">Client</span></span>  
 <span data-ttu-id="c9e4f-136">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c9e4f-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c9e4f-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c9e4f-138">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="c9e4f-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="c9e4f-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c9e4f-140">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c9e4f-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c9e4f-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c9e4f-142">Kod</span><span class="sxs-lookup"><span data-stu-id="c9e4f-142">Code</span></span>  
 <span data-ttu-id="c9e4f-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-143">The following code creates the client.</span></span> <span data-ttu-id="c9e4f-144">Tryb zabezpieczeń jest ustawiony na komunikat, a typ poświadczeń klienta ma wartość Certificate.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="c9e4f-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c9e4f-145">Configuration</span></span>  
 <span data-ttu-id="c9e4f-146">Poniższa konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="c9e4f-146">The following configures the client.</span></span> <span data-ttu-id="c9e4f-147">Certyfikat klienta musi być podana przy użyciu [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="c9e4f-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="c9e4f-148">Ponadto certyfikat usługi zostanie określona przy użyciu [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="c9e4f-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9e4f-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9e4f-149">See Also</span></span>  
 [<span data-ttu-id="c9e4f-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c9e4f-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="c9e4f-151">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="c9e4f-151">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)  
 [<span data-ttu-id="c9e4f-152">Porady: tworzenie i zainstalować certyfikaty tymczasowe w programie WCF dla zabezpieczeń transportu podczas tworzenia</span><span class="sxs-lookup"><span data-stu-id="c9e4f-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=244264)
