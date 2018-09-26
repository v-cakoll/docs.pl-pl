---
title: 'Instrukcje: Tworzenie tokenu niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: fd168bf2e5233d9119872b267aea466a7af07041
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199271"
---
# <a name="how-to-create-a-custom-token"></a>Instrukcje: Tworzenie tokenu niestandardowego
W tym temacie pokazano, jak utworzyć token zabezpieczeń niestandardowych przy użyciu <xref:System.IdentityModel.Tokens.SecurityToken> klasy i jak ją zintegrować z niestandardowego dostawcy tokenów zabezpieczeń i uwierzytelniania. Aby uzyskać pełny przykład kodu zobacz [niestandardowy Token](../../../../docs/framework/wcf/samples/custom-token.md) próbki.  
  
 A *token zabezpieczający* jest zasadniczo element XML, który jest używany przez środowisko zabezpieczeń usługi Windows Communication Foundation (WCF) do reprezentowania oświadczeń o nadawcy w wiadomości protokołu SOAP. Zabezpieczenia WCF zapewnia tokenów różne tryby uwierzytelniania dostarczane przez system. Przykłady obejmują tokenu zabezpieczeń certyfikatu X.509, reprezentowane przez <xref:System.IdentityModel.Tokens.X509SecurityToken> klasy lub token zabezpieczający Username reprezentowany przez <xref:System.IdentityModel.Tokens.UserNameSecurityToken> klasy.  
  
 Czasami tryb uwierzytelniania lub poświadczeń nie jest obsługiwana przez podane typy. W takim przypadku należy utworzyć token zabezpieczający niestandardowe, aby zapewnić reprezentację XML niestandardowe poświadczenia wewnątrz komunikatu protokołu SOAP.  
  
 Poniższe procedury pokazują, jak utworzyć token zabezpieczający niestandardowych i jak ją zintegrować z infrastruktura zabezpieczeń programu WCF. W tym temacie tworzy token karty kredytowej, który jest używany do przekazywania informacji dotyczących karty kredytowej klienta na serwerze.  
  
 Aby uzyskać więcej informacji na temat niestandardowych poświadczeń i Menedżer tokenów zabezpieczeń, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Zobacz <xref:System.IdentityModel.Tokens> przestrzeń nazw dla innych klas, które reprezentują tokenów zabezpieczających.  
  
 Aby uzyskać więcej informacji na temat klasy dostawcy i wystawcy uwierzytelnienia poświadczeń, Menedżer tokenów zabezpieczeń i zobacz [architekturę zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
 Aplikacja kliencka muszą być wyposażone w sposób określania informacji o karcie kredytowej dla infrastruktura zabezpieczeń. Te informacje staje się dostępny do aplikacji przez klasę poświadczenia niestandardowego klienta. Pierwszym krokiem jest utworzenie klasy do reprezentowania informacje dotyczące kart kredytowych klientów niestandardowych poświadczeń.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Aby utworzyć klasę, która reprezentuje informacje o karcie kredytowej wewnątrz poświadczeń klienta  
  
1.  Definiowanie nowej klasy, która reprezentuje informacje o karcie kredytowej dla aplikacji. Poniższy przykład nazwy klasy `CreditCardInfo`.  
  
2.  Dodaj odpowiednie właściwości do klasy, aby zezwolić informacji wymaganych do tokenu niestandardowego zestawu aplikacji. W tym przykładzie klasa ma trzy właściwości: `CardNumber`, `CardIssuer`, i `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Następnie należy utworzyć klasa, która reprezentuje token zabezpieczający niestandardowych. Ta klasa jest używana w dostawcy tokenów zabezpieczeń wystawcy uwierzytelnienia, a klasy serializatora do przekazywania informacji na temat token zabezpieczający, do i z usługi WCF infrastruktura zabezpieczeń.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Aby utworzyć klasę tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.SecurityToken> klasy. W tym przykładzie tworzy klasę o nazwie `CreditCardToken`.  
  
2.  Zastąp <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> właściwości. Ta właściwość jest używana, aby uzyskać identyfikator lokalny token zabezpieczający, który jest używany do wskaż reprezentację XML tokenu zabezpieczeń z innymi elementami wewnątrz komunikatu protokołu SOAP. W tym przykładzie identyfikatora tokenu można albo przekazać do niego jako parametr konstruktora lub nową losową jest generowana za każdym razem, gdy tworzone jest wystąpienie tokenu zabezpieczeń.  
  
3.  Implementowanie <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwości. Ta właściwość zwraca kolekcję kluczy zabezpieczeń, które reprezentuje wystąpienie tokenu zabezpieczeń. Te klucze może służyć przez architekturę WCF do podpisywania lub szyfrowania części komunikatu protokołu SOAP. W tym przykładzie token zabezpieczający karta kredytowa nie może zawierać żadnych kluczy zabezpieczeń; Dlatego implementacja zawsze zwraca pustą kolekcję.  
  
4.  Zastąp <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> i <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> właściwości. Te właściwości są używane przez architekturę WCF do sprawdzania poprawności wystąpienia tokenu zabezpieczeń. W tym przykładzie token zabezpieczający karty kredytowej ma tylko datę wygaśnięcia, więc `ValidFrom` właściwość zwraca <xref:System.DateTime> reprezentujący datę i godzinę utworzenia wystąpienia.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Gdy nowych zabezpieczeń, który jest tworzony typ tokenu, wymaga implementacji <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Implementacja jest używana w konfiguracji elementu powiązania zabezpieczeń do reprezentowania nowy typ tokenu. Klasa Parametry tokenu zabezpieczeń służy jako szablon, który jest używany do dopasowywania wystąpienie tokenu zabezpieczeń rzeczywiste do, gdy komunikat jest przetwarzany. Szablon zawiera dodatkowe właściwości, które aplikacja może użyć użytkownikowi określić kryteria, które muszą być zgodne do użycia lub uwierzytelnienia tokenu zabezpieczającego. Poniższy przykład nie można dodać żadnych dodatkowych właściwości, tylko dopasowaniu typu tokenu, gdy infrastruktura WCF wyszukuje wystąpienie tokenu zabezpieczeń do użycia lub do sprawdzania poprawności zabezpieczeń.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Aby utworzyć klasę parametrów tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy.  
  
2.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metody. Skopiuj wszystkie wewnętrzne pola zdefiniowane w klasie, jeśli istnieje. W tym przykładzie definiuje dodatkowe pola.  
  
3.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` Jeśli typ tokenu zabezpieczeń, reprezentowane przez tę klasę, może służyć do uwierzytelniania klienta do usługi. W tym przykładzie token zabezpieczający karty kredytowej może służyć do uwierzytelniania klienta do usługi.  
  
4.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` Jeśli typ tokenu zabezpieczeń, reprezentowane przez tę klasę, może służyć do uwierzytelniania usługi do klienta. W tym przykładzie token zabezpieczający karty kredytowej nie może służyć do uwierzytelniania usługi do klienta.  
  
5.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` Jeśli typ tokenu zabezpieczeń, reprezentowane przez tę klasę, mogą być mapowane na konta Windows. Jeśli tak, wynik uwierzytelniania jest reprezentowany przez <xref:System.Security.Principal.WindowsIdentity> wystąpienia klasy. W tym przykładzie token nie można mapować do konta Windows.  
  
6.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metody. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF, jeśli wymaga to dodania odwołania do wystąpienia tokenu zabezpieczeń, reprezentowane przez tę klasę parametrów tokenu zabezpieczeń. Obie rzeczywiste zabezpieczeń tokenu wystąpienia i <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> określający typ odwołania, która jest wymagana są przekazywane do tej metody jako argumenty. W tym przykładzie tylko wewnętrzne odwołania są obsługiwane przez karty kredytowej tokenu zabezpieczającego. <xref:System.IdentityModel.Tokens.SecurityToken> Klasa ma funkcje do tworzenia wewnętrznego odwołań; w związku z tym, implementacja nie wymaga dodatkowego kodu.  
  
7.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metody. Ta metoda jest wywoływana przez architekturę WCF, aby przekonwertować wystąpienie klasy parametrów tokenu zabezpieczeń wystąpienia <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> klasy. Aby utworzyć wystąpienie tokenu zabezpieczeń odpowiednich przez dostawcy tokenów zabezpieczeń zostanie użyty wynik.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpieczające są przekazywane wewnątrz wiadomości protokołu SOAP, które wymaga mechanizm tłumaczenia między reprezentacja tokenu zabezpieczeń w pamięci i reprezentacji w locie. WCF używa serializatora tokenu zabezpieczeń, aby wykonać to zadanie. Każdy niestandardowy token musi towarzyszyć Serializator tokenu zabezpieczeń niestandardowych, które mogą serializacji i deserializacji tokenu zabezpieczającego niestandardowe, z komunikatu protokołu SOAP.  
  
> [!NOTE]
>  Kluczy pochodnych są domyślnie włączone. Jeśli utworzyć token zabezpieczający niestandardowe i używać go jako token podstawowy klucz WCF wywodzi się z niego. Podczas tej czynności wywołuje niestandardowy Serializator tokenu zabezpieczeń do zapisania <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> dla tokenu zabezpieczającego niestandardowych podczas serializowania `DerivedKeyToken` do sieci. Na stronie odbierającej podczas deserializacji token wyłączone podczas transmisji `DerivedKeyToken` Serializator oczekuje `SecurityTokenReference` element jako element podrzędny najwyższego poziomu formantowi. Jeśli zabezpieczeń niestandardowy Serializator tokenów nie dodano `SecurityTokenReference` elementu podczas serializowania jego typ klauzuli, zgłaszany jest wyjątek.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Aby utworzyć element serializujący tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> klasy.  
  
2.  Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> metody, która opiera się na <xref:System.Xml.XmlReader> można odczytać strumienia XML. Metoda ta zwraca `true` jeśli implementacja serializator może wykonywać deserializację token zabezpieczający, na podstawie nadać jej bieżącego elementu. W tym przykładzie ta metoda sprawdza, czy bieżącego użytkownika odczytującego XML — element XML ma poprawne nazwy i przestrzeni nazw. Jeśli nie, wywołuje metodę implementacji klasy podstawowej tę metodę w celu obsługi elementu XML.  
  
3.  Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metody. Ta metoda odczytuje zawartość XML tokenu zabezpieczającego i tworzy odpowiedni reprezentacji w pamięci dla niego. Jeśli nie rozpoznaje element XML, na którym jest stały przekazywane odczytującego XML, wywołuje metodę implementacji klasy podstawowej do przetworzenia dostarczane przez system typy tokenów.  
  
4.  Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda zwraca `true` Jeśli umożliwia on konwertowanie reprezentacji tokenu w pamięci (przekazanego jako argument) do reprezentacji XML. Jeśli nie można dokonać konwersji, wywołuje metodę implementacji klasy podstawowej.  
  
5.  Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda konwertuje reprezentacji tokenu zabezpieczeń w pamięci na reprezentację XML. Jeśli metoda nie może przekonwertować, wywołuje metodę implementacji klasy podstawowej.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Po wykonaniu poprzednich czterech procedur, integracja token zabezpieczający niestandardowego dostawcy tokenów zabezpieczeń wystawcy uwierzytelnienia, Menedżer i poświadczeń klienta i usługi.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Aby zintegrować token zabezpieczający niestandardowe z dostawcy tokenów zabezpieczeń  
  
1.  Dostawcy tokenów zabezpieczeń tworzy, modyfikuje (w razie potrzeby) i zwraca wystąpienie tokenu. Aby utworzyć niestandardowego dostawcę dla tokenu zabezpieczającego niestandardowe, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metodę, aby zwrócić wystąpienia `CreditCardToken`. Aby uzyskać więcej informacji na temat dostawcy tokenów zabezpieczeń niestandardowe zobacz [porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Aby zintegrować token zabezpieczający niestandardowe z wystawcy uwierzytelniania tokenu zabezpieczeń  
  
1.  Wystawcy uwierzytelniania tokenu zabezpieczeń sprawdza poprawność zawartości tokenu zabezpieczającego, gdy jest wyodrębniany z komunikatu. Aby Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowe, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. Aby uzyskać więcej informacji na temat wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych zobacz [porady: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Aby zintegrować token zabezpieczający niestandardowe z usługą Menedżer tokenów zabezpieczeń  
  
1.  Menedżer tokenów zabezpieczeń tworzy odpowiedniego dostawcy tokenów zabezpieczeń uwierzytelniania i wystąpień Serializator tokenów. Aby utworzyć niestandardowe Menedżer tokenów, należy utworzyć klasę, która dziedziczy po elemencie <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy. Podstawowe metody używania klasy <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> do utworzenia odpowiedniego dostawcy i poświadczeń klienta lub usługę. Aby uzyskać więcej informacji na temat menedżerów tokenu zabezpieczeń niestandardowe zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Aby zintegrować token zabezpieczający niestandardowych za pomocą niestandardowego klienta i poświadczeń usługi  
  
1.  Niestandardowego klienta i poświadczeń usługi muszą zostać dodane do dostarczać interfejs API dla aplikacji umożliwić określenie niestandardowych tokenu informacje, które są używane przez infrastrukturę tokenu zabezpieczeń niestandardowych został wcześniej utworzony do udostępniania i uwierzytelnianie niestandardowe zabezpieczeń zawartość tokenu. Poniższe przykłady pokazują, jak można to zrobić. Aby uzyskać więcej informacji na temat niestandardowego klienta i poświadczeń usługi, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Klasa Parametry tokenu zabezpieczeń niestandardowych utworzone wcześniej umożliwia poinformować szablon zabezpieczeń WCF, czy token zabezpieczający niestandardowych należy użyć podczas komunikowania się z usługą. Poniższa procedura pokazuje, jak można to zrobić.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Aby zintegrować token zabezpieczający niestandardowe wraz z powiązaną  
  
1.  Klasa Parametry tokenu zabezpieczeń niestandardowy musi być określony w jednej z kolekcji parametrów tokenu, które są dostępne w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. W poniższym przykładzie użyto zbiorze zwróconym przez `SignedEncrypted`. Ten kod dodaje niestandardowy token karty kredytowej do każdej wiadomości wysłanych z klienta do usługi z jego zawartością automatycznie podpisane i szyfrowane.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 W tym temacie przedstawiono niezbędne do zaimplementowania i użycia tokenu niestandardowego różnych fragmentów kodu. Aby zobaczyć pełny przykład jak wszystkie te fragmenty kodu współdziałają ze sobą, zobacz [niestandardowy Token](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Tokens.SecurityToken>  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>  
 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Przewodnik: tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Instrukcje: tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Instrukcje: tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
