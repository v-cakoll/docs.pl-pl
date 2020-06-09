---
title: Zabezpieczenia komunikatów ze wzajemnymi certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 44d06762bf66950ea0cc06986c61ecd548ae2e0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576411"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="da89d-102">Zabezpieczenia komunikatów ze wzajemnymi certyfikatami</span><span class="sxs-lookup"><span data-stu-id="da89d-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="da89d-103">W poniższym scenariuszu przedstawiono usługę Windows Communication Foundation (WCF) i klient zabezpieczony przy użyciu trybu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="da89d-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="da89d-104">Klient i usługa są uwierzytelniani przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="da89d-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="da89d-105">Ten scenariusz jest interoperacyjny, ponieważ używa protokołu WS-Security z profilem tokenu certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="da89d-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da89d-106">Ten scenariusz nie wykonuje negocjacji certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="da89d-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="da89d-107">Certyfikat usługi musi zostać udostępniony klient z wyprzedzeniem o każdej komunikacji.</span><span class="sxs-lookup"><span data-stu-id="da89d-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="da89d-108">Certyfikat serwera może być dystrybuowany z aplikacją lub udostępniany w ramach komunikacji poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="da89d-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="da89d-109">![Zabezpieczenia komunikatów przy użyciu certyfikatów wzajemnych](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="da89d-109">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="da89d-110">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="da89d-110">Characteristic</span></span>|<span data-ttu-id="da89d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="da89d-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="da89d-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="da89d-112">Security Mode</span></span>|<span data-ttu-id="da89d-113">Komunikat</span><span class="sxs-lookup"><span data-stu-id="da89d-113">Message</span></span>|  
|<span data-ttu-id="da89d-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="da89d-114">Interoperability</span></span>|<span data-ttu-id="da89d-115">Tak, przy użyciu protokołu WS-Security i X. 509, zgodne z profilem tokeny certyfikatu i usługi.</span><span class="sxs-lookup"><span data-stu-id="da89d-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="da89d-116">Authentication</span><span class="sxs-lookup"><span data-stu-id="da89d-116">Authentication</span></span>|<span data-ttu-id="da89d-117">Wzajemne uwierzytelnianie serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="da89d-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="da89d-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="da89d-118">Integrity</span></span>|<span data-ttu-id="da89d-119">Tak</span><span class="sxs-lookup"><span data-stu-id="da89d-119">Yes</span></span>|  
|<span data-ttu-id="da89d-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="da89d-120">Confidentiality</span></span>|<span data-ttu-id="da89d-121">Tak</span><span class="sxs-lookup"><span data-stu-id="da89d-121">Yes</span></span>|  
|<span data-ttu-id="da89d-122">Transport</span><span class="sxs-lookup"><span data-stu-id="da89d-122">Transport</span></span>|<span data-ttu-id="da89d-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="da89d-123">HTTP</span></span>|  
|<span data-ttu-id="da89d-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="da89d-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="da89d-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="da89d-125">Service</span></span>  
 <span data-ttu-id="da89d-126">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="da89d-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="da89d-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="da89d-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="da89d-128">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="da89d-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="da89d-129">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="da89d-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="da89d-130">Kod</span><span class="sxs-lookup"><span data-stu-id="da89d-130">Code</span></span>  
 <span data-ttu-id="da89d-131">Poniższy kod przedstawia tworzenie punktu końcowego usługi, który korzysta z zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="da89d-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="da89d-132">Usługa wymaga certyfikatu do samodzielnego uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="da89d-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="da89d-133">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="da89d-133">Configuration</span></span>  
 <span data-ttu-id="da89d-134">Aby utworzyć tę samą usługę, można użyć następującej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="da89d-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="da89d-135">Klient</span><span class="sxs-lookup"><span data-stu-id="da89d-135">Client</span></span>  
 <span data-ttu-id="da89d-136">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="da89d-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="da89d-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="da89d-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="da89d-138">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="da89d-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="da89d-139">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="da89d-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="da89d-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="da89d-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="da89d-141">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da89d-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="da89d-142">Kod</span><span class="sxs-lookup"><span data-stu-id="da89d-142">Code</span></span>  
 <span data-ttu-id="da89d-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="da89d-143">The following code creates the client.</span></span> <span data-ttu-id="da89d-144">Tryb zabezpieczeń jest ustawiony na wartość komunikat, a dla opcji Typ poświadczeń klienta ustawiono wartość certyfikat.</span><span class="sxs-lookup"><span data-stu-id="da89d-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="da89d-145">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="da89d-145">Configuration</span></span>  
 <span data-ttu-id="da89d-146">Poniżej konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="da89d-146">The following configures the client.</span></span> <span data-ttu-id="da89d-147">Certyfikat klienta musi być określony przy użyciu [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="da89d-147">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="da89d-148">Ponadto certyfikat usługi jest określany przy użyciu [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="da89d-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da89d-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da89d-149">See also</span></span>

- [<span data-ttu-id="da89d-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="da89d-150">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="da89d-151">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="da89d-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="da89d-152">[Instrukcje: Tworzenie i instalowanie certyfikatów tymczasowych w programie WCF na potrzeby zabezpieczeń transportu podczas opracowywania](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="da89d-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
