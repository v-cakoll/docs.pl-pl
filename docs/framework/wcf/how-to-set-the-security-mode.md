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
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320893"
---
# <a name="how-to-set-the-security-mode"></a>Instrukcje: Ustawianie trybu zabezpieczeń

Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości". Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding> i tryb "oba", który znajduje się w <xref:System.ServiceModel.NetMsmqBinding>. Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.

Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby. Ten temat ustawia tryb z klasami <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.NetTcpBinding> i pokazuje, jak ustawić tryb programowo i za pomocą konfiguracji.

Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](./feature-details/security-overview.md), [Zabezpieczanie usług](securing-services.md)i [Zabezpieczanie usług i klientów](./feature-details/securing-services-and-clients.md). Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](./feature-details/transport-security.md) i [zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Aby ustawić tryb zabezpieczeń w kodzie

1. Utwórz wystąpienie klasy powiązania, której używasz. Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](system-provided-bindings.md). Ten przykład tworzy wystąpienie klasy <xref:System.ServiceModel.WSHttpBinding>.

2. Ustaw właściwość `Mode` obiektu zwróconego przez właściwość `Security`.

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

Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania właściwości `ClientCredentialType`. Na przykład przy użyciu klasy <xref:System.ServiceModel.WSHttpBinding> ustawienie Tryb na `Transport` oznacza, że właściwość <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> klasy <xref:System.ServiceModel.HttpTransportSecurity> ma mieć odpowiednią wartość.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu transportu

1. Utwórz wystąpienie powiązania.

2. Ustaw właściwość `Mode` na `Transport`.

3. Ustaw właściwość `ClientCredential` na odpowiednią wartość. Poniższy kod ustawia właściwość na `Windows`.

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu

1. Utwórz wystąpienie powiązania.

2. Ustaw właściwość `Mode` na `Message`.

3. Ustaw właściwość `ClientCredential` na odpowiednią wartość. Poniższy kod ustawia właściwość na `Certificate`.

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji

1. Dodaj odpowiedni element powiązania do elementu [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji. Poniższy przykład dodaje element [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .

2. Dodaj element `<binding>` i ustaw jego atrybut `name` na odpowiednią wartość.

3. Dodaj element `<security>` i ustaw atrybut `mode` na `Message`, `Transport` lub `TransportWithMessageCredential`.

4. Jeśli tryb jest ustawiony na `Transport`, Dodaj element `<transport>` i ustaw odpowiednią wartość atrybutu `clientCredential`.

     Poniższy przykład ustawia tryb na "`Transport"`, a następnie ustawia atrybut `clientCredentialType` elementu `<transport>` na" `Windows"`.

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatywnie można ustawić wartość `security mode` na "`Message"`", po którym następuje element `<"message">`. Ten przykład ustawia wartość `clientCredentialType` na "`Certificate"`.

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Użycie wartości <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> jest szczególnym przypadkiem i wyjaśniono poniżej.

### <a name="using-transportwithmessagecredential"></a>Korzystanie z TransportWithMessageCredential

Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential`, transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu. Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS). W związku z tym ustawienie właściwości `ClientCredentialType` dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity>) jest ignorowane.  Innymi słowy, można ustawić tylko `ClientCredentialType` obiektu zabezpieczeń wiadomości (dla powiązania `WSHttpBinding`, obiektu <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).

Aby uzyskać więcej informacji, zobacz [jak: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: konfigurowanie portu z certyfikatem SSL](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpieczenia transportu](./feature-details/transport-security.md)
- [Zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md)
- [Przegląd zabezpieczeń](./feature-details/security-overview.md)
- [Powiązania dostarczane przez system](system-provided-bindings.md)
- [@no__t — 1security >](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [@no__t — 1security >](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [@no__t — 1security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
