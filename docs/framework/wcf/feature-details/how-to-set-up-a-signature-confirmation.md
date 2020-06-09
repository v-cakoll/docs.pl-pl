---
title: 'Instrukcje: Konfigurowanie potwierdzenia sygnatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586926"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Instrukcje: Konfigurowanie potwierdzenia sygnatury

*Potwierdzenie podpisu* jest mechanizmem inicjatora komunikatów w celu upewnienia się, że odebrana odpowiedź została wygenerowana w odpowiedzi na oryginalny komunikat nadawcy. Potwierdzenie podpisu jest zdefiniowane w specyfikacji WS-Security 1,1. Jeśli punkt końcowy obsługuje WS-Security 1,0, nie można użyć potwierdzenia podpisu.

Poniższe procedury określają, jak włączyć potwierdzenie podpisu przy użyciu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . Tej samej procedury można użyć z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Procedura ta kompiluje się z podstawowymi krokami opisanymi w [instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-code"></a>Aby włączyć potwierdzenie podpisu w kodzie

1. Utworzenie wystąpienia <xref:System.ServiceModel.Channels.BindingElementCollection> klasy.

2. Utwórz wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.

3. Ustaw wartość <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> na `true` .

4. Dodaj element zabezpieczeń do kolekcji powiązań.

5. Utwórz niestandardowe powiązanie, zgodnie z opisem w [instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-configuration"></a>Aby włączyć potwierdzenie podpisu w konfiguracji

1. Dodaj `<customBinding>` element do sekcji w `<bindings>` pliku konfiguracji.

2. Dodaj `<binding>` element i ustaw odpowiednią wartość atrybutu Name.

3. Dodaj odpowiedni element kodowania. Poniższy przykład dodaje `<TextMessageEncoding>` element.

4. Dodaj `<security>` element podrzędny i ustaw `requireSignatureConfirmation` atrybut na `true` .

5. Opcjonalny. Aby włączyć potwierdzenie podpisu podczas ładowania, należy dodać [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny i ustawić `requireSignatureConfirmation` atrybut na `true` .

6. Dodaj odpowiedni element transportowy. Poniższy przykład dodaje [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :

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

Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawia <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> Właściwość na `true` . Należy zauważyć, że w tym przykładzie nie jest używany `<secureConversationBootstrap>` element przedstawiony w poprzednim przykładzie. Ten przykład ilustruje potwierdzenie podpisu w przypadku korzystania z tokenu systemu Windows (protokół Kerberos). W takim przypadku podpis klienta jest zwracany we wszystkich odpowiedziach usługi i zostaje potwierdzony przez klienta.

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
