---
title: "Instrukcje: Bezpieczne punkty końcowe metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e28b4dec851cc4115c2688540ebee151c91e4cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-secure-metadata-endpoints"></a>Instrukcje: Bezpieczne punkty końcowe metadanych
Metadane usługi mogą zawierać poufne informacje o aplikacji, która złośliwy użytkownik może wykorzystać. Konsumentów usługi może wymagać mechanizm bezpiecznego uzyskiwania metadanych dotyczących usługi. W związku z tym czasami jest niezbędne do opublikowania metadanych przy użyciu bezpiecznego punktu końcowego.  
  
 Punkty końcowe metadanych są zwykle chronione przy użyciu mechanizmów zabezpieczeń standardowe zdefiniowane w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpieczania punkty końcowe aplikacji. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 W tym temacie przedstawiono kroki, aby utworzyć punkt końcowy zabezpieczone przez certyfikat Secure Sockets Layer (SSL) lub innymi słowy, punkt końcowy HTTPS.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Aby utworzyć bezpieczny HTTPS GET końcowym metadanych w kodzie  
  
1.  Konfigurowanie portu z odpowiedniego certyfikatu X.509. Certyfikat musi pochodzić z zaufanego urzędu i musi mieć przeznaczenia "Autoryzacja usługi". Należy użyć narzędzia HttpCfg.exe do dołączenia certyfikatu do portu. Zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Podmiot certyfikatu lub jego systemu nazw domen (DNS) musi odpowiadać nazwie komputera. Jest to konieczne, ponieważ jeden z pierwszego czynności, które wykonuje mechanizmu HTTPS jest do sprawdzenia, czy certyfikat został wystawiony do tego samego identyfikatora URI (Uniform Resource) jako adres, na którym jest wywoływana.  
  
2.  Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy.  
  
3.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwość <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do `true`.  
  
4.  Ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> odpowiedni adres URL dla właściwości. Należy pamiętać, że jeśli określono adres bezwzględny adres URL musi rozpoczynać się od schemat "https://". Jeśli określisz adresem względnym, musi dostarczyć podstawowy adres HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, domyślnym adresem jest "", lub bezpośrednio w podstawowy adres HTTPS dla usługi.  
  
5.  Dodaj je do kolekcji zachowań który <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceDescription> klasy zwraca, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Aby utworzyć bezpieczny HTTPS GET końcowym metadanych w konfiguracji  
  
1.  Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementem pliku konfiguracji dla usługi.  
  
2.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elementu [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
3.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu `<serviceBehaviors>` elementu.  
  
4.  Ustaw `name` atrybutu `<behavior>` element odpowiednią wartość. `name` Atrybut jest wymagany. W poniższym przykładzie użyto wartości `mySvcBehavior`.  
  
5.  Dodaj [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) do `<behavior>` elementu.  
  
6.  Ustaw atrybut `httpsGetEnabled` elementu `<serviceMetadata>` na `true`.  
  
7.  Ustaw `httpsGetUrl` atrybutu `<serviceMetadata>` element odpowiednią wartość. Należy pamiętać, że jeśli określono adres bezwzględny adres URL musi rozpoczynać się od schemat "https://". Jeśli określisz adresem względnym, musi dostarczyć podstawowy adres HTTPS dla hosta usługi. Jeśli ta właściwość nie jest ustawiona, domyślnym adresem jest "", lub bezpośrednio w podstawowy adres HTTPS dla usługi.  
  
8.  Aby zachowanie używane z usługą, należy ustawić `behaviorConfiguration` atrybutu [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu na wartość atrybutu nazwy elementu zachowanie. Poniższy kod konfiguracji przedstawia pełny przykład.  
  
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
 Poniższy przykład tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> i dodaje punkt końcowy. Następnie tworzony wystąpienia <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy i ustawia właściwości w celu utworzenia punktu wymiany metadanych bezpieczne.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Przykładowy kod używa następujących nazw:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
