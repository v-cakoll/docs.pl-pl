---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6392ea0f17596406a8671a039bd78777d9e11e42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742646"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="8dd3f-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8dd3f-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="8dd3f-103">W poniższym scenariuszu przedstawiono klienta i usługę Windows Communication Foundation (WCF) zabezpieczony przez zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="8dd3f-104">Aby uzyskać więcej informacji na temat programowania, zobacz [How to: Zabezpieczanie usługi przy użyciu poświadczeń systemu Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="8dd3f-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="8dd3f-105">Intranetowa usługa sieci Web Wyświetla informacje o zasobach ludzkich.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="8dd3f-106">Klient jest aplikacją formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-106">The client is a Windows Form application.</span></span> <span data-ttu-id="8dd3f-107">Aplikacja jest wdrażana w domenie z kontrolerem Kerberos zabezpieczania domeny.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpieczenia transportu z uwierzytelnianiem systemu Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="8dd3f-109">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="8dd3f-109">Characteristic</span></span>|<span data-ttu-id="8dd3f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd3f-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8dd3f-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8dd3f-111">Security Mode</span></span>|<span data-ttu-id="8dd3f-112">Transport</span><span class="sxs-lookup"><span data-stu-id="8dd3f-112">Transport</span></span>|  
|<span data-ttu-id="8dd3f-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8dd3f-113">Interoperability</span></span>|<span data-ttu-id="8dd3f-114">Tylko WCF</span><span class="sxs-lookup"><span data-stu-id="8dd3f-114">WCF only</span></span>|  
|<span data-ttu-id="8dd3f-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="8dd3f-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="8dd3f-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="8dd3f-116">Authentication (Client)</span></span>|<span data-ttu-id="8dd3f-117">Tak (przy użyciu zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="8dd3f-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="8dd3f-118">Tak (przy użyciu zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="8dd3f-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="8dd3f-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="8dd3f-119">Integrity</span></span>|<span data-ttu-id="8dd3f-120">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd3f-120">Yes</span></span>|  
|<span data-ttu-id="8dd3f-121">Poufne</span><span class="sxs-lookup"><span data-stu-id="8dd3f-121">Confidentiality</span></span>|<span data-ttu-id="8dd3f-122">Tak</span><span class="sxs-lookup"><span data-stu-id="8dd3f-122">Yes</span></span>|  
|<span data-ttu-id="8dd3f-123">Transport</span><span class="sxs-lookup"><span data-stu-id="8dd3f-123">Transport</span></span>|<span data-ttu-id="8dd3f-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="8dd3f-124">NET.TCP</span></span>|  
|<span data-ttu-id="8dd3f-125">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="8dd3f-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8dd3f-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="8dd3f-126">Service</span></span>  
 <span data-ttu-id="8dd3f-127">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8dd3f-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8dd3f-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="8dd3f-129">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8dd3f-130">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8dd3f-131">Kod</span><span class="sxs-lookup"><span data-stu-id="8dd3f-131">Code</span></span>  
 <span data-ttu-id="8dd3f-132">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="8dd3f-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8dd3f-133">Configuration</span></span>  
 <span data-ttu-id="8dd3f-134">Aby skonfigurować punkt końcowy usługi, można użyć następującej konfiguracji zamiast kodu:</span><span class="sxs-lookup"><span data-stu-id="8dd3f-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="8dd3f-135">Klient</span><span class="sxs-lookup"><span data-stu-id="8dd3f-135">Client</span></span>  
 <span data-ttu-id="8dd3f-136">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8dd3f-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8dd3f-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="8dd3f-138">Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="8dd3f-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="8dd3f-139">Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8dd3f-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8dd3f-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8dd3f-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8dd3f-142">Kod</span><span class="sxs-lookup"><span data-stu-id="8dd3f-142">Code</span></span>  
 <span data-ttu-id="8dd3f-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-143">The following code creates the client.</span></span> <span data-ttu-id="8dd3f-144">Powiązanie jest skonfigurowane do korzystania z zabezpieczeń trybu transportu przy użyciu transportu TCP z typem poświadczeń klienta ustawionym na Windows.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="8dd3f-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8dd3f-145">Configuration</span></span>  
 <span data-ttu-id="8dd3f-146">W celu utworzenia klienta można użyć poniższej konfiguracji zamiast kodu.</span><span class="sxs-lookup"><span data-stu-id="8dd3f-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8dd3f-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dd3f-147">See also</span></span>

- [<span data-ttu-id="8dd3f-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="8dd3f-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="8dd3f-149">Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8dd3f-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="8dd3f-150">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8dd3f-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
