---
title: 'Instrukcje: Bezpieczne punkty końcowe metadanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: e6fbaabb97e4a8de3e4bdbcc0c105b6cf999c0d5
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50037590"
---
# <a name="how-to-secure-metadata-endpoints"></a>Instrukcje: Bezpieczne punkty końcowe metadanych
Metadane usługi mogą zawierać poufne informacje, o swojej aplikacji, w której złośliwy użytkownik może używać. Osoby korzystające z usługi może wymagać mechanizm bezpiecznego uzyskiwania metadanych dotyczących usługi. W związku z tym czasami jest niezbędne do opublikowania przy użyciu bezpiecznego punktu końcowego metadanych.  
  
 Punkty końcowe metadanych zwykle są chronione za pomocą mechanizmów standardowych zabezpieczeń określonych w Windows Communication Foundation (WCF) do zabezpieczania punktów końcowych aplikacji. (Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 W tym temacie przedstawiono kroki, aby utworzyć zabezpieczony przez certyfikat Secure Sockets Layer (SSL) lub innymi słowy, punkt końcowy HTTPS punktu końcowego.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Aby utworzyć bezpieczne HTTPS GET punkt końcowy metadanych w kodzie  
  
1.  Konfigurowanie portu z odpowiedniego certyfikatu X.509. Certyfikat musi pochodzić z zaufanego urzędu i musi mieć zamierzone użycie "Autoryzacja usługi". Do dołączenia certyfikatu do portu, należy użyć narzędzia HttpCfg.exe. Zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Podmiot certyfikatu lub jej systemu nazw domen (DNS) musi odpowiadać nazwie komputera. Jest to ważne, ponieważ jeden z pierwszych kroków, które wykonuje mechanizm HTTPS jest aby sprawdzić, czy certyfikat został wystawiony na ten sam identyfikator URI (Uniform Resource) jako adres, na którym jest wywoływana.  
  
2.  Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy.  
  
3.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy `true`.  
  
4.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwość do odpowiedniego adresu URL. Należy pamiętać, że jeśli określisz adresem bezwzględnym, adres URL musi rozpoczynać się ze schematem "https://". Jeśli określisz adres względny, musisz podać adres bazowy HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, adresem domyślnym jest "", lub bezpośrednio na adres podstawowy protokół HTTPS dla usługi.  
  
5.  Dodaj wystąpienie do kolekcji zachowań, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceDescription> klasy wraca, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Aby utworzyć bezpieczne HTTPS GET punkt końcowy metadanych w konfiguracji  
  
1.  Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element pliku konfiguracji usługi.  
  
2.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
3.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu `<serviceBehaviors>` elementu.  
  
4.  Ustaw `name` atrybutu `<behavior>` element do odpowiedniej wartości. `name` Atrybut jest wymagany. W poniższym przykładzie użyto wartości `mySvcBehavior`.  
  
5.  Dodaj [ \<serviceMetadata w pliku >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do `<behavior>` elementu.  
  
6.  Ustaw atrybut `httpsGetEnabled` elementu `<serviceMetadata>` na `true`.  
  
7.  Ustaw `httpsGetUrl` atrybutu `<serviceMetadata>` element do odpowiedniej wartości. Należy pamiętać, że jeśli określisz adresem bezwzględnym, adres URL musi rozpoczynać się ze schematem "https://". Jeśli określisz adres względny, musisz podać adres bazowy HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, adresem domyślnym jest "", lub bezpośrednio na adres podstawowy protokół HTTPS dla usługi.  
  
8.  Zachowanie za pomocą usługi, należy ustawić `behaviorConfiguration` atrybutu [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element z wartością atrybutu nazwy elementu zachowanie. Poniższy kod konfiguracji przedstawia kompletny przykład.  
  
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
 Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje punkt końcowy. Następnie kod tworzy wystąpienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy i ustawia właściwości w celu utworzenia punktu wymiany metadanych bezpieczne.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Przykład kodu używa następujących przestrzeni nazw:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
