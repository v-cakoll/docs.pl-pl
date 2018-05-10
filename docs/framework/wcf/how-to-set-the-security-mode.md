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
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e8c08fba0e4a74eafab00e75977a9f756c1b1cfa
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-set-the-security-mode"></a>Instrukcje: Ustawianie trybu zabezpieczeń
Zabezpieczenia systemu Windows Communication Foundation (WCF) ma trzy często używanych trybów zabezpieczeń, które zostały znalezione na najbardziej wstępnie zdefiniowanych powiązań: transportu, komunikat oraz "transportu z poświadczeniami komunikatu". Dwa tryby dodatkowe są specyficzne dla dwa powiązania: tryb "tylko transportu credential" znaleziono na <xref:System.ServiceModel.BasicHttpBinding>oraz "Zarówno" tryb na <xref:System.ServiceModel.NetMsmqBinding>. Jednak ten temat koncentruje się na trzech często używanych trybów zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Zauważ, że nie wszystkie wstępnie zdefiniowanych powiązań obsługuje wszystkie te tryby. W tym temacie Ustawia tryb z <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> klas i pokazuje, jak ustawić tryb programowo i za pomocą konfiguracji.  
  
 Aby uzyskać więcej informacji, zobacz zabezpieczeń WCF, zobacz [Omówienie zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md), i [zabezpieczanie usług i klientów](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aby uzyskać więcej informacji dotyczących trybu transportu i komunikatów, zobacz [zabezpieczeń transportu](../../../docs/framework/wcf/feature-details/transport-security.md) i [zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Aby ustawić tryb zabezpieczeń w kodzie  
  
1.  Tworzenie wystąpienia klasy powiązanie, którego używasz. Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md). W tym przykładzie powoduje utworzenie wystąpienia <xref:System.ServiceModel.WSHttpBinding> klasy.  
  
2.  Ustaw `Mode` właściwości obiektu zwróconego przez `Security` właściwości.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Możesz również ustawić tryb na wiadomość, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Lub ustaw tryb transportu z poświadczeniami komunikatu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Tryb można również ustawić w Konstruktorze powiązanie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Ustawienie właściwości ClientCredentialType  
 Ustawianie trybu do jednej z następujących wartości: Określa, jak ustawić `ClientCredentialType` właściwości. Na przykład za pomocą <xref:System.ServiceModel.WSHttpBinding> klasy ustawienie trybu `Transport` oznacza, że należy ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy odpowiednią wartość.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Można ustawić właściwości ClientCredentialType dla trybu transportu  
  
1.  Utwórz wystąpienie powiązania.  
  
2.  Ustaw `Mode` właściwości `Transport`.  
  
3.  Ustaw `ClientCredential` właściwości odpowiednią wartość. Poniższy kod ustawia właściwość `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Można ustawić właściwości ClientCredentialType dla trybu wiadomości  
  
1.  Utwórz wystąpienie powiązania.  
  
2.  Ustaw `Mode` właściwości `Message`.  
  
3.  Ustaw `ClientCredential` właściwości odpowiednią wartość. Poniższy kod ustawia właściwość `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Aby ustawić właściwość trybu i ClientCredentialType w konfiguracji  
  
1.  Dodaj odpowiednie powiązanie elementu [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracji. W poniższym przykładzie dodano [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.  
  
2.  Dodaj `<binding>` element i ustaw jej `name` atrybutu odpowiednią wartość.  
  
3.  Dodaj `<security>` element i ustaw `mode` atrybutu `Message`, `Transport`, lub `TransportWithMessageCredential`.  
  
4.  Jeśli ustawiono tryb `Transport`, Dodaj `<transport>` element i ustaw `clientCredential` atrybutu odpowiednią wartość.  
  
     Poniższy przykład przedstawia sposób "`Transport"`, a następnie ustawia `clientCredentialType` atrybutu `<transport>` elementu"`Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Możesz również ustawić `security mode` do "`Message"`, a następnie `<"message">` elementu. W tym przykładzie `clientCredentialType` do "`Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Przy użyciu <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> wartość jest szczególnych przypadkach i opisanej poniżej.  
  
### <a name="using-transportwithmessagecredential"></a>Przy użyciu TransportWithMessageCredential  
 Podczas ustawiania trybu zabezpieczeń `TransportWithMessageCredential`, transport określa konkretny mechanizm, który zapewnia zabezpieczeń na poziomie transportu. Na przykład protokołu HTTP używa protokołu Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP (HTTPS). W związku z tym ustawienie `ClientCredentialType` właściwość wszystkich obiektów zabezpieczeń transportu (takich jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowana.  Innymi słowy, można ustawić tylko `ClientCredentialType` obiektu zabezpieczeń wiadomości (dla `WSHttpBinding` powiązanie, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiektu).  
  
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
