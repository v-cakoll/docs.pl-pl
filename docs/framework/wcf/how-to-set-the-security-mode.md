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
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971977"
---
# <a name="how-to-set-the-security-mode"></a>Instrukcje: Ustawianie trybu zabezpieczeń

Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości". Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding>i tryb "oba", który znajduje się <xref:System.ServiceModel.NetMsmqBinding>w. Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.

Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby. W tym temacie opisano tryb przy użyciu <xref:System.ServiceModel.WSHttpBinding> klas <xref:System.ServiceModel.NetTcpBinding> i i pokazano, jak ustawić tryb programowo i za pomocą konfiguracji.

Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md), [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)i [Zabezpieczanie usług i klientów](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](../../../docs/framework/wcf/feature-details/transport-security.md) i [zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Aby ustawić tryb zabezpieczeń w kodzie

1. Utwórz wystąpienie klasy powiązania, której używasz. Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](../../../docs/framework/wcf/system-provided-bindings.md). Ten przykład tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy.

2. Ustaw właściwość obiektu zwróconego `Security` przez właściwość. `Mode`

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     Alternatywnie można ustawić tryb na komunikat, jak pokazano w poniższym kodzie.

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     Lub ustaw tryb transportu z poświadczeniami wiadomości, jak pokazano w poniższym kodzie.

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. Można również ustawić tryb w konstruktorze powiązania, jak pokazano w poniższym kodzie.

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a>Ustawianie właściwości ClientCredentialtype

Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania `ClientCredentialType` właściwości. Na <xref:System.ServiceModel.WSHttpBinding> przykład przy użyciu klasy, ustawienie trybu na `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> oznacza, że należy <xref:System.ServiceModel.HttpTransportSecurity> ustawić właściwość klasy na odpowiednią wartość.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu transportu

1. Utwórz wystąpienie powiązania.

2. Ustaw `Mode` właściwość `Transport`.

3. `ClientCredential` Ustaw właściwość na odpowiednią wartość. Poniższy kod ustawia właściwość na `Windows`.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu

1. Utwórz wystąpienie powiązania.

2. Ustaw `Mode` właściwość `Message`.

3. `ClientCredential` Ustaw właściwość na odpowiednią wartość. Poniższy kod ustawia właściwość na `Certificate`.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji

1. Dodaj odpowiedni element powiązania do [ \<elementu powiązań >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) w pliku konfiguracji. Poniższy przykład dodaje [ \<element > WSHttpBinding](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .

2. Dodaj element i ustaw jego `name` atrybut na odpowiednią wartość. `<binding>`

3. `mode` `Message`Dodaj element i ustaw atrybut na, `Transport`, lub `TransportWithMessageCredential`. `<security>`

4. Jeśli tryb jest ustawiony na `Transport`, `<transport>` Dodaj element i ustaw `clientCredential` odpowiednią wartość atrybutu.

     Poniższy przykład`Transport"`ustawia tryb na ", a następnie `clientCredentialType` ustawia atrybut `<transport>` elementu na"`Windows"`.

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatywnie możesz ustawić `security mode` do "`Message"`, po którym następuje `<"message">` element. W tym przykładzie ustawiono `clientCredentialType` wartość "`Certificate"`.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Użycie wartości jest szczególnym przypadkiem i wyjaśniono poniżej.

### <a name="using-transportwithmessagecredential"></a>Korzystanie z TransportWithMessageCredential

Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu. Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS). W związku z tym `ClientCredentialType` ustawienie właściwości dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowane.  Innymi słowy, można ustawić `ClientCredentialType` tylko obiekt zabezpieczeń wiadomości ( `WSHttpBinding` dla powiązania, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiekt).

Aby uzyskać więcej informacji, zobacz [jak: Użyj zabezpieczeń transportu i poświadczeń](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)komunikatów.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie portu z certyfikatem SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Instrukcje: Korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpieczenia transportu](../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpieczenia komunikatów](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Powiązania dostarczane przez system](../../../docs/framework/wcf/system-provided-bindings.md)
- [\<> zabezpieczeń](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<> zabezpieczeń](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<> zabezpieczeń](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
