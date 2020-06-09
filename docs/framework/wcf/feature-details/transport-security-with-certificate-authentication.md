---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 47322cbcddf9f33101bbfbeaa07a3fab74b9d26a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576021"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="73d87-102">Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów</span><span class="sxs-lookup"><span data-stu-id="73d87-102">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="73d87-103">W tym artykule omówiono użycie certyfikatów X. 509 na potrzeby uwierzytelniania serwera i klienta w przypadku korzystania z zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="73d87-103">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="73d87-104">Aby uzyskać więcej informacji na temat certyfikatów X. 509, zobacz [Certyfikaty klucza publicznego x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="73d87-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="73d87-105">Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcą certyfikatów innych firm.</span><span class="sxs-lookup"><span data-stu-id="73d87-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="73d87-106">W domenie systemu Windows Server usługi certyfikatów Active Directory mogą być używane do wystawiania certyfikatów na komputery klienckie w domenie.</span><span class="sxs-lookup"><span data-stu-id="73d87-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="73d87-107">W tym scenariuszu usługa jest hostowana w Internet Information Services (IIS), która jest skonfigurowana przy użyciu SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="73d87-107">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="73d87-108">Usługa została skonfigurowana przy użyciu certyfikatu SSL (X. 509), aby umożliwić klientom weryfikowanie tożsamości serwera.</span><span class="sxs-lookup"><span data-stu-id="73d87-108">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="73d87-109">Klient jest również skonfigurowany przy użyciu certyfikatu X. 509, który umożliwia usłudze weryfikowanie tożsamości klienta.</span><span class="sxs-lookup"><span data-stu-id="73d87-109">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="73d87-110">Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być traktowany jako zaufany przez serwer.</span><span class="sxs-lookup"><span data-stu-id="73d87-110">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="73d87-111">Rzeczywista Mechanics sposobu, w jaki usługa i klient sprawdzają tożsamość nawzajem, wykracza poza zakres tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="73d87-111">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="73d87-112">Aby uzyskać więcej informacji, zobacz [podpis cyfrowy](https://en.wikipedia.org/wiki/Digital_signature) w witrynie Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="73d87-112">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="73d87-113">Ten scenariusz implementuje wzorzec komunikatu żądania/odpowiedzi, jak pokazano na poniższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="73d87-113">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="73d87-114">![Bezpieczny transfer przy użyciu certyfikatów](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="73d87-114">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="73d87-115">Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](working-with-certificates.md) i [instrukcje: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="73d87-115">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="73d87-116">W poniższej tabeli opisano różne cechy scenariusza.</span><span class="sxs-lookup"><span data-stu-id="73d87-116">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="73d87-117">Charakterystyka</span><span class="sxs-lookup"><span data-stu-id="73d87-117">Characteristic</span></span>|<span data-ttu-id="73d87-118">Opis</span><span class="sxs-lookup"><span data-stu-id="73d87-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="73d87-119">Tryb zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="73d87-119">Security Mode</span></span>|<span data-ttu-id="73d87-120">Transport</span><span class="sxs-lookup"><span data-stu-id="73d87-120">Transport</span></span>|  
|<span data-ttu-id="73d87-121">Współdziałanie</span><span class="sxs-lookup"><span data-stu-id="73d87-121">Interoperability</span></span>|<span data-ttu-id="73d87-122">Z istniejącymi klientami i usługami sieci Web.</span><span class="sxs-lookup"><span data-stu-id="73d87-122">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="73d87-123">Uwierzytelnianie (serwer)</span><span class="sxs-lookup"><span data-stu-id="73d87-123">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="73d87-124">Uwierzytelnianie (klient)</span><span class="sxs-lookup"><span data-stu-id="73d87-124">Authentication (Client)</span></span>|<span data-ttu-id="73d87-125">Tak (przy użyciu certyfikatu SSL)</span><span class="sxs-lookup"><span data-stu-id="73d87-125">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="73d87-126">Tak (przy użyciu certyfikatu X. 509)</span><span class="sxs-lookup"><span data-stu-id="73d87-126">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="73d87-127">Integralność danych</span><span class="sxs-lookup"><span data-stu-id="73d87-127">Data Integrity</span></span>|<span data-ttu-id="73d87-128">Tak</span><span class="sxs-lookup"><span data-stu-id="73d87-128">Yes</span></span>|  
|<span data-ttu-id="73d87-129">Poufność danych</span><span class="sxs-lookup"><span data-stu-id="73d87-129">Data Confidentiality</span></span>|<span data-ttu-id="73d87-130">Tak</span><span class="sxs-lookup"><span data-stu-id="73d87-130">Yes</span></span>|  
|<span data-ttu-id="73d87-131">Transport</span><span class="sxs-lookup"><span data-stu-id="73d87-131">Transport</span></span>|<span data-ttu-id="73d87-132">HTTPS</span><span class="sxs-lookup"><span data-stu-id="73d87-132">HTTPS</span></span>|  
|<span data-ttu-id="73d87-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="73d87-133">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="73d87-134">Konfigurowanie usługi</span><span class="sxs-lookup"><span data-stu-id="73d87-134">Configure the Service</span></span>  
 <span data-ttu-id="73d87-135">Ponieważ usługa w tym scenariuszu jest hostowana w usługach IIS, jest konfigurowana za pomocą pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="73d87-135">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="73d87-136">Poniższy plik Web. config pokazuje, jak skonfigurować <xref:System.ServiceModel.WSHttpBinding> program do korzystania z poświadczeń klienta transportowego i X. 509.</span><span class="sxs-lookup"><span data-stu-id="73d87-136">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
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
  
## <a name="configure-the-client"></a><span data-ttu-id="73d87-137">Konfigurowanie klienta programu</span><span class="sxs-lookup"><span data-stu-id="73d87-137">Configure the Client</span></span>  
 <span data-ttu-id="73d87-138">Klienta można skonfigurować w kodzie lub w pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="73d87-138">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="73d87-139">Poniższy przykład pokazuje, jak skonfigurować klienta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="73d87-139">The following example shows how to configure the client in code.</span></span>  
  
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
  
 <span data-ttu-id="73d87-140">Alternatywnie można skonfigurować klienta w pliku App. config, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="73d87-140">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73d87-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73d87-141">See also</span></span>

- [<span data-ttu-id="73d87-142">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="73d87-142">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="73d87-143">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="73d87-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
