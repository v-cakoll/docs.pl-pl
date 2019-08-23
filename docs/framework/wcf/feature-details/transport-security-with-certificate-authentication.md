---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: f94be530fb680320813a93e256e8e411234f2e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968645"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
W tym temacie omówiono użycie certyfikatów X. 509 na potrzeby uwierzytelniania serwera i klienta w przypadku korzystania z zabezpieczeń transportu. Aby uzyskać więcej informacji na temat certyfikatów X. 509, zobacz [Certyfikaty klucza publicznego x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcą certyfikatów innych firm. W domenie systemu Windows Server usługi certyfikatów Active Directory mogą być używane do wystawiania certyfikatów na komputery klienckie w domenie. Aby uzyskać więcej informacji, zobacz [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). W tym scenariuszu usługa jest hostowana w Internet Information Services (IIS), która jest skonfigurowana przy użyciu SSL (SSL). Usługa została skonfigurowana przy użyciu certyfikatu SSL (X. 509), aby umożliwić klientom weryfikowanie tożsamości serwera. Klient jest również skonfigurowany przy użyciu certyfikatu X. 509, który umożliwia usłudze weryfikowanie tożsamości klienta. Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być traktowany jako zaufany przez serwer. Rzeczywista Mechanics sposobu, w jaki usługa i klient sprawdzają tożsamość nawzajem, wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [podpis cyfrowy w witrynie Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Ten scenariusz implementuje wzorzec komunikatu żądania/odpowiedzi, jak pokazano na poniższym diagramie.  
  
 ![Bezpieczny transfer przy użyciu certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")  
  
 Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [instrukcje: Skonfiguruj port za pomocą certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)SSL. W poniższej tabeli opisano różne cechy scenariusza.  
  
|Charakterystyk|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transportu|  
|Współdziałanie|Z istniejącymi klientami i usługami sieci Web.|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (przy użyciu certyfikatu SSL)<br /><br /> Tak (przy użyciu certyfikatu X. 509)|  
|Integralność danych|Tak|  
|Poufność danych|Tak|  
|Transportu|HTTPS|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurowanie usługi  
 Ponieważ usługa w tym scenariuszu jest hostowana w usługach IIS, jest konfigurowana za pomocą pliku Web. config. Poniższy plik Web. config pokazuje, <xref:System.ServiceModel.WSHttpBinding> jak skonfigurować program do korzystania z poświadczeń klienta transportowego i X. 509.  
  
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
  
## <a name="configure-the-client"></a>Konfigurowanie klienta programu  
 Klienta można skonfigurować w kodzie lub w pliku App. config. Poniższy przykład pokazuje, jak skonfigurować klienta w kodzie.  
  
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
  
 Alternatywnie można skonfigurować klienta w pliku App. config, jak pokazano w następującym przykładzie:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
