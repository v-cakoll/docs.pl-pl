---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319862"
---
# <a name="how-to-specify-client-credential-values"></a>Instrukcje: Określanie wartości poświadczeń klienta

Za pomocą Windows Communication Foundation (WCF) usługa może określić, jak klient jest uwierzytelniany w usłudze. Na przykład usługa może ustalić, że klient zostanie uwierzytelniony przy użyciu certyfikatu.

## <a name="to-determine-the-client-credential-type"></a>Aby określić typ poświadczeń klienta

1. Pobierz metadane z punktu końcowego metadanych usługi. Metadane zwykle składają się z dwóch plików: kodu klienta w wybranym języku programowania (domyślnie wizualizacji C#) i pliku konfiguracji XML. Jednym ze sposobów pobierania metadanych jest użycie narzędzia Svcutil. exe w celu zwrócenia kodu klienta i konfiguracji klienta. Aby uzyskać więcej informacji, zobacz [Pobieranie metadanych](./feature-details/retrieving-metadata.md) i [Narzędzia ServiceModel metadanych programu (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Otwórz plik konfiguracji XML. Jeśli używasz narzędzia Svcutil. exe, domyślną nazwą pliku jest Output. config.

3. Znajdź element **\<security >** z atrybutem **mode** ( **\<Security Mode =** `MessageOrTransport` **>** , gdzie `MessageOrTransport` jest ustawiony na jeden z trybów zabezpieczeń.

4. Znajdź element podrzędny, który jest zgodny z wartością trybu. Na przykład, jeśli tryb jest ustawiony na wartość **Message**, Znajdź **\<komunikat >** element zawarty w elemencie **\<Security >** .

5. Zwróć uwagę na wartość przypisaną do atrybutu **ClientCredentialType** . Rzeczywista wartość zależy od tego, który tryb jest używany, transport lub wiadomość.

Poniższy kod XML przedstawia konfigurację klienta przy użyciu zabezpieczeń komunikatów i wymaga certyfikatu do uwierzytelnienia klienta.

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Przykład: Tryb transportu TCP z certyfikatem jako poświadczenia klienta

Ten przykład ustawia tryb zabezpieczeń na transport i ustawia wartość poświadczeń klienta na certyfikat X. 509. W poniższych procedurach pokazano, jak ustawić wartość poświadczenia klienta na kliencie w kodzie i konfiguracji. Przyjęto założenie, że użyto [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu zwrócenia metadanych (kodu i konfiguracji) z usługi. Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Aby określić wartość poświadczeń klienta w kodzie

1. Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , aby wygenerować kod i konfigurację z usługi.

2. Utwórz wystąpienie klienta WCF przy użyciu wygenerowanego kodu.

3. W klasie Client ustaw właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> klasy <xref:System.ServiceModel.ClientBase%601> na odpowiednią wartość. Ten przykład ustawia właściwość na certyfikat X. 509 przy użyciu metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Można użyć dowolnego wyliczenia klasy <xref:System.Security.Cryptography.X509Certificates.X509FindType>. Nazwa podmiotu jest używana w tym miejscu w przypadku zmiany certyfikatu (z powodu daty wygaśnięcia). Użycie nazwy podmiotu umożliwia ponowne znalezienie certyfikatu przez infrastrukturę.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Aby określić wartość poświadczenia klienta w konfiguracji

1. Dodaj [\<zachowanie >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu do [> zachowań\<](../configure-apps/file-schema/wcf/behaviors.md) .

2. Dodaj element [\<clientcredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) do elementu [\<Behaviors >](../configure-apps/file-schema/wcf/behaviors.md) . Upewnij się, że atrybut Required `name` jest ustawiony na odpowiednią wartość.

3. Dodaj element [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) do elementu [\<ClientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) .

4. Ustaw następujące atrybuty na odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType`i `findValue`, jak pokazano w poniższym kodzie. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](./feature-details/working-with-certificates.md).

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. Podczas konfigurowania klienta należy określić zachowanie, ustawiając atrybut `behaviorConfiguration` elementu `<endpoint>`, jak pokazano w poniższym kodzie. Element Endpoint jest elementem podrzędnym elementu [>\<Client](../configure-apps/file-schema/wcf/client.md) . Ponadto Określ nazwę konfiguracji powiązania, ustawiając atrybut `bindingConfiguration` na powiązanie dla klienta. Jeśli używasz wygenerowanego pliku konfiguracji, nazwa powiązania jest generowana automatycznie. W tym przykładzie nazwa jest `"tcpBindingWithCredential"`.

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [Programowanie zabezpieczeń WCF](./feature-details/programming-wcf-security.md)
- [Wybieranie typu poświadczeń](./feature-details/selecting-a-credential-type.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Praca z certyfikatami](./feature-details/working-with-certificates.md)
- [Instrukcje: tworzenie klienta](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [> zabezpieczeń \<](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [zachowanie \<>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [zachowania \<>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
