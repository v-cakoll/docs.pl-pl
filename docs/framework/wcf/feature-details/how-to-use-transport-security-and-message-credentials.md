---
title: 'Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f9c90ac93a27f90479ee7225f62afb98a5000fe9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321485"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów
Zabezpieczanie usługi za pomocą transportu i komunikat poświadczeń używa najlepsze tryby zabezpieczeń transportu i komunikatów w Windows Communication Foundation (WCF). W sum zabezpieczeń warstwy transportu zapewnia integralności i poufności, podczas komunikat warstwy zabezpieczeń zawiera szereg poświadczenia, które nie są możliwe za pomocą mechanizmów zabezpieczeń transportu strict. W tym temacie przedstawiono podstawowe kroki implementacji transportu przy użyciu poświadczeń komunikatów za pomocą <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> powiązania. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [jak: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transportu określa konkretny mechanizm, który zapewnia zabezpieczenia na poziomie transportu. Dla protokołu HTTP mechanizm jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS); TCP jest protokół SSL za pośrednictwem protokołu TCP lub Windows.  
  
 W przypadku transportu HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding>), protokołu SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczenia na poziomie transportu. W takim przypadku należy skonfigurować komputer obsługujący usługę za pomocą certyfikatu SSL powiązany z portem, jak pokazano w dalszej części tego tematu.  
  
 W przypadku transportu TCP (przy użyciu <xref:System.ServiceModel.NetTcpBinding>), domyślnie podane zabezpieczeń na poziomie transportu jest zabezpieczeń Windows lub protokołu SSL za pośrednictwem protokołu TCP. Przy użyciu protokołu SSL za pośrednictwem protokołu TCP, należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodzie, jak pokazano w dalszej części tego tematu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Za pomocą powiązanie WSHttpBinding certyfikat zabezpieczeń transportu (w kodzie)  
  
1. Użyj narzędzia HttpCfg.exe można powiązać certyfikatu SSL z portem na maszynie. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2. Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3. Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość do odpowiedniej wartości. (Aby uzyskać więcej informacji, zobacz [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
4. Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywista nazwa komputera i numer portu, który certyfikat SSL jest powiązany z. (Ewentualnie można ustawić adres podstawowy w konfiguracji.)  
  
5. Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
6. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Do użytku z certyfikatem zabezpieczeń transportu (w kodzie) NetTcpBinding  
  
1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2. Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
3. Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "net.tcp". (Ewentualnie można ustawić adres podstawowy w konfiguracji.)  
  
4. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
5. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X.509 dla usługi.  
  
6. Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
7. Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Za pomocą NetTcpBinding Windows zabezpieczeń transportu (w kodzie)  
  
1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwość <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2. Ustawienia zabezpieczeń transportu do użycia Windows, ustawiając <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Zwróć uwagę, że jest to opcja domyślna).  
  
3. Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
4. Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "net.tcp". (Ewentualnie można ustawić adres podstawowy w konfiguracji.)  
  
5. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
6. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby jawnie ustawić certyfikat X.509 dla usługi.  
  
7. Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
8. Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodzie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Przy użyciu konfiguracji  
  
#### <a name="to-use-the-wshttpbinding"></a>Aby użyć powiązanie WSHttpBinding  
  
1. Skonfiguruj komputer tak, za pomocą certyfikatu SSL powiązany z portem. (Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Nie należy ustawić <`transport`> Wartość elementu w przypadku tej konfiguracji.  
  
2. Określanie typu poświadczeń klienta dla zabezpieczenia wiadomości. Poniższy przykład ustawia `clientCredentialType` atrybut <`message`> elementu `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Do użytku z certyfikatem zabezpieczeń transportu NetTcpBinding  
  
1. Dla protokołu SSL za pośrednictwem protokołu TCP, należy jawnie określić certyfikat w `<behaviors>` elementu. W poniższym przykładzie określono przez jego wystawcę certyfikatu w domyślnej lokalizacji magazynu (komputer lokalny i magazynów osobistych).  
  
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
  
2. Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania  
  
3. Dodaj element powiązania i ustaw `name` atrybutu do odpowiedniej wartości.  
  
4. Dodaj <`security`> element, a następnie ustaw `mode` atrybutu `TransportWithMessageCredential`.  
  
5. Dodaj <`message>` elementu, a następnie ustaw `clientCredentialType` atrybutu do odpowiedniej wartości.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Za pomocą NetTcpBinding Windows zabezpieczeń transportu  
  
1. Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania  
  
2. Dodaj <`binding`> element i ustaw `name` atrybutu do odpowiedniej wartości.  
  
3. Dodaj <`security`> element, a następnie ustaw `mode` atrybutu `TransportWithMessageCredential`.  
  
4. Dodaj <`transport`> element i ustaw `clientCredentialType` atrybutu `Windows`.  
  
5. Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu do odpowiedniej wartości. Poniższy kod ustawia wartość do certyfikatu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
