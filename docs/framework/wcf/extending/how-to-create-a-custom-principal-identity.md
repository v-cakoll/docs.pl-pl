---
title: 'Instrukcje: tworzenie niestandardowej tożsamości podmiotu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 9b8b18f6c66fdb8f2446d3ddc5c584c5bad44ef3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767276"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="bf2e0-102">Instrukcje: tworzenie niestandardowej tożsamości podmiotu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="bf2e0-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="bf2e0-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> To deklaratywne sposób kontrolowania dostępu do metody usługi.</span><span class="sxs-lookup"><span data-stu-id="bf2e0-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="bf2e0-104">Korzystając z tego atrybutu <xref:System.ServiceModel.Description.PrincipalPermissionMode> wyliczenie Określa tryb wykonywania sprawdzeń autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="bf2e0-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="bf2e0-105">Jeśli ten tryb jest równa <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umożliwia użytkownikowi określenie niestandardowej <xref:System.Security.Principal.IPrincipal> zwrócony przez klasę <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf2e0-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="bf2e0-106">W tym temacie przedstawiono scenariusz przypadku <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> jest używana w połączeniu z niestandardowych zasad autoryzacji i niestandardowy podmiot zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bf2e0-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="bf2e0-107">Aby uzyskać więcej informacji o korzystaniu z <xref:System.Security.Permissions.PrincipalPermissionAttribute>, zobacz [jak: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="bf2e0-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2e0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf2e0-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf2e0-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bf2e0-109">Compiling the Code</span></span>  
 <span data-ttu-id="bf2e0-110">Odwołania do następujących przestrzeni nazw są potrzebne, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="bf2e0-110">References to the following namespaces are needed to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="bf2e0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf2e0-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="bf2e0-112">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="bf2e0-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="bf2e0-113">Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="bf2e0-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
