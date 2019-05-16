---
title: 'Instrukcje: tworzenie elementu WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: 3a6564683a856c8d1eb47b1569f156e0b6d5cc67
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636417"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Instrukcje: tworzenie elementu WSFederationHttpBinding

W konsoli Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> klasy ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) udostępnia mechanizm do udostępniania usługi federacyjnej. Oznacza to, to usługa, która wymaga od klientów do uwierzytelniania za pomocą tokenu zabezpieczającego wydane przez usługę tokenu zabezpieczającego. W tym temacie pokazano, jak skonfigurować <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie i konfiguracji. Po utworzeniu powiązania, możesz skonfigurować punkt końcowy, aby użyć tego powiązania.

 Podstawowe kroki przedstawione poniżej:

1. Wybierz tryb zabezpieczeń. <xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje `Message`, end-to-end zabezpieczenia na poziomie komunikatu, który zapewnia nawet przez kilka przeskoków, i `TransportWithMessageCredential`, który zapewnia lepszą wydajność w przypadkach, w której klient i usługa może tworzyć bezpośrednie połączenie za pośrednictwem PROTOKÓŁ HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje również `None` jako tryb zabezpieczeń. Ten tryb nie jest bezpieczna i znajduje się tylko do celów debugowania. Jeśli punkt końcowy usługi jest wdrożona za pomocą <xref:System.ServiceModel.WSFederationHttpBinding> jego tryb zabezpieczeń ustawiono na `None`, wynikowy klienta powiązania (generowane przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) jest <xref:System.ServiceModel.WSHttpBinding> z Tryb zabezpieczeń `None`.

     W przeciwieństwie do innych powiązań dostarczanych przez system nie jest konieczne wybieranie typu poświadczeń klienta, korzystając z `WSFederationHttpBinding`. Jest to spowodowane typu poświadczeń klienta jest zawsze wystawiony token. Usługi WCF uzyskuje token z określonego wystawcę i przedstawia ten token do usługi do uwierzytelniania klienta.

2. Na komputerach klienckich federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwość adres URL usługi tokenu zabezpieczającego. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> do powiązania w celu użycia do komunikowania się z usługi tokenu zabezpieczającego.

3. Opcjonalna. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> właściwości do identyfikatora URI (Uniform Resource) typu tokenu. W usługach federacyjnych należy określić typ tokenu, który oczekuje, że usługa. Na klientach federacyjnych należy określić typ tokenu żądania klientów z usługi tokenu zabezpieczającego.

     Jeśli żaden typ tokenu jest określony, klientów generuje tokeny zabezpieczające żądania protokołu WS-Trust (RSTs) bez typ tokenu identyfikatora URI, i usług oczekują uwierzytelniania klienta przy użyciu tokenu zabezpieczeń potwierdzenia Markup Language (SAML) 1.1 domyślnie.

     Identyfikator URI dla tokenu języka SAML 1.1 jest `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcjonalna. W usługach federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> właściwości adresu URL metadanych usługi tokenu zabezpieczającego. Punkt końcowy metadanych umożliwia klientom usługi wybierz pary odpowiednie powiązanie/punktu końcowego, jeśli usługa jest skonfigurowana do publikowania metadanych. Aby uzyskać więcej informacji na temat publikowania metadanych, zobacz [Publikowanie metadanych](publishing-metadata.md).

 Można również ustawić inne właściwości, takie jak typ klucz używany jako klucza na dowód wystawiony token pakiet algorytmów, używać między klientem a service, czy do negocjowania lub jawnie określ poświadczenia usługi, żadnych szczególnych oświadczeń usługi oczekuje, że wystawiony token zawierał i wszelkie dodatkowe elementy XML, które muszą zostać dodane do żądania, które klient wysyła do usługi tokenu zabezpieczającego.

> [!NOTE]
>  `NegotiateServiceCredential` Właściwość ma zastosowanie tylko wtedy gdy `SecurityMode` ustawiono `Message`. Jeśli `SecurityMode` ustawiono `TransportWithMessageCredential`, a następnie `NegotiateServiceCredential` właściwość jest ignorowana.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Aby skonfigurować elementu WSFederationHttpBinding w kodzie

1. Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Ustaw <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> stosownie do potrzeb. Jeśli pakiet algorytmów innych niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> jest to konieczne, ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> właściwość z wartością pobranego z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości zgodnie z potrzebami.

4. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> właściwości <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` lub.`AsymmetricKey` zgodnie z wymaganiami.

5. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> właściwość odpowiednią wartość. Jeśli zostanie ustawiona żadna wartość, WCF, wartość domyślna to `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, co oznacza tokeny SAML 1.1.

6. Wymagany na kliencie, jeśli nie wystawcy lokalnego jest określona; Opcjonalnie w usłudze. Tworzenie <xref:System.ServiceModel.EndpointAddress> zawierający informacje dotyczące adresów i tożsamość usługi tokenów zabezpieczeń i przypisz <xref:System.ServiceModel.EndpointAddress> wystąpienia do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwości.

7. Wymagany na kliencie, jeśli nie wystawcy lokalnego jest określona; nie należy używać w usłudze. Tworzenie <xref:System.ServiceModel.Channels.Binding> dla `SecurityTokenService` i przypisać <xref:System.ServiceModel.Channels.Binding> wystąpienia do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> właściwości.

8. Nie używany przez klienta; Opcjonalnie w usłudze. Tworzenie <xref:System.ServiceModel.EndpointAddress> wystąpienie metadanych usługi tokenu zabezpieczeń i przypisz ją do `IssuerMetadataAddress` właściwości.

9. Opcjonalnie zarówno klient, jak i usługi. Utwórz i Dodaj co najmniej jeden <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> właściwości.

10. Opcjonalnie zarówno klient, jak i usługi. Utwórz i Dodaj co najmniej jeden <xref:System.Xml.XmlElement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> właściwości.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Aby utworzyć federacyjny punkt końcowy w konfiguracji

1. Tworzenie [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako element podrzędny elementu [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracyjnym aplikacji.

2. Tworzenie [ \<powiązania >](../../../../docs/framework/misc/binding.md) element jako element podrzędny elementu [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i ustaw `name` atrybutu do odpowiedniej wartości.

3. Tworzenie `<security>` element jako element podrzędny elementu [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.

4. Ustaw `mode` atrybutu na `<security>` element na wartość `Message` lub `TransportWithMessageCredential`, co jest wymagane.

5. Tworzenie `<message>` element jako element podrzędny elementu `<security>` elementu.

6. Opcjonalna. Ustaw `algorithmSuite` atrybutu na `<message>` element odpowiednią wartość. Wartość domyślna to `Basic256`.

7. Opcjonalna. Jeśli wymagana jest dowód klucza asymetrycznego, ustaw `issuedKeyType` atrybutu `<message>` elementu `AsymmetricKey`. Wartość domyślna to `SymmetricKey`.

8. Opcjonalna. Ustaw `issuedTokenType` atrybutu na `<message>` elementu.

9. Wymagany na kliencie, jeśli nie wystawcy lokalnego jest określona; Opcjonalnie w usłudze. Tworzenie `<issuer>` element jako element podrzędny elementu `<message>` elementu.

10. Ustaw `address` atrybutu `<issuer>` elementu i określ adres, w którym usługa tokenu zabezpieczającego akceptuje żądania tokenu.

11. Opcjonalna. Dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenów zabezpieczeń

12. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usług](service-identity-and-authentication.md).

13. Wymagany na kliencie, jeśli nie wystawcy lokalnego jest określona; nie należy używać w usłudze. Tworzenie [ \<powiązania >](../../../../docs/framework/misc/binding.md) element w sekcji powiązania, który może służyć do komunikowania się z usługi tokenu zabezpieczającego. Aby uzyskać więcej informacji na temat tworzenia powiązania, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Określanie wiązań utworzony w poprzednim kroku, ustawiając `binding` i `bindingConfiguration` atrybuty `<issuer>` elementu.

15. Nie używany przez klienta; Opcjonalnie w usłudze. Tworzenie `<issuerMetadata>` element jako element podrzędny <`message`> element. Następnie w `address` atrybutu na `<issuerMetadata>` elementu, określ adres, jaką jest opublikowanie jej metadanych usługi tokenu zabezpieczającego. Opcjonalnie dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.

16. Opcjonalnie zarówno klient, jak i usługi. Dodaj `<claimTypeRequirements>` element jako element podrzędny elementu `<message>` elementu. Określ wymaganych i opcjonalnych oświadczeń która zależy od usługi, dodając [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementów `<claimTypeRequirements>` elementu i określając oświadczenie to typ `claimType` atrybutu. Określ, czy dany oświadczeń jest wymagane lub opcjonalne, ustawiając `isOptional` atrybutu.

## <a name="example"></a>Przykład

Poniższy przykład kodu zawiera kod konfigurowania `WSFederationHttpBinding` obowiązkowo.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Federacja](federation.md)
- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
