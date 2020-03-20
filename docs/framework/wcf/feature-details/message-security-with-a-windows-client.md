---
title: Zabezpieczanie komunikatów za pomocą klienta systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: bcfeb5f863b1dd6cf9171a7fc53c8984ea68ecb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184628"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="a8291-102">Zabezpieczanie komunikatów za pomocą klienta systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a8291-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="a8291-103">W tym scenariuszu pokazano klienta i serwera fundacji komunikacji systemu Windows (WCF) zabezpieczonego trybem zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8291-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="a8291-104">Klient i usługa są uwierzytelniane przy użyciu poświadczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a8291-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="a8291-105">![Zabezpieczenia wiadomości za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="a8291-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="a8291-106">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="a8291-106">Characteristic</span></span>|<span data-ttu-id="a8291-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a8291-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a8291-108">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a8291-108">Security Mode</span></span>|<span data-ttu-id="a8291-109">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a8291-109">Message</span></span>|  
|<span data-ttu-id="a8291-110">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="a8291-110">Interoperability</span></span>|<span data-ttu-id="a8291-111">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="a8291-111">WCF Only</span></span>|  
|<span data-ttu-id="a8291-112">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="a8291-112">Authentication (Server)</span></span>|<span data-ttu-id="a8291-113">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="a8291-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="a8291-114">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="a8291-114">Authentication (Client)</span></span>|<span data-ttu-id="a8291-115">Wzajemne uwierzytelnianie serwera i klienta</span><span class="sxs-lookup"><span data-stu-id="a8291-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="a8291-116">Integralność</span><span class="sxs-lookup"><span data-stu-id="a8291-116">Integrity</span></span>|<span data-ttu-id="a8291-117">Tak, używanie wspólnego kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a8291-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="a8291-118">Poufność</span><span class="sxs-lookup"><span data-stu-id="a8291-118">Confidentiality</span></span>|<span data-ttu-id="a8291-119">Tak, używanie wspólnego kontekstu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a8291-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="a8291-120">Transport</span><span class="sxs-lookup"><span data-stu-id="a8291-120">Transport</span></span>|<span data-ttu-id="a8291-121">Netto. Tcp</span><span class="sxs-lookup"><span data-stu-id="a8291-121">NET.TCP</span></span>|  
|<span data-ttu-id="a8291-122">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="a8291-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="a8291-123">Usługa</span><span class="sxs-lookup"><span data-stu-id="a8291-123">Service</span></span>  
 <span data-ttu-id="a8291-124">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a8291-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a8291-125">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a8291-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="a8291-126">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a8291-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="a8291-127">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a8291-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a8291-128">Code</span><span class="sxs-lookup"><span data-stu-id="a8291-128">Code</span></span>  
 <span data-ttu-id="a8291-129">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa zabezpieczeń wiadomości w celu ustanowienia bezpiecznego kontekstu z komputerem z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="a8291-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="a8291-130">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="a8291-130">Configuration</span></span>  
 <span data-ttu-id="a8291-131">Zamiast kodu można użyć następującej konfiguracji do skonfigurowania usługi:</span><span class="sxs-lookup"><span data-stu-id="a8291-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a8291-132">Klient</span><span class="sxs-lookup"><span data-stu-id="a8291-132">Client</span></span>  
 <span data-ttu-id="a8291-133">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="a8291-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a8291-134">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a8291-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="a8291-135">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="a8291-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="a8291-136">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="a8291-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a8291-137">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="a8291-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a8291-138">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a8291-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="a8291-139">Code</span><span class="sxs-lookup"><span data-stu-id="a8291-139">Code</span></span>  
 <span data-ttu-id="a8291-140">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="a8291-140">The following code creates a client.</span></span> <span data-ttu-id="a8291-141">Powiązanie jest zabezpieczeń trybu wiadomości, a typ `Windows`poświadczeń klienta jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="a8291-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="a8291-142">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="a8291-142">Configuration</span></span>  
 <span data-ttu-id="a8291-143">Następująca konfiguracja jest używana do ustawiania właściwości klienta.</span><span class="sxs-lookup"><span data-stu-id="a8291-143">The following configuration is used to set the client properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8291-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8291-144">See also</span></span>

- [<span data-ttu-id="a8291-145">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a8291-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="a8291-146">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a8291-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
