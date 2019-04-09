---
title: 'Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 0b0da7e60cb54a1c3d6eb6d2d557f7312da1e9ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189344"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji
Za pomocą tokenu kontekstu zabezpieczeń stanową (SCT) w ramach bezpiecznej sesji, sesja może wytrzymać usługi odtwarzania. Na przykład gdy bezstanowe SCT jest używany w ramach bezpiecznej sesji i Internet Information Services (IIS) jest resetowany, następnie dane sesji, który jest skojarzony z usługą jest utracone. Te dane sesji obejmuje pamięci podręcznej SCT tokenu. Tak przy następnym klient wysyła usługi bezstanowej SCT, zwracany jest błąd, ponieważ nie można pobrać klucza, który jest skojarzony z SCT. Jeśli jednak stanowych SCT jest używany, klucz, który jest skojarzony z SCT jest zawarty w SCT. Ponieważ klucz jest zawarty w SCT i dlatego zawarte w wiadomości, bezpiecznej sesji nie występuje w usłudze odtwarzania. Domyślnie program Windows Communication Foundation (WCF) używa SCTs o bezstanowa w ramach bezpiecznej sesji. W tym temacie przedstawiono sposób użycia SCTs stanowych w ramach bezpiecznej sesji.  
  
> [!NOTE]
>  Stanowe SCTs nie można używać w ramach bezpiecznej sesji, która obejmuje kontraktu, który pochodzi od klasy <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  W przypadku aplikacji korzystających z SCTs stanowych w ramach bezpiecznej sesji tożsamość wątku dla usługi musi być konta użytkownika, który ma profil skojarzone z użytkownikami. Gdy uruchomiona jest usługa przy użyciu konta, który nie ma profilu użytkownika, takie jak `Local Service`, może być zgłaszany wyjątek.  
  
> [!NOTE]
>  Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez SCT stanowych. Stosowania stanowych SCTs personifikacji, <xref:System.InvalidOperationException> zgłaszany. Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Aby użyć SCTs stanowych w ramach bezpiecznej sesji  
  
-   Tworzenie niestandardowego powiązania, określający, że komunikaty protokołu SOAP są chronione przez bezpiecznej sesji, która używa SCT stanowych.  
  
    1.  Definiowanie niestandardowego powiązania, dodając [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element podrzędny do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Określ nazwę powiązania, ustawiając `name` atrybutu unikatową nazwę w pliku konfiguracji.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Określa tryb uwierzytelniania dla wiadomości wysyłanych do i z tej usługi, dodając [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element podrzędny do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Określ, że bezpiecznej sesji jest używany przez ustawienie `authenticationMode` atrybutu `SecureConversation`. Określ, że stanowych SCTs są używane przez ustawienie `requireSecurityContextCancellation` atrybutu `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Określ, jak klient jest uwierzytelniany podczas nawiązywania bezpiecznej sesji nawiązaniu przez dodanie [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny do [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Określ, jak klient jest uwierzytelniany, ustawiając `authenticationMode` atrybutu.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Określ kodowanie komunikatu przez dodanie elementu kodowania, takich jak [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Określ transportu, dodając element transportu, takich jak [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, który komunikatów za pomocą SCTs stanowych w ramach bezpiecznej sesji.  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania uruchomienie bezpiecznej sesji.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Podczas uwierzytelniania Windows jest używany w połączeniu z SCT stanowe, usługi WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości z funkcją wywołującą rzeczywistej tożsamości użytkownika, ale zamiast tego do nadawania właściwości anonimowych. Ponieważ w zabezpieczenia WCF, należy ponownie utworzyć zawartość usługi kontekstu zabezpieczeń dla każdego żądania z przychodzącego SCT, serwer nie zachować informacje o sesji zabezpieczeń w pamięci. Ponieważ nie jest możliwe do serializacji <xref:System.Security.Principal.WindowsIdentity> wystąpienie do SCT <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość zwraca Tożsamość anonimowa.  
  
 Następująca konfiguracja wykazuje to zachowanie.  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
