---
title: Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: bd64531116b1588683c2f5c8964e78e41e371ecf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955339"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="ef521-102">Zabezpieczenia komunikatów ze wzajemnymi certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ef521-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="ef521-103">W poniższym scenariuszu przedstawiono usługę Windows Communication Foundation (WCF) i klient zabezpieczony przy użyciu trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ef521-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="ef521-104">Klient i usługa są uwierzytelniani przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ef521-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="ef521-105">Ten scenariusz jest interoperacyjny, ponieważ używa protokołu WS-Security z profilem tokenu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="ef521-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef521-106">Ten scenariusz nie wykonuje negocjacji certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="ef521-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="ef521-107">Certyfikat usługi musi zostać udostępniony klient z wyprzedzeniem o każdej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ef521-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="ef521-108">Certyfikat serwera może być dystrybuowany z aplikacją lub udostępniany w ramach komunikacji poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="ef521-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="ef521-109">![Zabezpieczenia komunikatów przy użyciu certyfikatów wzajemnych](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="ef521-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="ef521-110">Charakterystyk</span><span class="sxs-lookup"><span data-stu-id="ef521-110">Characteristic</span></span>|<span data-ttu-id="ef521-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ef521-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ef521-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ef521-112">Security Mode</span></span>|<span data-ttu-id="ef521-113">Message</span><span class="sxs-lookup"><span data-stu-id="ef521-113">Message</span></span>|  
|<span data-ttu-id="ef521-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ef521-114">Interoperability</span></span>|<span data-ttu-id="ef521-115">Tak, przy użyciu protokołu WS-Security i X. 509, zgodne z profilem tokeny certyfikatu i usługi.</span><span class="sxs-lookup"><span data-stu-id="ef521-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="ef521-116">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="ef521-116">Authentication</span></span>|<span data-ttu-id="ef521-117">Wzajemne uwierzytelnianie serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="ef521-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="ef521-118">Spójn</span><span class="sxs-lookup"><span data-stu-id="ef521-118">Integrity</span></span>|<span data-ttu-id="ef521-119">Tak</span><span class="sxs-lookup"><span data-stu-id="ef521-119">Yes</span></span>|  
|<span data-ttu-id="ef521-120">Poufne</span><span class="sxs-lookup"><span data-stu-id="ef521-120">Confidentiality</span></span>|<span data-ttu-id="ef521-121">Tak</span><span class="sxs-lookup"><span data-stu-id="ef521-121">Yes</span></span>|  
|<span data-ttu-id="ef521-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="ef521-122">Transport</span></span>|<span data-ttu-id="ef521-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="ef521-123">HTTP</span></span>|  
|<span data-ttu-id="ef521-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="ef521-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ef521-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="ef521-125">Service</span></span>  
 <span data-ttu-id="ef521-126">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ef521-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ef521-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ef521-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="ef521-128">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ef521-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ef521-129">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ef521-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ef521-130">Kod</span><span class="sxs-lookup"><span data-stu-id="ef521-130">Code</span></span>  
 <span data-ttu-id="ef521-131">Poniższy kod przedstawia tworzenie punktu końcowego usługi, który korzysta z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ef521-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="ef521-132">Usługa wymaga certyfikatu do samodzielnego uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="ef521-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="ef521-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ef521-133">Configuration</span></span>  
 <span data-ttu-id="ef521-134">Aby utworzyć tę samą usługę, można użyć następującej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="ef521-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="ef521-135">Klient</span><span class="sxs-lookup"><span data-stu-id="ef521-135">Client</span></span>  
 <span data-ttu-id="ef521-136">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ef521-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ef521-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ef521-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="ef521-138">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="ef521-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="ef521-139">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ef521-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ef521-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="ef521-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ef521-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ef521-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ef521-142">Kod</span><span class="sxs-lookup"><span data-stu-id="ef521-142">Code</span></span>  
 <span data-ttu-id="ef521-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="ef521-143">The following code creates the client.</span></span> <span data-ttu-id="ef521-144">Tryb zabezpieczeń jest ustawiony na wartość komunikat, a dla opcji Typ poświadczeń klienta ustawiono wartość certyfikat.</span><span class="sxs-lookup"><span data-stu-id="ef521-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="ef521-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ef521-145">Configuration</span></span>  
 <span data-ttu-id="ef521-146">Poniżej konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="ef521-146">The following configures the client.</span></span> <span data-ttu-id="ef521-147">Certyfikat klienta musi być określony przy użyciu [ \<> ClientCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="ef521-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="ef521-148">Ponadto certyfikat usługi jest określany przy użyciu [ \<> defaultCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="ef521-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef521-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef521-149">See also</span></span>

- [<span data-ttu-id="ef521-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ef521-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="ef521-151">Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server</span><span class="sxs-lookup"><span data-stu-id="ef521-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
- [<span data-ttu-id="ef521-152">Instrukcje: Tworzenie i instalowanie certyfikatów tymczasowych w programie WCF na potrzeby zabezpieczeń transportu podczas opracowywania</span><span class="sxs-lookup"><span data-stu-id="ef521-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
