---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 1b2b451eb1ea6a1a49ce1ba8cc1edef1fe72d01b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184355"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="ebae8-102">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="ebae8-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="ebae8-103">Na poniższej ilustracji przedstawiono usługę i klienta programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ebae8-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="ebae8-104">Serwer potrzebuje prawidłowego certyfikatu X.509, który może być używany dla secure sockets layer (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="ebae8-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="ebae8-105">Ponadto usługa sieci Web ma już implementację SSL, która może być używana.</span><span class="sxs-lookup"><span data-stu-id="ebae8-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="ebae8-106">Aby uzyskać więcej informacji na temat włączania uwierzytelniania <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>podstawowego w internetowych usługach informacyjnych (IIS), zobacz .</span><span class="sxs-lookup"><span data-stu-id="ebae8-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Zrzut ekranu przedstawiający zabezpieczenia transportu z uwierzytelnianiem podstawowym.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="ebae8-108">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="ebae8-108">Characteristic</span></span>|<span data-ttu-id="ebae8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ebae8-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ebae8-110">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ebae8-110">Security Mode</span></span>|<span data-ttu-id="ebae8-111">Transport</span><span class="sxs-lookup"><span data-stu-id="ebae8-111">Transport</span></span>|  
|<span data-ttu-id="ebae8-112">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ebae8-112">Interoperability</span></span>|<span data-ttu-id="ebae8-113">Z istniejącymi klientami i usługami usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="ebae8-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="ebae8-114">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="ebae8-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="ebae8-115">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="ebae8-115">Authentication (Client)</span></span>|<span data-ttu-id="ebae8-116">Tak (przy użyciu protokołu HTTPS)</span><span class="sxs-lookup"><span data-stu-id="ebae8-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="ebae8-117">Tak (za pomocą nazwy użytkownika/hasła)</span><span class="sxs-lookup"><span data-stu-id="ebae8-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="ebae8-118">Integralność</span><span class="sxs-lookup"><span data-stu-id="ebae8-118">Integrity</span></span>|<span data-ttu-id="ebae8-119">Tak</span><span class="sxs-lookup"><span data-stu-id="ebae8-119">Yes</span></span>|  
|<span data-ttu-id="ebae8-120">Poufność</span><span class="sxs-lookup"><span data-stu-id="ebae8-120">Confidentiality</span></span>|<span data-ttu-id="ebae8-121">Tak</span><span class="sxs-lookup"><span data-stu-id="ebae8-121">Yes</span></span>|  
|<span data-ttu-id="ebae8-122">Transport</span><span class="sxs-lookup"><span data-stu-id="ebae8-122">Transport</span></span>|<span data-ttu-id="ebae8-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="ebae8-123">HTTPS</span></span>|  
|<span data-ttu-id="ebae8-124">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="ebae8-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ebae8-125">Usługa</span><span class="sxs-lookup"><span data-stu-id="ebae8-125">Service</span></span>  
 <span data-ttu-id="ebae8-126">Poniższy kod i konfiguracja są przeznaczone do uruchamiania niezależnie.</span><span class="sxs-lookup"><span data-stu-id="ebae8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ebae8-127">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="ebae8-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="ebae8-128">Utwórz usługę autonomiczną przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ebae8-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ebae8-129">Utwórz usługę przy użyciu dostarczonej konfiguracji, ale nie definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ebae8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebae8-130">Code</span><span class="sxs-lookup"><span data-stu-id="ebae8-130">Code</span></span>  
 <span data-ttu-id="ebae8-131">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi, który używa nazwy użytkownika domeny systemu Windows i hasła do zabezpieczeń transferu.</span><span class="sxs-lookup"><span data-stu-id="ebae8-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="ebae8-132">Należy zauważyć, że usługa wymaga certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="ebae8-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="ebae8-133">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [Jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ebae8-133">For more information, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="ebae8-134">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="ebae8-134">Configuration</span></span>  
 <span data-ttu-id="ebae8-135">Poniżej przedstawiono skonfigurowanie usługi do używania uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:</span><span class="sxs-lookup"><span data-stu-id="ebae8-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="ebae8-136">Klient</span><span class="sxs-lookup"><span data-stu-id="ebae8-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebae8-137">Code</span><span class="sxs-lookup"><span data-stu-id="ebae8-137">Code</span></span>  
 <span data-ttu-id="ebae8-138">Poniższy kod przedstawia kod klienta, który zawiera nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ebae8-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="ebae8-139">Należy pamiętać, że użytkownik musi podać prawidłową nazwę użytkownika i hasło systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebae8-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="ebae8-140">Kod do zwrócenia nazwy użytkownika i hasła nie jest wyświetlany w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="ebae8-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="ebae8-141">Użyj okna dialogowego lub innego interfejsu, aby zbadać użytkownika w poszukiwaniu informacji.</span><span class="sxs-lookup"><span data-stu-id="ebae8-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebae8-142">Nazwę użytkownika i hasło można ustawić tylko przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="ebae8-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="ebae8-143">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="ebae8-143">Configuration</span></span>  
 <span data-ttu-id="ebae8-144">Poniższy kod przedstawia konfigurację klienta.</span><span class="sxs-lookup"><span data-stu-id="ebae8-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebae8-145">Nie można użyć konfiguracji, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ebae8-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="ebae8-146">Konfiguracja pokazana w tym miejscu musi zostać rozszerzona za pomocą kodu, aby ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="ebae8-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebae8-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebae8-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="ebae8-148">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ebae8-148">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ebae8-149">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="ebae8-149">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="ebae8-150">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ebae8-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="ebae8-151">\<>clientCredentials</span><span class="sxs-lookup"><span data-stu-id="ebae8-151">\<clientCredentials></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="ebae8-152">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ebae8-152">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
