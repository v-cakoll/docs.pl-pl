---
title: "Niezabezpieczony klient i usługa w intranecie"
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
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0cfd98d401921c47bd85f8d4089e3efb437ca6b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="a2297-102">Niezabezpieczony klient i usługa w intranecie</span><span class="sxs-lookup"><span data-stu-id="a2297-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="a2297-103">Na poniższej ilustracji przedstawiono prosty [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi opracowany, aby podać informacje w sieci prywatnej bezpieczny do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2297-103">The following illustration depicts a simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="a2297-104">Zabezpieczeń nie jest wymagana, ponieważ dane są o niskiej ważności, powinien być z założenia bezpiecznej sieci lub zabezpieczeń jest zapewniana przez warstwę poniżej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a2297-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="a2297-105">![Niezabezpieczony klient sieci intranet i scenariusz obsługi](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="a2297-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="a2297-106">Cechy</span><span class="sxs-lookup"><span data-stu-id="a2297-106">Characteristic</span></span>|<span data-ttu-id="a2297-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2297-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a2297-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a2297-108">Security Mode</span></span>|<span data-ttu-id="a2297-109">Brak</span><span class="sxs-lookup"><span data-stu-id="a2297-109">None</span></span>|  
|<span data-ttu-id="a2297-110">Transportu</span><span class="sxs-lookup"><span data-stu-id="a2297-110">Transport</span></span>|<span data-ttu-id="a2297-111">TCP</span><span class="sxs-lookup"><span data-stu-id="a2297-111">TCP</span></span>|  
|<span data-ttu-id="a2297-112">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="a2297-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="a2297-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="a2297-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a2297-114">tylko</span><span class="sxs-lookup"><span data-stu-id="a2297-114"> only</span></span>|  
|<span data-ttu-id="a2297-115">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="a2297-115">Authentication</span></span>|<span data-ttu-id="a2297-116">Brak</span><span class="sxs-lookup"><span data-stu-id="a2297-116">None</span></span>|  
|<span data-ttu-id="a2297-117">Integralność</span><span class="sxs-lookup"><span data-stu-id="a2297-117">Integrity</span></span>|<span data-ttu-id="a2297-118">Brak</span><span class="sxs-lookup"><span data-stu-id="a2297-118">None</span></span>|  
|<span data-ttu-id="a2297-119">Poufność</span><span class="sxs-lookup"><span data-stu-id="a2297-119">Confidentiality</span></span>|<span data-ttu-id="a2297-120">Brak</span><span class="sxs-lookup"><span data-stu-id="a2297-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="a2297-121">Usługa</span><span class="sxs-lookup"><span data-stu-id="a2297-121">Service</span></span>  
 <span data-ttu-id="a2297-122">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a2297-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a2297-123">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a2297-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a2297-124">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="a2297-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="a2297-125">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a2297-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a2297-126">Kod</span><span class="sxs-lookup"><span data-stu-id="a2297-126">Code</span></span>  
 <span data-ttu-id="a2297-127">Poniższy kod przedstawia sposób tworzenia punktu końcowego z żadnych zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="a2297-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a2297-128">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a2297-128">Configuration</span></span>  
 <span data-ttu-id="a2297-129">Poniższy kod konfiguruje tego samego punktu końcowego za pomocą konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a2297-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a2297-130">Klient</span><span class="sxs-lookup"><span data-stu-id="a2297-130">Client</span></span>  
 <span data-ttu-id="a2297-131">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a2297-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a2297-132">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a2297-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="a2297-133">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="a2297-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="a2297-134">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a2297-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a2297-135">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="a2297-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a2297-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a2297-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a2297-137">Kod</span><span class="sxs-lookup"><span data-stu-id="a2297-137">Code</span></span>  
 <span data-ttu-id="a2297-138">Poniższy kod przedstawia podstawowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który uzyskuje dostęp do punktu końcowego niezabezpieczona przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="a2297-138">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="a2297-139">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a2297-139">Configuration</span></span>  
 <span data-ttu-id="a2297-140">Poniższy kod konfiguracji ma zastosowanie do klienta:</span><span class="sxs-lookup"><span data-stu-id="a2297-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2297-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2297-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="a2297-142">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a2297-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="a2297-143">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="a2297-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
