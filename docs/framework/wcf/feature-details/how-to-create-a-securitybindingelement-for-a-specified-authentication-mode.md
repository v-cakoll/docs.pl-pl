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
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="bfd34-102">Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="bfd34-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="bfd34-103">Windows Communication Foundation (WCF) oferuje kilka trybów, za pomocą których klienci i usługi mogą się wzajemnie uwierzytelniać.</span><span class="sxs-lookup"><span data-stu-id="bfd34-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="bfd34-104">Można utworzyć elementy powiązań zabezpieczeń dla tych trybów uwierzytelniania przy użyciu metod statycznych w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasie lub przez konfigurację, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bfd34-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="bfd34-105">Aby uzyskać więcej informacji o 18 trybach uwierzytelniania, zobacz [elementu SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="bfd34-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd34-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfd34-106">Example</span></span>  
 <span data-ttu-id="bfd34-107">Poniższy przykład kodu przedstawia metody tworzenia powiązań dla różnych trybów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="bfd34-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfd34-108">Po <xref:System.ServiceModel.Channels.SecurityBindingElement> utworzeniu wystąpienia obiektu wiele właściwości jest niemodyfikowalnych, takich jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> .</span><span class="sxs-lookup"><span data-stu-id="bfd34-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="bfd34-109">Wywołanie `set` takich właściwości nie powoduje ich zmiany.</span><span class="sxs-lookup"><span data-stu-id="bfd34-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bfd34-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfd34-110">See also</span></span>

- [<span data-ttu-id="bfd34-111">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bfd34-111">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="bfd34-112">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bfd34-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
