---
title: 'Instrukcje: tworzenie tokenu niestandardowego'
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
ms.openlocfilehash: 917278ef990842f2ce821474ffd1c6cd619ed289
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951778"
---
# <a name="how-to-create-a-custom-token"></a>Instrukcje: tworzenie tokenu niestandardowego
W tym temacie pokazano, jak utworzyć niestandardowy token zabezpieczający przy użyciu <xref:System.IdentityModel.Tokens.SecurityToken> klasy oraz jak zintegrować go z niestandardowym dostawcą tokenu zabezpieczeń i wystawcą uwierzytelnienia. Aby zapoznać się z kompletnym przykładem kodu, zapoznaj się z przykładem [niestandardowego tokenu](../../../../docs/framework/wcf/samples/custom-token.md) .  
  
 *Token zabezpieczający* jest zasadniczo elementem XML, który jest używany przez strukturę zabezpieczeń Windows Communication Foundation (WCF) do reprezentowania oświadczeń dotyczących nadawcy w komunikacie protokołu SOAP. Zabezpieczenia WCF udostępniają różne tokeny dla trybów uwierzytelniania dostępnych w systemie. Przykłady obejmują token zabezpieczający certyfikat X. 509 reprezentowany przez <xref:System.IdentityModel.Tokens.X509SecurityToken> klasę lub token zabezpieczający nazwy użytkownika reprezentowany <xref:System.IdentityModel.Tokens.UserNameSecurityToken> przez klasę.  
  
 Czasami tryb uwierzytelniania lub poświadczenia nie są obsługiwane przez udostępniane typy. W takim przypadku konieczne jest utworzenie niestandardowego tokenu zabezpieczającego, aby zapewnić reprezentację w formacie XML niestandardowego poświadczenia w komunikacie protokołu SOAP.  
  
 W poniższych procedurach pokazano, jak utworzyć niestandardowy token zabezpieczający i jak zintegrować go z infrastrukturą zabezpieczeń WCF. W tym temacie opisano Tworzenie tokenu karty kredytowej, który służy do przekazywania informacji o karcie kredytowej klienta na serwer.  
  
 Aby uzyskać więcej informacji na temat poświadczeń niestandardowych i Menedżera tokenów [zabezpieczających, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
 Zapoznaj <xref:System.IdentityModel.Tokens> się z przestrzenią nazw, aby poznać więcej klas, które reprezentują tokeny zabezpieczające.  
  
## <a name="procedures"></a>Procedury  
 Aplikacja kliencka musi być dostępna ze sposobem, aby określić informacje dotyczące karty kredytowej dla infrastruktury zabezpieczeń. Te informacje są udostępniane aplikacji przez niestandardową klasę poświadczeń klienta. Pierwszym krokiem jest utworzenie klasy do reprezentowania informacji o karcie kredytowej dla niestandardowych poświadczeń klienta.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Aby utworzyć klasę reprezentującą informacje o karcie kredytowej w poświadczeniach klienta  
  
1. Zdefiniuj nową klasę, która reprezentuje informacje o karcie kredytowej dla aplikacji. Poniższy przykład nazywa nazwę klasy `CreditCardInfo`.  
  
2. Dodaj odpowiednie właściwości do klasy, aby zezwolić aplikacji na zestaw niezbędnych informacji wymaganych przez Token niestandardowy. W tym przykładzie Klasa ma trzy właściwości: `CardNumber`, `CardIssuer`, i `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Następnie należy utworzyć klasę, która reprezentuje niestandardowy token zabezpieczający. Ta klasa jest używana przez dostawcę tokenów zabezpieczających, wystawca i klasy serializatorów do przekazywania informacji o tokenie zabezpieczającym do i z infrastruktury zabezpieczeń WCF.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Aby utworzyć niestandardową klasę tokenów zabezpieczających  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Tokens.SecurityToken> klasy. Ten przykład tworzy klasę o nazwie `CreditCardToken`.  
  
2. Zastąp <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> właściwość. Ta właściwość służy do uzyskiwania identyfikatora lokalnego tokenu zabezpieczającego, który służy do wskazywania reprezentacji XML tokenu zabezpieczającego z innych elementów w komunikacie protokołu SOAP. W tym przykładzie Identyfikator tokenu może być przesłany do niego jako parametr konstruktora lub nowy losowo jeden jest generowany za każdym razem, gdy tworzone jest wystąpienie tokenu zabezpieczeń.  
  
3. Zaimplementuj <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> właściwość. Ta właściwość zwraca kolekcję kluczy zabezpieczeń, które reprezentuje wystąpienie tokenu zabezpieczającego. Takie klucze mogą być używane przez funkcję WCF do podpisywania lub szyfrowania części wiadomości protokołu SOAP. W tym przykładzie token zabezpieczający karty kredytowej nie może zawierać żadnych kluczy zabezpieczeń; w związku z tym implementacja zawsze zwraca pustą kolekcję.  
  
4. Zastąp właściwości <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A>i. <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> Te właściwości są używane przez program WCF do określania ważności wystąpienia tokenu zabezpieczającego. W tym przykładzie token zabezpieczający karty kredytowej ma tylko datę wygaśnięcia, więc `ValidFrom` Właściwość <xref:System.DateTime> zwraca wartość reprezentującą datę i godzinę tworzenia wystąpienia.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 Gdy tworzony jest nowy typ tokenu zabezpieczającego, wymaga implementacji <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Implementacja jest używana w konfiguracji elementu powiązania zabezpieczeń, aby reprezentować nowy typ tokenu. Klasa parametrów tokenu zabezpieczającego służy jako szablon, który jest używany w celu dopasowania do rzeczywistego wystąpienia tokenu zabezpieczającego do momentu przetworzenia komunikatu. Szablon zawiera dodatkowe właściwości, których aplikacja może użyć do określenia kryteriów, które muszą być zgodne z tokenem zabezpieczający, aby można było go używać lub uwierzytelniać. Poniższy przykład nie dodaje żadnych dodatkowych właściwości, więc tylko typ tokenu zabezpieczającego jest dopasowywany, gdy Infrastruktura WCF szuka wystąpienia tokenu zabezpieczającego do użycia lub do walidacji.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Aby utworzyć niestandardową klasę parametrów tokenu zabezpieczającego  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy.  
  
2. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> metodę. Skopiuj wszystkie pola wewnętrzne zdefiniowane w klasie, jeśli istnieją. W tym przykładzie nie są zdefiniowane żadne dodatkowe pola.  
  
3. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` wartość, jeśli typ tokenu zabezpieczającego reprezentowany przez tę klasę może służyć do uwierzytelniania klienta w usłudze. W tym przykładzie token zabezpieczający karty kredytowej może służyć do uwierzytelniania klienta w usłudze.  
  
4. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` wartość, jeśli typ tokenu zabezpieczającego reprezentowany przez tę klasę może być używany do uwierzytelniania usługi dla klienta. W tym przykładzie token zabezpieczający karty kredytowej nie może zostać użyty do uwierzytelnienia usługi dla klienta.  
  
5. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> właściwość tylko do odczytu. Ta właściwość zwraca `true` wartość, jeśli typ tokenu zabezpieczającego reprezentowanego przez tę klasę można zamapować na konto systemu Windows. W takim przypadku wynik uwierzytelniania jest reprezentowany przez <xref:System.Security.Principal.WindowsIdentity> wystąpienie klasy. W tym przykładzie nie można zamapować tokenu na konto systemu Windows.  
  
6. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> metodę. Ta metoda jest wywoływana przez strukturę zabezpieczeń WCF, gdy wymaga odwołania do wystąpienia tokenu zabezpieczającego reprezentowanego przez tę klasę parametrów tokenu zabezpieczającego. Zarówno rzeczywiste wystąpienie tokenu zabezpieczającego, <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> jak i typ żądanego odwołania są przekazane do tej metody jako argumenty. W tym przykładzie tylko odwołania wewnętrzne są obsługiwane przez token zabezpieczający karty kredytowej. <xref:System.IdentityModel.Tokens.SecurityToken> Klasa ma funkcje do tworzenia odwołań wewnętrznych; w związku z tym implementacja nie wymaga dodatkowego kodu.  
  
7. Zaimplementuj <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metodę. Ta metoda jest wywoływana przez funkcję WCF w celu konwertowania wystąpienia klasy parametrów tokenu zabezpieczającego na wystąpienie <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> klasy. Ten wynik jest używany przez dostawców tokenów zabezpieczających do utworzenia odpowiedniego wystąpienia tokenu zabezpieczającego.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Tokeny zabezpieczające są przesyłane wewnątrz komunikatów protokołu SOAP, co wymaga mechanizmu tłumaczenia między reprezentacją tokenu zabezpieczającego w pamięci a reprezentacją w sieci. Aby wykonać to zadanie, WCF używa serializatora tokenów zabezpieczających. Każdy token niestandardowy musi być dołączony do niestandardowego serializatora tokenu zabezpieczającego, który może serializować i zdeserializować niestandardowego tokenu zabezpieczającego z komunikatu protokołu SOAP.  
  
> [!NOTE]
> Klucze pochodne są domyślnie włączone. Jeśli utworzysz niestandardowy token zabezpieczający i użyjesz go jako tokenu podstawowego, WCF poniesie klucz od tego. Podczas wykonywania tej operacji wywołuje serializator niestandardowego tokenu zabezpieczeń, aby napisać <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> dla niestandardowego tokenu zabezpieczającego podczas serializacji `DerivedKeyToken` do sieci. W przypadku zakończenia deserializacji tokenu `DerivedKeyToken` z sieci na końcu, serializator oczekuje `SecurityTokenReference` elementu jako element podrzędny najwyższego poziomu w sobie. Jeśli serializator niestandardowego tokenu zabezpieczającego nie dodał `SecurityTokenReference` elementu podczas serializowania jego typu klauzuli, zgłaszany jest wyjątek.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Aby utworzyć serializator niestandardowego tokenu zabezpieczającego  
  
1. Zdefiniuj nową klasę pochodną <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> klasy.  
  
2. <xref:System.Xml.XmlReader> Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> metodę, która polega na odczytaniu strumienia XML. Metoda zwraca `true` , jeśli implementacja serializatora może deserializować token zabezpieczający na podstawie podaną w jego bieżącym elemencie. W tym przykładzie metoda sprawdza, czy bieżący element XML czytnika XML ma poprawną nazwę elementu i przestrzeń nazw. Jeśli tak nie jest, wywołuje implementację klasy bazowej tej metody do obsługi elementu XML.  
  
3. Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> metody. Ta metoda odczytuje zawartość XML tokenu zabezpieczającego i konstruuje odpowiednią reprezentację w pamięci. Jeśli nie rozpoznaje elementu XML, w którym znajduje się przekazanego czytnika XML, wywołuje implementację klasy podstawowej w celu przetworzenia typów tokenów dostarczonych przez system.  
  
4. Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda zwraca `true` czy można skonwertować reprezentację tokenu w pamięci (przekazaną jako argument) na reprezentację w formacie XML. Jeśli nie można skonwertować, wywoła implementację klasy bazowej.  
  
5. Zastąp <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> metody. Ta metoda konwertuje reprezentację tokenu zabezpieczeń w pamięci na reprezentację w formacie XML. Jeśli metoda nie może konwertować, wywołuje implementację klasy bazowej.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 Po wykonaniu czterech powyższych procedur Zintegruj niestandardowy token zabezpieczający z dostawcą tokenu zabezpieczeń, wystawcą uwierzytelnienia, menedżerem oraz poświadczeniami usługi i klienta.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Aby zintegrować niestandardowy token zabezpieczeń z dostawcą tokenów zabezpieczających  
  
1. Dostawca tokenów zabezpieczających tworzy, modyfikuje (w razie potrzeby) i zwraca wystąpienie tokenu. Aby utworzyć niestandardowego dostawcę dla niestandardowego tokenu zabezpieczeń, Utwórz klasę, która dziedziczy z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> metodę zwracającą wystąpienie `CreditCardToken`elementu. Aby uzyskać więcej informacji o dostawcach niestandardowych tokenów [zabezpieczających, zobacz How to: Utwórz niestandardowego dostawcę](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)tokenów zabezpieczających.  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Aby zintegrować niestandardowy token zabezpieczeń z wystawcą uwierzytelnienia tokenu zabezpieczającego  
  
1. Wystawca uwierzytelnienia tokenów zabezpieczających weryfikuje zawartość tokenu zabezpieczającego, gdy zostanie wyodrębniony z wiadomości. Aby utworzyć niestandardową wystawcę uwierzytelniania dla niestandardowego tokenu zabezpieczeń, Utwórz klasę, która dziedziczy <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> z klasy. Poniższy przykład zastępuje <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> metodę. Aby uzyskać więcej informacji na temat wystawców niestandardowych tokenów [zabezpieczających, zobacz How to: Tworzenie niestandardowego wystawcy uwierzytelnienia](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)tokenu zabezpieczeń.  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Aby zintegrować niestandardowy token zabezpieczeń z menedżerem tokenów zabezpieczających  
  
1. Menedżer tokenów zabezpieczających tworzy odpowiedniego dostawcę tokenu, wystawcę uwierzytelnienia zabezpieczeń i wystąpienia serializatorów tokenów. Aby utworzyć niestandardowego menedżera tokenów, Utwórz klasę, która dziedziczy z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy. Podstawowe metody klasy wykorzystują <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> do tworzenia odpowiednich poświadczeń dostawcy i klienta lub usługi. Aby uzyskać więcej informacji na temat niestandardowych menedżerów tokenów zabezpieczających, zobacz [Przewodnik: Tworzenie niestandardowych poświadczeń](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Aby zintegrować niestandardowy token zabezpieczający z niestandardowym klientem i poświadczeniami usługi  
  
1. Niestandardowe poświadczenia klienta i usługi należy dodać, aby udostępnić interfejs API dla aplikacji, aby umożliwić określenie niestandardowych informacji o tokenach, które są używane przez infrastrukturę niestandardowego tokenu zabezpieczeń, która została wcześniej utworzona w celu zapewnienia i uwierzytelniania zabezpieczeń niestandardowych. zawartość tokenu. W poniższych przykładach pokazano, jak to zrobić. Aby uzyskać więcej informacji na temat niestandardowych poświadczeń klienta i usługi [, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Wcześniej utworzona Klasa parametrów niestandardowego tokenu zabezpieczającego służy do informowania struktury zabezpieczeń WCF o konieczności użycia niestandardowego tokenu zabezpieczającego podczas komunikacji z usługą. W poniższej procedurze pokazano, jak to zrobić.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Aby zintegrować niestandardowy token zabezpieczający z powiązaniem  
  
1. Klasa parametrów niestandardowego tokenu zabezpieczającego musi być określona w jednej z kolekcji parametrów tokenu, które są uwidocznione w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasie. Poniższy przykład używa kolekcji zwróconej przez `SignedEncrypted`. Kod dodaje niestandardowy token karty kredytowej do każdej wiadomości wysyłanej z klienta do usługi z zawartością, która została automatycznie podpisana i zaszyfrowana.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 W tym temacie przedstawiono różne fragmenty kodu niezbędne do zaimplementowania i użycia niestandardowego tokenu. Aby zobaczyć kompletny przykład dopasowania wszystkich tych fragmentów kodu, zobacz [Token niestandardowy](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Instrukcje: Tworzenie niestandardowego wystawcy uwierzytelniania tokenu zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
