---
title: Zabezpieczenia transportu z uwierzytelnianiem podstawowym
description: Zapoznaj się z tym scenariuszem WCF, który zawiera podstawowe uwierzytelnianie dla usługi i klienta programu WCF. Usługa musi mieć prawidłowy certyfikat, którego ufa klient.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: f15a19feaed631a76948efd24ee225acf789cb2d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244858"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="c3f06-104">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="c3f06-104">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="c3f06-105">Na poniższej ilustracji przedstawiono usługę i klienta Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c3f06-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="c3f06-106">Serwer musi mieć prawidłowy certyfikat X. 509, który może być używany dla SSL (SSL), a klienci muszą ufać certyfikatowi serwera.</span><span class="sxs-lookup"><span data-stu-id="c3f06-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="c3f06-107">Ponadto usługa sieci Web ma już implementację protokołu SSL, która może być używana.</span><span class="sxs-lookup"><span data-stu-id="c3f06-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="c3f06-108">Aby uzyskać więcej informacji na temat włączania uwierzytelniania podstawowego na Internet Information Services (IIS), zobacz <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .</span><span class="sxs-lookup"><span data-stu-id="c3f06-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![Zrzut ekranu przedstawiający zabezpieczenia transportu z uwierzytelnianiem podstawowym.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="c3f06-110">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="c3f06-110">Characteristic</span></span>|<span data-ttu-id="c3f06-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c3f06-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c3f06-112">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c3f06-112">Security Mode</span></span>|<span data-ttu-id="c3f06-113">Transport</span><span class="sxs-lookup"><span data-stu-id="c3f06-113">Transport</span></span>|  
|<span data-ttu-id="c3f06-114">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c3f06-114">Interoperability</span></span>|<span data-ttu-id="c3f06-115">Z istniejącymi usługami i klientami usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="c3f06-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="c3f06-116">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="c3f06-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="c3f06-117">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="c3f06-117">Authentication (Client)</span></span>|<span data-ttu-id="c3f06-118">Tak (przy użyciu protokołu HTTPS)</span><span class="sxs-lookup"><span data-stu-id="c3f06-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="c3f06-119">Tak (za poorednictwem nazwy użytkownika/hasła)</span><span class="sxs-lookup"><span data-stu-id="c3f06-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="c3f06-120">Integralność</span><span class="sxs-lookup"><span data-stu-id="c3f06-120">Integrity</span></span>|<span data-ttu-id="c3f06-121">Tak</span><span class="sxs-lookup"><span data-stu-id="c3f06-121">Yes</span></span>|  
|<span data-ttu-id="c3f06-122">Poufność</span><span class="sxs-lookup"><span data-stu-id="c3f06-122">Confidentiality</span></span>|<span data-ttu-id="c3f06-123">Tak</span><span class="sxs-lookup"><span data-stu-id="c3f06-123">Yes</span></span>|  
|<span data-ttu-id="c3f06-124">Transport</span><span class="sxs-lookup"><span data-stu-id="c3f06-124">Transport</span></span>|<span data-ttu-id="c3f06-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="c3f06-125">HTTPS</span></span>|  
|<span data-ttu-id="c3f06-126">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c3f06-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c3f06-127">Usługa</span><span class="sxs-lookup"><span data-stu-id="c3f06-127">Service</span></span>  
 <span data-ttu-id="c3f06-128">Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="c3f06-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c3f06-129">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c3f06-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="c3f06-130">Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c3f06-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="c3f06-131">Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c3f06-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3f06-132">Kod</span><span class="sxs-lookup"><span data-stu-id="c3f06-132">Code</span></span>  
 <span data-ttu-id="c3f06-133">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który używa nazwy użytkownika i hasła domeny systemu Windows do zabezpieczenia transferu.</span><span class="sxs-lookup"><span data-stu-id="c3f06-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="c3f06-134">Należy pamiętać, że usługa wymaga certyfikatu X. 509 do uwierzytelnienia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="c3f06-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="c3f06-135">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](working-with-certificates.md) i [instrukcje: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="c3f06-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="c3f06-136">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c3f06-136">Configuration</span></span>  
 <span data-ttu-id="c3f06-137">Poniżej przedstawiono Konfigurowanie usługi do korzystania z uwierzytelniania podstawowego z zabezpieczeniami na poziomie transportu:</span><span class="sxs-lookup"><span data-stu-id="c3f06-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="c3f06-138">Klient</span><span class="sxs-lookup"><span data-stu-id="c3f06-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3f06-139">Kod</span><span class="sxs-lookup"><span data-stu-id="c3f06-139">Code</span></span>  
 <span data-ttu-id="c3f06-140">Poniższy kod przedstawia kod klienta, który zawiera nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="c3f06-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="c3f06-141">Należy pamiętać, że użytkownik musi podać prawidłową nazwę użytkownika i hasło systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3f06-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="c3f06-142">Kod, który ma zwrócić nazwę użytkownika i hasło, nie jest tutaj wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="c3f06-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="c3f06-143">Użyj okna dialogowego lub innego interfejsu, aby wysłać zapytanie do użytkownika o informacje.</span><span class="sxs-lookup"><span data-stu-id="c3f06-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3f06-144">Nazwę użytkownika i hasło można ustawić tylko przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="c3f06-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="c3f06-145">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c3f06-145">Configuration</span></span>  
 <span data-ttu-id="c3f06-146">Poniższy kod przedstawia konfigurację klienta.</span><span class="sxs-lookup"><span data-stu-id="c3f06-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3f06-147">Nie można użyć konfiguracji w celu ustawienia nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="c3f06-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="c3f06-148">Pokazana tutaj konfiguracja musi zostać uzupełniona przy użyciu kodu w celu ustawienia nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="c3f06-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3f06-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3f06-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="c3f06-150">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="c3f06-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="c3f06-151">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="c3f06-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="c3f06-152">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c3f06-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="c3f06-153">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c3f06-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
