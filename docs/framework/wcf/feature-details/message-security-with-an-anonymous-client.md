---
title: "Zabezpieczenia komunikatów z anonimowym klientem"
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
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="d2fe4-102">Zabezpieczenia komunikatów z anonimowym klientem</span><span class="sxs-lookup"><span data-stu-id="d2fe4-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="d2fe4-103">Poniższy scenariusz przedstawia klientów i usług zabezpieczonych przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-103">The following scenario shows a client and service secured by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message security.</span></span> <span data-ttu-id="d2fe4-104">Celem projektu jest użycie zabezpieczeń wiadomości, a nie zabezpieczeń transportu, aby w przyszłości może obsługiwać bardziej rozbudowane modelu opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d2fe4-105">przy użyciu zaawansowanych oświadczenia dotyczące autoryzacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="d2fe4-105"> using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="d2fe4-106">Przykładową aplikację, zobacz [komunikat zabezpieczeń anonimowe](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="d2fe4-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="d2fe4-107">![Zabezpieczenia za pomocą klienta anynymous wiadomości](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="d2fe4-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="d2fe4-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="d2fe4-108">Characteristic</span></span>|<span data-ttu-id="d2fe4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d2fe4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d2fe4-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d2fe4-110">Security Mode</span></span>|<span data-ttu-id="d2fe4-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d2fe4-111">Message</span></span>|  
|<span data-ttu-id="d2fe4-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d2fe4-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d2fe4-113">tylko</span><span class="sxs-lookup"><span data-stu-id="d2fe4-113"> only</span></span>|  
|<span data-ttu-id="d2fe4-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="d2fe4-114">Authentication (Server)</span></span>|<span data-ttu-id="d2fe4-115">Początkowa negocjacji wymaga uwierzytelniania serwera, ale nie uwierzytelnianie klienta</span><span class="sxs-lookup"><span data-stu-id="d2fe4-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="d2fe4-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="d2fe4-116">Authentication (Client)</span></span>|<span data-ttu-id="d2fe4-117">Brak</span><span class="sxs-lookup"><span data-stu-id="d2fe4-117">None</span></span>|  
|<span data-ttu-id="d2fe4-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="d2fe4-118">Integrity</span></span>|<span data-ttu-id="d2fe4-119">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="d2fe4-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d2fe4-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="d2fe4-120">Confidentiality</span></span>|<span data-ttu-id="d2fe4-121">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="d2fe4-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d2fe4-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="d2fe4-122">Transport</span></span>|<span data-ttu-id="d2fe4-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="d2fe4-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="d2fe4-124">Usługa</span><span class="sxs-lookup"><span data-stu-id="d2fe4-124">Service</span></span>  
 <span data-ttu-id="d2fe4-125">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d2fe4-126">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d2fe4-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d2fe4-127">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="d2fe4-128">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d2fe4-129">Kod</span><span class="sxs-lookup"><span data-stu-id="d2fe4-129">Code</span></span>  
 <span data-ttu-id="d2fe4-130">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="d2fe4-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d2fe4-131">Configuration</span></span>  
 <span data-ttu-id="d2fe4-132">Następującej konfiguracji można zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="d2fe4-133">Element zachowania usługi służy do określenia certyfikatu, który jest używany do uwierzytelniania usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="d2fe4-134">Element usługi należy określić przy użyciu zachowanie `behaviorConfiguration` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="d2fe4-135">Element powiązania Określa, że typ poświadczeń klienta `None`, umożliwiając anonimowe klientów do korzystania z usługi.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="d2fe4-136">Klient</span><span class="sxs-lookup"><span data-stu-id="d2fe4-136">Client</span></span>  
 <span data-ttu-id="d2fe4-137">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d2fe4-138">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d2fe4-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d2fe4-139">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="d2fe4-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="d2fe4-140">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d2fe4-141">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d2fe4-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d2fe4-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d2fe4-143">Kod</span><span class="sxs-lookup"><span data-stu-id="d2fe4-143">Code</span></span>  
 <span data-ttu-id="d2fe4-144">Poniższy kod tworzy wystąpienie klienta.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="d2fe4-145">Powiązanie używa komunikat trybu zabezpieczeń i typu poświadczeń klienta ma wartość none.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="d2fe4-146">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d2fe4-146">Configuration</span></span>  
 <span data-ttu-id="d2fe4-147">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="d2fe4-147">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2fe4-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2fe4-148">See Also</span></span>  
 [<span data-ttu-id="d2fe4-149">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d2fe4-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d2fe4-150">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="d2fe4-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="d2fe4-151">Zabezpieczenia komunikatów z Anonimowością</span><span class="sxs-lookup"><span data-stu-id="d2fe4-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="d2fe4-152">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="d2fe4-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="d2fe4-153">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="d2fe4-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
