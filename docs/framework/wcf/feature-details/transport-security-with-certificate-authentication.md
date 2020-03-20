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
# <a name="transport-security-with-certificate-authentication"></a>Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów

W tym artykule omówiono przy użyciu certyfikatów X.509 dla uwierzytelniania serwera i klienta podczas korzystania z zabezpieczeń transportu. Aby uzyskać więcej informacji na temat certyfikatów X.509, zobacz [X.509 Certyfikaty kluczy publicznych](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Certyfikaty muszą być wystawiane przez urząd certyfikacji, który często jest zewnętrznym wystawcą certyfikatów. W domenie systemu Windows Server usługi certyfikatów Active Directory mogą być używane do wystawiania certyfikatów komputerom klienckim w domenie. W tym scenariuszu usługa jest hostowana w ramach internetowych usług informacyjnych (IIS), który jest skonfigurowany z warstwą bezpiecznych gniazd (SSL). Usługa jest skonfigurowana z certyfikatem SSL (X.509), aby umożliwić klientom weryfikację tożsamości serwera. Klient jest również skonfigurowany z certyfikatem X.509, który umożliwia usłudze zweryfikowanie tożsamości klienta. Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być zaufany przez serwer. Rzeczywista mechanika sposobu, w jaki usługa i klient weryfikuje tożsamość siebie nawzajem, wykracza poza zakres tego artykułu. Aby uzyskać więcej informacji, zobacz [Podpis cyfrowy](https://en.wikipedia.org/wiki/Digital_signature) w Wikipedii.
  
 W tym scenariuszu implementuje wzorzec komunikatów żądania/odpowiedzi, jak pokazano na poniższym diagramie.  
  
 ![Bezpieczny transfer przy użyciu certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [Jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). W poniższej tabeli opisano różne cechy scenariusza.  
  
|Charakterystyka|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transport|  
|Współdziałanie|Z istniejącymi klientami i usługami usługi sieci Web.|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (przy użyciu certyfikatu SSL)<br /><br /> Tak (przy użyciu certyfikatu X.509)|  
|Integralność danych|Tak|  
|Poufność danych|Tak|  
|Transport|HTTPS|  
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurowanie usługi  
 Ponieważ usługa w tym scenariuszu jest hostowana w usługach IIS, jest skonfigurowana z plikiem web.config. Poniżej web.config pokazuje, jak <xref:System.ServiceModel.WSHttpBinding> skonfigurować do korzystania z zabezpieczeń transportu i X.509 poświadczenia klienta.  
  
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
  
## <a name="configure-the-client"></a>Konfigurowanie klienta  
 Klienta można skonfigurować w kodzie lub w pliku app.config. W poniższym przykładzie pokazano, jak skonfigurować klienta w kodzie.  
  
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
  
 Alternatywnie można skonfigurować klienta w pliku App.config, jak pokazano w poniższym przykładzie:  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
