---
title: "Szyfrowanie podpisów cyfrowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 147f62a895983557267d0a18fdd1ea261ae6c855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="encryption-of-digital-signatures"></a>Szyfrowanie podpisów cyfrowych
Domyślnie komunikat jest podpisane i zaszyfrowane i podpisu cyfrowego jest zaszyfrowany. Można to kontrolowane przez utworzenie niestandardowego powiązania z wystąpieniem <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , a następnie ustawienie `MessageProtectionOrder` właściwości każdej klasy do <xref:System.ServiceModel.Security.MessageProtectionOrder> wartości wyliczenia. Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Ten proces trwa dłużej niż zwykłe podpisywania i szyfrowania 10 do 40 procent. Wyłączenie szyfrowania podpisu, jednak osoba atakująca może mieć odgadnąć treści wiadomości. Jest to możliwe, ponieważ wartość skrótu zwykły tekst każdej części podpisanych wiadomości zawiera element podpisu. Mimo że treść komunikatu jest domyślnie szyfrowane, niezaszyfrowane podpis zawiera skrótu treści wiadomości. Jeśli komunikat jest mały, osoba atakująca może mieć możliwość wywnioskować zawartość. Szyfrowanie podpis ograniczyć lub eliminuje tej możliwości.  
  
 Dlatego należy wyłączyć szyfrowanie podpisu, tylko wtedy, gdy wartość zawartości jest niski i bardziej wydajne będzie istotne, na przykład podczas wysyłania dużych plików binarnych, które mają wpływ na bezpieczeństwo.  
  
### <a name="to-disable-digital-signing"></a>Aby wyłączyć podpisów cyfrowych  
  
1.  Utwórz <xref:System.ServiceModel.Channels.CustomBinding>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Dodaj albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekcji powiązania.  
  
3.  Ustaw <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, lub ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie niestandardowych powiązań, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie niestandardowego powiązania dla trybu uwierzytelniania określonych, zobacz [porady: Tworzenie elementu SecurityBindingElement dla trybu uwierzytelniania określone](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Porady: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
