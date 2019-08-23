---
title: 'Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 6466d218ca21e7d2ee4f01f079f308348469fd97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934332"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania
Windows Communication Foundation (WCF) oferuje kilka trybów, za pomocą których klienci i usługi mogą się wzajemnie uwierzytelniać. Można utworzyć elementy powiązań zabezpieczeń dla tych trybów uwierzytelniania przy użyciu metod statycznych w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasie lub przez konfigurację, jak pokazano w poniższym przykładzie.  
  
 Aby uzyskać więcej informacji o 18 trybach uwierzytelniania, zobacz [elementu SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia metody tworzenia powiązań dla różnych trybów uwierzytelniania.  
  
> [!NOTE]
> Po utworzeniu wystąpienia <xref:System.ServiceModel.Channels.SecurityBindingElement> obiektu wiele właściwości jest niemodyfikowalnych, takich jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Wywołanie `set` takich właściwości nie powoduje ich zmiany.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
