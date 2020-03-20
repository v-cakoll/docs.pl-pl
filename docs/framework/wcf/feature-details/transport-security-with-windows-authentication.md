---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184314"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="bf35a-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bf35a-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="bf35a-103">Poniższy scenariusz przedstawia klienta i usługę Windows Communication Foundation (WCF) zabezpieczoną przez zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf35a-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="bf35a-104">Aby uzyskać więcej informacji na temat programowania, zobacz [Jak: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="bf35a-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="bf35a-105">W intraneenejnie sieci Web są wyświetlane informacje o zasobach ludzkich.</span><span class="sxs-lookup"><span data-stu-id="bf35a-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="bf35a-106">Klient jest aplikacją formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf35a-106">The client is a Windows Form application.</span></span> <span data-ttu-id="bf35a-107">Aplikacja jest wdrażana w domenie z kontrolerem Kerberos zabezpieczającym domenę.</span><span class="sxs-lookup"><span data-stu-id="bf35a-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpieczenia transportu za pomocą uwierzytelniania systemu Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="bf35a-109">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="bf35a-109">Characteristic</span></span>|<span data-ttu-id="bf35a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bf35a-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="bf35a-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bf35a-111">Security Mode</span></span>|<span data-ttu-id="bf35a-112">Transport</span><span class="sxs-lookup"><span data-stu-id="bf35a-112">Transport</span></span>|  
|<span data-ttu-id="bf35a-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="bf35a-113">Interoperability</span></span>|<span data-ttu-id="bf35a-114">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="bf35a-114">WCF only</span></span>|  
|<span data-ttu-id="bf35a-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="bf35a-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="bf35a-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="bf35a-116">Authentication (Client)</span></span>|<span data-ttu-id="bf35a-117">Tak (przy użyciu zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="bf35a-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="bf35a-118">Tak (przy użyciu zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="bf35a-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="bf35a-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="bf35a-119">Integrity</span></span>|<span data-ttu-id="bf35a-120">Tak</span><span class="sxs-lookup"><span data-stu-id="bf35a-120">Yes</span></span>|  
|<span data-ttu-id="bf35a-121">Poufność</span><span class="sxs-lookup"><span data-stu-id="bf35a-121">Confidentiality</span></span>|<span data-ttu-id="bf35a-122">Tak</span><span class="sxs-lookup"><span data-stu-id="bf35a-122">Yes</span></span>|  
|<span data-ttu-id="bf35a-123">Transport</span><span class="sxs-lookup"><span data-stu-id="bf35a-123">Transport</span></span>|<span data-ttu-id="bf35a-124">Netto. Tcp</span><span class="sxs-lookup"><span data-stu-id="bf35a-124">NET.TCP</span></span>|  
|<span data-ttu-id="bf35a-125">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="bf35a-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="bf35a-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="bf35a-126">Service</span></span>  
 <span data-ttu-id="bf35a-127">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="bf35a-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="bf35a-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bf35a-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="bf35a-129">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bf35a-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="bf35a-130">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="bf35a-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bf35a-131">Code</span><span class="sxs-lookup"><span data-stu-id="bf35a-131">Code</span></span>  
 <span data-ttu-id="bf35a-132">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa zabezpieczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf35a-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="bf35a-133">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="bf35a-133">Configuration</span></span>  
 <span data-ttu-id="bf35a-134">Zamiast kodu można użyć następującej konfiguracji do skonfigurowania punktu końcowego usługi:</span><span class="sxs-lookup"><span data-stu-id="bf35a-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="bf35a-135">Klient</span><span class="sxs-lookup"><span data-stu-id="bf35a-135">Client</span></span>  
 <span data-ttu-id="bf35a-136">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="bf35a-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="bf35a-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bf35a-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="bf35a-138">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="bf35a-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="bf35a-139">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="bf35a-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="bf35a-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="bf35a-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="bf35a-141">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bf35a-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="bf35a-142">Code</span><span class="sxs-lookup"><span data-stu-id="bf35a-142">Code</span></span>  
 <span data-ttu-id="bf35a-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="bf35a-143">The following code creates the client.</span></span> <span data-ttu-id="bf35a-144">Powiązanie jest skonfigurowane do używania zabezpieczeń trybu transportu z transportem TCP z typem poświadczeń klienta ustawionym na Windows.</span><span class="sxs-lookup"><span data-stu-id="bf35a-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="bf35a-145">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="bf35a-145">Configuration</span></span>  
 <span data-ttu-id="bf35a-146">Następująca konfiguracja może służyć zamiast kodu do utworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="bf35a-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf35a-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf35a-147">See also</span></span>

- [<span data-ttu-id="bf35a-148">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bf35a-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="bf35a-149">Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bf35a-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="bf35a-150">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bf35a-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
