---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: b226eed9218207cde99add61ef1f3eb64b459009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184305"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="12a81-102">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="12a81-102">Trusted Subsystem</span></span>
<span data-ttu-id="12a81-103">Klient uzyskuje dostęp do jednej lub kilku usług sieci Web, które są rozproszone w sieci.</span><span class="sxs-lookup"><span data-stu-id="12a81-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="12a81-104">Usługi sieci Web są zaprojektowane tak, aby dostęp do dodatkowych zasobów (takich jak bazy danych lub inne usługi sieci Web) jest hermetyzowany w logice biznesowej usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="12a81-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="12a81-105">Te zasoby muszą być chronione przed nieautoryzowanym dostępem.</span><span class="sxs-lookup"><span data-stu-id="12a81-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="12a81-106">Na poniższej ilustracji przedstawiono proces zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="12a81-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="12a81-107">![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="12a81-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="12a81-108">W poniższych krokach opisano proces zaufanego podsystemu w sposób zilustrowany:</span><span class="sxs-lookup"><span data-stu-id="12a81-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="12a81-109">Klient przesyła żądanie do zaufanego podsystemu wraz z poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="12a81-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="12a81-110">Zaufany podsystem uwierzytelnia i autoryzuje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="12a81-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="12a81-111">Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="12a81-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="12a81-112">Do tego żądania dołączają poświadczenia dla zaufanego podsystemu (lub konta usługi, na którym wykonywany jest proces zaufanego podsystemu).</span><span class="sxs-lookup"><span data-stu-id="12a81-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="12a81-113">Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="12a81-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="12a81-114">Następnie przetwarza żądanie i wystawia odpowiedź na zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="12a81-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="12a81-115">Zaufany podsystem przetwarza odpowiedź i wystawia własną odpowiedź na klienta.</span><span class="sxs-lookup"><span data-stu-id="12a81-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="12a81-116">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="12a81-116">Characteristic</span></span>|<span data-ttu-id="12a81-117">Opis</span><span class="sxs-lookup"><span data-stu-id="12a81-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="12a81-118">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12a81-118">Security Mode</span></span>|<span data-ttu-id="12a81-119">Komunikat</span><span class="sxs-lookup"><span data-stu-id="12a81-119">Message</span></span>|  
|<span data-ttu-id="12a81-120">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="12a81-120">Interoperability</span></span>|<span data-ttu-id="12a81-121">Tylko Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="12a81-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="12a81-122">Uwierzytelnianie (usługa)</span><span class="sxs-lookup"><span data-stu-id="12a81-122">Authentication (service)</span></span>|<span data-ttu-id="12a81-123">Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.</span><span class="sxs-lookup"><span data-stu-id="12a81-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="12a81-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="12a81-124">Authentication (client)</span></span>|<span data-ttu-id="12a81-125">Zaufany podsystem uwierzytelnia klienta, a zasób uwierzytelnia usługę zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="12a81-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="12a81-126">Integralność</span><span class="sxs-lookup"><span data-stu-id="12a81-126">Integrity</span></span>|<span data-ttu-id="12a81-127">Tak</span><span class="sxs-lookup"><span data-stu-id="12a81-127">Yes</span></span>|  
|<span data-ttu-id="12a81-128">Poufność</span><span class="sxs-lookup"><span data-stu-id="12a81-128">Confidentiality</span></span>|<span data-ttu-id="12a81-129">Tak</span><span class="sxs-lookup"><span data-stu-id="12a81-129">Yes</span></span>|  
|<span data-ttu-id="12a81-130">Transport</span><span class="sxs-lookup"><span data-stu-id="12a81-130">Transport</span></span>|<span data-ttu-id="12a81-131">HTTP między klientem a zaufaną usługą podsystemu.</span><span class="sxs-lookup"><span data-stu-id="12a81-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="12a81-132">Netto. Protokół TCP między zaufaną usługą podsystemu a zasobem (usługa zaplecza).</span><span class="sxs-lookup"><span data-stu-id="12a81-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="12a81-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="12a81-133">Binding</span></span>|<span data-ttu-id="12a81-134"><xref:System.ServiceModel.WSHttpBinding><xref:System.ServiceModel.NetTcpBinding> [i \<wsFederationhttpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="12a81-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="12a81-135">Zasób (usługa zaplecza)</span><span class="sxs-lookup"><span data-stu-id="12a81-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="12a81-136">Code</span><span class="sxs-lookup"><span data-stu-id="12a81-136">Code</span></span>  
 <span data-ttu-id="12a81-137">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zasobu, który używa zabezpieczeń transportu za pomocą protokołu transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="12a81-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="12a81-138">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="12a81-138">Configuration</span></span>  
 <span data-ttu-id="12a81-139">Następująca konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12a81-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="12a81-140">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="12a81-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="12a81-141">Code</span><span class="sxs-lookup"><span data-stu-id="12a81-141">Code</span></span>  
 <span data-ttu-id="12a81-142">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zaufanego podsystemu, który używa zabezpieczeń wiadomości za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="12a81-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="12a81-143">Poniższy kod przedstawia usługę w zaufanym podsystemie, która komunikuje się z usługą zaplecza przy użyciu zabezpieczeń transportu za pośrednictwem protokołu transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="12a81-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="12a81-144">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="12a81-144">Configuration</span></span>  
 <span data-ttu-id="12a81-145">Następująca konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12a81-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="12a81-146">Zanotuj dwa powiązania: Jeden zabezpiecza usługę hostowane w zaufanym podsystemie, a drugi komunikuje się między zaufanym podsystemem a usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="12a81-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="12a81-147">Klient</span><span class="sxs-lookup"><span data-stu-id="12a81-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="12a81-148">Code</span><span class="sxs-lookup"><span data-stu-id="12a81-148">Code</span></span>  
 <span data-ttu-id="12a81-149">Poniższy kod pokazuje, jak utworzyć klienta, który komunikuje się z zaufanym podsystemem przy użyciu zabezpieczeń wiadomości za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="12a81-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="12a81-150">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="12a81-150">Configuration</span></span>  
 <span data-ttu-id="12a81-151">Poniższy kod konfiguruje klienta do używania zabezpieczeń wiadomości za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="12a81-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="12a81-152">Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go skonfigurować).</span><span class="sxs-lookup"><span data-stu-id="12a81-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12a81-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12a81-153">See also</span></span>

- [<span data-ttu-id="12a81-154">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="12a81-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="12a81-155">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="12a81-155">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
