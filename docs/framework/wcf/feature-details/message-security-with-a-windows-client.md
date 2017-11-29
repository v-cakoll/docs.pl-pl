---
title: "Zabezpieczanie komunikatów za pomocą klienta systemu Windows"
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
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f2a9f2f44f5dfd44f00ae580423b1d2781ae5bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="2758f-102">Zabezpieczanie komunikatów za pomocą klienta systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2758f-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="2758f-103">W tym scenariuszu pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] na kliencie i serwerze zabezpieczone przez tryb zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2758f-103">This scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and server secured by message security mode.</span></span> <span data-ttu-id="2758f-104">Klient i usługa są uwierzytelniane przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2758f-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="2758f-105">![Zabezpieczenia za pomocą klienta systemu Windows wiadomości](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="2758f-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="2758f-106">Cechy</span><span class="sxs-lookup"><span data-stu-id="2758f-106">Characteristic</span></span>|<span data-ttu-id="2758f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2758f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2758f-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2758f-108">Security Mode</span></span>|<span data-ttu-id="2758f-109">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2758f-109">Message</span></span>|  
|<span data-ttu-id="2758f-110">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="2758f-110">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2758f-111">Tylko</span><span class="sxs-lookup"><span data-stu-id="2758f-111"> Only</span></span>|  
|<span data-ttu-id="2758f-112">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="2758f-112">Authentication (Server)</span></span>|<span data-ttu-id="2758f-113">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="2758f-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="2758f-114">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="2758f-114">Authentication (Client)</span></span>|<span data-ttu-id="2758f-115">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="2758f-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="2758f-116">Integralność</span><span class="sxs-lookup"><span data-stu-id="2758f-116">Integrity</span></span>|<span data-ttu-id="2758f-117">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="2758f-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="2758f-118">Poufność</span><span class="sxs-lookup"><span data-stu-id="2758f-118">Confidentiality</span></span>|<span data-ttu-id="2758f-119">Tak, przy użyciu kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="2758f-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="2758f-120">Transportu</span><span class="sxs-lookup"><span data-stu-id="2758f-120">Transport</span></span>|<span data-ttu-id="2758f-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="2758f-121">NET.TCP</span></span>|  
|<span data-ttu-id="2758f-122">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="2758f-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="2758f-123">Usługa</span><span class="sxs-lookup"><span data-stu-id="2758f-123">Service</span></span>  
 <span data-ttu-id="2758f-124">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="2758f-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2758f-125">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2758f-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="2758f-126">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="2758f-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="2758f-127">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2758f-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2758f-128">Kod</span><span class="sxs-lookup"><span data-stu-id="2758f-128">Code</span></span>  
 <span data-ttu-id="2758f-129">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, korzystającą z zabezpieczeń wiadomości w celu ustanowienia bezpiecznego kontekstu komputera z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="2758f-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="2758f-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2758f-130">Configuration</span></span>  
 <span data-ttu-id="2758f-131">Następującej konfiguracji można zamiast kodu — Konfiguracja usługi:</span><span class="sxs-lookup"><span data-stu-id="2758f-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="2758f-132">Klient</span><span class="sxs-lookup"><span data-stu-id="2758f-132">Client</span></span>  
 <span data-ttu-id="2758f-133">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="2758f-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2758f-134">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2758f-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="2758f-135">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="2758f-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="2758f-136">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2758f-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="2758f-137">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="2758f-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="2758f-138">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2758f-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="2758f-139">Kod</span><span class="sxs-lookup"><span data-stu-id="2758f-139">Code</span></span>  
 <span data-ttu-id="2758f-140">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="2758f-140">The following code creates a client.</span></span> <span data-ttu-id="2758f-141">Powiązanie jest komunikat trybu zabezpieczeń i ma ustawioną wartość typu poświadczeń klienta `Windows`.</span><span class="sxs-lookup"><span data-stu-id="2758f-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="2758f-142">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2758f-142">Configuration</span></span>  
 <span data-ttu-id="2758f-143">Następująca konfiguracja służy do ustawiania właściwości klienta.</span><span class="sxs-lookup"><span data-stu-id="2758f-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2758f-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2758f-144">See Also</span></span>  
 [<span data-ttu-id="2758f-145">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2758f-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="2758f-146">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="2758f-146">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
