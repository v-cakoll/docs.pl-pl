---
title: 'Instrukcje: Bezpieczne punkty końcowe metadanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 2746c608fb47b94446c5d7e10748ba185d555e7f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202331"
---
# <a name="how-to-secure-metadata-endpoints"></a>Instrukcje: Bezpieczne punkty końcowe metadanych

Metadane usługi mogą zawierać poufne informacje o aplikacji, których może użyć złośliwy użytkownik. Konsumenci usługi mogą również wymagać bezpiecznego mechanizmu uzyskiwania metadanych dotyczących usługi. W związku z tym czasami konieczne jest opublikowanie metadanych przy użyciu bezpiecznego punktu końcowego.

Punkty końcowe metadanych są zwykle zabezpieczone przy użyciu standardowych mechanizmów zabezpieczeń zdefiniowanych w Windows Communication Foundation (WCF) do zabezpieczania punktów końcowych aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń](security-overview.md).

W tym temacie przedstawiono procedurę tworzenia punktu końcowego zabezpieczonego za pomocą certyfikatu SSL (SSL) lub innych słów — punktu końcowego HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w kodzie

1. Skonfiguruj port przy użyciu odpowiedniego certyfikatu X. 509. Certyfikat musi pochodzić z zaufanego urzędu i musi mieć zamierzone użycie "Autoryzacja usługi". Aby dołączyć certyfikat do portu, należy użyć narzędzia HttpCfg. exe. Zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Podmiot certyfikatu lub jego system nazw domen (DNS) musi być zgodny z nazwą komputera. Jest to niezbędne, ponieważ jeden z pierwszych kroków wykonywanych przez mechanizm HTTPS polega na sprawdzeniu, czy certyfikat jest wystawiony dla tego samego Uniform Resource Identifier (URI), co adres, na którym jest wywoływany.

2. Utwórz nowe wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy.

3. Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> Właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy na `true` .

4. Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Właściwość na odpowiedni adres URL. Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu `https://` . W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.

5. Dodaj wystąpienie do kolekcji zachowań, która <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> zwraca właściwość klasy, jak pokazano w poniższym kodzie.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Aby utworzyć bezpieczny punkt końcowy metadanych GET HTTPS w konfiguracji

1. Dodaj [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element do [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu pliku konfiguracji dla usługi.

2. Dodaj [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element do [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.

3. Dodaj [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do `<serviceBehaviors>` elementu.

4. Ustaw `name` atrybut `<behavior>` elementu na odpowiednią wartość. `name` Atrybut jest wymagany. W poniższym przykładzie zastosowano wartość `mySvcBehavior` .

5. Dodaj [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) `<behavior>` element do elementu.

6. Ustaw atrybut `httpsGetEnabled` elementu `<serviceMetadata>` na `true`.

7. Ustaw `httpsGetUrl` atrybut `<serviceMetadata>` elementu na odpowiednią wartość. Należy pamiętać, że jeśli określisz adres bezwzględny, adres URL musi rozpoczynać się od schematu `https://` . W przypadku określenia adresu względnego należy podać adres podstawowy HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, adres domyślny to "", lub bezpośrednio z adresem podstawowym HTTPS usługi.

8. Aby użyć zachowania z usługą, należy ustawić `behaviorConfiguration` atrybut [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu na wartość atrybutu nazwy elementu Behavior. Poniższy kod konfiguracji pokazuje kompletny przykład.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a>Przykład

Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje punkt końcowy. Następnie kod tworzy wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy i ustawia właściwości do tworzenia bezpiecznego punktu wymiany metadanych.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

W przykładzie kodu są stosowane następujące przestrzenie nazw:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
