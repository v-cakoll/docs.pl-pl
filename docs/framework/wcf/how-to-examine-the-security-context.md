---
title: "Instrukcje: Badanie kontekstu zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4d6852a3162b3a8666c711d455e72517a91c4477
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-security-context"></a>Instrukcje: Badanie kontekstu zabezpieczeń
Programowania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usług, kontekst zabezpieczeń usługi umożliwia określenie szczegółów dotyczących poświadczeń klienta i oświadczeń używany do uwierzytelniania w usłudze. Jest to zrobić za pomocą właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy.  
  
 Na przykład można pobrać tożsamości bieżącego klienta za pomocą <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości. Aby określić, czy klient jest anonimowe, użyj <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> właściwości.  
  
 Można również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iteracji w kolekcji oświadczeń w <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.  
  
### <a name="to-get-the-current-security-context"></a>Aby uzyskać bieżący kontekst zabezpieczeń  
  
-   Dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> można pobrać bieżącego kontekstu zabezpieczeń. Sprawdź właściwości bieżącego kontekstu z odwołania.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Można określić tożsamości wywołującego  
  
1.  Drukowanie wartość <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Aby przeanalizować oświadczenia obiekt wywołujący  
  
1.  Zwraca bieżącą <xref:System.IdentityModel.Policy.AuthorizationContext> klasy. Użyj <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwość, aby powrócić do bieżącego kontekstu zabezpieczeń usługi, a następnie zwraca `AuthorizationContext` przy użyciu <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.  
  
2.  Kolekcja przeanalizować <xref:System.IdentityModel.Claims.ClaimSet> obiekty zwrócone przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do drukowania wartości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości bieżącego kontekstu zabezpieczeń i <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> właściwości, wartości zasobów oświadczenia i <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwości każdego oświadczenia w bieżącym zabezpieczeń kontekst.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W kodzie użyto następujących przestrzeni nazw:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
