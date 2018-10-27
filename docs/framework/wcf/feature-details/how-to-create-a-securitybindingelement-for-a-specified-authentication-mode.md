---
title: 'Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: afc89d14623a25dbaa1ac5c9a58e11dd3e963617
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50088679"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="de54d-102">Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="de54d-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="de54d-103">Windows Communication Foundation (WCF) udostępnia kilka tryby, według których klientów i usług uwierzytelniania ze sobą.</span><span class="sxs-lookup"><span data-stu-id="de54d-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="de54d-104">Możesz utworzyć zabezpieczeń elementy powiązania dla tych trybów uwierzytelniania przy użyciu metody statycznej na <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy lub przy użyciu konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="de54d-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="de54d-105">Aby uzyskać więcej informacji na temat trybów uwierzytelniana 18, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="de54d-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de54d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="de54d-106">Example</span></span>  
 <span data-ttu-id="de54d-107">Poniższy przykład kodu pokazuje metody tworzenia powiązania dla różnych metod uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="de54d-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de54d-108">Gdy wystąpienie <xref:System.ServiceModel.Channels.SecurityBindingElement> obiekt zostanie utworzony, wiele właściwości są niezmienne, takie jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="de54d-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="de54d-109">Wywoływanie `set` takich właściwości nie na ich zmianę.</span><span class="sxs-lookup"><span data-stu-id="de54d-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="de54d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de54d-110">See Also</span></span>  
 [<span data-ttu-id="de54d-111">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="de54d-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [<span data-ttu-id="de54d-112">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="de54d-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
