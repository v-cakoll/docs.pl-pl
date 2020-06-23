---
title: 'Instrukcje: Ustawianie trybu zabezpieczeń'
description: 'Dowiedz się, jak ustawić trzy popularne tryby zabezpieczeń WCF dla większości wstępnie zdefiniowanych powiązań: transport, Message i TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244546"
---
# <a name="how-to-set-the-security-mode"></a>Instrukcje: Ustawianie trybu zabezpieczeń

Zabezpieczenia Windows Communication Foundation (WCF) mają trzy popularne tryby zabezpieczeń, które znajdują się w większości wstępnie zdefiniowanych powiązań: transport, Message i "transport z poświadczeniami wiadomości". Dwa dodatkowe tryby są specyficzne dla dwóch powiązań: tryb "transport-Credential Only" znaleziony w <xref:System.ServiceModel.BasicHttpBinding> i tryb "oba", który znajduje się w <xref:System.ServiceModel.NetMsmqBinding> . Jednak ten temat koncentruje się na trzech wspólnych trybach zabezpieczeń: <xref:System.ServiceModel.SecurityMode.Transport> , <xref:System.ServiceModel.SecurityMode.Message> i <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .

Należy zauważyć, że nie każde wstępnie zdefiniowane powiązanie obsługuje wszystkie te tryby. W tym temacie opisano tryb przy użyciu <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> klas i i pokazano, jak ustawić tryb programowo i za pomocą konfiguracji.

Aby uzyskać więcej informacji, zobacz zabezpieczenia WCF, zobacz [Omówienie zabezpieczeń](./feature-details/security-overview.md), [Zabezpieczanie usług](securing-services.md)i [Zabezpieczanie usług i klientów](./feature-details/securing-services-and-clients.md). Aby uzyskać więcej informacji na temat trybu transportu i komunikatu, zobacz [zabezpieczenia transportu](./feature-details/transport-security.md) i [zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md).

## <a name="to-set-the-security-mode-in-code"></a>Aby ustawić tryb zabezpieczeń w kodzie

1. Utwórz wystąpienie klasy powiązania, której używasz. Aby uzyskać listę wstępnie zdefiniowanych powiązań, zobacz [powiązania dostarczone przez system](system-provided-bindings.md). Ten przykład tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy.

2. Ustaw `Mode` właściwość obiektu zwróconego przez `Security` Właściwość.

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

Ustawienie trybu na jedną z trzech wartości określa sposób ustawiania `ClientCredentialType` właściwości. Na przykład przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy, ustawienie trybu na `Transport` oznacza, że należy ustawić <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> Właściwość <xref:System.ServiceModel.HttpTransportSecurity> klasy na odpowiednią wartość.

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu transportu

1. Utwórz wystąpienie powiązania.

2. Ustaw `Mode` Właściwość na wartość `Transport` .

3. Ustaw `ClientCredential` Właściwość na odpowiednią wartość. Poniższy kod ustawia właściwość na `Windows` .

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Aby ustawić właściwość ClientCredentialtype dla trybu komunikatu

1. Utwórz wystąpienie powiązania.

2. Ustaw `Mode` Właściwość na wartość `Message` .

3. Ustaw `ClientCredential` Właściwość na odpowiednią wartość. Poniższy kod ustawia właściwość na `Certificate` .

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Aby ustawić tryb i Właściwość ClientCredentialtype w konfiguracji

1. Dodaj odpowiedni element powiązania do elementu w [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) pliku konfiguracji. Poniższy przykład dodaje [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.

2. Dodaj `<binding>` element i ustaw jego `name` atrybut na odpowiednią wartość.

3. Dodaj `<security>` element i ustaw `mode` atrybut na `Message` , `Transport` , lub `TransportWithMessageCredential` .

4. Jeśli tryb jest ustawiony na `Transport` , Dodaj `<transport>` element i ustaw `clientCredential` odpowiednią wartość atrybutu.

     Poniższy przykład ustawia tryb na " `Transport"` , a następnie ustawia `clientCredentialType` atrybut `<transport>` elementu na" `Windows"` .

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Alternatywnie możesz ustawić `security mode` do " `Message"` , po którym następuje `<"message">` element. W tym przykładzie ustawiono wartość `clientCredentialType` " `Certificate"` .

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     Użycie <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> wartości jest szczególnym przypadkiem i wyjaśniono poniżej.

### <a name="using-transportwithmessagecredential"></a>Korzystanie z TransportWithMessageCredential

Podczas ustawiania trybu zabezpieczeń na `TransportWithMessageCredential` , transport określa rzeczywisty mechanizm, który zapewnia zabezpieczenia na poziomie transportu. Na przykład protokół HTTP używa protokołu SSL (SSL) za pośrednictwem protokołu HTTP (HTTPS). W związku z tym ustawienie `ClientCredentialType` właściwości dowolnego obiektu zabezpieczeń transportu (takiego jak <xref:System.ServiceModel.HttpTransportSecurity> ) jest ignorowane.  Innymi słowy, można ustawić tylko `ClientCredentialType` obiekt zabezpieczeń wiadomości (dla `WSHttpBinding` powiązania, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> obiekt).

Aby uzyskać więcej informacji, zobacz [jak: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: konfigurowanie portu z certyfikatem SSL](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Zabezpieczenia transportu](./feature-details/transport-security.md)
- [Zabezpieczenia komunikatów](./feature-details/message-security-in-wcf.md)
- [Przegląd zabezpieczeń](./feature-details/security-overview.md)
- [Powiązania dostarczane przez system](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
