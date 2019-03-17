---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 96fce3cb56cf328e0fbb589113e3ac24519de557
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125450"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="5d0e0-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5d0e0-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="5d0e0-103">Następujący scenariusz pokazuje klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych przez usługę Windows security.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="5d0e0-104">Aby uzyskać więcej informacji na temat programowania, zobacz [jak: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="5d0e0-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="5d0e0-105">Intranet usługi sieci Web Wyświetla informacje o zasobów ludzkich.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="5d0e0-106">Klient to aplikacja formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-106">The client is a Windows Form application.</span></span> <span data-ttu-id="5d0e0-107">Aplikacja jest wdrażana w domenie za pomocą kontrolera Kerberos zabezpieczanie domeny.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Zabezpieczenia transportu z uwierzytelnianiem Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="5d0e0-109">Cechy</span><span class="sxs-lookup"><span data-stu-id="5d0e0-109">Characteristic</span></span>|<span data-ttu-id="5d0e0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5d0e0-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5d0e0-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5d0e0-111">Security Mode</span></span>|<span data-ttu-id="5d0e0-112">Transport</span><span class="sxs-lookup"><span data-stu-id="5d0e0-112">Transport</span></span>|  
|<span data-ttu-id="5d0e0-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="5d0e0-113">Interoperability</span></span>|<span data-ttu-id="5d0e0-114">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="5d0e0-114">WCF only</span></span>|  
|<span data-ttu-id="5d0e0-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="5d0e0-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="5d0e0-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="5d0e0-116">Authentication (Client)</span></span>|<span data-ttu-id="5d0e0-117">Tak (za pomocą zintegrowanego uwierzytelniania Windows)</span><span class="sxs-lookup"><span data-stu-id="5d0e0-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="5d0e0-118">Tak (za pomocą zintegrowanego uwierzytelniania Windows)</span><span class="sxs-lookup"><span data-stu-id="5d0e0-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="5d0e0-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="5d0e0-119">Integrity</span></span>|<span data-ttu-id="5d0e0-120">Tak</span><span class="sxs-lookup"><span data-stu-id="5d0e0-120">Yes</span></span>|  
|<span data-ttu-id="5d0e0-121">Poufność</span><span class="sxs-lookup"><span data-stu-id="5d0e0-121">Confidentiality</span></span>|<span data-ttu-id="5d0e0-122">Tak</span><span class="sxs-lookup"><span data-stu-id="5d0e0-122">Yes</span></span>|  
|<span data-ttu-id="5d0e0-123">Transport</span><span class="sxs-lookup"><span data-stu-id="5d0e0-123">Transport</span></span>|<span data-ttu-id="5d0e0-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="5d0e0-124">NET.TCP</span></span>|  
|<span data-ttu-id="5d0e0-125">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="5d0e0-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5d0e0-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="5d0e0-126">Service</span></span>  
 <span data-ttu-id="5d0e0-127">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5d0e0-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5d0e0-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5d0e0-129">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5d0e0-130">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5d0e0-131">Kod</span><span class="sxs-lookup"><span data-stu-id="5d0e0-131">Code</span></span>  
 <span data-ttu-id="5d0e0-132">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia Windows.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="5d0e0-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5d0e0-133">Configuration</span></span>  
 <span data-ttu-id="5d0e0-134">Następująca konfiguracja może służyć zamiast kodu do konfigurowania punktu końcowego usługi:</span><span class="sxs-lookup"><span data-stu-id="5d0e0-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="5d0e0-135">Klient</span><span class="sxs-lookup"><span data-stu-id="5d0e0-135">Client</span></span>  
 <span data-ttu-id="5d0e0-136">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5d0e0-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5d0e0-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5d0e0-138">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="5d0e0-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5d0e0-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5d0e0-140">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5d0e0-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5d0e0-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5d0e0-142">Kod</span><span class="sxs-lookup"><span data-stu-id="5d0e0-142">Code</span></span>  
 <span data-ttu-id="5d0e0-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-143">The following code creates the client.</span></span> <span data-ttu-id="5d0e0-144">Powiązanie jest skonfigurowane za pomocą transportu tryb zabezpieczeń transportu TCP za pomocą typu poświadczeń klienta równa Windows.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="5d0e0-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="5d0e0-145">Configuration</span></span>  
 <span data-ttu-id="5d0e0-146">Następująca konfiguracja może służyć zamiast kodu do tworzenia klienta.</span><span class="sxs-lookup"><span data-stu-id="5d0e0-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d0e0-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d0e0-147">See also</span></span>
- [<span data-ttu-id="5d0e0-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5d0e0-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5d0e0-149">Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń Windows</span><span class="sxs-lookup"><span data-stu-id="5d0e0-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [<span data-ttu-id="5d0e0-150">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="5d0e0-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
