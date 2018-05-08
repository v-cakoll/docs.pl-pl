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
ms.openlocfilehash: 374fde23a1bf8df704f76500b4808c16d142ddd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="saml-tokens-and-claims"></a>Tokeny i oświadczenia języka SAML
Zabezpieczenia potwierdzenia Markup Language (SAML) *tokenów* są oświadczenia reprezentacji XML. Domyślnie jest Windows Communication Foundation (WCF) używany w scenariuszach zabezpieczeń tokeny SAML *wystawionych tokenów*.  
  
 Tokeny SAML wykonania instrukcji, które są zestawy oświadczeń przez jedną jednostkę o innej jednostki. Na przykład w scenariuszach zabezpieczeń instrukcje są wykonywane przez usługę tokenu zabezpieczającego o użytkowniku w systemie. Usługa tokenu zabezpieczającego podpisuje token SAML, aby wskazać wiarygodności instrukcji zawartych w tokenie. Ponadto tokenu SAML jest skojarzony z materiału klucza kryptograficznego, gdy użytkownik tokenu SAML okaże informacje dotyczące. To potwierdzenie spełnia uzależniona, która była tokenu SAML, w rzeczywistości wystawiony dla tego użytkownika. Na przykład w typowy scenariusz:  
  
1.  Klient żąda tokenu SAML z usługą tokenu zabezpieczeń uwierzytelniania z usługą tokenu zabezpieczeń przy użyciu poświadczeń systemu Windows.  
  
2.  Usługa tokenu zabezpieczającego wystawia SAML token do klienta. Tokenu SAML jest podpisany przy użyciu certyfikatu skojarzonego z usługą tokenu zabezpieczeń i zawiera klucz potwierdzający zaszyfrowane dla usługi docelowej.  
  
3.  Klient odbiera również kopię *klucz potwierdzający*. Klient przedstawia tokenu SAML z usługą aplikacji ( *jednostki uzależnionej*) i podpisuje wiadomości z tego klucza potwierdzającego.  
  
4.  Podpis za pośrednictwem tokenu SAML informuje jednostki uzależnionej, czy usługa tokenu zabezpieczającego wystawiony token. Podpisu wiadomości utworzone za pomocą klucza potwierdzającego informuje jednostki uzależnionej, czy token został wystawiony dla klienta.  
  
## <a name="from-claims-to-samlattributes"></a>Z oświadczeń do SamlAttributes  
 W programie WCF, instrukcje w tokenach SAML są modelowane jako <xref:System.IdentityModel.Tokens.SamlAttribute> obiektów, które mogą być umieszczane bezpośrednio z <xref:System.IdentityModel.Claims.Claim> obiekty dostarczane <xref:System.IdentityModel.Claims.Claim> obiekt ma <xref:System.IdentityModel.Claims.Claim.Right%2A> właściwość <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> i <xref:System.IdentityModel.Claims.Claim.Resource%2A> właściwość jest Typ <xref:System.String>. Na przykład:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Gdy tokenów SAML są serializowane w wiadomości, gdy zostaną wystawione przez usługi tokenu zabezpieczającego lub mają być przedstawiane przez klientów do usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duży, aby zmieścił się w tokenie SAML i inne części wiadomości. W przypadku normalnych przydziały rozmiar komunikatu domyślne są wystarczające. Jednak w przypadku, gdy tokenu SAML jest duży, ponieważ zawiera on setki oświadczenia, konieczne może być zwiększyć przydziały w celu uwzględnienia Zserializowany token. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Z SamlAttributes oświadczeń  
 Po odebraniu wiadomości tokeny SAML, różne oświadczenia w tokenie SAML są włączone do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> obiektów, które są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext>. Oświadczenia z każdym instrukcji SAML są zwracane przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> i można zbadać w celu określenia, czy do uwierzytelniania i autoryzacji użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Tworzenie oświadczenia i wartości zasobów](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Instrukcje: tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
