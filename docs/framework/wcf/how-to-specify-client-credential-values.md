---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
description: Dowiedz się, w jaki sposób usługa WCF może określić sposób uwierzytelniania klienta w ramach tej usługi. W tym przykładzie określono certyfikat X. 509 i Tryb transportu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244455"
---
# <a name="how-to-specify-client-credential-values"></a>Instrukcje: Określanie wartości poświadczeń klienta

Za pomocą Windows Communication Foundation (WCF) usługa może określić, jak klient jest uwierzytelniany w usłudze. Na przykład usługa może ustalić, że klient zostanie uwierzytelniony przy użyciu certyfikatu.

## <a name="to-determine-the-client-credential-type"></a>Aby określić typ poświadczeń klienta

1. Pobierz metadane z punktu końcowego metadanych usługi. Metadane zwykle składają się z dwóch plików: kodu klienta w wybranym języku programowania (Domyślnie Visual C#) i pliku konfiguracji XML. Jednym ze sposobów pobierania metadanych jest użycie narzędzia Svcutil.exe do zwrócenia kodu klienta i konfiguracji klienta. Aby uzyskać więcej informacji, zobacz [Pobieranie metadanych](./feature-details/retrieving-metadata.md) i [Narzędzia ServiceModel metadanych (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).

2. Otwórz plik konfiguracji XML. Jeśli używasz narzędzia Svcutil.exe, domyślna nazwa pliku jest Output.config.

3. Znajdź **\<security>** element z atrybutem **mode** ( **\<security mode =**`MessageOrTransport`**>** gdzie `MessageOrTransport` jest ustawiony jeden z trybów zabezpieczeń.

4. Znajdź element podrzędny, który jest zgodny z wartością trybu. Na przykład, jeśli tryb jest ustawiony na **komunikat**, Znajdź **\<message>** element zawarty w **\<security>** elemencie.

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

Ten przykład ustawia tryb zabezpieczeń na transport i ustawia wartość poświadczeń klienta na certyfikat X. 509. W poniższych procedurach pokazano, jak ustawić wartość poświadczenia klienta na kliencie w kodzie i konfiguracji. Przyjęto założenie, że użyto [Narzędzia do obsługi metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do zwrócenia metadanych (kodu i konfiguracji) z usługi. Aby uzyskać więcej informacji, zobacz [How to: Create a Client](how-to-create-a-wcf-client.md).

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Aby określić wartość poświadczeń klienta w kodzie

1. Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , aby wygenerować kod i konfigurację z usługi.

2. Utwórz wystąpienie klienta WCF przy użyciu wygenerowanego kodu.

3. W klasie Client Ustaw <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość <xref:System.ServiceModel.ClientBase%601> klasy na odpowiednią wartość. Ten przykład ustawia właściwość na certyfikat X. 509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     Można użyć dowolnego wyliczenia <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy. Nazwa podmiotu jest używana w tym miejscu w przypadku zmiany certyfikatu (z powodu daty wygaśnięcia). Użycie nazwy podmiotu umożliwia ponowne znalezienie certyfikatu przez infrastrukturę.

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Aby określić wartość poświadczenia klienta w konfiguracji

1. Dodaj [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.

2. Dodaj [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu. Upewnij się, że atrybut wymagany jest ustawiony `name` na odpowiednią wartość.

3. Dodaj [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element do [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elementu.

4. Ustaw następujące atrybuty na odpowiednie wartości: `storeLocation` , `storeName` , `x509FindType` , i `findValue` , jak pokazano w poniższym kodzie. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](./feature-details/working-with-certificates.md).

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

5. Podczas konfigurowania klienta należy określić zachowanie, ustawiając `behaviorConfiguration` atrybut `<endpoint>` elementu, jak pokazano w poniższym kodzie. Element Endpoint jest elementem podrzędnym [\<client>](../configure-apps/file-schema/wcf/client.md) elementu. Ponadto Określ nazwę konfiguracji powiązania przez ustawienie `bindingConfiguration` atrybutu na powiązanie dla klienta. Jeśli używasz wygenerowanego pliku konfiguracji, nazwa powiązania jest generowana automatycznie. W tym przykładzie nazwa jest `"tcpBindingWithCredential"` .

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>Zobacz też

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
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
