---
title: 'Instrukcje: wyłączanie szyfrowania podpisów cyfrowych'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 7ef305fdfd9a4ee61dfd89fdd46f2dc03a350977
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595404"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Instrukcje: wyłączanie szyfrowania podpisów cyfrowych
Domyślnie komunikat jest podpisany i podpis jest szyfrowany cyfrowo. Jest to kontrolowane przez utworzenie powiązania niestandardowego z wystąpieniem <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawieniem `MessageProtectionOrder` właściwości każdej klasy na <xref:System.ServiceModel.Security.MessageProtectionOrder> wartość wyliczenia. Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ten proces zużywa do 30% więcej czasu niż po prostu podpisywanie i szyfrowanie na podstawie ogólnego rozmiaru komunikatów (mniejszym komunikatem jest większy wpływ na wydajność). Wyłączenie szyfrowania podpisu może jednak pozwolić atakującemu na odpuszczenie zawartości komunikatu. Jest to możliwe, ponieważ element Signature zawiera kod skrótu zwykłego tekstu każdej podpisanej części wiadomości. Na przykład mimo że treść komunikatu jest zaszyfrowana domyślnie, podpis niezaszyfrowany zawiera kod skrótu treści komunikatu przed szyfrowaniem. Jeśli zestaw możliwych wartości dla podpisanej i zaszyfrowanej części jest mały, osoba atakująca może mieć możliwość wywnioskowania zawartości, sprawdzając wartość skrótu. Szyfrowanie podpisu ogranicza ten wektor ataku.  
  
 W związku z tym należy wyłączyć szyfrowanie podpisu tylko wtedy, gdy wartość zawartości jest niska lub zbiór możliwych wartości zawartości jest duży i niedeterministyczny, a wzrost wydajności jest ważniejszy niż wyeliminowanie opisanego powyżej ataku.  
  
> [!NOTE]
> Jeśli w zaszyfrowanej wiadomości nie ma nic, element Signature nie jest szyfrowany, nawet gdy <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Właściwość or jest ustawiona na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . Takie zachowanie występuje nawet w przypadku powiązań dostarczonych przez system; wszystkie powiązania dostarczone przez system mają kolejność ochrony wiadomości ustawioną na `SignBeforeEncryptAndEncryptSignature` . Jednak generowanie programu WCF w Web Services Description Language (WSDL) nadal będzie zawierać `<sp:EncryptSignature>` potwierdzenie.  
  
### <a name="to-disable-digital-signing"></a>Aby wyłączyć podpisywanie cyfrowe  
  
1. Utwórz <xref:System.ServiceModel.Channels.CustomBinding> . Aby uzyskać więcej informacji, zobacz [jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Dodaj albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekcji powiązań.  
  
3. Ustaw <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Właściwość na wartość <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> lub ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Właściwość na <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> .  
  
## <a name="see-also"></a>Zobacz też

- [Możliwości zabezpieczeń powiązań niestandardowych](security-capabilities-with-custom-bindings.md)
