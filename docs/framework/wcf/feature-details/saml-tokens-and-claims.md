---
title: Tokeny i oświadczenia języka SAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: 04517e5089f55c2d2b08a492439026d33ed9069d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339843"
---
# <a name="saml-tokens-and-claims"></a>Tokeny i oświadczenia języka SAML
Zabezpieczenia potwierdzenia Markup Language (SAML) *tokenów* są reprezentacji XML oświadczeń. Domyślnie są tokeny SAML, które korzysta z usługi Windows Communication Foundation (WCF) w scenariuszach federacyjnego zabezpieczenia *wystawionych tokenów*.  
  
 Tokeny SAML, wykonaj instrukcje, które są zestawami oświadczenia wprowadzone przez jedną jednostkę o innej jednostki. Na przykład w scenariuszach federacyjnego zabezpieczenia instrukcje są wykonywane przez usługę tokenu zabezpieczającego o użytkowniku w systemie. Usługa tokenu zabezpieczającego podpisuje token SAML, aby wskazać wiarygodności instrukcji zawartych w tokenie. Ponadto SAML token jest skojarzony z materiału klucza kryptograficznego, użytkownika w tokenie języka SAML upoważnienie wiedzę na temat. Dowód ten spełnia jednostki uzależnionej strona, która była tokenu SAML, w rzeczywistości wystawiony dla tego użytkownika. Na przykład w typowym scenariuszu:  
  
1. Klient żąda tokenu SAML z usługi tokenu zabezpieczeń, którzy uwierzytelniają się do usługi tokenu zabezpieczeń przy użyciu poświadczeń Windows.  
  
2. Usługa tokenu zabezpieczającego wystawia SAML token do klienta. SAML token jest podpisany przy użyciu certyfikatu skojarzonego z usługi tokenu zabezpieczeń i zawiera klucz potwierdzający zaszyfrowane dla usługi docelowej.  
  
3. Klient odbiera także kopię *klucz potwierdzający*. Klient przedstawia token SAML z usługą application ( *jednostki uzależnionej*) i podpisuje wiadomości przy użyciu tego klucza weryfikacji.  
  
4. Podpis w tokenie języka SAML informuje uzależnionej, czy usługa tokenu zabezpieczającego wystawiony token. Podpisu wiadomości utworzone przy użyciu klucza weryfikacji informuje uzależnionej, czy token został wystawiony dla klienta.  
  
## <a name="from-claims-to-samlattributes"></a>Z oświadczeń SamlAttributes  
 W programie WCF, instrukcje w tokeny SAML są modelowane jako <xref:System.IdentityModel.Tokens.SamlAttribute> obiektów, które mogą zostać wypełnione bezpośrednio z <xref:System.IdentityModel.Claims.Claim> obiektów, pod warunkiem <xref:System.IdentityModel.Claims.Claim> obiekt ma <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwość <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> i <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość jest Typ <xref:System.String>. Na przykład:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Gdy tokeny SAML są serializowane w wiadomości, wystawiane przez usługę tokenu zabezpieczającego lub gdy są one zgłaszane przez klientów do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duża, aby uwzględnić w tokenie języka SAML i inne części wiadomości. W warunkach normalnych domyślne limity przydziału rozmiaru wiadomości są wystarczające. Jednak w przypadku, gdy SAML token jest duże, ponieważ zawiera ona setki oświadczenia, konieczne może zwiększyć te limity, aby pomieścić Zserializowany token. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes do oświadczeń  
 Po odebraniu wiadomości tokeny SAML, różne oświadczenia w tokenie SAML są przekształcane w <xref:System.IdentityModel.Policy.IAuthorizationPolicy> obiektów, które są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext>. Oświadczenia z każdej instrukcji SAML są zwracane przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> i można zbadać w celu ustalenia, czy do uwierzytelniania i autoryzacji użytkownika.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Tworzenie oświadczenia i wartości zasobów](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Instrukcje: Tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
