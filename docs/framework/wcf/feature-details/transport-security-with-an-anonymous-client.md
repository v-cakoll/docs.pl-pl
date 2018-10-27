---
title: Zabezpieczanie transportu za pomocą anonimowego klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 858ceb217ce30708a7d24c62ca18f8f59ba49d4c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183070"
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="91343-102">Zabezpieczanie transportu za pomocą anonimowego klienta</span><span class="sxs-lookup"><span data-stu-id="91343-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="91343-103">W tym scenariuszu usług Windows Communication Foundation (WCF) używane zabezpieczeń transportowych (HTTPS), aby upewnić się, poufności i integralności.</span><span class="sxs-lookup"><span data-stu-id="91343-103">This Windows Communication Foundation (WCF) scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="91343-104">Serwer musi zostać uwierzytelniony przy użyciu certyfikatu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="91343-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="91343-105">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest zatem anonimowe.</span><span class="sxs-lookup"><span data-stu-id="91343-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="91343-106">Dla przykładowej aplikacji, zobacz [zabezpieczenia transportu WS](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="91343-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> <span data-ttu-id="91343-107">Aby uzyskać więcej informacji na temat zabezpieczeń transportu zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="91343-107">For more information about transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 <span data-ttu-id="91343-108">Aby uzyskać więcej informacji na temat używania certyfikatu z usługą, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="91343-108">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="91343-109">![Za pomocą zabezpieczeń transportu z anonimowym klientem](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="91343-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="91343-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="91343-110">Characteristic</span></span>|<span data-ttu-id="91343-111">Opis</span><span class="sxs-lookup"><span data-stu-id="91343-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="91343-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="91343-112">Security Mode</span></span>|<span data-ttu-id="91343-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="91343-113">Transport</span></span>|  
|<span data-ttu-id="91343-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="91343-114">Interoperability</span></span>|<span data-ttu-id="91343-115">Przy użyciu istniejących usług sieci Web i klientów</span><span class="sxs-lookup"><span data-stu-id="91343-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="91343-116">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="91343-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="91343-117">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="91343-117">Authentication (Client)</span></span>|<span data-ttu-id="91343-118">Tak</span><span class="sxs-lookup"><span data-stu-id="91343-118">Yes</span></span><br /><br /> <span data-ttu-id="91343-119">Poziom aplikacji (bez obsługi WCF)</span><span class="sxs-lookup"><span data-stu-id="91343-119">Application level (no WCF support)</span></span>|  
|<span data-ttu-id="91343-120">Integralność</span><span class="sxs-lookup"><span data-stu-id="91343-120">Integrity</span></span>|<span data-ttu-id="91343-121">Tak</span><span class="sxs-lookup"><span data-stu-id="91343-121">Yes</span></span>|  
|<span data-ttu-id="91343-122">Poufność</span><span class="sxs-lookup"><span data-stu-id="91343-122">Confidentiality</span></span>|<span data-ttu-id="91343-123">Tak</span><span class="sxs-lookup"><span data-stu-id="91343-123">Yes</span></span>|  
|<span data-ttu-id="91343-124">Transportu</span><span class="sxs-lookup"><span data-stu-id="91343-124">Transport</span></span>|<span data-ttu-id="91343-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="91343-125">HTTPS</span></span>|  
|<span data-ttu-id="91343-126">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="91343-126">Binding</span></span>|<span data-ttu-id="91343-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="91343-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="91343-128">Usługa</span><span class="sxs-lookup"><span data-stu-id="91343-128">Service</span></span>  
 <span data-ttu-id="91343-129">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="91343-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="91343-130">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="91343-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="91343-131">Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91343-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="91343-132">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="91343-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="91343-133">Kod</span><span class="sxs-lookup"><span data-stu-id="91343-133">Code</span></span>  
 <span data-ttu-id="91343-134">Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:</span><span class="sxs-lookup"><span data-stu-id="91343-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="91343-135">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="91343-135">Configuration</span></span>  
 <span data-ttu-id="91343-136">Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91343-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="91343-137">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i w związku z tym jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="91343-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="https://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="91343-138">Klient</span><span class="sxs-lookup"><span data-stu-id="91343-138">Client</span></span>  
 <span data-ttu-id="91343-139">Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="91343-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="91343-140">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="91343-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="91343-141">Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).</span><span class="sxs-lookup"><span data-stu-id="91343-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="91343-142">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="91343-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="91343-143">Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="91343-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="91343-144">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="91343-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="91343-145">Kod</span><span class="sxs-lookup"><span data-stu-id="91343-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="91343-146">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="91343-146">Configuration</span></span>  
 <span data-ttu-id="91343-147">Następująca konfiguracja może służyć zamiast kodu do konfiguracji obsługiwanej usługi.</span><span class="sxs-lookup"><span data-stu-id="91343-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91343-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91343-148">See Also</span></span>  
 [<span data-ttu-id="91343-149">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="91343-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="91343-150">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="91343-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="91343-151">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="91343-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="91343-152">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="91343-152">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
