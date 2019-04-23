---
title: 'Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338998"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta
*Tożsamości* funkcji Windows Communication Foundation (WCF) umożliwia klientowi określenie z wyprzedzeniem oczekiwaną tożsamość usługi. Zawsze, gdy serwer uwierzytelnia klienta, tożsamość jest sprawdzana względem oczekiwaną tożsamość. (Objaśnienia dotyczące tożsamości i jak to działa, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 Jeśli to konieczne, można dostosować weryfikacji przy użyciu weryfikatora tożsamości niestandardowej. Na przykład można wykonać testy weryfikacyjne opisane tożsamości usługi dodatkowe. W tym przykładzie weryfikatora tożsamości niestandardowej sprawdza, czy dodatkowe oświadczenia w certyfikacie X.509 zwrócona z serwera. Dla przykładowej aplikacji, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Aby rozszerzyć klasę wartość właściwości EndpointIdentity  
  
1. Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.ServiceModel.EndpointIdentity> klasy. W tym przykładzie nazwy rozszerzenia `OrgEndpointIdentity`.  
  
2. Dodaj składowe prywatne oraz właściwości, które będą używane przez rozszerzonych <xref:System.ServiceModel.Security.IdentityVerifier> klasy do sprawdzania tożsamości przed oświadczenia w tokenie zabezpieczającym zwrócony przez usługę. Ten przykład definiuje jedną właściwość: `OrganizationClaim` właściwości.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Aby rozszerzyć klasę IdentityVerifier  
  
1. Zdefiniuj nową klasę, która pochodzi od klasy <xref:System.ServiceModel.Security.IdentityVerifier>. W tym przykładzie nazwy rozszerzenia `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. Zastąp <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody. Metoda określa, czy sprawdzić tożsamości zakończonych powodzeniem lub niepowodzeniem.  
  
3. `CheckAccess` Metoda ma dwa parametry. Pierwsza to wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy. Druga to wystąpienie <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
     W implementacji metody Sprawdź zbiór oświadczenia zwrócone przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy i wykonywania kontroli uwierzytelniania zgodnie z potrzebami. W tym przykładzie rozpoczyna się od wyszukiwania wszelkie roszczenia, które jest typu "Nazwy wyróżniającej", a następnie porównuje nazwę z rozszerzeniem programu <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Aby wdrożyć metodę TryGetIdentity  
  
1. Implementowanie <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metody, która określa, czy wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy mogą być zwracane przez klienta. Infrastruktura WCF wymaga wykonania `TryGetIdentity` metoda najpierw pobierania tożsamości usługi z komunikatu. Następnie wywołuje infrastruktury `CheckAccess` wdrożenia za pomocą zwróconych `EndpointIdentity` i <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2. W `TryGetIdentity` metodę, umieść następujący kod:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Implementowanie niestandardowego powiązania i ustaw IdentityVerifier niestandardowe  
  
1. Utwórz metodę, która zwraca <xref:System.ServiceModel.Channels.Binding> obiektu. Rozpoczyna się w tym przykładzie tworzone jest wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustawia jej tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>i jego <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> do <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2. Tworzenie <xref:System.ServiceModel.Channels.BindingElementCollection> przy użyciu <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3. Zwróć <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekcji i obsadź ją <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zmiennej.  
  
4. Ustaw <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> właściwość <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> nowe wystąpienie klasy `CustomIdentityVerifier` klasy został wcześniej utworzony.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. Niestandardowego powiązania, który jest zwracany jest używany do utworzenia wystąpienia klienta i klasy. Klienta można wykonać sprawdzenia weryfikacji tożsamości niestandardowej usługi jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano pełne wdrożenie <xref:System.ServiceModel.Security.IdentityVerifier> klasy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano pełne wdrożenie <xref:System.ServiceModel.EndpointIdentity> klasy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
