---
title: Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
caps.latest.revision: 20
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 19b54739d82fe7363319211d3f753416e0966aed
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-certificate-authentication"></a>Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów
W tym temacie omówiono przy użyciu certyfikatów X.509 do uwierzytelniania klienta i serwera, korzystając z zabezpieczeń transportu. Aby uzyskać więcej informacji na temat X.509 Zobacz certyfikaty [certyfikatów kluczy publicznych X.509](http://msdn.microsoft.com/library/bb540819\(VS.85\).aspx). Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcy certyfikatów innych firm. W domenie systemu Windows Server usługi certyfikatów Active Directory może służyć do wystawiania certyfikatów dla komputerów klienckich w domenie. Aby uzyskać więcej informacji, zobacz [usług certyfikatów systemu Windows 2008 R2](http://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). W tym scenariuszu usługi jest obsługiwane w obszarze Internet usługi informacyjne (IIS), której skonfigurowano protokołem SSL Secure Sockets Layer (). Usługa jest skonfigurowana z certyfikatem SSL (X.509), aby umożliwić klientom zweryfikowanie tożsamości serwera. Klient jest konfigurowane również certyfikatu X.509, który umożliwia usłudze do weryfikacji tożsamości klienta. Certyfikat serwera musi być uważany za zaufany przez klienta i certyfikat klienta musi być uważany za zaufany przez serwer. Rzeczywiste mechanika jak usługa i klient sprawdza tożsamość siebie nawzajem wykracza poza zakres tego tematu. Aby uzyskać więcej informacji, zobacz [podpisu cyfrowego w witrynie Wikipedia](http://go.microsoft.com/fwlink/?LinkId=253157).  
  
 W tym scenariuszu implementuje wzorzec komunikat żądania/odpowiedzi, jak pokazano na poniższym diagramie.  
  
 ![Bezpiecznego transferu za pomocą certyfikatów](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Aby uzyskać więcej informacji dotyczących używania certyfikatu z usługą, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md). W poniższej tabeli opisano różne charakterystyki scenariusza.  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transportu|  
|Współdziałanie|Z istniejących klientów usługi sieci Web i usług.|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (za pomocą certyfikatu SSL)<br /><br /> Tak (za pomocą certyfikatu X.509)|  
|Integralność danych|Tak|  
|Poufność danych|Tak|  
|Transportu|HTTPS|  
|Powiązanie|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Skonfiguruj usługę  
 Ponieważ usługę w tym scenariuszu jest obsługiwany w środowisku usług IIS, jest on skonfigurowany z pliku web.config. Następujący plik web.config przedstawiono sposób konfigurowania <xref:System.ServiceModel.WSHttpBinding> Aby użyć zabezpieczeń transportu i poświadczeń klienta X.509.  
  
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
 Klienta można skonfigurować w kodzie, lub w pliku app.config. Poniższy przykład pokazuje, jak skonfigurować klienta w kodzie.  
  
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
  
 Klient może również skonfigurować w pliku App.config, jak pokazano w poniższym przykładzie:  
  
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
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
