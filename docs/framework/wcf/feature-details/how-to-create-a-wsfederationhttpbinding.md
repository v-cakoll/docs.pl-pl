---
title: 'Instrukcje: Tworzenie WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: c3ce90c74ae61dfcbfc0b05fc17b25fe0118e071
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141693"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Instrukcje: Tworzenie WSFederationHttpBinding

W Windows Communication Foundation (WCF) Klasa <xref:System.ServiceModel.WSFederationHttpBinding> ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) zapewnia mechanizm ujawniania usługi federacyjnej. Oznacza to, że usługa, która wymaga od klientów uwierzytelnienia przy użyciu tokenu zabezpieczającego wystawionego przez usługę tokenu zabezpieczającego. W tym temacie przedstawiono sposób konfigurowania <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie i konfiguracji. Po utworzeniu powiązania można skonfigurować punkt końcowy do korzystania z tego powiązania.

 Podstawowe kroki zostały opisane w następujący sposób:

1. Wybierz tryb zabezpieczeń. <xref:System.ServiceModel.WSFederationHttpBinding> obsługuje `Message`, która zapewnia kompleksowe zabezpieczenia na poziomie komunikatów, nawet w wielu przeskokach i `TransportWithMessageCredential`, co zapewnia lepszą wydajność w przypadkach, gdy klient i usługa mogą nawiązać bezpośrednie połączenie za pośrednictwem protokołu HTTPS.

    > [!NOTE]
    > <xref:System.ServiceModel.WSFederationHttpBinding> obsługuje również `None` jako tryb zabezpieczeń. Ten tryb nie jest zabezpieczony i jest udostępniany tylko do celów debugowania. Jeśli punkt końcowy usługi został wdrożony z <xref:System.ServiceModel.WSFederationHttpBinding> z trybem zabezpieczeń ustawionym na `None`, powstałe powiązanie klienta (generowane przez [Narzędzie do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) jest <xref:System.ServiceModel.WSHttpBinding> z trybem zabezpieczeń `None`.

     W przeciwieństwie do innych powiązań dostarczonych przez system nie należy wybierać typu poświadczeń klienta podczas korzystania z `WSFederationHttpBinding`. Wynika to z faktu, że typ poświadczeń klienta jest zawsze wystawiony token. Usługa WCF uzyskuje token od określonego wystawcy i przedstawia ten token usłudze w celu uwierzytelnienia klienta.

2. Na klientach federacyjnych ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> na adres URL usługi tokenu zabezpieczającego. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> na powiązanie, które ma być używane do komunikacji z usługą tokenu zabezpieczającego.

3. Opcjonalny. Ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> na Uniform Resource Identifier (URI) typu tokenu. W obszarze Usługi federacyjne Określ typ tokenu oczekiwany przez usługę. W przypadku klientów federacyjnych Określ token typu żądania klientów z usługi tokenu zabezpieczającego.

     Jeśli typ tokenu nie zostanie określony, klienci generują tokeny zabezpieczające żądania WS-Trust (RSTs) bez identyfikatora URI typu tokenu, a usługi domyślnie oczekują na uwierzytelnianie klienta przy użyciu tokenu potwierdzeń zabezpieczeń (SAML) 1,1.

     Identyfikator URI dla tokenu SAML 1,1 jest `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcjonalny. W usługach federacyjnych ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> na adres URL metadanych usługi tokenu zabezpieczającego. Punkt końcowy metadanych umożliwia klientom usługi wybór odpowiedniej pary powiązań/punktów końcowych, jeśli usługa jest skonfigurowana do publikowania metadanych. Aby uzyskać więcej informacji na temat publikowania metadanych, zobacz [Publikowanie metadanych](publishing-metadata.md).

 Można również ustawić inne właściwości, w tym typ klucza używany jako klucz dowodu w wystawionym tokenie, pakiet algorytmów, który ma być używany między klientem a usługą, zarówno w przypadku negocjowania, jak i jawnego określenia poświadczeń usługi, wszelkich określonych oświadczeń usługi oczekuje, że wystawiony token zawiera, i wszelkie dodatkowe elementy XML, które należy dodać do żądania wysyłanego przez klienta do usługi tokenu zabezpieczającego.

> [!NOTE]
> Właściwość `NegotiateServiceCredential` ma zastosowanie tylko wtedy, gdy `SecurityMode` jest ustawiona na `Message`. Jeśli `SecurityMode` jest ustawiona na `TransportWithMessageCredential`, właściwość `NegotiateServiceCredential` jest ignorowana.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Aby skonfigurować WSFederationHttpBinding w kodzie

1. Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding>.

2. W razie potrzeby ustaw właściwość <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> na <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>. Jeśli wymagany jest pakiet algorytmów inny niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A>, należy ustawić właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> na wartość pobraną z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Ustaw odpowiednio Właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A>.

4. Ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> na <xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey` lub.`AsymmetricKey` zgodnie z potrzebami.

5. Ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> na odpowiednią wartość. Jeśli wartość nie jest ustawiona, program WCF domyślnie `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, co wskazuje tokeny SAML 1,1.

6. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz <xref:System.ServiceModel.EndpointAddress>, który zawiera informacje o adresie i tożsamości usługi tokenu zabezpieczającego, a następnie przypisz wystąpienie <xref:System.ServiceModel.EndpointAddress> do właściwości <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A>.

7. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. Utwórz <xref:System.ServiceModel.Channels.Binding> dla `SecurityTokenService` i przypisz wystąpienie <xref:System.ServiceModel.Channels.Binding> do właściwości <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>.

8. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz wystąpienie <xref:System.ServiceModel.EndpointAddress> dla metadanych usługi tokenu zabezpieczającego i przypisz je do właściwości `IssuerMetadataAddress`.

9. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj co najmniej jedno wystąpienie <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> do kolekcji zwróconej przez właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>.

10. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj co najmniej jedno wystąpienie <xref:System.Xml.XmlElement> do kolekcji zwróconej przez właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Aby utworzyć federacyjny punkt końcowy w konfiguracji

1. Utwórz [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako element podrzędny [\<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) w pliku konfiguracyjnym aplikacji.

2. Utwórz [\<powiązania >](../../configure-apps/file-schema/wcf/bindings.md) jako element podrzędny [\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i ustaw odpowiednią wartość atrybutu `name`.

3. Utwórz `<security>` elementu jako element podrzędny elementu [\<powiązania >](../../configure-apps/file-schema/wcf/bindings.md) .

4. W razie potrzeby ustaw atrybut `mode` w elemencie `<security>` na wartość `Message` lub `TransportWithMessageCredential`.

5. Utwórz `<message>` elementu jako element podrzędny elementu `<security>`.

6. Opcjonalny. Ustaw atrybut `algorithmSuite` dla elementu `<message>` z odpowiednią wartością. Wartość domyślna to `Basic256`.

7. Opcjonalny. Jeśli klucz dowodu asymetrycznego jest wymagany, ustaw atrybut `issuedKeyType` elementu `<message>` na `AsymmetricKey`. Wartość domyślna to `SymmetricKey`.

8. Opcjonalny. Ustaw atrybut `issuedTokenType` dla elementu `<message>`.

9. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz `<issuer>` elementu jako element podrzędny elementu `<message>`.

10. Ustaw atrybut `address` na element `<issuer>` i określ adres, pod którym usługa tokenu zabezpieczającego akceptuje żądania tokenów.

11. Opcjonalny. Dodawanie `<identity>` elementu podrzędnego i Określanie tożsamości usługi tokenu zabezpieczającego

12. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](service-identity-and-authentication.md).

13. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. Utwórz element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) w sekcji powiązania, którego można użyć do komunikowania się z usługą tokenu zabezpieczającego. Aby uzyskać więcej informacji na temat tworzenia powiązań, zobacz [How to: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Określ powiązanie utworzone w poprzednim kroku, ustawiając atrybuty `binding` i `bindingConfiguration` elementu `<issuer>`.

15. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz `<issuerMetadata>` elementu jako element podrzędny <`message`> elementu. Następnie w atrybucie `address` elementu `<issuerMetadata>` Określ adres, pod którym usługa tokenu zabezpieczającego ma publikować swoje metadane. Opcjonalnie dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.

16. Opcjonalne zarówno na kliencie, jak i w usłudze. Dodaj `<claimTypeRequirements>` elementu jako element podrzędny elementu `<message>`. Określ wymagane i opcjonalne oświadczenia, na których bazuje usługa, dodając [\<dodać elementy >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) do elementu `<claimTypeRequirements>` i określić typ oświadczenia przy użyciu atrybutu `claimType`. Określ, czy podane żądanie jest wymagane, czy opcjonalne, ustawiając atrybut `isOptional`.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje kod służący do samodzielnego konfigurowania `WSFederationHttpBinding`.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Federacja](federation.md)
- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
