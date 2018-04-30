---
title: Zabezpieczanie transportu za pomocą anonimowego klienta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 2b52a32db1f1ac02f9204198a4cda5d4cb157486
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-an-anonymous-client"></a><span data-ttu-id="6e083-102">Zabezpieczanie transportu za pomocą anonimowego klienta</span><span class="sxs-lookup"><span data-stu-id="6e083-102">Transport Security with an Anonymous Client</span></span>
<span data-ttu-id="6e083-103">To [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenariuszu zapewnienie poufności i integralności zabezpieczeń transportowych (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="6e083-103">This [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenario uses transport security (HTTPS) to ensure confidentiality and integrity.</span></span> <span data-ttu-id="6e083-104">Serwer musi zostać uwierzytelniony przy użyciu certyfikatu protokołu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="6e083-104">The server must be authenticated with a Secure Sockets Layer (SSL) certificate, and the clients must trust the server's certificate.</span></span> <span data-ttu-id="6e083-105">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="6e083-105">The client is not authenticated by any mechanism and is, therefore, anonymous.</span></span>  
  
 <span data-ttu-id="6e083-106">Przykładową aplikację, zobacz [zabezpieczenia transportu WS](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="6e083-106">For a sample application, see [WS Transport Security](../../../../docs/framework/wcf/samples/ws-transport-security.md).</span></span> <span data-ttu-id="6e083-107">Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6e083-107">For more information about transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
 <span data-ttu-id="6e083-108">Aby uzyskać więcej informacji dotyczących używania certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="6e083-108">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 <span data-ttu-id="6e083-109">![Za pomocą zabezpieczeń transportu za pomocą anonimowego klienta](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span><span class="sxs-lookup"><span data-stu-id="6e083-109">![Using transport security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")</span></span>  
  
|<span data-ttu-id="6e083-110">Cechy</span><span class="sxs-lookup"><span data-stu-id="6e083-110">Characteristic</span></span>|<span data-ttu-id="6e083-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6e083-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6e083-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6e083-112">Security Mode</span></span>|<span data-ttu-id="6e083-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="6e083-113">Transport</span></span>|  
|<span data-ttu-id="6e083-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="6e083-114">Interoperability</span></span>|<span data-ttu-id="6e083-115">Z istniejącymi usługami sieci Web i klientami</span><span class="sxs-lookup"><span data-stu-id="6e083-115">With existing Web services and clients</span></span>|  
|<span data-ttu-id="6e083-116">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="6e083-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="6e083-117">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="6e083-117">Authentication (Client)</span></span>|<span data-ttu-id="6e083-118">Tak</span><span class="sxs-lookup"><span data-stu-id="6e083-118">Yes</span></span><br /><br /> <span data-ttu-id="6e083-119">Poziom aplikacji (nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje)</span><span class="sxs-lookup"><span data-stu-id="6e083-119">Application level (no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] support)</span></span>|  
|<span data-ttu-id="6e083-120">Integralność</span><span class="sxs-lookup"><span data-stu-id="6e083-120">Integrity</span></span>|<span data-ttu-id="6e083-121">Tak</span><span class="sxs-lookup"><span data-stu-id="6e083-121">Yes</span></span>|  
|<span data-ttu-id="6e083-122">Poufność</span><span class="sxs-lookup"><span data-stu-id="6e083-122">Confidentiality</span></span>|<span data-ttu-id="6e083-123">Tak</span><span class="sxs-lookup"><span data-stu-id="6e083-123">Yes</span></span>|  
|<span data-ttu-id="6e083-124">Transportu</span><span class="sxs-lookup"><span data-stu-id="6e083-124">Transport</span></span>|<span data-ttu-id="6e083-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="6e083-125">HTTPS</span></span>|  
|<span data-ttu-id="6e083-126">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="6e083-126">Binding</span></span>|<span data-ttu-id="6e083-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="6e083-127"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>|  
  
## <a name="service"></a><span data-ttu-id="6e083-128">Usługa</span><span class="sxs-lookup"><span data-stu-id="6e083-128">Service</span></span>  
 <span data-ttu-id="6e083-129">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="6e083-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6e083-130">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e083-130">Do one of the following:</span></span>  
  
-   <span data-ttu-id="6e083-131">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="6e083-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="6e083-132">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6e083-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6e083-133">Kod</span><span class="sxs-lookup"><span data-stu-id="6e083-133">Code</span></span>  
 <span data-ttu-id="6e083-134">Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:</span><span class="sxs-lookup"><span data-stu-id="6e083-134">The following code shows how to create an endpoint using transport security:</span></span>  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a><span data-ttu-id="6e083-135">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6e083-135">Configuration</span></span>  
 <span data-ttu-id="6e083-136">Poniższy kod konfiguruje tego samego punktu końcowego za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e083-136">The following code sets up the same endpoint using configuration.</span></span> <span data-ttu-id="6e083-137">Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i dlatego jest anonimowy.</span><span class="sxs-lookup"><span data-stu-id="6e083-137">The client is not authenticated by any mechanism, and is therefore anonymous.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
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
  
## <a name="client"></a><span data-ttu-id="6e083-138">Klient</span><span class="sxs-lookup"><span data-stu-id="6e083-138">Client</span></span>  
 <span data-ttu-id="6e083-139">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="6e083-139">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6e083-140">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e083-140">Do one of the following:</span></span>  
  
-   <span data-ttu-id="6e083-141">Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).</span><span class="sxs-lookup"><span data-stu-id="6e083-141">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="6e083-142">Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6e083-142">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="6e083-143">W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument.</span><span class="sxs-lookup"><span data-stu-id="6e083-143">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="6e083-144">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6e083-144">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="6e083-145">Kod</span><span class="sxs-lookup"><span data-stu-id="6e083-145">Code</span></span>  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a><span data-ttu-id="6e083-146">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6e083-146">Configuration</span></span>  
 <span data-ttu-id="6e083-147">Następującej konfiguracji można zamiast kodu do skonfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="6e083-147">The following configuration can be used instead of the code to set up the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e083-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e083-148">See Also</span></span>  
 [<span data-ttu-id="6e083-149">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6e083-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="6e083-150">Zabezpieczenia transportu WS</span><span class="sxs-lookup"><span data-stu-id="6e083-150">WS Transport Security</span></span>](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [<span data-ttu-id="6e083-151">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="6e083-151">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [<span data-ttu-id="6e083-152">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="6e083-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
