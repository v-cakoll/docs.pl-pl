---
title: 'Instrukcje: Badanie kontekstu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 64e566fb8d0cfadc2a46d0a335ddb2799739f9f9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187783"
---
# <a name="how-to-examine-the-security-context"></a>Instrukcje: Badanie kontekstu zabezpieczeń
Podczas programowania usług Windows Communication Foundation (WCF), Usługa kontekstu zabezpieczeń umożliwia określenie szczegółowe informacje dotyczące poświadczeń klienta i oświadczeń używany do uwierzytelniania w usłudze. Jest to wykonywane przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy.  
  
 Na przykład, można pobrać tożsamości bieżącego klienta za pomocą <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości. Aby określić, czy klient jest anonimowe, użyj <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> właściwości.  
  
 Możesz również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iteracji w kolekcji oświadczeń w <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.  
  
### <a name="to-get-the-current-security-context"></a>Aby uzyskać bieżący kontekst zabezpieczeń  
  
-   Dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> można pobrać bieżącego kontekstu zabezpieczeń. Sprawdź właściwości bieżącego kontekstu z odwołania.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Aby ustalić tożsamość elementu wywołującego  
  
1.  Drukuj wartość <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Aby przeanalizować oświadczenia obiekt wywołujący  
  
1.  Zwraca bieżący <xref:System.IdentityModel.Policy.AuthorizationContext> klasy. Użyj <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwość zwraca bieżący kontekst zabezpieczeń usługi, a następnie wrócisz `AuthorizationContext` przy użyciu <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> właściwości.  
  
2.  Analizowanie kolekcję <xref:System.IdentityModel.Claims.ClaimSet> obiektów zwróconych przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład drukuje wartości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości bieżącego kontekstu zabezpieczeń i <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> właściwość, wartość zasobu, oświadczenia, a <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwości każdego oświadczenia w bieżącym zabezpieczeń kontekst.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kod używa następujących przestrzeni nazw:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
