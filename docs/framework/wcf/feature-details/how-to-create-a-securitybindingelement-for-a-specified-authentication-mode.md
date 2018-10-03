---
title: 'Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
ms.openlocfilehash: 6204a2832bbdc0c6631903687fcd8a1c45b35d03
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036966"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania
Windows Communication Foundation (WCF) udostępnia kilka tryby, według których klientów i usług uwierzytelniania ze sobą. Możesz utworzyć zabezpieczeń elementy powiązania dla tych trybów uwierzytelniania przy użyciu metody statycznej na <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy lub przy użyciu konfiguracji, jak pokazano w poniższym przykładzie.  
  
 Aby uzyskać więcej informacji na temat trybów uwierzytelniana 18, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje metody tworzenia powiązania dla różnych metod uwierzytelniania.  
  
> [!NOTE]
>  Gdy wystąpienie <xref:System.ServiceModel.Channels.SecurityBindingElement> obiekt zostanie utworzony, wiele właściwości są niezmienne, takie jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Wywoływanie `set` takich właściwości nie na ich zmianę.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
