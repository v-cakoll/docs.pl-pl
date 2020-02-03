---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 9ac563ad237749665e9cc53c15aec35f461abfc0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742664"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="e824a-102">Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="e824a-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="e824a-103">W tym artykule omówiono użycie certyfikatów X. 509 na potrzeby uwierzytelniania serwera i klienta w przypadku korzystania z zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="e824a-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="e824a-104">Aby uzyskać więcej informacji na temat certyfikatów X. 509, zobacz [Certyfikaty klucza publicznego x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="e824a-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="e824a-105">Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcą certyfikatów innych firm.</span><span class="sxs-lookup"><span data-stu-id="e824a-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="e824a-106">W domenie systemu Windows Server usługi certyfikatów Active Directory mogą być używane do wystawiania certyfikatów na komputery klienckie w domenie.</span><span class="sxs-lookup"><span data-stu-id="e824a-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="e824a-107">W tym scenariuszu usługa jest hostowana w Internet Information Services (IIS), która jest skonfigurowana przy użyciu SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="e824a-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="e824a-108">Usługa została skonfigurowana przy użyciu certyfikatu SSL (X. 509), aby umożliwić klientom weryfikowanie tożsamości serwera.</span><span class="sxs-lookup"><span data-stu-id="e824a-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="e824a-109">Klient jest również skonfigurowany przy użyciu certyfikatu X. 509, który umożliwia usłudze weryfikowanie tożsamości klienta.</span><span class="sxs-lookup"><span data-stu-id="e824a-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="e824a-110">Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być traktowany jako zaufany przez serwer.</span><span class="sxs-lookup"><span data-stu-id="e824a-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="e824a-111">Rzeczywista Mechanics sposobu, w jaki usługa i klient sprawdzają tożsamość nawzajem, wykracza poza zakres tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="e824a-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="e824a-112">Aby uzyskać więcej informacji, zobacz [podpis cyfrowy](https://en.wikipedia.org/wiki/Digital_signature) w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="e824a-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="e824a-113">Ten scenariusz implementuje wzorzec komunikatu żądania/odpowiedzi, jak pokazano na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="e824a-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="e824a-114">![Bezpieczny transfer przy użyciu certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="e824a-114">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="e824a-115">Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [instrukcje: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e824a-115">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="e824a-116">W poniższej tabeli opisano różne cechy scenariusza.</span><span class="sxs-lookup"><span data-stu-id="e824a-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="e824a-117">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="e824a-117">Characteristic</span></span>|<span data-ttu-id="e824a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e824a-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e824a-119">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e824a-119">Security Mode</span></span>|<span data-ttu-id="e824a-120">Transport</span><span class="sxs-lookup"><span data-stu-id="e824a-120">Transport</span></span>|  
|<span data-ttu-id="e824a-121">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="e824a-121">Interoperability</span></span>|<span data-ttu-id="e824a-122">Z istniejącymi klientami i usługami sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e824a-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="e824a-123">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="e824a-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e824a-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="e824a-124">Authentication (Client)</span></span>|<span data-ttu-id="e824a-125">Tak (przy użyciu certyfikatu SSL)</span><span class="sxs-lookup"><span data-stu-id="e824a-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="e824a-126">Tak (przy użyciu certyfikatu X. 509)</span><span class="sxs-lookup"><span data-stu-id="e824a-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="e824a-127">Integralność danych</span><span class="sxs-lookup"><span data-stu-id="e824a-127">Data Integrity</span></span>|<span data-ttu-id="e824a-128">Tak</span><span class="sxs-lookup"><span data-stu-id="e824a-128">Yes</span></span>|  
|<span data-ttu-id="e824a-129">Poufność danych</span><span class="sxs-lookup"><span data-stu-id="e824a-129">Data Confidentiality</span></span>|<span data-ttu-id="e824a-130">Tak</span><span class="sxs-lookup"><span data-stu-id="e824a-130">Yes</span></span>|  
|<span data-ttu-id="e824a-131">Transport</span><span class="sxs-lookup"><span data-stu-id="e824a-131">Transport</span></span>|<span data-ttu-id="e824a-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="e824a-132">HTTPS</span></span>|  
|<span data-ttu-id="e824a-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="e824a-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="e824a-134">Konfigurowanie usługi</span><span class="sxs-lookup"><span data-stu-id="e824a-134">Configure the Service</span></span>  
 <span data-ttu-id="e824a-135">Ponieważ usługa w tym scenariuszu jest hostowana w usługach IIS, jest konfigurowana za pomocą pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="e824a-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="e824a-136">Poniższy plik Web. config zawiera informacje na temat konfigurowania <xref:System.ServiceModel.WSHttpBinding> do korzystania z zabezpieczeń transportu i poświadczeń klienta X. 509.</span><span class="sxs-lookup"><span data-stu-id="e824a-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="e824a-137">Konfigurowanie klienta programu</span><span class="sxs-lookup"><span data-stu-id="e824a-137">Configure the Client</span></span>  
 <span data-ttu-id="e824a-138">Klienta można skonfigurować w kodzie lub w pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="e824a-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="e824a-139">Poniższy przykład pokazuje, jak skonfigurować klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e824a-139">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="e824a-140">Alternatywnie można skonfigurować klienta w pliku App. config, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e824a-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e824a-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e824a-141">See also</span></span>

- [<span data-ttu-id="e824a-142">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e824a-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="e824a-143">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e824a-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
