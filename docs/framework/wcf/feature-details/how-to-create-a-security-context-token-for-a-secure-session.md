---
title: 'Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 02e0403f9ae5bb437145fa3a015edc69b884c4d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185018"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji
Za pomocą tokenu kontekstu zabezpieczeń stanowego (SCT) w bezpiecznej sesji, sesja może wytrzymać usługi są poddawane recyklingowi. Na przykład, gdy bezstanowy SCT jest używany w bezpiecznej sesji i internet information services (IIS) jest resetowany, a następnie dane sesji, który jest skojarzony z usługą jest tracona. Te dane sesji obejmują pamięć podręczną tokenów SCT. Tak więc następnym razem, gdy klient wysyła usługę bezstanowy SCT, zwracany jest błąd, ponieważ nie można pobrać klucza skojarzonego z SCT. Jeśli jednak używany jest stanowy SCT, klucz, który jest skojarzony z SCT jest zawarty w SCT. Ponieważ klucz jest zawarty w SCT i w związku z tym zawarte w wiadomości, bezpiecznej sesji nie ma wpływu na usługi są poddawane recyklingowi. Domyślnie Windows Communication Foundation (WCF) używa bezstanowych SCT w bezpiecznej sesji. W tym temacie szczegółowo opisano, jak używać stanowych SCT w bezpiecznej sesji.  
  
> [!NOTE]
> Stateful SCTs nie mogą być używane w bezpiecznej sesji, która obejmuje umowy, która pochodzi z <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
> W przypadku aplikacji, które używają stanowych SCT w bezpiecznej sesji, tożsamość wątku dla usługi musi być kontem użytkownika, które ma skojarzony profil użytkownika. Gdy usługa jest uruchamiana na koncie, które nie `Local Service`ma profilu użytkownika, na przykład , może zostać zgłoszony wyjątek.  
  
> [!NOTE]
> Gdy personifikacja jest wymagana w systemie Windows XP, należy użyć bezpiecznej sesji bez stanowego SCT. Gdy stanowe SCTs są używane <xref:System.InvalidOperationException> z personifikacji, jest generowany. Aby uzyskać więcej informacji, zobacz [Nieobsługiwały scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Aby użyć stanowych sct w bezpiecznej sesji  
  
- Utwórz niestandardowe powiązanie, które określa, że wiadomości PROTOKOŁU SOAP są chronione przez bezpieczną sesję, która używa stanowego SCT.  
  
    1. Zdefiniuj niestandardowe powiązanie, dodając [ \<niestandardowy>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. Dodaj [ \<element](../../configure-apps/file-schema/wcf/bindings.md) podrzędny wiązania>do [ \<niestandardowego>. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         Określ nazwę powiązania, `name` ustawiając atrybut na unikatową nazwę w pliku konfiguracyjnym.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. Określ tryb uwierzytelniania wiadomości wysyłanych do i z tej usługi, dodając [ \<element podrzędny>zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do [ \<niestandardowego>. ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         Określ, że bezpieczna sesja `authenticationMode` jest `SecureConversation`używana, ustawiając atrybut . Określ, że stany SC są `requireSecurityContextCancellation` używane `false`przez ustawienie atrybutu .  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Określ sposób uwierzytelniania klienta podczas ustanawiania bezpiecznej sesji, dodając [ \<element podrzędny secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) do [ \<>zabezpieczeń ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Określ sposób uwierzytelniania klienta, `authenticationMode` ustawiając atrybut.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Określ kodowanie wiadomości, dodając element kodowania, taki jak [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Określ transport, dodając element transportu, taki jak [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Poniższy przykład kodu używa konfiguracji, aby określić niestandardowe powiązanie, którego wiadomości mogą używać ze stanowymi sct w bezpiecznej sesji.  
  
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
 Poniższy przykład kodu tworzy niestandardowe <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> powiązanie, które używa trybu uwierzytelniania do uruchamiania bezpiecznej sesji.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Gdy uwierzytelnianie systemu Windows jest używany w połączeniu ze stanowym SCT, WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość z tożsamością rzeczywistego obiektu wywołującego, ale zamiast tego ustawia właściwość na anonimową. Ponieważ zabezpieczenia WCF musi ponownie utworzyć zawartość kontekstu zabezpieczeń usługi dla każdego żądania z przychodzącego SCT, serwer nie śledzi sesji zabezpieczeń w pamięci. Ponieważ nie można serializować <xref:System.Security.Principal.WindowsIdentity> wystąpienia w SCT, <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość zwraca anonimową tożsamość.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [\<>niestandardowe](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
