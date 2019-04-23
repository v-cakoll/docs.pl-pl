---
title: Szyfrowanie podpisów cyfrowych
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: ea53a575802f1e7903a66c2eda466c8937fb02f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341598"
---
# <a name="encryption-of-digital-signatures"></a>Szyfrowanie podpisów cyfrowych
Domyślnie wiadomość jest podpisane i szyfrowane i podpisu cyfrowego są szyfrowane. Można to kontrolować za tworzenie niestandardowego powiązania za pomocą wystąpienia <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , a następnie ustawiając `MessageProtectionOrder` właściwości każdej klasy, aby <xref:System.ServiceModel.Security.MessageProtectionOrder> wartość wyliczenia. Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ten proces trwa 10 do 40 procent dłużej niż po prostu podpisywanie i szyfrowanie. Wyłączanie szyfrowania podpisów, jednak mogą umożliwić osobie atakującej do odgadnięcia treści wiadomości. Jest to możliwe, ponieważ element podpis zawiera skrótu zwykły tekst każdej części podpisanych wiadomości. Na przykład mimo, że treść komunikatu jest domyślne szyfrowanie przekazywanego materiału, niezaszyfrowane podpis zawiera wartość skrótu treści wiadomości. Jeśli komunikat jest mały, osoba atakująca może być zawartość. Szyfrowanie podpis zmniejsza lub eliminuje to martwić.  
  
 W związku z tym należy wyłączyć szyfrowanie podpisu, tylko wtedy, gdy wartość zawartość jest niska, i przyrost wydajności będzie znaczący, na przykład podczas wysyłania dużych plików binarnych, które mają wpływ na zabezpieczenia.  
  
### <a name="to-disable-digital-signing"></a>Aby wyłączyć cyfrowego podpisywania  
  
1. Utwórz <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Dodaj opcję <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> kolekcji powiązania.  
  
3. Ustaw <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, lub ustawić <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania dla trybu uwierzytelniania określonych zobacz [jak: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
