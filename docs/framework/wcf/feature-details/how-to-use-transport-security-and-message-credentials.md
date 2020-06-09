---
title: 'Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f49c0eb46141081b91100a5ae1869cbcf556e353
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579387"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów
Zabezpieczanie usługi przy użyciu poświadczeń transportowych i komunikatów jest zgodne z najlepszymi trybami zabezpieczeń transportu i komunikatów w programie Windows Communication Foundation (WCF). W obszarze suma zabezpieczenia warstwy transport zapewnia integralność i poufność, natomiast zabezpieczenia warstwy komunikatów zapewniają wiele poświadczeń, które nie są możliwe przy użyciu ścisłych mechanizmów zabezpieczeń transportu. W tym temacie przedstawiono podstawowe kroki wdrażania transportu za pomocą poświadczeń przy użyciu <xref:System.ServiceModel.WSHttpBinding> powiązań i <xref:System.ServiceModel.NetTcpBinding> . Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [How to: Set a Security Mode](../how-to-set-the-security-mode.md).  
  
 Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential` , transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu. W przypadku protokołu HTTP mechanizm jest SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS); w przypadku protokołu TCP jest to protokół SSL za pośrednictwem protokołu TCP lub Windows.  
  
 Jeśli transport jest HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding> ), protokół SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczenia na poziomie transportu. W takim przypadku należy skonfigurować komputer hostujący usługę przy użyciu certyfikatu SSL powiązanego z portem, jak pokazano w dalszej części tego tematu.  
  
 Jeśli transport to TCP (przy użyciu programu <xref:System.ServiceModel.NetTcpBinding> ), domyślnie zapewnione zabezpieczenia na poziomie transportu to zabezpieczenia systemu Windows lub SSL za pośrednictwem protokołu TCP. W przypadku korzystania z protokołu SSL za pośrednictwem protokołu TCP należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak pokazano w dalszej części tego tematu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Aby użyć WSHttpBinding z certyfikatem do zabezpieczenia transportu (w kodzie)  
  
1. Za pomocą narzędzia HttpCfg. exe Powiąż certyfikat SSL z portem na maszynie. Aby uzyskać więcej informacji, zobacz [How to: Configure a port with a SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
3. Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> Właściwość na odpowiednią wartość. (Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](selecting-a-credential-type.md)). Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.  
  
4. Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym. Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywistą nazwę komputera i numer portu, z którym jest powiązany certyfikat SSL. (Alternatywnie można ustawić adres podstawowy w konfiguracji).  
  
5. Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
6. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Aby użyć NetTcpBinding z certyfikatem do zabezpieczenia transportu (w kodzie)  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.  
  
3. Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym. Należy pamiętać, że adres musi używać schematu "net. TCP". (Alternatywnie można ustawić adres podstawowy w konfiguracji).  
  
4. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
5. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X. 509 dla usługi.  
  
6. Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
7. Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Aby użyć NetTcpBinding z systemem Windows do zabezpieczenia transportu (w kodzie)  
  
1. Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .  
  
2. Ustaw zabezpieczenia transportu, aby używały systemu Windows przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows> . (Należy zauważyć, że jest to wartość domyślna).  
  
3. Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartości.  
  
4. Utwórz wystąpienie <xref:System.Uri> klasy z odpowiednim adresem podstawowym. Należy pamiętać, że adres musi używać schematu "net. TCP". (Alternatywnie można ustawić adres podstawowy w konfiguracji).  
  
5. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
6. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X. 509 dla usługi.  
  
7. Dodaj punkt końcowy usługi przy użyciu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
8. Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Korzystanie z konfiguracji  
  
#### <a name="to-use-the-wshttpbinding"></a>Aby użyć WSHttpBinding  
  
1. Skonfiguruj komputer przy użyciu certyfikatu SSL powiązanego z portem. (Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)). Nie trzeba ustawiać <`transport`> wartości elementu przy użyciu tej konfiguracji.  
  
2. Określ typ poświadczeń klienta dla zabezpieczeń na poziomie wiadomości. Poniższy przykład ustawia `clientCredentialType` atrybut <`message` elementu> na `UserName` .  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Aby użyć NetTcpBinding z certyfikatem na potrzeby zabezpieczeń transportu  
  
1. W przypadku protokołu SSL za pośrednictwem protokołu TCP należy jawnie określić certyfikat w `<behaviors>` elemencie. W poniższym przykładzie określono certyfikat wystawcy w domyślnej lokalizacji magazynu (komputer lokalny i magazyny osobiste).  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Dodawanie [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązań  
  
3. Dodaj element powiązania i ustaw `name` odpowiednią wartość atrybutu.  
  
4. Dodaj `security` element> <i ustaw `mode` atrybut na `TransportWithMessageCredential` .  
  
5. Dodaj element <`message>` i ustaw `clientCredentialType` odpowiednią wartość atrybutu.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Aby użyć NetTcpBinding z systemem Windows do zabezpieczenia transportu  
  
1. Dodaj [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązań,  
  
2. Dodaj `binding` element> <i ustaw `name` odpowiednią wartość atrybutu.  
  
3. Dodaj `security` element> <i ustaw `mode` atrybut na `TransportWithMessageCredential` .  
  
4. Dodaj `transport` element> <i ustaw `clientCredentialType` atrybut na `Windows` .  
  
5. Dodaj `message` element> <i ustaw `clientCredentialType` odpowiednią wartość atrybutu. Poniższy kod ustawia wartość dla certyfikatu.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: ustawianie trybu zabezpieczeń](../how-to-set-the-security-mode.md)
- [Zabezpieczanie usług](../securing-services.md)
- [Zabezpieczanie usług i klientów](securing-services-and-clients.md)
