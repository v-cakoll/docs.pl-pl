---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 3e48c397cb97cdfeb476daaf09d997e9609b3467
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201494"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="12fce-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="12fce-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="12fce-103">Następujący scenariusz pokazuje klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych przez usługę Windows security.</span><span class="sxs-lookup"><span data-stu-id="12fce-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="12fce-104">Aby uzyskać więcej informacji na temat programowania, zobacz [instrukcje: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="12fce-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="12fce-105">Intranet usługi sieci Web Wyświetla informacje o zasobów ludzkich.</span><span class="sxs-lookup"><span data-stu-id="12fce-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="12fce-106">Klient to aplikacja formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="12fce-106">The client is a Windows Form application.</span></span> <span data-ttu-id="12fce-107">Aplikacja jest wdrażana w domenie za pomocą kontrolera Kerberos zabezpieczanie domeny.</span><span class="sxs-lookup"><span data-stu-id="12fce-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="12fce-108">![Transport security przy użyciu uwierzytelniania Windows](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="12fce-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="12fce-109">Cechy</span><span class="sxs-lookup"><span data-stu-id="12fce-109">Characteristic</span></span>|<span data-ttu-id="12fce-110">Opis</span><span class="sxs-lookup"><span data-stu-id="12fce-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="12fce-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12fce-111">Security Mode</span></span>|<span data-ttu-id="12fce-112">Transportu</span><span class="sxs-lookup"><span data-stu-id="12fce-112">Transport</span></span>|  
|<span data-ttu-id="12fce-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="12fce-113">Interoperability</span></span>|<span data-ttu-id="12fce-114">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="12fce-114">WCF only</span></span>|  
|<span data-ttu-id="12fce-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="12fce-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="12fce-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="12fce-116">Authentication (Client)</span></span>|<span data-ttu-id="12fce-117">Tak (za pomocą zintegrowanego uwierzytelniania Windows)</span><span class="sxs-lookup"><span data-stu-id="12fce-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="12fce-118">Tak (za pomocą zintegrowanego uwierzytelniania Windows)</span><span class="sxs-lookup"><span data-stu-id="12fce-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="12fce-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="12fce-119">Integrity</span></span>|<span data-ttu-id="12fce-120">Tak</span><span class="sxs-lookup"><span data-stu-id="12fce-120">Yes</span></span>|  
|<span data-ttu-id="12fce-121">Poufność</span><span class="sxs-lookup"><span data-stu-id="12fce-121">Confidentiality</span></span>|<span data-ttu-id="12fce-122">Tak</span><span class="sxs-lookup"><span data-stu-id="12fce-122">Yes</span></span>|  
|<span data-ttu-id="12fce-123">Transportu</span><span class="sxs-lookup"><span data-stu-id="12fce-123">Transport</span></span>|<span data-ttu-id="12fce-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="12fce-124">NET.TCP</span></span>|  
|<span data-ttu-id="12fce-125">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="12fce-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="12fce-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="12fce-126">Service</span></span>  
 <span data-ttu-id="12fce-127">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="12fce-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="12fce-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="12fce-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="12fce-129">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12fce-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="12fce-130">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="12fce-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="12fce-131">Kod</span><span class="sxs-lookup"><span data-stu-id="12fce-131">Code</span></span>  
 <span data-ttu-id="12fce-132">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia Windows.</span><span class="sxs-lookup"><span data-stu-id="12fce-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="12fce-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="12fce-133">Configuration</span></span>  
 <span data-ttu-id="12fce-134">Następująca konfiguracja może służyć zamiast kodu do konfigurowania punktu końcowego usługi:</span><span class="sxs-lookup"><span data-stu-id="12fce-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="12fce-135">Klient</span><span class="sxs-lookup"><span data-stu-id="12fce-135">Client</span></span>  
 <span data-ttu-id="12fce-136">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="12fce-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="12fce-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="12fce-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="12fce-138">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="12fce-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="12fce-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="12fce-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="12fce-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="12fce-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="12fce-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="12fce-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="12fce-142">Kod</span><span class="sxs-lookup"><span data-stu-id="12fce-142">Code</span></span>  
 <span data-ttu-id="12fce-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="12fce-143">The following code creates the client.</span></span> <span data-ttu-id="12fce-144">Powiązanie jest skonfigurowane za pomocą transportu tryb zabezpieczeń transportu TCP za pomocą typu poświadczeń klienta równa Windows.</span><span class="sxs-lookup"><span data-stu-id="12fce-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="12fce-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="12fce-145">Configuration</span></span>  
 <span data-ttu-id="12fce-146">Następująca konfiguracja może służyć zamiast kodu do tworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="12fce-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12fce-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12fce-147">See Also</span></span>  
 [<span data-ttu-id="12fce-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12fce-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="12fce-149">Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="12fce-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="12fce-150">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="12fce-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
