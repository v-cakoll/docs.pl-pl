---
title: Niezabezpieczony klient i usługa w intranecie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: eb165b69e1312363a8cc7c1a3ceea66a422d54f7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200114"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="72243-102">Niezabezpieczony klient i usługa w intranecie</span><span class="sxs-lookup"><span data-stu-id="72243-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="72243-103">Poniższa ilustracja przedstawia prostą usługę Windows Communication Foundation (WCF) opracowany, aby udostępniać informacje o bezpiecznej sieci prywatnej dla aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="72243-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="72243-104">Zabezpieczeń nie jest wymagany, dane o niskiej ważności, powinien być założenia bezpieczne sieci, ponieważ zabezpieczenia przez warstwę poniżej infrastruktury usług WCF.</span><span class="sxs-lookup"><span data-stu-id="72243-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="72243-105">![Niezabezpieczony klient i intranecie scenariusz obsługi](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="72243-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="72243-106">Cechy</span><span class="sxs-lookup"><span data-stu-id="72243-106">Characteristic</span></span>|<span data-ttu-id="72243-107">Opis</span><span class="sxs-lookup"><span data-stu-id="72243-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="72243-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="72243-108">Security Mode</span></span>|<span data-ttu-id="72243-109">Brak</span><span class="sxs-lookup"><span data-stu-id="72243-109">None</span></span>|  
|<span data-ttu-id="72243-110">Transportu</span><span class="sxs-lookup"><span data-stu-id="72243-110">Transport</span></span>|<span data-ttu-id="72243-111">TCP</span><span class="sxs-lookup"><span data-stu-id="72243-111">TCP</span></span>|  
|<span data-ttu-id="72243-112">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="72243-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="72243-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="72243-113">Interoperability</span></span>|<span data-ttu-id="72243-114">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="72243-114">WCF only</span></span>|  
|<span data-ttu-id="72243-115">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="72243-115">Authentication</span></span>|<span data-ttu-id="72243-116">Brak</span><span class="sxs-lookup"><span data-stu-id="72243-116">None</span></span>|  
|<span data-ttu-id="72243-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="72243-117">Integrity</span></span>|<span data-ttu-id="72243-118">Brak</span><span class="sxs-lookup"><span data-stu-id="72243-118">None</span></span>|  
|<span data-ttu-id="72243-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="72243-119">Confidentiality</span></span>|<span data-ttu-id="72243-120">Brak</span><span class="sxs-lookup"><span data-stu-id="72243-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="72243-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="72243-121">Service</span></span>  
 <span data-ttu-id="72243-122">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="72243-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="72243-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="72243-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="72243-124">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72243-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="72243-125">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="72243-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="72243-126">Kod</span><span class="sxs-lookup"><span data-stu-id="72243-126">Code</span></span>  
 <span data-ttu-id="72243-127">Poniższy kod przedstawia sposób tworzenia punktu końcowego z żadnych zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="72243-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="72243-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="72243-128">Configuration</span></span>  
 <span data-ttu-id="72243-129">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="72243-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="72243-130">Klient</span><span class="sxs-lookup"><span data-stu-id="72243-130">Client</span></span>  
 <span data-ttu-id="72243-131">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="72243-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="72243-132">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="72243-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="72243-133">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="72243-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="72243-134">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="72243-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="72243-135">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="72243-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="72243-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="72243-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="72243-137">Kod</span><span class="sxs-lookup"><span data-stu-id="72243-137">Code</span></span>  
 <span data-ttu-id="72243-138">Poniższy kod przedstawia podstawowe klienta WCF, który uzyskuje dostęp do niezabezpieczonych punkt końcowy korzystający z protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="72243-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="72243-139">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="72243-139">Configuration</span></span>  
 <span data-ttu-id="72243-140">Poniższy kod konfiguracji ma zastosowanie do klienta:</span><span class="sxs-lookup"><span data-stu-id="72243-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72243-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72243-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="72243-142">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="72243-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="72243-143">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="72243-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
