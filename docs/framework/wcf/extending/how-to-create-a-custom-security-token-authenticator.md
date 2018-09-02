---
title: 'Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: cbd45580e84a0723d28bab538bc0ffe388899d61
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462412"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń
W tym temacie przedstawiono sposób tworzenia wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych oraz zintegrować ją z usługą Menedżer tokenów zabezpieczeń niestandardowych. Wystawcy uwierzytelniania tokenu zabezpieczeń sprawdza poprawność zawartości tokenu zabezpieczającego z dołączonym wiadomości przychodzącej. Jeśli weryfikacja zakończy się powodzeniem, wystawcy uwierzytelnienia zwraca kolekcję <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień, gdy obliczane, zwracany jest zestaw oświadczeń.  
  
 Aby użyć wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych w Windows Communication Foundation (WCF), należy najpierw utworzyć niestandardowe poświadczenia i zabezpieczeń implementacje Menedżer tokenów. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poświadczeń i zabezpieczeń Menedżer tokenów zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Aby uzyskać więcej informacji na temat klasy dostawcy i wystawcy uwierzytelnienia poświadczeń, Menedżer tokenów zabezpieczeń i zobacz [architekturę zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Aby utworzyć wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> klasy.  
  
2.  Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> metody. Metoda ta zwraca `true` lub `false` w zależności od tego, czy niestandardowe wystawcy uwierzytelnienia można sprawdzić poprawność przychodzącego tokenu typu lub nie.  
  
3.  Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Ta metoda musi sprawdzić zawartość tokenów, odpowiednio. Jeśli token przechodzi do kroku weryfikacji, zwraca kolekcję <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień. W poniższym przykładzie użyto implementację zasad autoryzacja niestandardowa, która zostanie utworzona w następnej procedurze.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Powyższy kod zwraca kolekcję obiektów zasad autoryzacji w <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> metody. Usługi WCF nie udostępnia publiczne implementację tego interfejsu. Poniższa procedura pokazuje, jak to zrobić dla własnych wymagań.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Do utworzenia niestandardowych zasad autoryzacji  
  
1.  Definiowanie, wdrażanie nowej klasy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> interfejsu.  
  
2.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> właściwość tylko do odczytu. Jednym ze sposobów zaimplementowania tej właściwości jest wygenerować unikatowy identyfikator globalny (GUID) w konstruktorze klasy i przywrócić go za każdym razem, gdy wartość tej właściwości jest wymagane.  
  
3.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> właściwość tylko do odczytu. Ta właściwość musi zwracać wystawcy zestawów oświadczeń, które są uzyskiwane z tokenu. Wystawca tokenu lub urząd który jest odpowiedzialny za sprawdzanie poprawności zawartości tokenu powinna odpowiadać tym wystawcą. W poniższym przykładzie użyto wystawcy oświadczenia, które przekazane do tej klasy z niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń utworzone w poprzedniej procedurze. Wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych używa zestawu oświadczeń dostarczane przez system (zwrócone przez <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwość) do reprezentowania wystawca token nazwy użytkownika.  
  
4.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody. Ta metoda wypełni wystąpienie <xref:System.IdentityModel.Policy.EvaluationContext> klasy (przekazanego jako argument) przy użyciu oświadczeń, które są oparte na przychodzące zawartości tokenu zabezpieczeń. Metoda ta zwraca `true` po zakończeniu z oceną. W przypadkach, gdy implementacja zależy od obecności innych zasad autoryzacji, które udostępniają dodatkowe informacje na kontekst oceny tej metody może zwrócić `false` Jeśli nie ma wymaganych informacji jeszcze w kontekście oceny. W takim przypadku WCF będzie wywoływać metody ponownie po przeprowadzeniu oceny innych zasad autoryzacji wygenerowany dla komunikatu przychodzącego, jeśli co najmniej jeden z tych zasad autoryzacji zmodyfikowany kontekst oceny.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) zawiera opis sposobu tworzenia niestandardowych poświadczeń i niestandardowe zabezpieczeń Menedżer tokenów. Aby użyć niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń utworzone, w tym miejscu implementację Menedżer tokenów zabezpieczeń zostanie zmodyfikowany na potrzeby zwracają niestandardowych aplikacji authenticator z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody. Metoda zwraca wystawcy uwierzytelnienia, gdy wymóg tokenu zabezpieczeń odpowiednich jest przekazywany w.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Aby zintegrować wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych z Menedżer tokenów zabezpieczeń niestandardowe  
  
1.  Zastąp <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody w danej implementacji Menedżer tokenów zabezpieczeń niestandardowych.  
  
2.  Dodaj logikę do metody, aby umożliwić zwracają Twojego niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Poniższy przykład zwraca wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych, jeśli typ tokenu wymagania tokenu jest nazwą użytkownika (reprezentowane przez <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> właściwości) i danych wejściowych (kierunek wiadomości, dla którego wnioskuje się wystawcy uwierzytelniania tokenu zabezpieczeń reprezentowane przez <xref:System.ServiceModel.Description.MessageDirection.Input> pola).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
