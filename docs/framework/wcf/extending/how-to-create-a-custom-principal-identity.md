---
title: 'Instrukcje: Tworzenie niestandardowej tożsamości podmiotu zabezpieczeń'
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
ms.openlocfilehash: e3ecee7be32cef7fc5371e56cfc32e2d0ef7ae6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488042"
---
# <a name="how-to-create-a-custom-principal-identity"></a>Instrukcje: Tworzenie niestandardowej tożsamości podmiotu zabezpieczeń
<xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest deklaratywne środki kontroli dostępu do metody usługi. Korzystając z tego atrybutu <xref:System.ServiceModel.Description.PrincipalPermissionMode> wyliczenie Określa tryb wykonywania sprawdzeń autoryzacji. Jeśli ten tryb jest równa <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umożliwia użytkownikowi określenie niestandardowego <xref:System.Security.Principal.IPrincipal> zwrócony przez klasę <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwości. W tym temacie przedstawiono scenariusz podczas <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> jest używany w połączeniu z niestandardowych zasad autoryzacji i niestandardowy podmiot zabezpieczeń.  
  
 Aby uzyskać więcej informacji o korzystaniu z <xref:System.Security.Permissions.PrincipalPermissionAttribute>, zobacz [porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Odwołania do następujących przestrzeni nazw są potrzebne, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
