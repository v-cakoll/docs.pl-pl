---
title: 'Instrukcje: Ustawianie trybu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 9f4f83502016fb749c75776dd6c2dc2bd01476e6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183350"
---
# <a name="how-to-set-the-security-mode"></a>Instrukcje: Ustawianie trybu zabezpieczeń
Zabezpieczenia usług Windows Communication Foundation (WCF) ma trzy często używanych trybów zabezpieczeń, które znajdują się na najbardziej wstępnie zdefiniowanych powiązań: transportu, wiadomości i "transport z poświadczeniami komunikatu". Dwa tryby dodatkowe są specyficzne dla dwa powiązania: tryb "tylko transportu credential" znalezione na <xref:System.ServiceModel.BasicHttpBinding>i "Oba" Tryb znalezione na <xref:System.ServiceModel.NetMsmqBinding>. Jednak ten temat koncentruje się na trzech często używanych trybów zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Należy pamiętać, że nie każde powiązanie wstępnie zdefiniowanych obsługuje wszystkie z następujących trybów. W tym temacie Ustawia tryb za pomocą <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> klasy i pokazuje, jak ustawić tryb programowo i za pośrednictwem konfiguracji.  
  
 Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md), i [zabezpieczania usług i klientów](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aby uzyskać więcej informacji na temat trybu transportu i wiadomości zobacz [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) i [zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Aby ustawić tryb zabezpieczeń w kodzie  
  
1.  Utwórz wystąpienie klasy powiązania, którego używasz. Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). W tym przykładzie tworzone jest wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy.  
  
2.  Ustaw `Mode` własności obiektu zwróconego przez `Security` właściwości.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Alternatywnie Ustaw tryb wiadomości, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Lub ustaw tryb transportu z poświadczeniami komunikatu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Można również ustawić tryb w Konstruktorze powiązanie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Ustawienie właściwości ClientCredentialType  
 Po ustawieniu trybu na jedną z trzech wartości określa, jak ustawić `ClientCredentialType` właściwości. Na przykład za pomocą <xref:System.ServiceModel.WSHttpBinding> klasy, po ustawieniu trybu na `Transport` oznacza, że należy ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy do odpowiedniej wartości.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aby ustawić właściwość ClientCredentialType dla trybu transportu  
  
1.  Utwórz wystąpienie wiązania.  
  
2.  Ustaw `Mode` właściwość `Transport`.  
  
3.  Ustaw `ClientCredential` właściwość do odpowiedniej wartości. Poniższy kod ustawia właściwość `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Aby ustawić właściwość ClientCredentialType dla trybu wiadomości  
  
1.  Utwórz wystąpienie wiązania.  
  
2.  Ustaw `Mode` właściwość `Message`.  
  
3.  Ustaw `ClientCredential` właściwość do odpowiedniej wartości. Poniższy kod ustawia właściwość `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Aby ustawić tryb i właściwości ClientCredentialType o wartości właściwości w konfiguracji  
  
1.  Dodaj odpowiednie powiązanie elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element pliku konfiguracji. W poniższym przykładzie dodano [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.  
  
2.  Dodaj `<binding>` element i ustaw jego `name` atrybutu do odpowiedniej wartości.  
  
3.  Dodaj `<security>` element i ustaw `mode` atrybutu `Message`, `Transport`, lub `TransportWithMessageCredential`.  
  
4.  Jeśli tryb jest ustawiony na `Transport`, Dodaj `<transport>` element i ustaw `clientCredential` atrybutu do odpowiedniej wartości.  
  
     Poniższy przykład ustawia tryb "`Transport"`, a następnie ustawia `clientCredentialType` atrybutu `<transport>` elementu"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Alternatywnie, ustawić `security mode` do "`Message"`, a następnie `<"message">` elementu. W tym przykładzie `clientCredentialType` do "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Za pomocą <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> wartość jest przypadkiem szczególnym i zostało wyjaśnione poniżej.  
  
### <a name="using-transportwithmessagecredential"></a>Za pomocą TransportWithMessageCredential  
 Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transportu określa konkretny mechanizm, który zapewnia zabezpieczenia na poziomie transportu. Na przykład protokołu HTTP używa protokołu Secure Sockets Layer (SSL), za pośrednictwem protokołu HTTPS (HTTP). W związku z tym, ustawienie `ClientCredentialType` właściwości dowolnego obiektu zabezpieczeń transportu (takie jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowana.  Innymi słowy, można ustawić tylko `ClientCredentialType` obiektu zabezpieczeń wiadomości (dla `WSHttpBinding` powiązania <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiektu).  
  
 Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Zabezpieczenia transportu](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<Zabezpieczenia >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [\<Zabezpieczenia >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [\<Zabezpieczenia >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
