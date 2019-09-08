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
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797069"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Instrukcje: tworzenie niestandardowej tożsamości podmiotu zabezpieczeń
<xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest deklaratywnym sposobem kontrolowania dostępu do metod usługi. W przypadku korzystania z <xref:System.ServiceModel.Description.PrincipalPermissionMode> tego atrybutu Wyliczenie określa tryb wykonywania kontroli autoryzacji. Gdy ten tryb jest ustawiony na <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umożliwia użytkownikowi określenie klasy niestandardowej <xref:System.Security.Principal.IPrincipal> zwracanej przez <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwość. W tym temacie przedstawiono scenariusz, <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> gdy jest używany w połączeniu z niestandardowymi zasadami autoryzacji i niestandardowym podmiotem zabezpieczeń.  
  
 Aby uzyskać więcej informacji o korzystaniu <xref:System.Security.Permissions.PrincipalPermissionAttribute>z [programu, zobacz How to: Ogranicz dostęp za pomocą klasy](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Do kompilowania kodu są konieczne odwołania do następujących przestrzeni nazw:  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Instrukcje: Używanie dostawcy roli ASP.NET z usługą](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
