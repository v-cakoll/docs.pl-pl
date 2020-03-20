---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184330"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="2e301-102">Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="2e301-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="2e301-103">W tym artykule omówiono przy użyciu certyfikatów X.509 dla uwierzytelniania serwera i klienta podczas korzystania z zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="2e301-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="2e301-104">Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz [X.509 Certyfikaty kluczy publicznych](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="2e301-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="2e301-105">Certyfikaty muszą być wystawiane przez urząd certyfikacji, który często jest zewnętrznym wystawcą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2e301-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="2e301-106">W domenie systemu Windows Server usługi certyfikatów Active Directory mogą być używane do wystawiania certyfikatów komputerom klienckim w domenie.</span><span class="sxs-lookup"><span data-stu-id="2e301-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="2e301-107">W tym scenariuszu usługa jest hostowana w ramach internetowych usług informacyjnych (IIS), który jest skonfigurowany z warstwą bezpiecznych gniazd (SSL).</span><span class="sxs-lookup"><span data-stu-id="2e301-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="2e301-108">Usługa jest skonfigurowana z certyfikatem SSL (X.509), aby umożliwić klientom weryfikację tożsamości serwera.</span><span class="sxs-lookup"><span data-stu-id="2e301-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="2e301-109">Klient jest również skonfigurowany z certyfikatem X.509, który umożliwia usłudze zweryfikowanie tożsamości klienta.</span><span class="sxs-lookup"><span data-stu-id="2e301-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="2e301-110">Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być zaufany przez serwer.</span><span class="sxs-lookup"><span data-stu-id="2e301-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="2e301-111">Rzeczywista mechanika sposobu, w jaki usługa i klient weryfikuje tożsamość siebie nawzajem, wykracza poza zakres tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="2e301-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="2e301-112">Aby uzyskać więcej informacji, zobacz [Podpis cyfrowy](https://en.wikipedia.org/wiki/Digital_signature) w Wikipedii.</span><span class="sxs-lookup"><span data-stu-id="2e301-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="2e301-113">W tym scenariuszu implementuje wzorzec komunikatów żądania/odpowiedzi, jak pokazano na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="2e301-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="2e301-114">![Bezpieczny transfer przy użyciu certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="2e301-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="2e301-115">Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [Jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="2e301-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="2e301-116">W poniższej tabeli opisano różne cechy scenariusza.</span><span class="sxs-lookup"><span data-stu-id="2e301-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="2e301-117">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="2e301-117">Characteristic</span></span>|<span data-ttu-id="2e301-118">Opis</span><span class="sxs-lookup"><span data-stu-id="2e301-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2e301-119">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2e301-119">Security Mode</span></span>|<span data-ttu-id="2e301-120">Transport</span><span class="sxs-lookup"><span data-stu-id="2e301-120">Transport</span></span>|  
|<span data-ttu-id="2e301-121">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="2e301-121">Interoperability</span></span>|<span data-ttu-id="2e301-122">Z istniejącymi klientami i usługami usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2e301-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="2e301-123">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="2e301-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="2e301-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="2e301-124">Authentication (Client)</span></span>|<span data-ttu-id="2e301-125">Tak (przy użyciu certyfikatu SSL)</span><span class="sxs-lookup"><span data-stu-id="2e301-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="2e301-126">Tak (przy użyciu certyfikatu X.509)</span><span class="sxs-lookup"><span data-stu-id="2e301-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="2e301-127">Integralność danych</span><span class="sxs-lookup"><span data-stu-id="2e301-127">Data Integrity</span></span>|<span data-ttu-id="2e301-128">Tak</span><span class="sxs-lookup"><span data-stu-id="2e301-128">Yes</span></span>|  
|<span data-ttu-id="2e301-129">Poufność danych</span><span class="sxs-lookup"><span data-stu-id="2e301-129">Data Confidentiality</span></span>|<span data-ttu-id="2e301-130">Tak</span><span class="sxs-lookup"><span data-stu-id="2e301-130">Yes</span></span>|  
|<span data-ttu-id="2e301-131">Transport</span><span class="sxs-lookup"><span data-stu-id="2e301-131">Transport</span></span>|<span data-ttu-id="2e301-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e301-132">HTTPS</span></span>|  
|<span data-ttu-id="2e301-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="2e301-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="2e301-134">Konfigurowanie usługi</span><span class="sxs-lookup"><span data-stu-id="2e301-134">Configure the Service</span></span>  
 <span data-ttu-id="2e301-135">Ponieważ usługa w tym scenariuszu jest hostowana w usługach IIS, jest skonfigurowana z plikiem web.config.</span><span class="sxs-lookup"><span data-stu-id="2e301-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="2e301-136">Poniżej web.config pokazuje, jak <xref:System.ServiceModel.WSHttpBinding> skonfigurować do korzystania z zabezpieczeń transportu i X.509 poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="2e301-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="2e301-137">Konfigurowanie klienta</span><span class="sxs-lookup"><span data-stu-id="2e301-137">Configure the Client</span></span>  
 <span data-ttu-id="2e301-138">Klienta można skonfigurować w kodzie lub w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="2e301-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="2e301-139">W poniższym przykładzie pokazano, jak skonfigurować klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2e301-139">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="2e301-140">Alternatywnie można skonfigurować klienta w pliku App.config, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2e301-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e301-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e301-141">See also</span></span>

- [<span data-ttu-id="2e301-142">Omówienie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2e301-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="2e301-143">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2e301-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
