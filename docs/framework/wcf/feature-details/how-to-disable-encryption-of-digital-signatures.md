---
title: 'Instrukcje: wyłączanie szyfrowania podpisów cyfrowych'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 461c5af2c7fbb98486a8decbe4aa998d8d21070d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911179"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Instrukcje: wyłączanie szyfrowania podpisów cyfrowych
Domyślnie komunikat jest podpisany i podpis jest szyfrowany cyfrowo. Jest to kontrolowane przez utworzenie powiązania niestandardowego z wystąpieniem <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> lub i ustawieniem `MessageProtectionOrder` właściwości każdej klasy na <xref:System.ServiceModel.Security.MessageProtectionOrder> wartość wyliczenia. Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ten proces zużywa do 30% więcej czasu niż po prostu podpisywanie i szyfrowanie na podstawie ogólnego rozmiaru komunikatów (mniejszym komunikatem jest większy wpływ na wydajność). Wyłączenie szyfrowania podpisu może jednak pozwolić atakującemu na odpuszczenie zawartości komunikatu. Jest to możliwe, ponieważ element Signature zawiera kod skrótu zwykłego tekstu każdej podpisanej części wiadomości. Na przykład mimo że treść komunikatu jest zaszyfrowana domyślnie, podpis niezaszyfrowany zawiera kod skrótu treści komunikatu przed szyfrowaniem. Jeśli zestaw możliwych wartości dla podpisanej i zaszyfrowanej części jest mały, osoba atakująca może mieć możliwość wywnioskowania zawartości, sprawdzając wartość skrótu. Szyfrowanie podpisu ogranicza ten wektor ataku.  
  
 W związku z tym należy wyłączyć szyfrowanie podpisu tylko wtedy, gdy wartość zawartości jest niska lub zbiór możliwych wartości zawartości jest duży i niedeterministyczny, a wzrost wydajności jest ważniejszy niż wyeliminowanie opisanego powyżej ataku.  
  
> [!NOTE]
> Jeśli w zaszyfrowanej wiadomości nie ma nic, element Signature nie jest szyfrowany, nawet gdy <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Właściwość or <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> jest ustawiona na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Takie zachowanie występuje nawet w przypadku powiązań dostarczonych przez system; wszystkie powiązania dostarczone przez system mają kolejność ochrony wiadomości ustawioną na `SignBeforeEncryptAndEncryptSignature`. Jednak generowanie programu WCF w Web Services Description Language (WSDL) nadal będzie zawierać `<sp:EncryptSignature>` potwierdzenie.  
  
### <a name="to-disable-digital-signing"></a>Aby wyłączyć podpisywanie cyfrowe  
  
1. Utwórz <xref:System.ServiceModel.Channels.CustomBinding>. Aby uzyskać więcej informacji, zobacz [jak: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Dodaj<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> albo do kolekcji powiązań.  
  
3. Ustaw właściwość na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>wartość lub ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwość na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Zobacz także

- [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
