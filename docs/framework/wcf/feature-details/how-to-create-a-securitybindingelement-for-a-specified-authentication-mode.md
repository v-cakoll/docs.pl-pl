---
title: 'Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 9aebe6d8cc82c454161daead49b55f02a1cca4a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598947"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania
Windows Communication Foundation (WCF) oferuje kilka trybów, za pomocą których klienci i usługi mogą się wzajemnie uwierzytelniać. Można utworzyć elementy powiązań zabezpieczeń dla tych trybów uwierzytelniania przy użyciu metod statycznych w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasie lub przez konfigurację, jak pokazano w poniższym przykładzie.  
  
 Aby uzyskać więcej informacji o 18 trybach uwierzytelniania, zobacz [elementu SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia metody tworzenia powiązań dla różnych trybów uwierzytelniania.  
  
> [!NOTE]
> Po <xref:System.ServiceModel.Channels.SecurityBindingElement> utworzeniu wystąpienia obiektu wiele właściwości jest niemodyfikowalnych, takich jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> . Wywołanie `set` takich właściwości nie powoduje ich zmiany.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Tryby uwierzytelniania elementu SecurityBindingElement](securitybindingelement-authentication-modes.md)
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
