---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: ac789ba81d728c067be515479e749440bb5809d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779396"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="ddf47-102">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="ddf47-102">Trusted Subsystem</span></span>
<span data-ttu-id="ddf47-103">Klient uzyskuje dostęp do usług sieci Web, które są rozpowszechniane w sieci.</span><span class="sxs-lookup"><span data-stu-id="ddf47-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="ddf47-104">Usługi sieci Web zostały zaprojektowane, tak że dostęp do dodatkowych zasobów (np. baz danych lub inne usługi sieci Web) są hermetyzowane w logice biznesowej usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ddf47-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="ddf47-105">Te zasoby muszą być chronione przed nieautoryzowanym dostępem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="ddf47-106">Poniższa ilustracja przedstawia proces zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="ddf47-107">![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="ddf47-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="ddf47-108">W poniższych krokach opisano proces zaufany podsystem, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="ddf47-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1.  <span data-ttu-id="ddf47-109">Klient przesyła żądanie do zaufany podsystem, wraz z poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="ddf47-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2.  <span data-ttu-id="ddf47-110">Zaufany podsystem uwierzytelnia i autoryzuje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ddf47-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3.  <span data-ttu-id="ddf47-111">Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="ddf47-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="ddf47-112">To żądanie towarzyszy poświadczenia zaufany podsystem (lub konta usługi, w którym jest wykonywana procesu zaufany podsystem).</span><span class="sxs-lookup"><span data-stu-id="ddf47-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4.  <span data-ttu-id="ddf47-113">Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="ddf47-114">Następnie przetwarza żądanie i wysyła odpowiedź do zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5.  <span data-ttu-id="ddf47-115">Zaufany podsystem przetwarza odpowiedź i generuje odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="ddf47-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="ddf47-116">Cechy</span><span class="sxs-lookup"><span data-stu-id="ddf47-116">Characteristic</span></span>|<span data-ttu-id="ddf47-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf47-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ddf47-118">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ddf47-118">Security Mode</span></span>|<span data-ttu-id="ddf47-119">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ddf47-119">Message</span></span>|  
|<span data-ttu-id="ddf47-120">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="ddf47-120">Interoperability</span></span>|<span data-ttu-id="ddf47-121">Windows Communication Foundation (WCF) tylko.</span><span class="sxs-lookup"><span data-stu-id="ddf47-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="ddf47-122">Uwierzytelniania (usługa)</span><span class="sxs-lookup"><span data-stu-id="ddf47-122">Authentication (service)</span></span>|<span data-ttu-id="ddf47-123">Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.</span><span class="sxs-lookup"><span data-stu-id="ddf47-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="ddf47-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="ddf47-124">Authentication (client)</span></span>|<span data-ttu-id="ddf47-125">Zaufany podsystem uwierzytelnia klienta i zasobów uwierzytelnia usługi zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="ddf47-126">Integralność</span><span class="sxs-lookup"><span data-stu-id="ddf47-126">Integrity</span></span>|<span data-ttu-id="ddf47-127">Tak</span><span class="sxs-lookup"><span data-stu-id="ddf47-127">Yes</span></span>|  
|<span data-ttu-id="ddf47-128">Poufność</span><span class="sxs-lookup"><span data-stu-id="ddf47-128">Confidentiality</span></span>|<span data-ttu-id="ddf47-129">Tak</span><span class="sxs-lookup"><span data-stu-id="ddf47-129">Yes</span></span>|  
|<span data-ttu-id="ddf47-130">Transportu</span><span class="sxs-lookup"><span data-stu-id="ddf47-130">Transport</span></span>|<span data-ttu-id="ddf47-131">Protokół HTTP między klientem a usługą zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="ddf47-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="ddf47-132">NET. TCP między usługą zaufany podsystem i zasobów (usłudze zaplecza).</span><span class="sxs-lookup"><span data-stu-id="ddf47-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="ddf47-133">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="ddf47-133">Binding</span></span>|<span data-ttu-id="ddf47-134"><xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ddf47-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="ddf47-135">Zasób (usługa zaplecza)</span><span class="sxs-lookup"><span data-stu-id="ddf47-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="ddf47-136">Kod</span><span class="sxs-lookup"><span data-stu-id="ddf47-136">Code</span></span>  
 <span data-ttu-id="ddf47-137">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi dla zasobu, która używa zabezpieczenia transportu za pośrednictwem protokołu transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="ddf47-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="ddf47-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ddf47-138">Configuration</span></span>  
 <span data-ttu-id="ddf47-139">Następująca konfiguracja konfiguruje ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ddf47-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="ddf47-140">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="ddf47-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="ddf47-141">Kod</span><span class="sxs-lookup"><span data-stu-id="ddf47-141">Code</span></span>  
 <span data-ttu-id="ddf47-142">Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi dla zaufany podsystem, który używa Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ddf47-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="ddf47-143">Poniższy kod przedstawia usługę w zaufany podsystem, który komunikuje się za pomocą usługi zaplecza za pośrednictwem protokołu transportu TCP za pomocą zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="ddf47-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="ddf47-144">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ddf47-144">Configuration</span></span>  
 <span data-ttu-id="ddf47-145">Następująca konfiguracja konfiguruje ten sam punkt końcowy, za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ddf47-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="ddf47-146">Należy zauważyć dwa powiązania: zabezpiecza jedną usługę hostowaną w zaufany podsystem, a druga komunikuje się między zaufany podsystem i usługi zaplecza.</span><span class="sxs-lookup"><span data-stu-id="ddf47-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="ddf47-147">Klient</span><span class="sxs-lookup"><span data-stu-id="ddf47-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="ddf47-148">Kod</span><span class="sxs-lookup"><span data-stu-id="ddf47-148">Code</span></span>  
 <span data-ttu-id="ddf47-149">Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufany podsystem przy użyciu Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ddf47-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="ddf47-150">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ddf47-150">Configuration</span></span>  
 <span data-ttu-id="ddf47-151">Poniższy kod konfiguruje klienta w celu użycia Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ddf47-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="ddf47-152">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="ddf47-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddf47-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddf47-153">See Also</span></span>  
 [<span data-ttu-id="ddf47-154">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ddf47-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ddf47-155">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="ddf47-155">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
