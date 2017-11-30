---
title: 'Instrukcje: Tworzenie tokenu niestandardowego'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cdcb6d48fe3da9bf63dc1a97bfab1743dc78a3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-token"></a>Instrukcje: Tworzenie tokenu niestandardowego
W tym temacie przedstawiono sposób tworzenia tokenu zabezpieczeń niestandardowych przy użyciu <xref:System.IdentityModel.Tokens.SecurityToken> klasy i jak zintegrować ją z dostawcy tokenów zabezpieczających niestandardowych i wystawcy uwierzytelnienia. Pełny przykład kodu dla [niestandardowy Token](../../../../docs/framework/wcf/samples/custom-token.md) próbki.  
  
 A *tokenu zabezpieczającego* jest zasadniczo element XML, który jest używany przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework zabezpieczeń do reprezentowania oświadczenia dotyczące nadawcy wiadomości protokołu SOAP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]funkcja zabezpieczenia oferuje różne tokenów do tryby uwierzytelniania dostarczane przez system. Przykłady obejmują tokenu zabezpieczającego certyfikatu X.509 reprezentowany przez <xref:System.IdentityModel.Tokens.X509SecurityToken> klasy lub tokenu zabezpieczającego nazwy użytkownika reprezentowanego przez <xref:System.IdentityModel.Tokens.UserNameSecurityToken> klasy.  
  
 Czasami tryb uwierzytelniania lub poświadczenia nie jest obsługiwany przez udostępnionych typów. W takim przypadku jest niezbędne do utworzenia tokenu zabezpieczającego niestandardowych zapewnienie reprezentację XML niestandardowego poświadczenia wewnątrz komunikatu protokołu SOAP.  
  
 W poniższych procedurach przedstawiono sposób tworzenia tokenu zabezpieczającego niestandardowych oraz sposób zintegrować ją z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpieczeń. W tym temacie tworzy token karty kredytowej, który jest używany do przekazywania informacji o karcie kredytowej klienta do serwera.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]niestandardowe poświadczenia i Menedżer tokenów zabezpieczających, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Zobacz <xref:System.IdentityModel.Tokens> przestrzeń nazw dla innych klas, które reprezentują tokenów zabezpieczających.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]poświadczenia, Menedżer tokenów zabezpieczających oraz klasy dostawcy i uwierzytelniania, zobacz [Architektura zabezpieczeń](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
## <a name="procedures"></a>Procedury  
 Aplikacja kliencka muszą być wyposażone w sposób, aby określić informacje o karcie kredytowej infrastruktury zabezpieczeń. Te informacje były dostępne dla aplikacji przez klasę poświadczeń klienta. Pierwszym krokiem jest można utworzyć klasy do reprezentowania informacje o karcie kredytowej dla poświadczeń klienta.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Aby utworzyć klasę, która reprezentuje informacje o karcie kredytowej wewnątrz poświadczeń klienta  
  
1.  Zdefiniuj nową klasę, która reprezentuje informacje o karcie kredytowej dla aplikacji. Poniższy przykład nazwy klasy `CreditCardInfo`.  
  
2.  Dodaj odpowiednie właściwości do klasy, aby zezwolić informacji wymaganych dla tokenu niestandardowego zestawu aplikacji. W tym przykładzie klasa ma trzy właściwości: `CardNumber`, `CardIssuer`, i `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Następnie należy utworzyć Klasa reprezentująca token zabezpieczający niestandardowych. Ta klasa jest używana przez token dostawcy uwierzytelniania i serializator klasy zabezpieczeń do przekazywania informacji o tokenie zabezpieczeń do i z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpieczeń.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Aby utworzyć klasę tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.SecurityToken> klasy. W tym przykładzie tworzy klasę o nazwie `CreditCardToken`.  
  
2.  Zastąpienie <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> właściwości. Ta właściwość jest używana, aby określić lokalny identyfikator tokenu zabezpieczeń, który służy do punktu na jej reprezentację XML tokenu zabezpieczeń z innymi elementami wewnątrz komunikatu protokołu SOAP. W tym przykładzie identyfikatora tokenu może być przekazany do niego jako parametru konstruktora lub nową losowe jest generowana za każdym razem, gdy jest tworzone wystąpienie tokenu zabezpieczeń.  
  
3.  Implementowanie <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwości. Ta właściwość zwraca kolekcję kluczy zabezpieczeń, które reprezentuje wystąpienie tokenu zabezpieczeń. Te klucze mogą być używane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do podpisywania lub szyfrowania części komunikatu protokołu SOAP. W tym przykładzie tokenu zabezpieczającego karty kredytowej nie może zawierać żadnych kluczy zabezpieczeń; w związku z tym zawsze implementacja zwraca pustą kolekcję.  
  
4.  Zastąpienie <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> i <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> właściwości. Te właściwości są używane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do sprawdzania poprawności wystąpienia tokenu zabezpieczeń. W tym przykładzie karty kredytowej tokenu zabezpieczeń ma tylko datę wygaśnięcia, więc `ValidFrom` zwraca <xref:System.DateTime> reprezentujący datę i godzinę utworzenia wystąpienia.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Gdy nowy zabezpieczający typ tokenu jest tworzony, wymaga wykonania <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Implementacja jest używana w Konfiguracja elementu powiązania zabezpieczeń do reprezentowania nowy typ tokenu. Klasa Parametry tokenu zabezpieczeń służy jako szablon, który jest używany do dopasowywania wystąpienie tokenu zabezpieczeń rzeczywiste do, gdy komunikat jest przetwarzany. Szablon zawiera dodatkowe właściwości, które aplikacji można użyć do określenia kryteriów, które tokenu zabezpieczającego muszą być zgodne do użycia lub uwierzytelniony. Poniższy przykład nie dodaje żadnych dodatkowych właściwości tylko dopasowaniu typ tokenu zabezpieczeń podczas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury wyszukuje wystąpienie tokenu zabezpieczeń do użycia, lub do sprawdzania poprawności.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Aby utworzyć klasę Parametry tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy.  
  
2.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metody. Skopiuj wszystkie pola wewnętrznego zdefiniowany w klasie, jeśli istnieje. W tym przykładzie nie definiuje żadnych dodatkowych pól.  
  
3.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> właściwości tylko do odczytu. Ta właściwość zwraca `true` Jeśli typ tokenu zabezpieczeń reprezentowanego przez tę klasę może służyć do uwierzytelniania klienta do usługi. W tym przykładzie tokenu zabezpieczającego karty kredytowej może służyć do uwierzytelniania klienta do usługi.  
  
4.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> właściwości tylko do odczytu. Ta właściwość zwraca `true` Jeśli typ tokenu zabezpieczeń reprezentowanego przez tę klasę może służyć do uwierzytelniania usługi na kliencie. W tym przykładzie tokenu zabezpieczającego karty kredytowej nie może służyć do uwierzytelniania usługi na kliencie.  
  
5.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> właściwości tylko do odczytu. Ta właściwość zwraca `true` Jeśli reprezentowanego przez tę klasę typ tokenu zabezpieczeń mogą być mapowane na konta systemu Windows. Jeśli tak, wynik uwierzytelniania jest reprezentowana przez <xref:System.Security.Principal.WindowsIdentity> wystąpienie klasy. W tym przykładzie token nie można zamapować na konto systemu Windows.  
  
6.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metody. Ta metoda jest wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń platformę, gdy wymaga odwołania do wystąpienia tokenu zabezpieczeń reprezentowanego przez tę klasę Parametry tokenu zabezpieczeń. Zarówno rzeczywiste zabezpieczeń tokenu wystąpienie i <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> , który określa typ odwołania, który jest wymagany są przekazywane do tej metody jako argumenty. W tym przykładzie tylko wewnętrzne odwołania są obsługiwane przez karty kredytowej tokenu zabezpieczającego. <xref:System.IdentityModel.Tokens.SecurityToken> Klasa ma funkcje do tworzenia odwołań wewnętrzny; w związku z tym implementacja nie wymaga dodatkowego kodu.  
  
7.  Implementowanie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metody. Ta metoda jest wywoływana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przekonwertować zabezpieczeń wystąpienie do wystąpienia klasy Parametry tokenu <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> klasy. Aby utworzyć wystąpienie tokenu zabezpieczeń odpowiednich przez dostawców tokenów zabezpieczeń zostanie użyty wynik.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpieczające są przesyłane w wiadomości SOAP, które wymaga mechanizm tłumaczenia między reprezentacja tokenu zabezpieczeń w pamięci i reprezentacja w locie. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa Serializator tokenu zabezpieczającego, aby wykonać to zadanie. Każdy token niestandardowy musi towarzyszyć Serializator tokenu zabezpieczającego niestandardowych, które mogą serializacji i deserializacji tokenu zabezpieczającego niestandardowych z komunikatu protokołu SOAP.  
  
> [!NOTE]
>  Pochodne klucze są domyślnie włączone. Jeśli utworzysz tokenu zabezpieczającego niestandardowych i używać go jako token podstawowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pochodną klucza. Podczas tej czynności wywołuje niestandardowy Serializator tokenu zabezpieczającego zapisu <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> dla tokenu zabezpieczającego niestandardowych podczas serializowania `DerivedKeyToken` można przewodowo. Na stronie odbierającej, podczas deserializacji tokenu poza umieszczonego w sieci `DerivedKeyToken` Serializator oczekuje `SecurityTokenReference` element jako element podrzędny najwyższego poziomu w samej siebie. Jeśli nie dodano Serializator tokenu zabezpieczającego niestandardowych `SecurityTokenReference` elementu podczas serializowania jego typ klauzuli, jest zgłaszany wyjątek.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Aby utworzyć serializatora tokenu zabezpieczeń niestandardowych  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> klasy.  
  
2.  Zastąpienie <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> metodę, która zależy od <xref:System.Xml.XmlReader> odczytywać strumień XML. Metoda zwraca `true` jeśli implementacja serializator może wykonywać deserializację na podstawie tokenu zabezpieczającego nadać jej bieżącego elementu. W tym przykładzie ta metoda sprawdza, czy bieżący obiektu odczytującego XML — element XML ma element poprawną nazwę i przestrzeń nazw. Jeśli nie, wywołuje metodę Implementacja klasy podstawowej tę metodę w celu obsługi elementu XML.  
  
3.  Zastąpienie <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metody. Ta metoda odczytuje zawartość XML tokenu zabezpieczającego i tworzy odpowiednie reprezentacji w pamięci dla niego. Jeśli nie rozpoznaje elementu XML, na którym jest stały przekazany czytnika XML, wywołuje metodę implementację klasy podstawowej, aby przetworzyć typy tokenów dostarczane przez system.  
  
4.  Zastąpienie <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda zwraca `true` Jeśli umożliwia on konwertowanie reprezentacja tokenu w pamięci (przekazany jako argument) na końcu reprezentacji XML. Jeśli nie można dokonać konwersji, wywołuje metodę implementacji klasy podstawowej.  
  
5.  Zastąpienie <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda konwertuje reprezentacja tokenu zabezpieczeń w pamięci w reprezentacji XML. Jeśli metoda nie może dokonać konwersji, wywołuje metodę implementacji klasy podstawowej.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Po zakończeniu cztery poprzedniej procedury, integracja tokenu zabezpieczającego niestandardowych z dostawcy tokenów zabezpieczających, uwierzytelniania, Menedżer i poświadczeń klienta i usługi.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Token zabezpieczający niestandardowy jest integrowana z dostawcy tokenów zabezpieczających  
  
1.  Dostawcy tokenów zabezpieczających tworzy, modyfikuje (w razie potrzeby) i zwraca wystąpienie tokenu. Można utworzyć niestandardowego dostawcę dla tokenu zabezpieczającego niestandardowych, Utwórz klasę, która dziedziczy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> sposób zwrócenia wystąpienia klasy `CreditCardToken`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dostawcy tokenów zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego dostawcy tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Token zabezpieczający niestandardowy jest integrowana z wystawcę uwierzytelnienia tokenów zabezpieczających  
  
1.  Sprawdza poprawność zawartości tokenu zabezpieczającego wystawcę uwierzytelnienia tokenów zabezpieczających, gdy został wyodrębniony z komunikatu. Aby utworzyć niestandardowego wystawcy uwierzytelnienia tokenu zabezpieczającego niestandardowych, Utwórz klasę, która dziedziczy po <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metody. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych, zobacz [porady: Tworzenie niestandardowego wystawcę uwierzytelnienia tokenów zabezpieczających](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Token zabezpieczający niestandardowy jest integrowana z Menedżer tokenów zabezpieczających  
  
1.  Menedżer tokenów zabezpieczających tworzy odpowiedniego dostawcy tokenów zabezpieczeń uwierzytelniania i wystąpień serializatora tokenu. Aby utworzyć niestandardowe Menedżer tokenów, należy utworzyć klasę, która dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy. Podstawowe metody Użyj klasy <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> do utworzenia odpowiedniego dostawcy i poświadczeń klienta lub usługi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Menedżerowie tokenu zabezpieczeń niestandardowych, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Token zabezpieczający niestandardowy jest integrowana z niestandardowego klienta i poświadczeń usługi  
  
1.  Niestandardowe klienta i poświadczeń usługi muszą zostać dodane do dostarczać interfejs API do pozwala na stosowanie niestandardowych informacji o tokenie używanego przez infrastrukturę tokenu zabezpieczeń niestandardowe utworzone wcześniej do udostępniania i uwierzytelniania niestandardowego zabezpieczeń aplikacji Token zawartość. Poniższe przykłady pokazują, jak to zrobić. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]niestandardowe klienta i poświadczenia usługi, zobacz [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Klasa Parametry tokenu zabezpieczeń niestandardowe utworzone wcześniej umożliwia Poinformuj [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework zabezpieczeń tokenu zabezpieczającego niestandardowy musi być używany podczas komunikacji z usługą. W poniższej procedurze wyjaśniono, jak to zrobić.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Integracja z powiązaniem tokenu zabezpieczającego niestandardowych  
  
1.  Klasa Parametry tokenu zabezpieczeń niestandardowych musi być określony w jednej z kolekcji Parametry tokenu, które są dostępne w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. W poniższym przykładzie użyto kolekcji zwróconej przez `SignedEncrypted`. Ten kod dodaje niestandardowy token karty kredytowej do każdej wiadomości wysłanych z klienta do usługi z zawartością automatycznie podpisane i zaszyfrowane.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 W tym temacie przedstawiono niezbędne do zaimplementowania i użycia niestandardowy token różnych fragmentów kodu. Aby wyświetlić pełny przykład tego, jak te fragmenty kodu dopasowania, zobacz [niestandardowy Token](../../../../docs/framework/wcf/samples/custom-token.md).  
  
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
 [Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Porady: tworzenie wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
