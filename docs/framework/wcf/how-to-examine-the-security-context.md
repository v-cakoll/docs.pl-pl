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
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320989"
---
# <a name="how-to-examine-the-security-context"></a>Instrukcje: Badanie kontekstu zabezpieczeń
Podczas programowania usług Windows Communication Foundation (WCF) kontekst zabezpieczenia usługi umożliwia określenie szczegółowych informacji o poświadczeniach klienta i oświadczeniach używanych do uwierzytelniania w usłudze. Jest to realizowane przy użyciu właściwości klasy <xref:System.ServiceModel.ServiceSecurityContext>.  
  
 Na przykład można pobrać tożsamość bieżącego klienta przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> lub <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>. Aby określić, czy klient jest anonimowy, użyj właściwości <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.  
  
 Można również określić, jakie oświadczenia są wykonywane w imieniu klienta przez iterację kolekcji oświadczeń we właściwości <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
### <a name="to-get-the-current-security-context"></a>Aby uzyskać bieżący kontekst zabezpieczeń  
  
- Uzyskaj dostęp do właściwości statycznej <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>, aby uzyskać bieżący kontekst zabezpieczeń. Przeanalizuj wszystkie właściwości bieżącego kontekstu z odwołania.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Aby określić tożsamość obiektu wywołującego  
  
1. Drukuj wartość właściwości <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Aby przeanalizować oświadczenia obiektu wywołującego  
  
1. Zwróć bieżącą klasę <xref:System.IdentityModel.Policy.AuthorizationContext>. Użyj właściwości <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>, aby zwrócić bieżący kontekst zabezpieczeń usługi, a następnie Zwróć `AuthorizationContext` przy użyciu właściwości <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
2. Przeanalizuj kolekcję obiektów <xref:System.IdentityModel.Claims.ClaimSet> zwracanych przez właściwość <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> klasy <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład drukuje wartości właściwości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> bieżącego kontekstu zabezpieczeń oraz Właściwość <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, wartość zasobu dla żądania oraz Właściwość <xref:System.IdentityModel.Claims.Claim.Right%2A> każdego żądania w bieżącym kontekście zabezpieczeń.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Kod używa następujących przestrzeni nazw:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług](securing-services.md)
- [Uwierzytelnianie i tożsamość usług](./feature-details/service-identity-and-authentication.md)
