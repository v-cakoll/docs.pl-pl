---
title: 'Porady: tworzenie weryfikatora tożsamości niestandardowego klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 99d46b19e744190c50a2ba316fe0f59a8f6cf07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Porady: tworzenie weryfikatora tożsamości niestandardowego klienta
*Tożsamości* funkcji Windows Communication Foundation (WCF) umożliwia klientowi z góry określić oczekiwaną tożsamość usługi. Zawsze, gdy serwer uwierzytelnia do klienta, tożsamość jest sprawdzana względem Oczekiwana tożsamość. (Aby uzyskać informacje o tożsamości i jej działania, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 W razie potrzeby można dostosować weryfikacji przy użyciu weryfikatora tożsamości niestandardowej. Na przykład można wykonać testy weryfikacji tożsamości dodatkowych usług. W tym przykładzie weryfikatora tożsamość niestandardowa sprawdza dodatkowe oświadczeń w certyfikatu X.509 zwrócone z serwera. Przykładową aplikację, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Aby rozszerzyć klasy właściwość EndpointIdentity elementu  
  
1.  Zdefiniuj nową klasę, która jest pochodną <xref:System.ServiceModel.EndpointIdentity> klasy. W tym przykładzie nazwy rozszerzenia `OrgEndpointIdentity`.  
  
2.  Dodawanie członków prywatnych oraz właściwości, które będą używane przez rozszerzony <xref:System.ServiceModel.Security.IdentityVerifier> klasy można przeprowadzić sprawdzenia tożsamości przed oświadczenia w tokenie zabezpieczającym zwrócony przez usługę. W tym przykładzie zdefiniowano jedną właściwość: `OrganizationClaim` właściwości.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Aby rozszerzyć klasy IdentityVerifier  
  
1.  Zdefiniuj nową klasę, która jest pochodną <xref:System.ServiceModel.Security.IdentityVerifier>. W tym przykładzie nazwy rozszerzenia `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Zastąpienie <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody. Metoda określa, czy sprawdzić tożsamości powodzeniem lub niepowodzeniem.  
  
3.  `CheckAccess` Metoda ma dwa parametry. Pierwsza to wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy. Drugim jest wystąpieniem <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
     W implementacji metody, sprawdź kolekcji oświadczeń zwrócony przez <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> klasy, a następnie automatycznie uwierzytelniające zgodnie z potrzebami. Ten przykład rozpoczyna się od znajdowanie oświadczenie jest typu "Nazwy wyróżniającej", a następnie porównuje Nazwa rozszerzenia <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Aby zaimplementować metodę TryGetIdentity  
  
1.  Implementowanie <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metodę, która określa, czy wystąpienie <xref:System.ServiceModel.EndpointIdentity> klasy może być zwracany przez klienta. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury wymaga wykonania `TryGetIdentity` metodę, aby najpierw pobrać tożsamości usługi z komunikatu. Następnie wywołuje infrastruktury `CheckAccess` implementację zwróconego `EndpointIdentity` i <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  W `TryGetIdentity` metodę, umieść następujący kod:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Do wdrażania niestandardowego powiązania i ustawić IdentityVerifier niestandardowych  
  
1.  Tworzenie metody, która zwraca <xref:System.ServiceModel.Channels.Binding> obiektu. Rozpoczyna się w tym przykładzie tworzy wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustawia jej tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>, a jego <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> do <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Utwórz <xref:System.ServiceModel.Channels.BindingElementCollection> przy użyciu <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3.  Zwraca <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekcji i rzutować obiekt <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zmiennej.  
  
4.  Ustaw <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> właściwość <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> klasę, aby nowe wystąpienie klasy `CustomIdentityVerifier` klasy utworzone wcześniej.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  Niestandardowego powiązania, który jest zwracany jest używany do utworzenia wystąpienia klienta i klasy. Klient następnie można przeprowadzić weryfikacji tożsamości niestandardowej usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pełną implementację <xref:System.ServiceModel.Security.IdentityVerifier> klasy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pełną implementację <xref:System.ServiceModel.EndpointIdentity> klasy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Zasady autoryzacji](../../../../docs/framework/wcf/samples/authorization-policy.md)
