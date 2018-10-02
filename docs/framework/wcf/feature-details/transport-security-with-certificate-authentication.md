---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
author: BrucePerlerMS
ms.openlocfilehash: 42de15daef7b18e7422bae836128356f37c1f03d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046412"
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
W tym temacie omówiono, za pomocą certyfikatów X.509 do uwierzytelniania klienta i serwera, korzystając z zabezpieczeń transportu. Aby uzyskać więcej informacji na temat X.509 certyfikatów Zobacz [klucz publiczny certyfikatu X.509](https://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Certyfikaty muszą być wystawiane przez urząd certyfikacji, które są często wystawcy certyfikatów innych firm. W domenie systemu Windows Server Active Directory Certificate Services może służyć do wystawiania certyfikatów na komputerach klienckich w domenie. Aby uzyskać więcej informacji, zobacz [usług certyfikatów systemu Windows 2008 R2](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). W tym scenariuszu usługa jest hostowana w Internet Information Services (IIS), który jest skonfigurowany z Secure Sockets Layer (SSL). Usługa jest skonfigurowana za pomocą certyfikatu SSL (X.509) umożliwia klientom zweryfikować tożsamość serwera. Klient jest również skonfigurowany przy użyciu certyfikatu X.509, który umożliwia usłudze do zweryfikowania tożsamości klienta. Certyfikat serwera musi być zaufany przez klienta, a certyfikat klienta musi być zaufany przez serwer. Rzeczywiste mechanika jak usługa i klient sprawdza jego tożsamość wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [podpisu cyfrowego w witrynie Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).  
  
 W tym scenariuszu implementuje wzorzec komunikatów Żądanie/nietypizowana odpowiedź, jak pokazano na poniższym diagramie.  
  
 ![Bezpieczny transfer przy użyciu certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Aby uzyskać więcej informacji na temat używania certyfikatu z usługą, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). W poniższej tabeli opisano różne cechy scenariusza.  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transportu|  
|Współdziałanie|Za pomocą istniejących klientów usługi sieci Web i usług.|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (za pomocą certyfikatu SSL)<br /><br /> Tak (za pomocą certyfikatu X.509)|  
|Integralność danych|Tak|  
|Poufność danych|Tak|  
|Transportu|HTTPS|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Konfigurowanie usługi  
 Ponieważ usługa, w tym scenariuszu jest obsługiwany w środowisku usług IIS, jest konfigurowana do pliku web.config. Następujący plik web.config przedstawia sposób konfigurowania <xref:System.ServiceModel.WSHttpBinding> do korzystania z zabezpieczeń transportu i poświadczeń klienta X.509.  
  
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
 Klienta można skonfigurować w kodzie lub w pliku app.config. Poniższy przykład pokazuje, jak skonfigurować klienta w kodzie.  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
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
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
