---
title: 'Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e6c41ed32d63932bc1fac72bc6e727eb82806617
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966082"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji
Przy użyciu tokenu stanowego kontekstu zabezpieczeń (SCT) w bezpiecznej sesji, sesja może przetrzymywać odtwarzanie usługi. Na przykład gdy w bezpiecznej sesji jest używany niestanowy SCT, a Internet Information Services (IIS) jest resetowany, dane sesji skojarzone z usługą zostaną utracone. Dane sesji obejmują pamięć podręczną tokenów SCT. W związku z tym następnym razem, gdy klient wysyła usługę do bezstanowego SCT, zwracany jest błąd, ponieważ nie można pobrać klucza skojarzonego z SCT. Jeśli jednak używany jest stanowy SCT, wówczas klucz skojarzony z SCT jest zawarty w SCT. Ponieważ klucz znajduje się w obrębie SCT i w związku z tym jest zawarty w komunikacie, usługa nie ma na nie wpływ na bezpieczną sesję. Domyślnie Windows Communication Foundation (WCF) używa bezstanowej SCTs w bezpiecznej sesji. W tym temacie szczegółowo opisano sposób używania SCTs stanowej w bezpiecznej sesji.  
  
> [!NOTE]
> Stanowej SCTs nie można używać w bezpiecznej sesji, która obejmuje kontrakt pochodzący z <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
> W przypadku aplikacji korzystających ze stanowych SCTs w bezpiecznej sesji tożsamość wątku dla usługi musi być kontem użytkownika, które ma skojarzony profil użytkownika. Gdy usługa jest uruchamiana przy użyciu konta, które nie ma profilu użytkownika, takiego jak `Local Service`, może zostać zgłoszony wyjątek.  
  
> [!NOTE]
> Jeśli w systemie Windows XP jest wymagana personifikacja, należy użyć bezpiecznej sesji bez stanowego SCT. Gdy stanowe SCTs są używane z personifikacją <xref:System.InvalidOperationException> , jest generowany. Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Aby użyć SCTs stanowej w bezpiecznej sesji  
  
- Tworzenie niestandardowego powiązania, które określa, że komunikaty protokołu SOAP są chronione za pomocą bezpiecznej sesji, która korzysta ze stanowego SCT.  
  
    1. Definiowanie niestandardowego powiązania przez dodanie niestandardowego elementubinding [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji usługi.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. Dodaj powiązanie [ >elemenciepodrzędnymdo>CustomBinding.\<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
         Określ nazwę powiązania przez ustawienie `name` atrybutu na unikatową nazwę w pliku konfiguracji.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. Określ tryb uwierzytelniania dla komunikatów wysyłanych do i z tej usługi przez dodanie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)podrzędnego > zabezpieczeń do > niestandardowychbinding.  
  
         Określ, że bezpieczna sesja jest używana przez ustawienie `authenticationMode` atrybutu na. `SecureConversation` Określ, że stanowe SCTs są używane przez `requireSecurityContextCancellation` ustawienie atrybutu `false`na.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Określ sposób uwierzytelniania klienta podczas ustanawiania bezpiecznej sesji przez dodanie [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)podrzędnego secureConversationBootstrap > do > zabezpieczeń.  
  
         Określ sposób uwierzytelniania klienta przez ustawienie `authenticationMode` atrybutu.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Określ kodowanie wiadomości poprzez dodanie elementu kodowania, takiego jak [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Określ transport poprzez dodanie elementu transportu, takiego jak [ \<> httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, które mogą być używane przez komunikaty ze stanem SCTs w bezpiecznej sesji.  
  
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
 Poniższy przykład kodu tworzy niestandardowe powiązanie, które używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> trybu uwierzytelniania do uruchamiania bezpiecznej sesji.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Gdy uwierzytelnianie systemu Windows jest używane w połączeniu z stanem SCT, funkcja WCF nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości przy użyciu tożsamości rzeczywistego obiektu wywołującego, ale ustawia właściwość na wartość anonimowe. Ze względu na to, że zabezpieczenia WCF muszą ponownie utworzyć zawartość kontekstu zabezpieczeń usługi dla każdego żądania z nieprzychodzącego SCT, serwer nie śledzi sesji zabezpieczeń w pamięci. Ponieważ nie można serializować <xref:System.Security.Principal.WindowsIdentity> wystąpienia do SCT <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> , właściwość zwraca tożsamość anonimową.  
  
 W poniższej konfiguracji przedstawiono takie zachowanie.  
  
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
