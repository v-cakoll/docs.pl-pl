---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 4f3166b8f1e59a100f54574ab548f5dae88eb5cd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742640"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="df656-102">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="df656-102">Trusted Subsystem</span></span>
<span data-ttu-id="df656-103">Klient uzyskuje dostęp do co najmniej jednej usługi sieci Web, która jest dystrybuowana przez sieć.</span><span class="sxs-lookup"><span data-stu-id="df656-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="df656-104">Usługi sieci Web są zaprojektowane tak, aby dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web) był hermetyzowany w logice biznesowej usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="df656-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="df656-105">Te zasoby muszą być chronione przed nieautoryzowanym dostępem.</span><span class="sxs-lookup"><span data-stu-id="df656-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="df656-106">Poniższa ilustracja przedstawia proces zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="df656-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="df656-107">![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="df656-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="df656-108">W poniższych krokach opisano proces zaufanego podsystemu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="df656-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="df656-109">Klient przesyła żądanie do zaufanego podsystemu wraz z poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="df656-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="df656-110">Zaufany podsystem uwierzytelnia użytkownika i autoryzuje go.</span><span class="sxs-lookup"><span data-stu-id="df656-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="df656-111">Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="df656-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="df656-112">Do tego żądania dołączane są poświadczenia dla zaufanego podsystemu (lub konta usługi, w ramach którego jest wykonywany proces zaufanego podsystemu).</span><span class="sxs-lookup"><span data-stu-id="df656-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="df656-113">Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="df656-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="df656-114">Następnie przetwarza żądanie i wystawia odpowiedź na zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="df656-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="df656-115">Zaufany podsystem przetwarza odpowiedź i emituje własną odpowiedź do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="df656-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="df656-116">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="df656-116">Characteristic</span></span>|<span data-ttu-id="df656-117">Opis</span><span class="sxs-lookup"><span data-stu-id="df656-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="df656-118">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="df656-118">Security Mode</span></span>|<span data-ttu-id="df656-119">Komunikat</span><span class="sxs-lookup"><span data-stu-id="df656-119">Message</span></span>|  
|<span data-ttu-id="df656-120">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="df656-120">Interoperability</span></span>|<span data-ttu-id="df656-121">Tylko Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="df656-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="df656-122">Uwierzytelnianie (usługa)</span><span class="sxs-lookup"><span data-stu-id="df656-122">Authentication (service)</span></span>|<span data-ttu-id="df656-123">Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.</span><span class="sxs-lookup"><span data-stu-id="df656-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="df656-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="df656-124">Authentication (client)</span></span>|<span data-ttu-id="df656-125">Zaufany podsystem uwierzytelnia klienta, a zasób uwierzytelnia usługę zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="df656-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="df656-126">Integralność</span><span class="sxs-lookup"><span data-stu-id="df656-126">Integrity</span></span>|<span data-ttu-id="df656-127">Tak</span><span class="sxs-lookup"><span data-stu-id="df656-127">Yes</span></span>|  
|<span data-ttu-id="df656-128">Poufne</span><span class="sxs-lookup"><span data-stu-id="df656-128">Confidentiality</span></span>|<span data-ttu-id="df656-129">Tak</span><span class="sxs-lookup"><span data-stu-id="df656-129">Yes</span></span>|  
|<span data-ttu-id="df656-130">Transport</span><span class="sxs-lookup"><span data-stu-id="df656-130">Transport</span></span>|<span data-ttu-id="df656-131">Protokół HTTP między klientem a usługą zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="df656-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="df656-132">Waga. TCP między usługą zaufanego podsystemu a zasobem (usługa zaplecza).</span><span class="sxs-lookup"><span data-stu-id="df656-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="df656-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="df656-133">Binding</span></span>|<span data-ttu-id="df656-134"><xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="df656-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="df656-135">Zasób (usługa zaplecza)</span><span class="sxs-lookup"><span data-stu-id="df656-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="df656-136">Kod</span><span class="sxs-lookup"><span data-stu-id="df656-136">Code</span></span>  
 <span data-ttu-id="df656-137">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zasobu, który używa zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.</span><span class="sxs-lookup"><span data-stu-id="df656-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="df656-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="df656-138">Configuration</span></span>  
 <span data-ttu-id="df656-139">Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="df656-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="df656-140">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="df656-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="df656-141">Kod</span><span class="sxs-lookup"><span data-stu-id="df656-141">Code</span></span>  
 <span data-ttu-id="df656-142">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zaufanego podsystemu, który używa zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="df656-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="df656-143">Poniższy kod przedstawia usługę w zaufanym podsystemie, który komunikuje się z usługą zaplecza przy użyciu zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.</span><span class="sxs-lookup"><span data-stu-id="df656-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="df656-144">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="df656-144">Configuration</span></span>  
 <span data-ttu-id="df656-145">Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="df656-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="df656-146">Zwróć uwagę na dwa powiązania: jeden zabezpiecza usługę hostowaną w zaufanym podsystemie, a druga komunikuje się między zaufanym podsystemem a usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="df656-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="df656-147">Klient</span><span class="sxs-lookup"><span data-stu-id="df656-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="df656-148">Kod</span><span class="sxs-lookup"><span data-stu-id="df656-148">Code</span></span>  
 <span data-ttu-id="df656-149">Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufanym podsystemem przy użyciu zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="df656-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="df656-150">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="df656-150">Configuration</span></span>  
 <span data-ttu-id="df656-151">Poniższy kod służy do konfigurowania klienta do korzystania z zabezpieczeń komunikatów za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="df656-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="df656-152">Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go konfigurować).</span><span class="sxs-lookup"><span data-stu-id="df656-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df656-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df656-153">See also</span></span>

- [<span data-ttu-id="df656-154">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="df656-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="df656-155">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="df656-155">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
