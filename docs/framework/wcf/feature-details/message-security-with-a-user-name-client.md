---
title: Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 215d23be53fad330b6ab056af83ad907f207259e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503975"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="03371-102">Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="03371-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="03371-103">Na poniższej ilustracji przedstawiono usługi Windows Communication Foundation (WCF) i klient zabezpieczone przy użyciu zabezpieczeń na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="03371-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="03371-104">Usługa jest uwierzytelniana przy użyciu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="03371-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="03371-105">Klient jest uwierzytelniany przy użyciu nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="03371-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="03371-106">Dla przykładowej aplikacji, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="03371-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="03371-107">![Zabezpieczenia komunikatów przy użyciu uwierzytelniania nazwy użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="03371-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="03371-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="03371-108">Characteristic</span></span>|<span data-ttu-id="03371-109">Opis</span><span class="sxs-lookup"><span data-stu-id="03371-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="03371-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="03371-110">Security Mode</span></span>|<span data-ttu-id="03371-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="03371-111">Message</span></span>|  
|<span data-ttu-id="03371-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="03371-112">Interoperability</span></span>|<span data-ttu-id="03371-113">Windows Communication Foundation (WCF) tylko</span><span class="sxs-lookup"><span data-stu-id="03371-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="03371-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="03371-114">Authentication (Server)</span></span>|<span data-ttu-id="03371-115">Początkowego negocjowania wymaga uwierzytelniania przez serwer</span><span class="sxs-lookup"><span data-stu-id="03371-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="03371-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="03371-116">Authentication (Client)</span></span>|<span data-ttu-id="03371-117">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="03371-117">User name/password</span></span>|  
|<span data-ttu-id="03371-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="03371-118">Integrity</span></span>|<span data-ttu-id="03371-119">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="03371-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="03371-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="03371-120">Confidentiality</span></span>|<span data-ttu-id="03371-121">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="03371-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="03371-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="03371-122">Transport</span></span>|<span data-ttu-id="03371-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="03371-123">HTTP</span></span>|  
|<span data-ttu-id="03371-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="03371-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="03371-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="03371-125">Service</span></span>  
 <span data-ttu-id="03371-126">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="03371-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="03371-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="03371-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="03371-128">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="03371-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="03371-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="03371-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="03371-130">Kod</span><span class="sxs-lookup"><span data-stu-id="03371-130">Code</span></span>  
 <span data-ttu-id="03371-131">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="03371-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="03371-132">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="03371-132">Configuration</span></span>  
 <span data-ttu-id="03371-133">Następująca konfiguracja można używać zamiast kodu:</span><span class="sxs-lookup"><span data-stu-id="03371-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="03371-134">Klient</span><span class="sxs-lookup"><span data-stu-id="03371-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="03371-135">Kod</span><span class="sxs-lookup"><span data-stu-id="03371-135">Code</span></span>  
 <span data-ttu-id="03371-136">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="03371-136">The following code creates the client.</span></span> <span data-ttu-id="03371-137">Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="03371-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="03371-138">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="03371-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="03371-139">Kod, aby zwrócić nazwę użytkownika i hasło nie został tutaj pokazany, ponieważ muszą być wykonane na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03371-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="03371-140">Na przykład okno formularzy Windows do wykonywania zapytań użytkownika na potrzeby danych.</span><span class="sxs-lookup"><span data-stu-id="03371-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="03371-141">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="03371-141">Configuration</span></span>  
 <span data-ttu-id="03371-142">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="03371-142">The following code configures the client.</span></span> <span data-ttu-id="03371-143">Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="03371-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="03371-144">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="03371-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03371-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03371-145">See Also</span></span>  
 [<span data-ttu-id="03371-146">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="03371-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="03371-147">Nazwa użytkownika zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="03371-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="03371-148">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="03371-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="03371-149">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="03371-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="03371-150">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="03371-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
