---
title: Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 3dd21268d4ea7dc59c74889ac94dc86678e91865
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184637"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="322ad-102">Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="322ad-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="322ad-103">Na poniższej ilustracji przedstawiono usługę Windows Communication Foundation (WCF) i klienta zabezpieczonego przy użyciu zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="322ad-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="322ad-104">Usługa jest uwierzytelniona za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="322ad-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="322ad-105">Klient uwierzytelnia się przy użyciu nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="322ad-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="322ad-106">Aby zapoznać się z przykładową aplikacją, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="322ad-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="322ad-107">![Zabezpieczenia wiadomości przy użyciu uwierzytelniania nazwy użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="322ad-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="322ad-108">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="322ad-108">Characteristic</span></span>|<span data-ttu-id="322ad-109">Opis</span><span class="sxs-lookup"><span data-stu-id="322ad-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="322ad-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="322ad-110">Security Mode</span></span>|<span data-ttu-id="322ad-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="322ad-111">Message</span></span>|  
|<span data-ttu-id="322ad-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="322ad-112">Interoperability</span></span>|<span data-ttu-id="322ad-113">Tylko Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="322ad-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="322ad-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="322ad-114">Authentication (Server)</span></span>|<span data-ttu-id="322ad-115">Początkowa negocjacja wymaga uwierzytelnienia serwera</span><span class="sxs-lookup"><span data-stu-id="322ad-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="322ad-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="322ad-116">Authentication (Client)</span></span>|<span data-ttu-id="322ad-117">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="322ad-117">User name/password</span></span>|  
|<span data-ttu-id="322ad-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="322ad-118">Integrity</span></span>|<span data-ttu-id="322ad-119">Tak, używanie wspólnego kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="322ad-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="322ad-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="322ad-120">Confidentiality</span></span>|<span data-ttu-id="322ad-121">Tak, używanie wspólnego kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="322ad-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="322ad-122">Transport</span><span class="sxs-lookup"><span data-stu-id="322ad-122">Transport</span></span>|<span data-ttu-id="322ad-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="322ad-123">HTTP</span></span>|  
|<span data-ttu-id="322ad-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="322ad-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="322ad-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="322ad-125">Service</span></span>  
 <span data-ttu-id="322ad-126">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="322ad-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="322ad-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="322ad-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="322ad-128">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="322ad-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="322ad-129">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="322ad-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="322ad-130">Code</span><span class="sxs-lookup"><span data-stu-id="322ad-130">Code</span></span>  
 <span data-ttu-id="322ad-131">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="322ad-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="322ad-132">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="322ad-132">Configuration</span></span>  
 <span data-ttu-id="322ad-133">Zamiast kodu można użyć następującej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="322ad-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
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
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="322ad-134">Klient</span><span class="sxs-lookup"><span data-stu-id="322ad-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="322ad-135">Code</span><span class="sxs-lookup"><span data-stu-id="322ad-135">Code</span></span>  
 <span data-ttu-id="322ad-136">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="322ad-136">The following code creates the client.</span></span> <span data-ttu-id="322ad-137">Powiązanie jest zabezpieczeń trybu wiadomości, a typ `UserName`poświadczeń klienta jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="322ad-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="322ad-138">Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go skonfigurować).</span><span class="sxs-lookup"><span data-stu-id="322ad-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="322ad-139">Kod do zwrócenia nazwy użytkownika i hasła nie jest wyświetlany w tym miejscu, ponieważ musi być wykonane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="322ad-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="322ad-140">Na przykład użyj okna dialogowego Formularze systemu Windows, aby zbadać użytkownika o dane.</span><span class="sxs-lookup"><span data-stu-id="322ad-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="322ad-141">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="322ad-141">Configuration</span></span>  
 <span data-ttu-id="322ad-142">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="322ad-142">The following code configures the client.</span></span> <span data-ttu-id="322ad-143">Powiązanie jest zabezpieczeń trybu wiadomości, a typ `UserName`poświadczeń klienta jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="322ad-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="322ad-144">Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go skonfigurować).</span><span class="sxs-lookup"><span data-stu-id="322ad-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
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
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="322ad-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="322ad-145">See also</span></span>

- [<span data-ttu-id="322ad-146">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="322ad-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="322ad-147">Nazwa użytkownika zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="322ad-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="322ad-148">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="322ad-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="322ad-149">\<>tożsamości</span><span class="sxs-lookup"><span data-stu-id="322ad-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="322ad-150">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="322ad-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
