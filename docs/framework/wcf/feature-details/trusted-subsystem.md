---
title: Zaufany podsystem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: f90906b4c3fc1d1d76977451abfb238bb33fb581
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595118"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="17269-102">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="17269-102">Trusted Subsystem</span></span>
<span data-ttu-id="17269-103">Klient uzyskuje dostęp do co najmniej jednej usługi sieci Web, która jest dystrybuowana przez sieć.</span><span class="sxs-lookup"><span data-stu-id="17269-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="17269-104">Usługi sieci Web są zaprojektowane tak, aby dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web) był hermetyzowany w logice biznesowej usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17269-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="17269-105">Te zasoby muszą być chronione przed nieautoryzowanym dostępem.</span><span class="sxs-lookup"><span data-stu-id="17269-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="17269-106">Poniższa ilustracja przedstawia proces zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="17269-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="17269-107">![Zaufany podsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="17269-107">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="17269-108">W poniższych krokach opisano proces zaufanego podsystemu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="17269-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="17269-109">Klient przesyła żądanie do zaufanego podsystemu wraz z poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="17269-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="17269-110">Zaufany podsystem uwierzytelnia użytkownika i autoryzuje go.</span><span class="sxs-lookup"><span data-stu-id="17269-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="17269-111">Zaufany podsystem wysyła komunikat żądania do zasobu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="17269-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="17269-112">Do tego żądania dołączane są poświadczenia dla zaufanego podsystemu (lub konta usługi, w ramach którego jest wykonywany proces zaufanego podsystemu).</span><span class="sxs-lookup"><span data-stu-id="17269-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="17269-113">Zasób zaplecza uwierzytelnia i autoryzuje zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="17269-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="17269-114">Następnie przetwarza żądanie i wystawia odpowiedź na zaufany podsystem.</span><span class="sxs-lookup"><span data-stu-id="17269-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="17269-115">Zaufany podsystem przetwarza odpowiedź i emituje własną odpowiedź do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="17269-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="17269-116">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="17269-116">Characteristic</span></span>|<span data-ttu-id="17269-117">Opis</span><span class="sxs-lookup"><span data-stu-id="17269-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="17269-118">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="17269-118">Security Mode</span></span>|<span data-ttu-id="17269-119">Komunikat</span><span class="sxs-lookup"><span data-stu-id="17269-119">Message</span></span>|  
|<span data-ttu-id="17269-120">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="17269-120">Interoperability</span></span>|<span data-ttu-id="17269-121">Tylko Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="17269-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="17269-122">Uwierzytelnianie (usługa)</span><span class="sxs-lookup"><span data-stu-id="17269-122">Authentication (service)</span></span>|<span data-ttu-id="17269-123">Usługa tokenu zabezpieczającego uwierzytelnia i autoryzuje klientów.</span><span class="sxs-lookup"><span data-stu-id="17269-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="17269-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="17269-124">Authentication (client)</span></span>|<span data-ttu-id="17269-125">Zaufany podsystem uwierzytelnia klienta, a zasób uwierzytelnia usługę zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="17269-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="17269-126">Integralność</span><span class="sxs-lookup"><span data-stu-id="17269-126">Integrity</span></span>|<span data-ttu-id="17269-127">Tak</span><span class="sxs-lookup"><span data-stu-id="17269-127">Yes</span></span>|  
|<span data-ttu-id="17269-128">Poufność</span><span class="sxs-lookup"><span data-stu-id="17269-128">Confidentiality</span></span>|<span data-ttu-id="17269-129">Tak</span><span class="sxs-lookup"><span data-stu-id="17269-129">Yes</span></span>|  
|<span data-ttu-id="17269-130">Transport</span><span class="sxs-lookup"><span data-stu-id="17269-130">Transport</span></span>|<span data-ttu-id="17269-131">Protokół HTTP między klientem a usługą zaufanego podsystemu.</span><span class="sxs-lookup"><span data-stu-id="17269-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="17269-132">Waga. TCP między usługą zaufanego podsystemu a zasobem (usługa zaplecza).</span><span class="sxs-lookup"><span data-stu-id="17269-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="17269-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="17269-133">Binding</span></span>|<span data-ttu-id="17269-134"><xref:System.ServiceModel.WSHttpBinding>lub<xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="17269-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="17269-135">Zasób (usługa zaplecza)</span><span class="sxs-lookup"><span data-stu-id="17269-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="17269-136">Kod</span><span class="sxs-lookup"><span data-stu-id="17269-136">Code</span></span>  
 <span data-ttu-id="17269-137">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zasobu, który używa zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.</span><span class="sxs-lookup"><span data-stu-id="17269-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="17269-138">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="17269-138">Configuration</span></span>  
 <span data-ttu-id="17269-139">Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="17269-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="trusted-subsystem"></a><span data-ttu-id="17269-140">Zaufany podsystem</span><span class="sxs-lookup"><span data-stu-id="17269-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="17269-141">Kod</span><span class="sxs-lookup"><span data-stu-id="17269-141">Code</span></span>  
 <span data-ttu-id="17269-142">Poniższy kod pokazuje, jak utworzyć punkt końcowy usługi dla zaufanego podsystemu, który używa zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="17269-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="17269-143">Poniższy kod przedstawia usługę w zaufanym podsystemie, który komunikuje się z usługą zaplecza przy użyciu zabezpieczeń transportu za pośrednictwem protokołu transportowego TCP.</span><span class="sxs-lookup"><span data-stu-id="17269-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="17269-144">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="17269-144">Configuration</span></span>  
 <span data-ttu-id="17269-145">Poniższa konfiguracja konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="17269-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="17269-146">Zwróć uwagę na dwa powiązania: jeden zabezpiecza usługę hostowaną w zaufanym podsystemie, a druga komunikuje się między zaufanym podsystemem a usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="17269-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="17269-147">Klient</span><span class="sxs-lookup"><span data-stu-id="17269-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="17269-148">Kod</span><span class="sxs-lookup"><span data-stu-id="17269-148">Code</span></span>  
 <span data-ttu-id="17269-149">Poniższy kod przedstawia sposób tworzenia klienta, który komunikuje się z zaufanym podsystemem przy użyciu zabezpieczeń komunikatów przez protokół HTTP i nazwę użytkownika i hasło na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="17269-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="17269-150">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="17269-150">Configuration</span></span>  
 <span data-ttu-id="17269-151">Poniższy kod służy do konfigurowania klienta do korzystania z zabezpieczeń komunikatów za pośrednictwem protokołu HTTP oraz nazwy użytkownika i hasła na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="17269-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="17269-152">Nazwę użytkownika i hasło można określić tylko przy użyciu kodu (nie można go konfigurować).</span><span class="sxs-lookup"><span data-stu-id="17269-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17269-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17269-153">See also</span></span>

- [<span data-ttu-id="17269-154">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="17269-154">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="17269-155">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="17269-155">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
