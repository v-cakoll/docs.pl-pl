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
# <a name="how-to-create-a-custom-principal-identity"></a>Instrukcje: tworzenie niestandardowej tożsamości podmiotu zabezpieczeń
<xref:System.Security.Permissions.PrincipalPermissionAttribute> To deklaratywne sposób kontrolowania dostępu do metody usługi. Korzystając z tego atrybutu <xref:System.ServiceModel.Description.PrincipalPermissionMode> wyliczenie Określa tryb wykonywania sprawdzeń autoryzacji. Jeśli ten tryb jest równa <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umożliwia użytkownikowi określenie niestandardowej <xref:System.Security.Principal.IPrincipal> zwrócony przez klasę <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwości. W tym temacie przedstawiono scenariusz przypadku <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> jest używana w połączeniu z niestandardowych zasad autoryzacji i niestandardowy podmiot zabezpieczeń.  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Security.Permissions.PrincipalPermissionAttribute>, zobacz [jak: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Odwołania do następujących przestrzeni nazw są potrzebne, aby skompilować kod:  
  
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
- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
