---
title: 'Jak: tworzenie niestandardowego tokenu zabezpieczającego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
ms.openlocfilehash: 7bbe59958f59f76046c0a112463cfa64d09c14d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185587"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Jak: tworzenie niestandardowego tokenu zabezpieczającego
W tym temacie pokazano, jak utworzyć niestandardowy token zabezpieczający i jak zintegrować go z niestandardowym menedżerem tokenów zabezpieczających. Wystawca uwierzytelnienia tokenu zabezpieczającego sprawdza poprawność zawartości tokenu zabezpieczającego dostarczonego z wiadomością przychodzącą. Jeśli sprawdzanie poprawności zakończy się pomyślnie, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystawca uwierzytelnienia zwraca kolekcję wystąpień, które po ocenie zwraca zestaw oświadczeń.  
  
 Aby użyć niestandardowego tokenu zabezpieczającego w programie Windows Communication Foundation (WCF), należy najpierw utworzyć niestandardowe poświadczenia i implementacje menedżera tokenów zabezpieczeń. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poświadczeń i menedżera tokenów [zabezpieczających, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](walkthrough-creating-custom-client-and-service-credentials.md).
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Aby utworzyć niestandardowy token zabezpieczający  
  
1. Zdefiniuj nową <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> klasę pochodną klasy.  
  
2. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> w tej metodzie. Metoda zwraca `true` `false` lub w zależności od tego, czy niestandardowy wystawca uwierzytelniający może sprawdzić poprawność typu tokenu przychodzącego, czy nie.  
  
3. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> w tej metodzie. Ta metoda musi odpowiednio sprawdzić poprawność zawartości tokenu. Jeśli token przechodzi krok sprawdzania poprawności, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> zwraca kolekcję wystąpień. W poniższym przykładzie użyto implementacji zasad autoryzacji niestandardowej, która zostanie utworzona w następnej procedurze.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Poprzedni kod zwraca kolekcję zasad <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> autoryzacji w metodzie. WCF nie zapewnia publicznej implementacji tego interfejsu. Poniższa procedura pokazuje, jak to zrobić dla własnych wymagań.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Aby utworzyć niestandardowe zasady autoryzacji  
  
1. Zdefiniuj nową <xref:System.IdentityModel.Policy.IAuthorizationPolicy> klasę implementującą interfejs.  
  
2. Zaimplementuj właściwość tylko do odczytu. <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> Jednym ze sposobów zaimplementowania tej właściwości jest wygenerowanie globalnie unikatowego identyfikatora (GUID) w konstruktorze klasy i zwrócenie go za każdym razem, gdy żądana jest wartość dla tej właściwości.  
  
3. Zaimplementuj właściwość tylko do odczytu. <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> Ta właściwość musi zwrócić wystawcę zestawów oświadczeń, które są uzyskiwane z tokenu. Ten wystawca powinien odpowiadać wystawcy tokenu lub organowi odpowiedzialnemu za sprawdzanie poprawności zawartości tokenu. W poniższym przykładzie użyto oświadczenia wystawcy, który przeszedł do tej klasy z niestandardowego tokenu zabezpieczającego uwierzytelnienia utworzonego w poprzedniej procedurze. Niestandardowy token zabezpieczający używa zestawu oświadczeń dostarczonych przez <xref:System.IdentityModel.Claims.ClaimSet.System%2A> system (zwróconego przez właściwość) do reprezentowania wystawcy tokenu nazwy użytkownika.  
  
4. Zaimplementuj <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodę. Ta metoda wypełnia wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy (przekazywane jako argument) z oświadczeń, które są oparte na przychodzących zawartości tokenu zabezpieczającego. Metoda zwraca, `true` gdy odbywa się z oceny. W przypadkach, gdy implementacja opiera się na obecności innych zasad autoryzacji, `false` które dostarczają dodatkowych informacji do kontekstu oceny, ta metoda może zwrócić, jeśli wymagane informacje nie są jeszcze obecne w kontekście oceny. W takim przypadku WCF wywoła metodę ponownie po ocenie wszystkich innych zasad autoryzacji wygenerowanych dla wiadomości przychodzącej, jeśli co najmniej jedna z tych zasad autoryzacji zmodyfikowała kontekst oceny.  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](walkthrough-creating-custom-client-and-service-credentials.md) opisano sposób tworzenia poświadczeń niestandardowych i niestandardowego menedżera tokenów zabezpieczających. Aby użyć niestandardowego tokenu zabezpieczającego utworzonego w tym miejscu, implementacja menedżera tokenów zabezpieczających jest modyfikowana w celu zwrócenia niestandardowego wystawcy uwierzytelnienia z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> tej metody. Metoda zwraca wystawcę uwierzytelniacza, gdy przekazywane jest odpowiednie wymaganie tokenu zabezpieczającego.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Aby zintegrować niestandardowy token zabezpieczający z niestandardowym menedżerem tokenów zabezpieczających  
  
1. Zastąd <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> w implementacji niestandardowego menedżera tokenów zabezpieczeń należy zastąpić tę metodę.  
  
2. Dodaj logikę do metody, aby umożliwić jej zwrócenie niestandardowego tokenu zabezpieczającego na podstawie parametru. <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> Poniższy przykład zwraca niestandardowy token zabezpieczający, jeśli typ tokenu wymagania tokenu jest nazwą użytkownika (reprezentowane przez <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> właściwość) i kierunek komunikatu, dla którego żądany jest token zabezpieczający jest wymagane (reprezentowane przez <xref:System.ServiceModel.Description.MessageDirection.Input> pole).  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.UserNameSecurityToken>
- [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](walkthrough-creating-custom-client-and-service-credentials.md)
- [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](how-to-create-a-custom-security-token-provider.md)
