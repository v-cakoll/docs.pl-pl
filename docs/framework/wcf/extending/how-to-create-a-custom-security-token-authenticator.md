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
ms.openlocfilehash: ba554ed23ae039796f51f4a699d368c4a6c0587e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809391"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń
W tym temacie pokazano, jak utworzyć wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych oraz jak zintegrować ją z Menedżer tokenów zabezpieczających niestandardowych. Wystawcę uwierzytelnienia tokenów zabezpieczających sprawdza poprawność zawartości tokenu zabezpieczającego dostarczane z komunikatu przychodzącego. Jeśli weryfikacja zakończy się powodzeniem, serwer uwierzytelniający zwraca kolekcję <xref:System.IdentityModel.Policy.IAuthorizationPolicy> obiektów, po obliczeniu zwraca zestaw oświadczeń.  
  
 Aby użyć wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych w systemie Windows Communication Foundation (WCF), należy najpierw utworzyć niestandardowych poświadczeń i zabezpieczeń implementacje Menedżer tokenów. Aby uzyskać więcej informacji na temat tworzenia niestandardowych poświadczeń i zabezpieczeń Menedżer tokenów, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md). Aby uzyskać więcej informacji o poświadczenia, Menedżer tokenów zabezpieczających oraz klasy dostawcy i uwierzytelniania, zobacz [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>Aby utworzyć wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> klasy.  
  
2.  Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> metody. Metoda zwraca `true` lub `false` w zależności od tego, czy niestandardowego wystawcy uwierzytelnienia można zweryfikować typ tokenu przychodzącego lub nie.  
  
3.  Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Ta metoda musi odpowiednio walidacji tokenu zawartości. Token przeszedł sprawdzania poprawności kroku, zwraca zbiór <xref:System.IdentityModel.Policy.IAuthorizationPolicy> wystąpień. W poniższym przykładzie użyto implementacji zasad autoryzacji niestandardowej, która zostanie utworzona w następnej procedurze.  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 Poprzedni kod zwraca kolekcję zasad autoryzacji w <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> metody. Usługi WCF nie zawiera publicznej implementację tego interfejsu. Poniższa procedura pokazuje, jak w tym celu do własnych wymagań.  
  
#### <a name="to-create-a-custom-authorization-policy"></a>Do tworzenia niestandardowych zasad autoryzacji  
  
1.  Zdefiniuj nowy Implementacja klasy <xref:System.IdentityModel.Policy.IAuthorizationPolicy> interfejsu.  
  
2.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> właściwości tylko do odczytu. Jednym ze sposobów wdrożenia tej właściwości jest Wygeneruj Unikatowy identyfikator globalny (GUID) w konstruktorze klasy i przywróć jego każdorazowego żądanej wartości dla tej właściwości.  
  
3.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> właściwości tylko do odczytu. Ta właściwość musi zwracać wystawcę zestawów oświadczeń, które są uzyskiwane z tokenu. Wystawca tokenu lub urząd, który jest odpowiedzialny za sprawdzanie poprawności tokenu zawartość powinna odpowiadać tym wystawcą. W poniższym przykładzie użyto Oświadczenie wystawcy przekazany do tej klasy z wystawcę uwierzytelnienia tokenów zabezpieczających niestandardowego utworzonego w poprzedniej procedurze. Wystawca uwierzytelnienia tokenu zabezpieczeń niestandardowych korzysta z zestawu oświadczeń dostarczane przez system (zwrócony przez <xref:System.IdentityModel.Claims.ClaimSet.System%2A> właściwości) do reprezentowania wystawca token nazwy użytkownika.  
  
4.  Implementowanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metody. Ta metoda powoduje wypełnienie wystąpienia <xref:System.IdentityModel.Policy.EvaluationContext> klasy (przekazany jako argument) z oświadczeń, które są oparte na zawartość tokenu zabezpieczeń przychodzących. Metoda zwraca `true` po zakończeniu z oceną. W przypadku wdrożenia zależy od obecności innych zasad autoryzacji, które znajdują się dodatkowe informacje w kontekście oceny tej metody można powrócić `false` Jeśli wymaganych informacji nie ma jeszcze w kontekście oceny. W takim przypadku WCF będzie wywoływać metodę ponownie po przeprowadzeniu oceny innych zasad autoryzacji generowane komunikatu przychodzącego, jeśli co najmniej jeden z tych zasad autoryzacji zmodyfikowane kontekst oceny.  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 [Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md) opisuje sposób tworzenia niestandardowych poświadczeń i niestandardowych zabezpieczeń Menedżer tokenów. Umożliwia wystawcę uwierzytelnienia tokenów zabezpieczających niestandardowe utworzone w tym miejscu implementacja Menedżer tokenów zabezpieczających są modyfikowane w celu zwracać niestandardowego wystawcy uwierzytelnienia z <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody. Gdy wymagania tokenu zabezpieczeń odpowiednich jest przekazywany w, metoda zwraca wystawcy uwierzytelnienia.  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>Aby zintegrować wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych z Menedżer tokenów zabezpieczających niestandardowych  
  
1.  Zastąpienie <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> metody w implementacji Menedżer tokenów zabezpieczeń niestandardowych.  
  
2.  Dodaj logikę do metody, aby włączyć go do zwrócenia z niestandardowych wystawcę uwierzytelnienia tokenów zabezpieczających na podstawie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Poniższy przykład zwraca wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych, jeśli typ tokenu wymagania tokenu jest nazwa użytkownika (reprezentowane przez <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> właściwości), a kierunek wiadomości, dla którego wnioskuje się wystawcę uwierzytelnienia tokenów zabezpieczających jest danych wejściowych ( reprezentowane przez <xref:System.ServiceModel.Description.MessageDirection.Input> pól).  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
