---
title: 'Instrukcje: konfigurowanie potwierdzenia sygnatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 56e8720a6130d2908fbfb83bd243a54fae9a2406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315819"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Instrukcje: konfigurowanie potwierdzenia sygnatury
*Potwierdzenie podpisu* jest mechanizm dla inicjatora wiadomości upewnić się, czy odebrano odpowiedź został wygenerowany w odpowiedzi na pierwotny komunikat nadawcy. Potwierdzenie podpisu jest zdefiniowana w specyfikacji WS-Security 1.1. Jeśli punkt końcowy obsługuje WS-Security w wersji 1.0, nie można użyć potwierdzenia podpisu.  
  
 Poniższych procedur Określ sposób umożliwić używanie potwierdzenia podpisu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Można użyć tej samej procedury z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Procedura opiera się na podstawowe czynności opisane w [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>Aby włączyć potwierdzenia podpisu w kodzie  
  
1. Utworzenie wystąpienia <xref:System.ServiceModel.Channels.BindingElementCollection> klasy.  
  
2. Utwórz wystąpienie obiektu <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.  
  
3. Ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> do `true`.  
  
4. Dodaj element zabezpieczeń do kolekcji powiązania.  
  
5. Tworzenie niestandardowego powiązania, jak to określono w [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>Aby włączyć potwierdzenia podpisu w konfiguracji  
  
1. Dodaj `<customBinding>` elementu `<bindings>` sekcję pliku konfiguracji.  
  
2. Dodaj `<binding>` element i ustaw nazwę atrybutu do odpowiedniej wartości.  
  
3. Dodaj odpowiedni element kodowania. W poniższym przykładzie dodano `<TextMessageEncoding>` elementu.  
  
4. Dodaj `<security>` element podrzędny i ustaw `requireSignatureConfirmation` atrybutu `true`.  
  
5. Opcjonalna. Aby włączyć potwierdzenia podpisu podczas uruchamiania, należy dodać [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny i ustaw `equireSignatureConfirmation` atrybutu `true`.  
  
6. Dodaj element odpowiednie transportu. W poniższym przykładzie dodano [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawia <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> właściwość `true`. Należy zauważyć, że w tym przykładzie nie używa `<secureConversationBootstrap>` widocznego w poprzednim przykładzie. W przykładzie pokazano potwierdzenia podpisu, używając tokenu Windows (protokół Kerberos). W takim przypadku podpis klienta jest zwracany w odpowiedzi na wszystkie usługi i został potwierdzony przez klienta.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
