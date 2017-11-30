---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
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
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 68550646f806b30f072b4270a336698011db54d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="95058-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95058-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="95058-103">Poniżej przedstawiono scenariusz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta i usługi zabezpieczonej przez zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95058-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by Windows security.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95058-104">programowania, zobacz [porady: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="95058-104"> programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="95058-105">Intranet usługi sieci Web Wyświetla informacje o zasoby ludzkie.</span><span class="sxs-lookup"><span data-stu-id="95058-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="95058-106">Klient jest aplikacją formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95058-106">The client is a Windows Form application.</span></span> <span data-ttu-id="95058-107">Aplikacja jest wdrażana w domenie za pomocą kontrolera protokołu Kerberos, zabezpieczanie domeny.</span><span class="sxs-lookup"><span data-stu-id="95058-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="95058-108">![Transport zabezpieczeń z uwierzytelnianiem systemu Windows](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="95058-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="95058-109">Cechy</span><span class="sxs-lookup"><span data-stu-id="95058-109">Characteristic</span></span>|<span data-ttu-id="95058-110">Opis</span><span class="sxs-lookup"><span data-stu-id="95058-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="95058-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95058-111">Security Mode</span></span>|<span data-ttu-id="95058-112">Transportu</span><span class="sxs-lookup"><span data-stu-id="95058-112">Transport</span></span>|  
|<span data-ttu-id="95058-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="95058-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95058-114">tylko</span><span class="sxs-lookup"><span data-stu-id="95058-114"> only</span></span>|  
|<span data-ttu-id="95058-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="95058-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="95058-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="95058-116">Authentication (Client)</span></span>|<span data-ttu-id="95058-117">Tak (za pomocą zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="95058-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="95058-118">Tak (za pomocą zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="95058-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="95058-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="95058-119">Integrity</span></span>|<span data-ttu-id="95058-120">Tak</span><span class="sxs-lookup"><span data-stu-id="95058-120">Yes</span></span>|  
|<span data-ttu-id="95058-121">Poufność</span><span class="sxs-lookup"><span data-stu-id="95058-121">Confidentiality</span></span>|<span data-ttu-id="95058-122">Tak</span><span class="sxs-lookup"><span data-stu-id="95058-122">Yes</span></span>|  
|<span data-ttu-id="95058-123">Transportu</span><span class="sxs-lookup"><span data-stu-id="95058-123">Transport</span></span>|<span data-ttu-id="95058-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="95058-124">NET.TCP</span></span>|  
|<span data-ttu-id="95058-125">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="95058-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="95058-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="95058-126">Service</span></span>  
 <span data-ttu-id="95058-127">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="95058-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="95058-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="95058-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="95058-129">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="95058-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="95058-130">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="95058-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="95058-131">Kod</span><span class="sxs-lookup"><span data-stu-id="95058-131">Code</span></span>  
 <span data-ttu-id="95058-132">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95058-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="95058-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="95058-133">Configuration</span></span>  
 <span data-ttu-id="95058-134">Następującej konfiguracji można zamiast kodu do konfigurowania punktu końcowego usługi:</span><span class="sxs-lookup"><span data-stu-id="95058-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="95058-135">Klient</span><span class="sxs-lookup"><span data-stu-id="95058-135">Client</span></span>  
 <span data-ttu-id="95058-136">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="95058-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="95058-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="95058-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="95058-138">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="95058-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="95058-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="95058-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="95058-140">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="95058-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="95058-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="95058-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="95058-142">Kod</span><span class="sxs-lookup"><span data-stu-id="95058-142">Code</span></span>  
 <span data-ttu-id="95058-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="95058-143">The following code creates the client.</span></span> <span data-ttu-id="95058-144">Powiązanie jest skonfigurowany do używania tryb zabezpieczeń transportu z transportu TCP typu poświadczeń klienta do systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95058-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="95058-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="95058-145">Configuration</span></span>  
 <span data-ttu-id="95058-146">Następującej konfiguracji można zamiast kodu można utworzyć klienta.</span><span class="sxs-lookup"><span data-stu-id="95058-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95058-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95058-147">See Also</span></span>  
 [<span data-ttu-id="95058-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="95058-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="95058-149">Porady: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95058-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="95058-150">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="95058-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
