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
ms.openlocfilehash: 6220365d5c43299a75d1e0fa8e46a7392b0ccaa2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590374"
---
# <a name="saml-tokens-and-claims"></a>Tokeny i oświadczenia języka SAML
*Tokeny* języka SAML (Security Assertions Markup Language) to XML reprezentacje oświadczeń. Domyślne tokeny protokołu SAML Windows Communication Foundation (WCF) w scenariuszach zabezpieczeń federacyjnych są *wystawiane*.  
  
 Tokeny języka SAML zawierają instrukcje, które są zestawami oświadczeń wykonanych przez jedną jednostkę o innej jednostce. Na przykład w scenariuszach zabezpieczeń federacyjnych instrukcje są wykonywane przez usługę tokenu zabezpieczającego użytkownika w systemie. Usługa tokenu zabezpieczającego podpisuje token SAML, aby wskazać prawdziwość instrukcji zawartych w tokenie. Ponadto token SAML jest skojarzony z materiałem klucza kryptograficznego, który użytkownik tokenu SAML udowadnia. Ten test jest zgodny z jednostką uzależnioną, że token SAML był w rzeczywistości wystawiany dla tego użytkownika. Na przykład w typowym scenariuszu:  
  
1. Klient żąda tokenu SAML z usługi tokenu zabezpieczającego, uwierzytelniając się w tej usłudze tokenu zabezpieczającego przy użyciu poświadczeń systemu Windows.  
  
2. Usługa tokenu zabezpieczającego wysyła do klienta token SAML. Token SAML jest podpisany za pomocą certyfikatu skojarzonego z usługą tokenu zabezpieczeń i zawiera klucz dowodu szyfrowany dla usługi docelowej.  
  
3. Klient otrzymuje również kopię *klucza testowego*. Klient przedstawia następnie token SAML do usługi aplikacji (jednostki *uzależnionej*) i podpisuje komunikat z tym kluczem potwierdzającym.  
  
4. Sygnatura za pośrednictwem tokenu SAML informuje jednostkę uzależnioną, że usługa tokenu zabezpieczającego wystawiła token. Sygnatura komunikatu utworzona przy użyciu klucza potwierdzającego informuje jednostkę uzależnioną, że token został wystawiony dla klienta.  
  
## <a name="from-claims-to-samlattributes"></a>Z oświadczeń do SamlAttributes  
 W programie WCF instrukcje w tokenach SAML są modelowane jako <xref:System.IdentityModel.Tokens.SamlAttribute> obiekty, które mogą być wypełniane bezpośrednio z <xref:System.IdentityModel.Claims.Claim> obiektów, pod warunkiem, że <xref:System.IdentityModel.Claims.Claim> obiekt ma <xref:System.IdentityModel.Claims.Claim.Right%2A> Właściwość <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> , a <xref:System.IdentityModel.Claims.Claim.Resource%2A> Właściwość jest typu <xref:System.String> . Przykład:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> Gdy tokeny SAML są serializowane w komunikatach, gdy są wystawiane przez usługę tokenu zabezpieczającego lub gdy są one prezentowane przez klientów usług w ramach uwierzytelniania, maksymalny przydział rozmiaru komunikatu musi być wystarczająco duży, aby pomieścić token SAML i inne części komunikatów. W normalnych przypadkach domyślne limity przydziału rozmiaru wiadomości są wystarczające. Jednak w przypadkach, gdy token SAML jest duży, ponieważ zawiera setki oświadczeń, może być konieczne zwiększenie liczby przydziałów w celu uwzględnienia serializowanego tokenu. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń danych](security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>Od SamlAttributes do oświadczeń  
 Gdy w komunikatach są odbierane tokeny SAML, różne instrukcje w tokenie SAML są włączane do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> obiektów, które są umieszczane w <xref:System.IdentityModel.Policy.AuthorizationContext> . Oświadczenia z każdej instrukcji SAML są zwracane przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> Właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> i mogą być badane w celu ustalenia, czy należy uwierzytelniać i autoryzować użytkownika.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federacja](federation.md)
- [Instrukcje: tworzenie klienta federacyjnego](how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](how-to-configure-credentials-on-a-federation-service.md)
- [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md)
- [Oświadczenia i tokeny](claims-and-tokens.md)
- [Tworzenie oświadczenia i wartości zasobów](claim-creation-and-resource-values.md)
- [Instrukcje: Tworzenie oświadczenia niestandardowego](../extending/how-to-create-a-custom-claim.md)
