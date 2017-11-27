---
title: "Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e29ae3a0374f6ee027180835629eacceaa928d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów
Zabezpieczanie usługi za pomocą poświadczeń transportowe i komunikatów używa najlepiej tryby zabezpieczenia transportowe i komunikatów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. W sum transport layer security zapewnia integralności i poufności, gdy komunikat warstwy zabezpieczeń zawiera szereg poświadczenia, które nie są możliwe za pomocą mechanizmów zabezpieczeń transportu strict. W tym temacie przedstawiono podstawowe czynności w przypadku implementowania transportu z poświadczeniami komunikatu za pomocą <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> powiązania. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ustawianie trybu zabezpieczeń, zobacz [porady: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Podczas ustawiania trybu zabezpieczeń `TransportWithMessageCredential`, transport określa konkretny mechanizm, który zapewnia zabezpieczeń na poziomie transportu. W przypadku protokołu HTTP mechanizm jest Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS); TCP jest protokół SSL za pośrednictwem protokołu TCP lub systemu Windows.  
  
 W przypadku transportu HTTP (przy użyciu <xref:System.ServiceModel.WSHttpBinding>), SSL za pośrednictwem protokołu HTTP zapewnia zabezpieczeń na poziomie transportu. W takim przypadku należy skonfigurować komputer obsługujący usługę za pomocą certyfikatu SSL powiązany z portem, jak pokazano w dalszej części tego tematu.  
  
 W przypadku transportu TCP (przy użyciu <xref:System.ServiceModel.NetTcpBinding>), domyślnie zabezpieczeń poziomu transportu jest zabezpieczenia systemu Windows lub SSL za pośrednictwem protokołu TCP. Przy użyciu protokołu SSL za pośrednictwem protokołu TCP, należy określić certyfikat przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak pokazano w dalszej części tego tematu.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Aby użyć klasy WSHttpBinding przy użyciu certyfikatu zabezpieczeń transportu (w kodzie)  
  
1.  Użyj narzędzia HttpCfg.exe można powiązać certyfikatu SSL z portem na maszynie. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Ustaw <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwości odpowiednią wartość. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
4.  Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "HTTPS" i musi zawierać rzeczywistą nazwą komputera i numer portu, który jest powiązany certyfikat SSL. (Alternatywnie można ustawić adres podstawowy w konfiguracji.)  
  
5.  Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
6.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> i Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Aby użyć NetTcpBinding z certyfikatem zabezpieczeń transportu (w kodzie)  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
3.  Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "net.tcp". (Alternatywnie można ustawić adres podstawowy w konfiguracji.)  
  
4.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
5.  Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy jawnie ustaw certyfikatu X.509 usługi.  
  
6.  Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
7.  Wywołanie <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Aby użyć NetTcpBinding z systemem Windows dla zabezpieczeń transportu (w kodzie)  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.NetTcpBinding> klasy i ustaw <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Ustawienia zabezpieczeń transportu do używania systemu Windows przez ustawienie <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> do <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Należy pamiętać, że jest to wartość domyślna).  
  
3.  Ustaw <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpowiednią wartość. Poniższy kod używa <xref:System.ServiceModel.MessageCredentialType.Certificate> wartość.  
  
4.  Utwórz wystąpienie <xref:System.Uri> klasy przy użyciu odpowiedniego adresu podstawowego. Należy pamiętać, że adres musi używać schematu "net.tcp". (Alternatywnie można ustawić adres podstawowy w konfiguracji.)  
  
5.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy.  
  
6.  Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy jawnie ustaw certyfikatu X.509 usługi.  
  
7.  Dodawanie punktu końcowego usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.  
  
8.  Wywołanie <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Za pomocą konfiguracji  
  
#### <a name="to-use-the-wshttpbinding"></a>Aby użyć klasy WSHttpBinding  
  
1.  Skonfiguruj komputer z certyfikatem SSL powiązany z portem. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). Nie należy ustawić <`transport`> Wartość elementu z tą konfiguracją.  
  
2.  Określ typ poświadczeń klienta dla zabezpieczeń na poziomie wiadomości. W poniższym przykładzie `clientCredentialType` atrybut <`message`> elementu `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Aby użyć NetTcpBinding z certyfikatem zabezpieczeń transportu  
  
1.  Dla protokołu SSL za pośrednictwem protokołu TCP, należy jawnie określić certyfikat w `<behaviors>` elementu. W poniższym przykładzie przez jego wystawcę certyfikatu w domyślnej lokalizacji magazynu (komputer lokalny i magazyny osobiste).  
  
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
  
2.  Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania  
  
3.  Dodaj element powiązania i ustaw `name` atrybutu odpowiednią wartość.  
  
4.  Dodaj <`security`> element i ustaw `mode` atrybutu `TransportWithMessageCredential`.  
  
5.  Dodaj <`message>` element i ustaw `clientCredentialType` atrybutu odpowiednią wartość.  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Aby użyć NetTcpBinding z systemem Windows dla zabezpieczeń transportu  
  
1.  Dodaj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do sekcji powiązania  
  
2.  Dodaj <`binding`> element i ustaw `name` atrybutu odpowiednią wartość.  
  
3.  Dodaj <`security`> element i ustaw `mode` atrybutu `TransportWithMessageCredential`.  
  
4.  Dodaj <`transport`> element i ustaw `clientCredentialType` atrybutu `Windows`.  
  
5.  Dodaj <`message`> element i ustaw `clientCredentialType` atrybutu odpowiednią wartość. Poniższy kod ustawia wartość do certyfikatu.  
  
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
 [Porady: Ustawianie trybu zabezpieczeń](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
