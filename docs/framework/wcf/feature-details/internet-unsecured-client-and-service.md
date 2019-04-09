---
title: Niezabezpieczony klient internetowy i usługa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: ca6b028ef20095d6faeb125151772eedf1500fa0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133760"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="51b68-102">Niezabezpieczony klient internetowy i usługa</span><span class="sxs-lookup"><span data-stu-id="51b68-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="51b68-103">Na poniższej ilustracji przedstawiono przykład publiczne, niezabezpieczony klient usługi Windows Communication Foundation (WCF) i usługi:</span><span class="sxs-lookup"><span data-stu-id="51b68-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Zrzut ekranu pokazujący niezabezpieczony scenariusz Internet](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="51b68-105">Cechy</span><span class="sxs-lookup"><span data-stu-id="51b68-105">Characteristic</span></span>|<span data-ttu-id="51b68-106">Opis</span><span class="sxs-lookup"><span data-stu-id="51b68-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="51b68-107">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="51b68-107">Security Mode</span></span>|<span data-ttu-id="51b68-108">Brak</span><span class="sxs-lookup"><span data-stu-id="51b68-108">None</span></span>|  
|<span data-ttu-id="51b68-109">Transport</span><span class="sxs-lookup"><span data-stu-id="51b68-109">Transport</span></span>|<span data-ttu-id="51b68-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="51b68-110">HTTP</span></span>|  
|<span data-ttu-id="51b68-111">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="51b68-111">Binding</span></span>|<xref:System.ServiceModel.BasicHttpBinding> <span data-ttu-id="51b68-112">w kodzie lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51b68-112">in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="51b68-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="51b68-113">Interoperability</span></span>|<span data-ttu-id="51b68-114">Za pomocą istniejących klientów usługi sieci Web i usług</span><span class="sxs-lookup"><span data-stu-id="51b68-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="51b68-115">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="51b68-115">Authentication</span></span>|<span data-ttu-id="51b68-116">Brak</span><span class="sxs-lookup"><span data-stu-id="51b68-116">None</span></span>|  
|<span data-ttu-id="51b68-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="51b68-117">Integrity</span></span>|<span data-ttu-id="51b68-118">Brak</span><span class="sxs-lookup"><span data-stu-id="51b68-118">None</span></span>|  
|<span data-ttu-id="51b68-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="51b68-119">Confidentiality</span></span>|<span data-ttu-id="51b68-120">Brak</span><span class="sxs-lookup"><span data-stu-id="51b68-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="51b68-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="51b68-121">Service</span></span>  
 <span data-ttu-id="51b68-122">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="51b68-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="51b68-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="51b68-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="51b68-124">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51b68-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="51b68-125">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="51b68-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="51b68-126">Kod</span><span class="sxs-lookup"><span data-stu-id="51b68-126">Code</span></span>  
 <span data-ttu-id="51b68-127">Poniższy kod przedstawia sposób tworzenia punktu końcowego z żadnych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="51b68-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="51b68-128">Domyślnie <xref:System.ServiceModel.BasicHttpBinding> została ustawiona na tryb zabezpieczeń <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="51b68-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="51b68-129">Konfiguracja usługi</span><span class="sxs-lookup"><span data-stu-id="51b68-129">Service Configuration</span></span>  
 <span data-ttu-id="51b68-130">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="51b68-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="51b68-131">Klient</span><span class="sxs-lookup"><span data-stu-id="51b68-131">Client</span></span>  
 <span data-ttu-id="51b68-132">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="51b68-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="51b68-133">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="51b68-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="51b68-134">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="51b68-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="51b68-135">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="51b68-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="51b68-136">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="51b68-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="51b68-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="51b68-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="51b68-138">Kod</span><span class="sxs-lookup"><span data-stu-id="51b68-138">Code</span></span>  
 <span data-ttu-id="51b68-139">Poniższy kod przedstawia podstawowe klienta WCF, który uzyskuje dostęp do punktu końcowego niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="51b68-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="51b68-140">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="51b68-140">Client Configuration</span></span>  
 <span data-ttu-id="51b68-141">Poniższy kod konfiguruje klienta.</span><span class="sxs-lookup"><span data-stu-id="51b68-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51b68-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51b68-142">See also</span></span>

- [<span data-ttu-id="51b68-143">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="51b68-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [<span data-ttu-id="51b68-144">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="51b68-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="51b68-145">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="51b68-145">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
