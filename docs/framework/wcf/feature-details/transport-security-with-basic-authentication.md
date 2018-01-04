---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
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
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fe6b996c37e66f41c3946b8ef3437f8fa82c5201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="ada8c-102">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="ada8c-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="ada8c-103">Na poniższej ilustracji pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="ada8c-103">The following illustration shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client.</span></span> <span data-ttu-id="ada8c-104">Serwer musi mieć prawidłowy certyfikat X.509, który może służyć do Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="ada8c-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="ada8c-105">Ponadto usługa sieci Web jest już implementacja protokołu SSL, który może służyć.</span><span class="sxs-lookup"><span data-stu-id="ada8c-105">Further, the Web service already has an SSL implementation that can be used.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ada8c-106">Włączenie uwierzytelniania podstawowego na Internet Information Services (IIS), zobacz [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="ada8c-106"> enabling basic authentication on Internet Information Services (IIS), see [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="ada8c-107">![Transport zabezpieczeń z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="ada8c-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="ada8c-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="ada8c-108">Characteristic</span></span>|<span data-ttu-id="ada8c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ada8c-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ada8c-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ada8c-110">Security Mode</span></span>|<span data-ttu-id="ada8c-111">Transportu</span><span class="sxs-lookup"><span data-stu-id="ada8c-111">Transport</span></span>|  
|<span data-ttu-id="ada8c-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ada8c-112">Interoperability</span></span>|<span data-ttu-id="ada8c-113">Z istniejących klientów usługi sieci Web i usług</span><span class="sxs-lookup"><span data-stu-id="ada8c-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="ada8c-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="ada8c-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ada8c-115">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="ada8c-115">Authentication (Client)</span></span>|<span data-ttu-id="ada8c-116">Tak (za pomocą protokołu HTTPS)</span><span class="sxs-lookup"><span data-stu-id="ada8c-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="ada8c-117">Tak (za pomocą nazwy użytkownika i hasło)</span><span class="sxs-lookup"><span data-stu-id="ada8c-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="ada8c-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="ada8c-118">Integrity</span></span>|<span data-ttu-id="ada8c-119">Tak</span><span class="sxs-lookup"><span data-stu-id="ada8c-119">Yes</span></span>|  
|<span data-ttu-id="ada8c-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="ada8c-120">Confidentiality</span></span>|<span data-ttu-id="ada8c-121">Tak</span><span class="sxs-lookup"><span data-stu-id="ada8c-121">Yes</span></span>|  
|<span data-ttu-id="ada8c-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="ada8c-122">Transport</span></span>|<span data-ttu-id="ada8c-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ada8c-123">HTTPS</span></span>|  
|<span data-ttu-id="ada8c-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="ada8c-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ada8c-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="ada8c-125">Service</span></span>  
 <span data-ttu-id="ada8c-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="ada8c-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ada8c-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ada8c-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="ada8c-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="ada8c-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="ada8c-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ada8c-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ada8c-130">Kod</span><span class="sxs-lookup"><span data-stu-id="ada8c-130">Code</span></span>  
 <span data-ttu-id="ada8c-131">Poniższy kod przedstawia sposób tworzenia punkt końcowy usługi, którego używa nazwy użytkownika domeny systemu Windows i hasło dla zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="ada8c-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="ada8c-132">Należy pamiętać, że usługa wymaga certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="ada8c-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="ada8c-133">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ada8c-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="ada8c-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ada8c-134">Configuration</span></span>  
 <span data-ttu-id="ada8c-135">Następujące konfiguruje usługę do używania uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:</span><span class="sxs-lookup"><span data-stu-id="ada8c-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ada8c-136">Klient</span><span class="sxs-lookup"><span data-stu-id="ada8c-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="ada8c-137">Kod</span><span class="sxs-lookup"><span data-stu-id="ada8c-137">Code</span></span>  
 <span data-ttu-id="ada8c-138">Poniższy kod przedstawia kodu klienta, który zawiera nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ada8c-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="ada8c-139">Należy pamiętać, że użytkownik musi podać prawidłową nazwę użytkownika systemu Windows i hasło.</span><span class="sxs-lookup"><span data-stu-id="ada8c-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="ada8c-140">Kod, aby zwrócić nazwę użytkownika i hasło nie jest wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="ada8c-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="ada8c-141">Użyj okna dialogowego lub inny interfejs do badania użytkownika o informacje.</span><span class="sxs-lookup"><span data-stu-id="ada8c-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ada8c-142">Nazwa użytkownika i hasło można ustawić tylko przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="ada8c-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="ada8c-143">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ada8c-143">Configuration</span></span>  
 <span data-ttu-id="ada8c-144">Poniższy kod przedstawia konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="ada8c-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ada8c-145">Nie można użyć konfiguracji, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ada8c-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="ada8c-146">Konfiguracja pokazane musi zostać rozszerzony przy użyciu kodu, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ada8c-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
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
  
## <a name="see-also"></a><span data-ttu-id="ada8c-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ada8c-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="ada8c-148">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ada8c-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ada8c-149">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="ada8c-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="ada8c-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ada8c-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ada8c-151">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ada8c-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="ada8c-152">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="ada8c-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
