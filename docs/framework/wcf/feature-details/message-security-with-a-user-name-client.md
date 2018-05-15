---
title: Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7bda1bc18e2b5af1365c799c6f2be9d8d220e9ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="88307-102">Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="88307-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="88307-103">Na poniższej ilustracji przedstawiono usługi Windows Communication Foundation (WCF) i klientem zabezpieczone przy użyciu zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="88307-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="88307-104">Usługa jest uwierzytelniane za pomocą certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="88307-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="88307-105">Klient jest uwierzytelniany przy użyciu nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="88307-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="88307-106">Przykładową aplikację, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="88307-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="88307-107">![Zabezpieczenia komunikatów przy użyciu uwierzytelniania nazwa użytkownika](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="88307-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="88307-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="88307-108">Characteristic</span></span>|<span data-ttu-id="88307-109">Opis</span><span class="sxs-lookup"><span data-stu-id="88307-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="88307-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="88307-110">Security Mode</span></span>|<span data-ttu-id="88307-111">Komunikat</span><span class="sxs-lookup"><span data-stu-id="88307-111">Message</span></span>|  
|<span data-ttu-id="88307-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="88307-112">Interoperability</span></span>|<span data-ttu-id="88307-113">Windows Communication Foundation (WCF) tylko</span><span class="sxs-lookup"><span data-stu-id="88307-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="88307-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="88307-114">Authentication (Server)</span></span>|<span data-ttu-id="88307-115">Początkowa negocjacji wymaga uwierzytelniania serwera</span><span class="sxs-lookup"><span data-stu-id="88307-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="88307-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="88307-116">Authentication (Client)</span></span>|<span data-ttu-id="88307-117">Nazwa użytkownika/hasło</span><span class="sxs-lookup"><span data-stu-id="88307-117">User name/password</span></span>|  
|<span data-ttu-id="88307-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="88307-118">Integrity</span></span>|<span data-ttu-id="88307-119">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="88307-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="88307-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="88307-120">Confidentiality</span></span>|<span data-ttu-id="88307-121">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="88307-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="88307-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="88307-122">Transport</span></span>|<span data-ttu-id="88307-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="88307-123">HTTP</span></span>|  
|<span data-ttu-id="88307-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="88307-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="88307-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="88307-125">Service</span></span>  
 <span data-ttu-id="88307-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="88307-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="88307-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="88307-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="88307-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="88307-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="88307-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="88307-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="88307-130">Kod</span><span class="sxs-lookup"><span data-stu-id="88307-130">Code</span></span>  
 <span data-ttu-id="88307-131">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="88307-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="88307-132">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="88307-132">Configuration</span></span>  
 <span data-ttu-id="88307-133">Zamiast kodu mogą być używane następującej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="88307-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="88307-134">Klient</span><span class="sxs-lookup"><span data-stu-id="88307-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="88307-135">Kod</span><span class="sxs-lookup"><span data-stu-id="88307-135">Code</span></span>  
 <span data-ttu-id="88307-136">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="88307-136">The following code creates the client.</span></span> <span data-ttu-id="88307-137">Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `UserName`.</span><span class="sxs-lookup"><span data-stu-id="88307-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="88307-138">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="88307-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="88307-139">Kod, aby zwrócić nazwę użytkownika i hasło nie jest wyświetlane w tym miejscu, ponieważ musi zostać wykonana na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88307-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="88307-140">Na przykład okno formularzy systemu Windows do badania użytkownika dla danych.</span><span class="sxs-lookup"><span data-stu-id="88307-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="88307-141">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="88307-141">Configuration</span></span>  
 <span data-ttu-id="88307-142">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="88307-142">The following code configures the client.</span></span> <span data-ttu-id="88307-143">Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `UserName`.</span><span class="sxs-lookup"><span data-stu-id="88307-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="88307-144">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="88307-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88307-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88307-145">See Also</span></span>  
 [<span data-ttu-id="88307-146">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="88307-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="88307-147">Nazwa użytkownika zabezpieczeń komunikatów</span><span class="sxs-lookup"><span data-stu-id="88307-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="88307-148">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="88307-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="88307-149">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="88307-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="88307-150">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="88307-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
