---
title: Niezabezpieczony klient internetowy i usługa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: ca6b028ef20095d6faeb125151772eedf1500fa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038730"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="cd6ee-102">Niezabezpieczony klient internetowy i usługa</span><span class="sxs-lookup"><span data-stu-id="cd6ee-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="cd6ee-103">Na poniższej ilustracji przedstawiono przykład publiczne, niezabezpieczony klient usługi Windows Communication Foundation (WCF) i usługi:</span><span class="sxs-lookup"><span data-stu-id="cd6ee-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Zrzut ekranu pokazujący niezabezpieczony scenariusz Internet](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="cd6ee-105">Cechy</span><span class="sxs-lookup"><span data-stu-id="cd6ee-105">Characteristic</span></span>|<span data-ttu-id="cd6ee-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cd6ee-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="cd6ee-107">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cd6ee-107">Security Mode</span></span>|<span data-ttu-id="cd6ee-108">Brak</span><span class="sxs-lookup"><span data-stu-id="cd6ee-108">None</span></span>|  
|<span data-ttu-id="cd6ee-109">Transport</span><span class="sxs-lookup"><span data-stu-id="cd6ee-109">Transport</span></span>|<span data-ttu-id="cd6ee-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="cd6ee-110">HTTP</span></span>|  
|<span data-ttu-id="cd6ee-111">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="cd6ee-111">Binding</span></span>|<span data-ttu-id="cd6ee-112"><xref:System.ServiceModel.BasicHttpBinding> w kodzie lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="cd6ee-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="cd6ee-113">Interoperability</span></span>|<span data-ttu-id="cd6ee-114">Za pomocą istniejących klientów usługi sieci Web i usług</span><span class="sxs-lookup"><span data-stu-id="cd6ee-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="cd6ee-115">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="cd6ee-115">Authentication</span></span>|<span data-ttu-id="cd6ee-116">Brak</span><span class="sxs-lookup"><span data-stu-id="cd6ee-116">None</span></span>|  
|<span data-ttu-id="cd6ee-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="cd6ee-117">Integrity</span></span>|<span data-ttu-id="cd6ee-118">Brak</span><span class="sxs-lookup"><span data-stu-id="cd6ee-118">None</span></span>|  
|<span data-ttu-id="cd6ee-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="cd6ee-119">Confidentiality</span></span>|<span data-ttu-id="cd6ee-120">Brak</span><span class="sxs-lookup"><span data-stu-id="cd6ee-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="cd6ee-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="cd6ee-121">Service</span></span>  
 <span data-ttu-id="cd6ee-122">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cd6ee-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cd6ee-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="cd6ee-124">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="cd6ee-125">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cd6ee-126">Kod</span><span class="sxs-lookup"><span data-stu-id="cd6ee-126">Code</span></span>  
 <span data-ttu-id="cd6ee-127">Poniższy kod przedstawia sposób tworzenia punktu końcowego z żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="cd6ee-128">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> została ustawiona na tryb zabezpieczeń <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="cd6ee-129">Konfiguracja usługi</span><span class="sxs-lookup"><span data-stu-id="cd6ee-129">Service Configuration</span></span>  
 <span data-ttu-id="cd6ee-130">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-130">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="cd6ee-131">Klient</span><span class="sxs-lookup"><span data-stu-id="cd6ee-131">Client</span></span>  
 <span data-ttu-id="cd6ee-132">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="cd6ee-133">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cd6ee-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="cd6ee-134">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="cd6ee-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="cd6ee-135">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="cd6ee-136">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="cd6ee-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cd6ee-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="cd6ee-138">Kod</span><span class="sxs-lookup"><span data-stu-id="cd6ee-138">Code</span></span>  
 <span data-ttu-id="cd6ee-139">Poniższy kod przedstawia podstawowe klienta WCF, który uzyskuje dostęp do punktu końcowego niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="cd6ee-140">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="cd6ee-140">Client Configuration</span></span>  
 <span data-ttu-id="cd6ee-141">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="cd6ee-141">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd6ee-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd6ee-142">See also</span></span>

- [<span data-ttu-id="cd6ee-143">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cd6ee-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [<span data-ttu-id="cd6ee-144">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cd6ee-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="cd6ee-145">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="cd6ee-145">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
