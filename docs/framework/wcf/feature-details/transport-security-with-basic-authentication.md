---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 65d076a9fef716fca4fe87df6bc5c7773e2dda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499118"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="d81ac-102">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="d81ac-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="d81ac-103">Na poniższej ilustracji przedstawiono usługi Windows Communication Foundation (WCF) i klienta.</span><span class="sxs-lookup"><span data-stu-id="d81ac-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="d81ac-104">Serwer musi mieć prawidłowy certyfikat X.509, który może służyć do Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="d81ac-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="d81ac-105">Ponadto usługa sieci Web jest już implementacja protokołu SSL, który może służyć.</span><span class="sxs-lookup"><span data-stu-id="d81ac-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="d81ac-106">Aby uzyskać więcej informacji dotyczących włączania uwierzytelniania podstawowego na Internet Information Services (IIS), zobacz [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).</span><span class="sxs-lookup"><span data-stu-id="d81ac-106">For more information about enabling basic authentication on Internet Information Services (IIS), see [http://go.microsoft.com/fwlink/?LinkId=83822](http://go.microsoft.com/fwlink/?LinkId=83822).</span></span>  
  
 <span data-ttu-id="d81ac-107">![Transport zabezpieczeń z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span><span class="sxs-lookup"><span data-stu-id="d81ac-107">![Transport security with basic authentication](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")</span></span>  
  
|<span data-ttu-id="d81ac-108">Cechy</span><span class="sxs-lookup"><span data-stu-id="d81ac-108">Characteristic</span></span>|<span data-ttu-id="d81ac-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d81ac-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d81ac-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d81ac-110">Security Mode</span></span>|<span data-ttu-id="d81ac-111">Transportu</span><span class="sxs-lookup"><span data-stu-id="d81ac-111">Transport</span></span>|  
|<span data-ttu-id="d81ac-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d81ac-112">Interoperability</span></span>|<span data-ttu-id="d81ac-113">Z istniejących klientów usługi sieci Web i usług</span><span class="sxs-lookup"><span data-stu-id="d81ac-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="d81ac-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="d81ac-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="d81ac-115">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="d81ac-115">Authentication (Client)</span></span>|<span data-ttu-id="d81ac-116">Tak (za pomocą protokołu HTTPS)</span><span class="sxs-lookup"><span data-stu-id="d81ac-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="d81ac-117">Tak (za pomocą nazwy użytkownika i hasło)</span><span class="sxs-lookup"><span data-stu-id="d81ac-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="d81ac-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="d81ac-118">Integrity</span></span>|<span data-ttu-id="d81ac-119">Tak</span><span class="sxs-lookup"><span data-stu-id="d81ac-119">Yes</span></span>|  
|<span data-ttu-id="d81ac-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="d81ac-120">Confidentiality</span></span>|<span data-ttu-id="d81ac-121">Tak</span><span class="sxs-lookup"><span data-stu-id="d81ac-121">Yes</span></span>|  
|<span data-ttu-id="d81ac-122">Transportu</span><span class="sxs-lookup"><span data-stu-id="d81ac-122">Transport</span></span>|<span data-ttu-id="d81ac-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="d81ac-123">HTTPS</span></span>|  
|<span data-ttu-id="d81ac-124">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="d81ac-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d81ac-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="d81ac-125">Service</span></span>  
 <span data-ttu-id="d81ac-126">Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="d81ac-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d81ac-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d81ac-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="d81ac-128">Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.</span><span class="sxs-lookup"><span data-stu-id="d81ac-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="d81ac-129">Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d81ac-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d81ac-130">Kod</span><span class="sxs-lookup"><span data-stu-id="d81ac-130">Code</span></span>  
 <span data-ttu-id="d81ac-131">Poniższy kod przedstawia sposób tworzenia punkt końcowy usługi, którego używa nazwy użytkownika domeny systemu Windows i hasło dla zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="d81ac-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="d81ac-132">Należy pamiętać, że usługa wymaga certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="d81ac-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="d81ac-133">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d81ac-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="d81ac-134">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d81ac-134">Configuration</span></span>  
 <span data-ttu-id="d81ac-135">Następujące konfiguruje usługę do używania uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:</span><span class="sxs-lookup"><span data-stu-id="d81ac-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d81ac-136">Klient</span><span class="sxs-lookup"><span data-stu-id="d81ac-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="d81ac-137">Kod</span><span class="sxs-lookup"><span data-stu-id="d81ac-137">Code</span></span>  
 <span data-ttu-id="d81ac-138">Poniższy kod przedstawia kodu klienta, który zawiera nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="d81ac-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="d81ac-139">Należy pamiętać, że użytkownik musi podać prawidłową nazwę użytkownika systemu Windows i hasło.</span><span class="sxs-lookup"><span data-stu-id="d81ac-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="d81ac-140">Kod, aby zwrócić nazwę użytkownika i hasło nie jest wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d81ac-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="d81ac-141">Użyj okna dialogowego lub inny interfejs do badania użytkownika o informacje.</span><span class="sxs-lookup"><span data-stu-id="d81ac-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d81ac-142">Nazwa użytkownika i hasło można ustawić tylko przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="d81ac-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="d81ac-143">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d81ac-143">Configuration</span></span>  
 <span data-ttu-id="d81ac-144">Poniższy kod przedstawia konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="d81ac-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d81ac-145">Nie można użyć konfiguracji, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="d81ac-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="d81ac-146">Konfiguracja pokazane musi zostać rozszerzony przy użyciu kodu, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="d81ac-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d81ac-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d81ac-147">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [<span data-ttu-id="d81ac-148">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="d81ac-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d81ac-149">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="d81ac-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="d81ac-150">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d81ac-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d81ac-151">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d81ac-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [<span data-ttu-id="d81ac-152">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="d81ac-152">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
