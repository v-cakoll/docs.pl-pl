---
title: Niezabezpieczony klient i usługa w intranecie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 2fa13a12a377cc16a95318367605d8b5d92769a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184686"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="301eb-102">Niezabezpieczony klient i usługa w intranecie</span><span class="sxs-lookup"><span data-stu-id="301eb-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="301eb-103">Na poniższej ilustracji przedstawiono prostą usługę Windows Communication Foundation (WCF) opracowaną w celu dostarczania informacji o bezpiecznej sieci prywatnej aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="301eb-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="301eb-104">Zabezpieczenia nie jest wymagane, ponieważ dane mają niewielkie znaczenie, oczekuje się, że sieć będzie z natury bezpieczna lub zabezpieczenia są dostarczane przez warstwę poniżej infrastruktury WCF.</span><span class="sxs-lookup"><span data-stu-id="301eb-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Scenariusz niezabezpieczonego klienta i usługi intranetu.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="301eb-106">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="301eb-106">Characteristic</span></span>|<span data-ttu-id="301eb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="301eb-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="301eb-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="301eb-108">Security Mode</span></span>|<span data-ttu-id="301eb-109">Brak</span><span class="sxs-lookup"><span data-stu-id="301eb-109">None</span></span>|  
|<span data-ttu-id="301eb-110">Transport</span><span class="sxs-lookup"><span data-stu-id="301eb-110">Transport</span></span>|<span data-ttu-id="301eb-111">TCP</span><span class="sxs-lookup"><span data-stu-id="301eb-111">TCP</span></span>|  
|<span data-ttu-id="301eb-112">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="301eb-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="301eb-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="301eb-113">Interoperability</span></span>|<span data-ttu-id="301eb-114">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="301eb-114">WCF only</span></span>|  
|<span data-ttu-id="301eb-115">Authentication</span><span class="sxs-lookup"><span data-stu-id="301eb-115">Authentication</span></span>|<span data-ttu-id="301eb-116">Brak</span><span class="sxs-lookup"><span data-stu-id="301eb-116">None</span></span>|  
|<span data-ttu-id="301eb-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="301eb-117">Integrity</span></span>|<span data-ttu-id="301eb-118">Brak</span><span class="sxs-lookup"><span data-stu-id="301eb-118">None</span></span>|  
|<span data-ttu-id="301eb-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="301eb-119">Confidentiality</span></span>|<span data-ttu-id="301eb-120">Brak</span><span class="sxs-lookup"><span data-stu-id="301eb-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="301eb-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="301eb-121">Service</span></span>  
 <span data-ttu-id="301eb-122">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="301eb-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="301eb-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="301eb-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="301eb-124">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="301eb-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="301eb-125">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="301eb-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="301eb-126">Code</span><span class="sxs-lookup"><span data-stu-id="301eb-126">Code</span></span>  
 <span data-ttu-id="301eb-127">Poniższy kod pokazuje, jak utworzyć punkt końcowy bez zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="301eb-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="301eb-128">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="301eb-128">Configuration</span></span>  
 <span data-ttu-id="301eb-129">Poniższy kod konfiguruje ten sam punkt końcowy przy użyciu konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="301eb-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="301eb-130">Klient</span><span class="sxs-lookup"><span data-stu-id="301eb-130">Client</span></span>  
 <span data-ttu-id="301eb-131">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="301eb-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="301eb-132">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="301eb-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="301eb-133">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="301eb-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="301eb-134">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="301eb-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="301eb-135">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="301eb-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="301eb-136">Przykład:</span><span class="sxs-lookup"><span data-stu-id="301eb-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="301eb-137">Code</span><span class="sxs-lookup"><span data-stu-id="301eb-137">Code</span></span>  
 <span data-ttu-id="301eb-138">Poniższy kod przedstawia podstawowy klient WCF, który uzyskuje dostęp do niezabezpieczonego punktu końcowego przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="301eb-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="301eb-139">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="301eb-139">Configuration</span></span>  
 <span data-ttu-id="301eb-140">Następujący kod konfiguracji ma zastosowanie do klienta:</span><span class="sxs-lookup"><span data-stu-id="301eb-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="301eb-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="301eb-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="301eb-142">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="301eb-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="301eb-143">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="301eb-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
