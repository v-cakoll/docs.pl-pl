---
title: 'Instrukcje: wyłączanie szyfrowania podpisów cyfrowych'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: e2fd2a058e636ebf398f9d0c71a93788ccd7dfa0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325270"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Instrukcje: wyłączanie szyfrowania podpisów cyfrowych
Domyślnie wiadomość jest podpisany i podpisu cyfrowego są szyfrowane. Jest to kontrolowane przez tworzenie niestandardowego powiązania za pomocą wystąpienia <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawienie `MessageProtectionOrder` właściwości każdej klasy, aby <xref:System.ServiceModel.Security.MessageProtectionOrder> wartość wyliczenia. Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ten proces zużywa do 30 procent więcej czasu niż po prostu podpisywania i szyfrowania oparte na całkowity rozmiar komunikatu (mniejszy komunikat o błędzie, tym większy wpływ na wydajność). Wyłączanie szyfrowania podpisów, jednak mogą umożliwić osobie atakującej do odgadnięcia treści komunikatu. Jest to możliwe, ponieważ element podpis zawiera skrótu zwykły tekst każdej części podpisanych wiadomości. Na przykład mimo, że treść komunikatu jest domyślne szyfrowanie przekazywanego materiału, niezaszyfrowane podpis zawiera skrótu przed szyfrowania treści wiadomości. Jeśli zestaw możliwych wartości dla części podpisane i zaszyfrowane jest mały, osoba atakująca może być zawartość, analizując wartość skrótu. Szyfrowanie podpis zmniejsza zagrożenie tego ataku.  
  
 W związku z tym należy wyłączyć szyfrowanie podpisu, tylko wtedy, gdy wartość zawartości jest niski lub zestaw możliwych wartości zawartości jest duży i niedeterministyczne i przyrost wydajności jest ważniejsza niż ograniczanie ryzyka ataków opisanych powyżej.  
  
> [!NOTE]
>  Jeśli nie ma nic w wiadomości, która jest zaszyfrowany, element podpis nie jest zaszyfrowany, nawet wtedy, gdy <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. To zachowanie występuje nawet w przypadku powiązania dostarczane przez system; wszystkie powiązania dostarczane przez system mają kolejność ochrony komunikatów równa `SignBeforeEncryptAndEncryptSignature`. Jednak sieci Web Services Description Language (WSDL) WCF generuje będzie nadal zawierać `<sp:EncryptSignature>` potwierdzenia.  
  
### <a name="to-disable-digital-signing"></a>Aby wyłączyć cyfrowego podpisywania  
  
1. Utwórz <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Dodaj opcję <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kolekcji powiązania.  
  
3. Ustaw <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, lub ustawić <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Zobacz także

- [Możliwości zabezpieczeń wiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
