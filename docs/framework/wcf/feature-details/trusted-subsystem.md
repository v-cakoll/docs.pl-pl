---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 59c44609017ab18a176624b7ef6d409005151c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="trusted-subsystem"></a><span data-ttu-id="759b1-102">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="759b1-102">Trusted Subsystem</span></span>
<span data-ttu-id="759b1-103">Klient uzyskuje dostęp do usług sieci Web, które są rozproszone w sieci.</span><span class="sxs-lookup"><span data-stu-id="759b1-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="759b1-104">Usługi sieci Web są zaprojektowane, że dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web) jest hermetyzowany logiki biznesowej usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="759b1-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="759b1-105">Te zasoby muszą być chronione przed nieautoryzowanym dostępem.</span><span class="sxs-lookup"><span data-stu-id="759b1-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="759b1-106">Poniższa ilustracja przedstawia proces zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="759b1-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="759b1-107">![Zaufany podsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="759b1-107">![Trusted subsystem](../../../../docs/framework/wcf/feature-details/media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="759b1-108">W poniższych krokach opisano proces zaufany podsystem zgodnie z opisami:</span><span class="sxs-lookup"><span data-stu-id="759b1-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1.  <span data-ttu-id="759b1-109">Klient przesyła żądanie zaufany podsystem, wraz z poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="759b1-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2.  <span data-ttu-id="759b1-110">Zaufany podsystem uwierzytelnia i autoryzuje użytkownika.</span><span class="sxs-lookup"><span data-stu-id="759b1-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3.  <span data-ttu-id="759b1-111">Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="759b1-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="759b1-112">To żądanie towarzyszy poświadczenia zaufany podsystem (lub konta usługi, którym jest wykonywany proces zaufany podsystem).</span><span class="sxs-lookup"><span data-stu-id="759b1-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4.  <span data-ttu-id="759b1-113">Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="759b1-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="759b1-114">Następnie przetwarza żądanie i odpowiedź zaufany podsystem problemy.</span><span class="sxs-lookup"><span data-stu-id="759b1-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5.  <span data-ttu-id="759b1-115">Zaufany podsystem przetwarza odpowiedzi i generuje odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="759b1-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="759b1-116">Cechy</span><span class="sxs-lookup"><span data-stu-id="759b1-116">Characteristic</span></span>|<span data-ttu-id="759b1-117">Opis</span><span class="sxs-lookup"><span data-stu-id="759b1-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="759b1-118">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="759b1-118">Security Mode</span></span>|<span data-ttu-id="759b1-119">Komunikat</span><span class="sxs-lookup"><span data-stu-id="759b1-119">Message</span></span>|  
|<span data-ttu-id="759b1-120">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="759b1-120">Interoperability</span></span>|<span data-ttu-id="759b1-121">Windows Communication Foundation (WCF) tylko.</span><span class="sxs-lookup"><span data-stu-id="759b1-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="759b1-122">Uwierzytelnianie (usługa)</span><span class="sxs-lookup"><span data-stu-id="759b1-122">Authentication (service)</span></span>|<span data-ttu-id="759b1-123">Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.</span><span class="sxs-lookup"><span data-stu-id="759b1-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="759b1-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="759b1-124">Authentication (client)</span></span>|<span data-ttu-id="759b1-125">Zaufany podsystem umożliwiają uwierzytelnienie klienta a zasobu usługi zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="759b1-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="759b1-126">Integralność</span><span class="sxs-lookup"><span data-stu-id="759b1-126">Integrity</span></span>|<span data-ttu-id="759b1-127">Tak</span><span class="sxs-lookup"><span data-stu-id="759b1-127">Yes</span></span>|  
|<span data-ttu-id="759b1-128">Poufność</span><span class="sxs-lookup"><span data-stu-id="759b1-128">Confidentiality</span></span>|<span data-ttu-id="759b1-129">Tak</span><span class="sxs-lookup"><span data-stu-id="759b1-129">Yes</span></span>|  
|<span data-ttu-id="759b1-130">Transportu</span><span class="sxs-lookup"><span data-stu-id="759b1-130">Transport</span></span>|<span data-ttu-id="759b1-131">Protokół HTTP między klientem a usługą zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="759b1-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="759b1-132">NET. TCP między usługą zaufany podsystem i zasobów (usługi zaplecza).</span><span class="sxs-lookup"><span data-stu-id="759b1-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="759b1-133">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="759b1-133">Binding</span></span>|<span data-ttu-id="759b1-134"><xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="759b1-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="759b1-135">Zasobu (usługa zaplecza)</span><span class="sxs-lookup"><span data-stu-id="759b1-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="759b1-136">Kod</span><span class="sxs-lookup"><span data-stu-id="759b1-136">Code</span></span>  
 <span data-ttu-id="759b1-137">Poniższy kod przedstawia sposób tworzenia punktu końcowego dla zasobu, który używa zabezpieczeń transportu za pośrednictwem protokołu transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="759b1-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="759b1-138">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="759b1-138">Configuration</span></span>  
 <span data-ttu-id="759b1-139">Następująca konfiguracja konfiguruje tego samego punktu końcowego za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="759b1-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="759b1-140">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="759b1-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="759b1-141">Kod</span><span class="sxs-lookup"><span data-stu-id="759b1-141">Code</span></span>  
 <span data-ttu-id="759b1-142">Poniższy kod przedstawia sposób tworzenia punktu końcowego dla zaufanych podsystemu, który używa Zabezpieczanie komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="759b1-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="759b1-143">Poniższy kod przedstawia usługę w podsystemie zaufany, który komunikuje się z usługą zaplecza za pomocą zabezpieczeń transportu za pośrednictwem protokołu transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="759b1-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="759b1-144">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="759b1-144">Configuration</span></span>  
 <span data-ttu-id="759b1-145">Następująca konfiguracja konfiguruje tego samego punktu końcowego za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="759b1-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="759b1-146">Należy zwrócić uwagę dwa powiązania: jeden zabezpiecza usługi hostowanej w podsystemie zaufanych i innych zapewnia komunikację między zaufany podsystem i usługi zaplecza.</span><span class="sxs-lookup"><span data-stu-id="759b1-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="759b1-147">Klient</span><span class="sxs-lookup"><span data-stu-id="759b1-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="759b1-148">Kod</span><span class="sxs-lookup"><span data-stu-id="759b1-148">Code</span></span>  
 <span data-ttu-id="759b1-149">Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufany podsystem przy użyciu zabezpieczenia komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="759b1-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="759b1-150">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="759b1-150">Configuration</span></span>  
 <span data-ttu-id="759b1-151">Poniższy kod konfiguruje klienta do zabezpieczenia komunikatów za pośrednictwem protokołu HTTP i nazwę użytkownika i hasło uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="759b1-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="759b1-152">Nazwa użytkownika i hasło można określić tylko przy użyciu kodu (nie jest konfigurowalne).</span><span class="sxs-lookup"><span data-stu-id="759b1-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="759b1-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="759b1-153">See Also</span></span>  
 [<span data-ttu-id="759b1-154">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="759b1-154">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="759b1-155">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="759b1-155">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
