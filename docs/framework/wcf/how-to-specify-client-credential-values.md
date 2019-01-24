---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 110b8ffe2fb3e00d7a6787e32d066f62126ebf9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617190"
---
# <a name="how-to-specify-client-credential-values"></a>Instrukcje: Określanie wartości poświadczeń klienta
Za pomocą usługi Windows Communication Foundation (WCF), usługi można określić, jak klient jest uwierzytelniany w usłudze. Na przykład usługi można zastrzec uwierzytelnienia klienta przy użyciu certyfikatu.  
  
### <a name="to-determine-the-client-credential-type"></a>Aby określić typ poświadczeń klienta  
  
1.  Pobieranie metadanych z punktu końcowego metadanych usługi. Metadane zazwyczaj składa się z dwóch plików: Kod klienta w wybranym języku programowania (wartość domyślna to Visual C#), a plik konfiguracyjny XML. Jest jednym ze sposobów, aby pobrać metadane na potrzeby narzędzia Svcutil.exe zwrócić kod klienta i konfiguracji klienta. Aby uzyskać więcej informacji, zobacz [podczas pobierania metadanych](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) i [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  Otwórz plik konfiguracyjny XML. Jeśli używasz narzędzia Svcutil.exe, domyślna nazwa pliku jest Output.config.  
  
3.  Znajdź  **\<zabezpieczeń >** element z **tryb** atrybutu (**< tryb zabezpieczeń =** `MessageOrTransport` **>** gdzie `MessageOrTransport` jest ustawiona na jeden z trybów zabezpieczeń.  
  
4.  Znajdź element podrzędny, który odpowiada wartość trybu. Na przykład, jeśli jest tryb **komunikat**, Znajdź  **\<komunikatu >** elementów znajdujących się w  **\<zabezpieczeń >** elementu.  
  
5.  Zwróć uwagę na wartość przypisana do **clientCredentialType** atrybutu. Wartość rzeczywista zależy od tego, który tryb jest używany, transportu lub komunikatu.  
  
 Następujący kod XML przedstawia konfigurację dla korzystanie z zabezpieczeń komunikatów co wymaga certyfikatu klienta do uwierzytelniania klienta.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Przykład: Tryb transportu TCP za pomocą certyfikatu jako poświadczeń klienta  
 W tym przykładzie Ustawia tryb zabezpieczeń transportu i ustawia wartość poświadczenia klienta certyfikatu X.509. Poniższe procedury pokazują, jak można ustawić wartości poświadczeń klienta na komputerze klienckim w kodzie i konfiguracji. Założono, że korzystasz z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zwrócić metadanych (kod i konfiguracji) z usługi. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Aby określić wartości poświadczeń klienta na komputerze klienckim w kodzie  
  
1.  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kodu i konfiguracji z usługi.  
  
2.  Utwórz wystąpienie klienta WCF, za pomocą wygenerowanego kodu.  
  
3.  W klasie klienta ustaw <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy do odpowiedniej wartości. W tym przykładzie ustawia właściwość do certyfikatów X.509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Można użyć dowolnego z wyliczenia o <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy. Nazwa podmiotu jest używany w tym miejscu, w przypadku, gdy certyfikat jest zmieniony (ze względu na datę wygaśnięcia). Przy użyciu nazwy podmiotu umożliwia infrastruktury można znaleźć certyfikatu ponownie.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Aby określić wartości poświadczeń klienta na komputerze klienckim w konfiguracji  
  
1.  Dodaj [ \<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
2.  Dodaj [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu. Pamiętaj ustawić wymaganych `name` atrybutu do odpowiedniej wartości.  
  
3.  Dodaj [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
4.  Ustaw następujące atrybuty odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType`, i `findValue`, jak pokazano w poniższym kodzie. Aby uzyskać więcej informacji na temat certyfikatów, zobacz [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
  
5.  Podczas konfigurowania klienta należy określić zachowanie przez ustawienie `behaviorConfiguration` atrybutu `<endpoint>` elementu, jak pokazano w poniższym kodzie. Punkt końcowy element jest elementem podrzędnym [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elementu. Ponadto należy określić nazwę konfiguracji powiązania, ustawiając `bindingConfiguration` atrybut do powiązania dla klienta. Jeśli używasz pliku konfiguracji wygenerowanego Nazwa powiązania jest generowany automatycznie. W tym przykładzie nazwa to `"tcpBindingWithCredential"`.  
  
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
- [Programowanie zabezpieczeń WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Wybieranie typu poświadczeń](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<Zabezpieczenia >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
