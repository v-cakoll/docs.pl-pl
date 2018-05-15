---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d291cd3d00f8d0d40e0b8543d5347e1509cb8b90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="c70b5-102">Zabezpieczenia transportu z uwierzytelnianiem systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c70b5-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="c70b5-103">Poniższy scenariusz przedstawia klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych przez zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c70b5-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="c70b5-104">Aby uzyskać więcej informacji na temat programowania w języku, zobacz [porady: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="c70b5-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="c70b5-105">Intranet usługi sieci Web Wyświetla informacje o zasoby ludzkie.</span><span class="sxs-lookup"><span data-stu-id="c70b5-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="c70b5-106">Klient jest aplikacją formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c70b5-106">The client is a Windows Form application.</span></span> <span data-ttu-id="c70b5-107">Aplikacja jest wdrażana w domenie za pomocą kontrolera protokołu Kerberos, zabezpieczanie domeny.</span><span class="sxs-lookup"><span data-stu-id="c70b5-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="c70b5-108">![Transport zabezpieczeń z uwierzytelnianiem systemu Windows](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="c70b5-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="c70b5-109">Cechy</span><span class="sxs-lookup"><span data-stu-id="c70b5-109">Characteristic</span></span>|<span data-ttu-id="c70b5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c70b5-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c70b5-111">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c70b5-111">Security Mode</span></span>|<span data-ttu-id="c70b5-112">Transportu</span><span class="sxs-lookup"><span data-stu-id="c70b5-112">Transport</span></span>|  
|<span data-ttu-id="c70b5-113">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c70b5-113">Interoperability</span></span>|<span data-ttu-id="c70b5-114">Tylko usługi WCF</span><span class="sxs-lookup"><span data-stu-id="c70b5-114">WCF only</span></span>|  
|<span data-ttu-id="c70b5-115">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="c70b5-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="c70b5-116">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="c70b5-116">Authentication (Client)</span></span>|<span data-ttu-id="c70b5-117">Tak (za pomocą zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="c70b5-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="c70b5-118">Tak (za pomocą zintegrowanego uwierzytelniania systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="c70b5-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="c70b5-119">Integralność</span><span class="sxs-lookup"><span data-stu-id="c70b5-119">Integrity</span></span>|<span data-ttu-id="c70b5-120">Tak</span><span class="sxs-lookup"><span data-stu-id="c70b5-120">Yes</span></span>|  
|<span data-ttu-id="c70b5-121">Poufność</span><span class="sxs-lookup"><span data-stu-id="c70b5-121">Confidentiality</span></span>|<span data-ttu-id="c70b5-122">Tak</span><span class="sxs-lookup"><span data-stu-id="c70b5-122">Yes</span></span>|  
|<span data-ttu-id="c70b5-123">Transportu</span><span class="sxs-lookup"><span data-stu-id="c70b5-123">Transport</span></span>|<span data-ttu-id="c70b5-124">NET. TCP</span><span class="sxs-lookup"><span data-stu-id="c70b5-124">NET.TCP</span></span>|  
|<span data-ttu-id="c70b5-125">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="c70b5-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c70b5-126">Usługa</span><span class="sxs-lookup"><span data-stu-id="c70b5-126">Service</span></span>  
 <span data-ttu-id="c70b5-127">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c70b5-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c70b5-128">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c70b5-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c70b5-129">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="c70b5-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="c70b5-130">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c70b5-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c70b5-131">Kod</span><span class="sxs-lookup"><span data-stu-id="c70b5-131">Code</span></span>  
 <span data-ttu-id="c70b5-132">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c70b5-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="c70b5-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c70b5-133">Configuration</span></span>  
 <span data-ttu-id="c70b5-134">Następującej konfiguracji można zamiast kodu do konfigurowania punktu końcowego usługi:</span><span class="sxs-lookup"><span data-stu-id="c70b5-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="c70b5-135">Klient</span><span class="sxs-lookup"><span data-stu-id="c70b5-135">Client</span></span>  
 <span data-ttu-id="c70b5-136">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="c70b5-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c70b5-137">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c70b5-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="c70b5-138">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="c70b5-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="c70b5-139">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c70b5-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c70b5-140">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="c70b5-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c70b5-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c70b5-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c70b5-142">Kod</span><span class="sxs-lookup"><span data-stu-id="c70b5-142">Code</span></span>  
 <span data-ttu-id="c70b5-143">Poniższy kod tworzy klienta.</span><span class="sxs-lookup"><span data-stu-id="c70b5-143">The following code creates the client.</span></span> <span data-ttu-id="c70b5-144">Powiązanie jest skonfigurowany do używania tryb zabezpieczeń transportu z transportu TCP typu poświadczeń klienta do systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c70b5-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="c70b5-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c70b5-145">Configuration</span></span>  
 <span data-ttu-id="c70b5-146">Następującej konfiguracji można zamiast kodu można utworzyć klienta.</span><span class="sxs-lookup"><span data-stu-id="c70b5-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c70b5-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c70b5-147">See Also</span></span>  
 [<span data-ttu-id="c70b5-148">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c70b5-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="c70b5-149">Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c70b5-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="c70b5-150">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="c70b5-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
