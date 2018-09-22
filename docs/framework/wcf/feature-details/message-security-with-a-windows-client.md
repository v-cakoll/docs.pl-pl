---
title: Zabezpieczanie komunikatów za pomocą klienta systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 34f6078baba86868fa03f37873731c39e73ac81f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568784"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="57683-102">Zabezpieczanie komunikatów za pomocą klienta systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57683-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="57683-103">W tym scenariuszu pokazano klienta usługi Windows Communication Foundation (WCF) i serwer zabezpieczony przez trybu zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="57683-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="57683-104">Klient i usługa są uwierzytelniane przy użyciu poświadczeń Windows.</span><span class="sxs-lookup"><span data-stu-id="57683-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="57683-105">![Zabezpieczenia za pomocą klienta Windows wiadomości](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="57683-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="57683-106">Cechy</span><span class="sxs-lookup"><span data-stu-id="57683-106">Characteristic</span></span>|<span data-ttu-id="57683-107">Opis</span><span class="sxs-lookup"><span data-stu-id="57683-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="57683-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="57683-108">Security Mode</span></span>|<span data-ttu-id="57683-109">Komunikat</span><span class="sxs-lookup"><span data-stu-id="57683-109">Message</span></span>|  
|<span data-ttu-id="57683-110">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="57683-110">Interoperability</span></span>|<span data-ttu-id="57683-111">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="57683-111">WCF Only</span></span>|  
|<span data-ttu-id="57683-112">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="57683-112">Authentication (Server)</span></span>|<span data-ttu-id="57683-113">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="57683-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="57683-114">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="57683-114">Authentication (Client)</span></span>|<span data-ttu-id="57683-115">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="57683-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="57683-116">Integralność</span><span class="sxs-lookup"><span data-stu-id="57683-116">Integrity</span></span>|<span data-ttu-id="57683-117">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="57683-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="57683-118">Poufność</span><span class="sxs-lookup"><span data-stu-id="57683-118">Confidentiality</span></span>|<span data-ttu-id="57683-119">Tak, za pomocą kontekstu zabezpieczeń udostępnionego</span><span class="sxs-lookup"><span data-stu-id="57683-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="57683-120">Transportu</span><span class="sxs-lookup"><span data-stu-id="57683-120">Transport</span></span>|<span data-ttu-id="57683-121">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="57683-121">NET.TCP</span></span>|  
|<span data-ttu-id="57683-122">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="57683-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="57683-123">Usługa</span><span class="sxs-lookup"><span data-stu-id="57683-123">Service</span></span>  
 <span data-ttu-id="57683-124">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="57683-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="57683-125">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="57683-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="57683-126">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="57683-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="57683-127">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="57683-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="57683-128">Kod</span><span class="sxs-lookup"><span data-stu-id="57683-128">Code</span></span>  
 <span data-ttu-id="57683-129">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który używa zabezpieczenia komunikatów w celu ustanowienia bezpiecznej kontekstu z maszyną Windows.</span><span class="sxs-lookup"><span data-stu-id="57683-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="57683-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="57683-130">Configuration</span></span>  
 <span data-ttu-id="57683-131">Następująca konfiguracja może służyć zamiast kodu do skonfigurowania usługi:</span><span class="sxs-lookup"><span data-stu-id="57683-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="57683-132">Klient</span><span class="sxs-lookup"><span data-stu-id="57683-132">Client</span></span>  
 <span data-ttu-id="57683-133">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="57683-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="57683-134">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="57683-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="57683-135">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="57683-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="57683-136">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="57683-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="57683-137">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="57683-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="57683-138">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="57683-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="57683-139">Kod</span><span class="sxs-lookup"><span data-stu-id="57683-139">Code</span></span>  
 <span data-ttu-id="57683-140">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="57683-140">The following code creates a client.</span></span> <span data-ttu-id="57683-141">Powiązanie jest komunikat tryb zabezpieczeń, oraz typu poświadczeń klienta jest ustawiona na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="57683-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="57683-142">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="57683-142">Configuration</span></span>  
 <span data-ttu-id="57683-143">Następująca konfiguracja służy do ustawiania właściwości klienta.</span><span class="sxs-lookup"><span data-stu-id="57683-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57683-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57683-144">See Also</span></span>  
 [<span data-ttu-id="57683-145">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="57683-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="57683-146">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="57683-146">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
