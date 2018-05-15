---
title: Niezabezpieczony klient i usługa w intranecie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d08e8b5f9a22fc558af6f8f7c2ca3049e4a692ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="4d5d2-102">Niezabezpieczony klient i usługa w intranecie</span><span class="sxs-lookup"><span data-stu-id="4d5d2-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="4d5d2-103">Na poniższej ilustracji przedstawiono prosty opracowany, aby podać informacje w sieci prywatnej bezpieczny do aplikacji WCF usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4d5d2-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="4d5d2-104">Zabezpieczeń nie jest wymagana, ponieważ dane są o niskiej ważności, powinien być z założenia bezpiecznej sieci lub zabezpieczeń jest zapewniana przez warstwy poniżej infrastruktura WCF.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="4d5d2-105">![Niezabezpieczony klient sieci intranet i scenariusz obsługi](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="4d5d2-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="4d5d2-106">Cechy</span><span class="sxs-lookup"><span data-stu-id="4d5d2-106">Characteristic</span></span>|<span data-ttu-id="4d5d2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d5d2-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4d5d2-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4d5d2-108">Security Mode</span></span>|<span data-ttu-id="4d5d2-109">Brak</span><span class="sxs-lookup"><span data-stu-id="4d5d2-109">None</span></span>|  
|<span data-ttu-id="4d5d2-110">Transportu</span><span class="sxs-lookup"><span data-stu-id="4d5d2-110">Transport</span></span>|<span data-ttu-id="4d5d2-111">TCP</span><span class="sxs-lookup"><span data-stu-id="4d5d2-111">TCP</span></span>|  
|<span data-ttu-id="4d5d2-112">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="4d5d2-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="4d5d2-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="4d5d2-113">Interoperability</span></span>|<span data-ttu-id="4d5d2-114">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="4d5d2-114">WCF only</span></span>|  
|<span data-ttu-id="4d5d2-115">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="4d5d2-115">Authentication</span></span>|<span data-ttu-id="4d5d2-116">Brak</span><span class="sxs-lookup"><span data-stu-id="4d5d2-116">None</span></span>|  
|<span data-ttu-id="4d5d2-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="4d5d2-117">Integrity</span></span>|<span data-ttu-id="4d5d2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="4d5d2-118">None</span></span>|  
|<span data-ttu-id="4d5d2-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="4d5d2-119">Confidentiality</span></span>|<span data-ttu-id="4d5d2-120">Brak</span><span class="sxs-lookup"><span data-stu-id="4d5d2-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="4d5d2-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="4d5d2-121">Service</span></span>  
 <span data-ttu-id="4d5d2-122">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4d5d2-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="4d5d2-124">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="4d5d2-125">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d5d2-126">Kod</span><span class="sxs-lookup"><span data-stu-id="4d5d2-126">Code</span></span>  
 <span data-ttu-id="4d5d2-127">Poniższy kod przedstawia sposób tworzenia punktu końcowego z żadnych zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="4d5d2-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4d5d2-128">Configuration</span></span>  
 <span data-ttu-id="4d5d2-129">Poniższy kod konfiguruje tego samego punktu końcowego za pomocą konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="4d5d2-130">Klient</span><span class="sxs-lookup"><span data-stu-id="4d5d2-130">Client</span></span>  
 <span data-ttu-id="4d5d2-131">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4d5d2-132">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="4d5d2-133">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="4d5d2-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="4d5d2-134">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4d5d2-135">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4d5d2-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="4d5d2-137">Kod</span><span class="sxs-lookup"><span data-stu-id="4d5d2-137">Code</span></span>  
 <span data-ttu-id="4d5d2-138">Poniższy kod przedstawia podstawowe klienta WCF, który uzyskuje dostęp do punktu końcowego niezabezpieczona przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="4d5d2-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="4d5d2-139">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4d5d2-139">Configuration</span></span>  
 <span data-ttu-id="4d5d2-140">Poniższy kod konfiguracji ma zastosowanie do klienta:</span><span class="sxs-lookup"><span data-stu-id="4d5d2-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d5d2-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d5d2-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="4d5d2-142">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4d5d2-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="4d5d2-143">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="4d5d2-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
