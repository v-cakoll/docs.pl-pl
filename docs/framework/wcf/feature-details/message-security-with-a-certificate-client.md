---
title: Zabezpieczenia komunikatów z klientem dysponującym certyfikatem
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: 16
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 9bb7efa82e14f899ddcbb2fdfd26eba2023bdd61
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="8c6c0-102">Zabezpieczenia komunikatów z klientem dysponującym certyfikatem</span><span class="sxs-lookup"><span data-stu-id="8c6c0-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="8c6c0-103">Poniżej przedstawiono scenariusz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klient i usługa zabezpieczone przy użyciu trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="8c6c0-104">Klient i usługa są uwierzytelniane za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="8c6c0-105">Aby uzyskać więcej informacji, zobacz [rozproszone zabezpieczenia aplikacji](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c0-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="8c6c0-106">Przykładową aplikację, zobacz [certyfikat zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c0-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="8c6c0-107">![Klient z certyfikatem](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="8c6c0-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="8c6c0-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="8c6c0-108">Characteristic</span></span>|<span data-ttu-id="8c6c0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8c6c0-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8c6c0-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8c6c0-110">Security Mode</span></span>|<span data-ttu-id="8c6c0-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8c6c0-111">Message</span></span>|  
|<span data-ttu-id="8c6c0-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8c6c0-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8c6c0-113"> tylko</span><span class="sxs-lookup"><span data-stu-id="8c6c0-113"> only</span></span>|  
|<span data-ttu-id="8c6c0-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="8c6c0-114">Authentication (Server)</span></span>|<span data-ttu-id="8c6c0-115">Za pomocą certyfikatu usługi</span><span class="sxs-lookup"><span data-stu-id="8c6c0-115">Using service certificate</span></span>|  
|<span data-ttu-id="8c6c0-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="8c6c0-116">Authentication (Client)</span></span>|<span data-ttu-id="8c6c0-117">Przy użyciu certyfikatu klienta</span><span class="sxs-lookup"><span data-stu-id="8c6c0-117">Using client certificate</span></span>|  
|<span data-ttu-id="8c6c0-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="8c6c0-118">Integrity</span></span>|<span data-ttu-id="8c6c0-119">Tak</span><span class="sxs-lookup"><span data-stu-id="8c6c0-119">Yes</span></span>|  
|<span data-ttu-id="8c6c0-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="8c6c0-120">Confidentiality</span></span>|<span data-ttu-id="8c6c0-121">Tak</span><span class="sxs-lookup"><span data-stu-id="8c6c0-121">Yes</span></span>|  
|<span data-ttu-id="8c6c0-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="8c6c0-122">Transport</span></span>|<span data-ttu-id="8c6c0-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="8c6c0-123">HTTP</span></span>|  
|<span data-ttu-id="8c6c0-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="8c6c0-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8c6c0-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="8c6c0-125">Service</span></span>  
 <span data-ttu-id="8c6c0-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8c6c0-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8c6c0-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8c6c0-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="8c6c0-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8c6c0-130">Kod</span><span class="sxs-lookup"><span data-stu-id="8c6c0-130">Code</span></span>  
 <span data-ttu-id="8c6c0-131">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z ustanowić bezpiecznego kontekstu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="8c6c0-132">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8c6c0-132">Configuration</span></span>  
 <span data-ttu-id="8c6c0-133">Następującej konfiguracji można zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="8c6c0-134">Klient</span><span class="sxs-lookup"><span data-stu-id="8c6c0-134">Client</span></span>  
 <span data-ttu-id="8c6c0-135">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8c6c0-136">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8c6c0-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8c6c0-137">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="8c6c0-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="8c6c0-138">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8c6c0-139">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8c6c0-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8c6c0-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8c6c0-141">Kod</span><span class="sxs-lookup"><span data-stu-id="8c6c0-141">Code</span></span>  
 <span data-ttu-id="8c6c0-142">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-142">The following code creates the client.</span></span> <span data-ttu-id="8c6c0-143">Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="8c6c0-144">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8c6c0-144">Configuration</span></span>  
 <span data-ttu-id="8c6c0-145">Następująca konfiguracja Określa certyfikat klienta, używając zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="8c6c0-146">Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c0-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="8c6c0-147">Kod używa również <`identity`> elementu, aby określić systemu nazw domen (DNS) tożsamości serwera oczekiwanego.</span><span class="sxs-lookup"><span data-stu-id="8c6c0-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8c6c0-148"> tożsamości, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c0-148"> identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c6c0-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c6c0-149">See Also</span></span>  
 [<span data-ttu-id="8c6c0-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8c6c0-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="8c6c0-151">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="8c6c0-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8c6c0-152">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="8c6c0-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="8c6c0-153">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="8c6c0-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
