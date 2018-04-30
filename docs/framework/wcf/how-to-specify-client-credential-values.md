---
title: 'Instrukcje: Określanie wartości poświadczeń klienta'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856d33f88b55c35927998b15acc7bbf8ff1e9fe2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-client-credential-values"></a>Instrukcje: Określanie wartości poświadczeń klienta
Przy użyciu [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], usługi można określić, jak klient jest uwierzytelniony do usługi. Na przykład usługi można określić uwierzytelnienia klienta przy użyciu certyfikatu.  
  
### <a name="to-determine-the-client-credential-type"></a>Aby określić typ poświadczeń klienta  
  
1.  Pobieranie metadanych z punktu końcowego metadanych usługi. Metadane zazwyczaj składa się z dwóch plików: Kod klienta w języku programowania wybranym (wartość domyślna to Visual C#) i pliku konfiguracji XML. Jednym ze sposobów pobierania metadanych jest korzystać z narzędzia Svcutil.exe do zwrócenia kod klienta i konfiguracji klienta. Aby uzyskać więcej informacji, zobacz [pobierania metadanych](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) i [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
2.  Otwórz plik konfiguracji XML. Jeśli korzystasz z narzędzia Svcutil.exe w domyślnej nazwy pliku jest Output.config.  
  
3.  Znajdź  **\<zabezpieczeń >** element z **tryb** atrybutu (**< tryb zabezpieczeń =** `MessageOrTransport` **>** gdzie `MessageOrTransport` jest ustawiona na jeden z trybów zabezpieczeń.  
  
4.  Znajdź element podrzędny, która jest zgodna z wartością tryb. Na przykład, jeśli ustawiono tryb **komunikat**, Znajdź  **\<wiadomości >** element zawarty w  **\<zabezpieczeń >** elementu.  
  
5.  Zwróć uwagę na wartość przypisana do **clientCredentialType** atrybutu. Bieżąca wartość zależy od tego, który tryb jest używany, transportu lub wiadomości.  
  
 Poniższy kod XML przedstawia konfigurację korzystanie z zabezpieczeń komunikatów i wymaga certyfikatu klienta do uwierzytelniania klienta.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>Przykład: Tryb transportu protokołu TCP z certyfikatu jako poświadczeń klienta  
 W tym przykładzie ustawiono tryb zabezpieczeń transportu i ustawia wartość poświadczenia klienta certyfikatu X.509. Poniższe procedury pokazują, jak można ustawić wartości poświadczeń klienta na komputerze klienckim w kodzie i konfiguracji. Przy założeniu, że użyto [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do zwracania metadanych (kod i konfiguracja) z usługi. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>Aby określić wartość poświadczenia klienta na komputerze klienckim w kodzie  
  
1.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania kodu i konfiguracji usługi.  
  
2.  Utwórz wystąpienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta przy użyciu wygenerowanego kodu.  
  
3.  W klasie klienta, należy ustawić <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy odpowiednią wartość. W tym przykładzie ustawiono właściwość certyfikatu X.509 przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     Można użyć dowolnego z wyliczenia o <xref:System.Security.Cryptography.X509Certificates.X509FindType> klasy. Nazwa podmiotu jest używany w tym miejscu, w przypadku zmiany certyfikatu (ze względu na datę wygaśnięcia). Za pomocą nazwy podmiotu umożliwia infrastruktury znaleźć certyfikat ponownie.  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>Aby określić wartość poświadczenia klienta na komputerze klienckim w konfiguracji  
  
1.  Dodaj [ \<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
2.  Dodaj [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu. Należy ustawić wymaganych `name` atrybutu odpowiednią wartość.  
  
3.  Dodaj [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
4.  Ustaw następujące atrybuty odpowiednie wartości: `storeLocation`, `storeName`, `x509FindType`, i `findValue`, jak pokazano w poniższym kodzie. Aby uzyskać więcej informacji o certyfikatach, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
  
5.  Podczas konfigurowania klienta, Określ zachowanie przez ustawienie `behaviorConfiguration` atrybutu `<endpoint>` element, jak pokazano w poniższym kodzie. Element punktu końcowego jest elementem podrzędnym [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elementu. Ponadto określ nazwę konfiguracji powiązania, ustawiając `bindingConfiguration` atrybutu w celu powiązania dla klienta. Jeśli używasz plik konfiguracji wygenerowane automatycznie generowana jest nazwa wiązania. W tym przykładzie nazwa jest `"tcpBindingWithCredential"`.  
  
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
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [Programowanie zabezpieczeń WCF](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Wybieranie typu poświadczeń](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [\<Zabezpieczenia >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [\<message>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [\<zachowanie >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
