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
ms.openlocfilehash: ccc28c46e8be0b835cf08d372ef85b8a66e989ef
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595443"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Instrukcje: tworzenie elementu WSFederationHttpBinding

W Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> Klasa ( [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) zapewnia mechanizm ujawniania usługi federacyjnej. Oznacza to, że usługa, która wymaga od klientów uwierzytelnienia przy użyciu tokenu zabezpieczającego wystawionego przez usługę tokenu zabezpieczającego. W tym temacie pokazano, jak skonfigurować <xref:System.ServiceModel.WSFederationHttpBinding> zarówno kod, jak i konfigurację. Po utworzeniu powiązania można skonfigurować punkt końcowy do korzystania z tego powiązania.

 Podstawowe kroki zostały opisane w następujący sposób:

1. Wybierz tryb zabezpieczeń. <xref:System.ServiceModel.WSFederationHttpBinding>Obsługuje `Message` , która zapewnia kompleksowe zabezpieczenia na poziomie komunikatu, nawet dla wielu przeskoków, i `TransportWithMessageCredential` , co zapewnia lepszą wydajność w przypadkach, gdy klient i usługa mogą nawiązać bezpośrednie połączenie za pośrednictwem protokołu HTTPS.

    > [!NOTE]
    > Program <xref:System.ServiceModel.WSFederationHttpBinding> obsługuje również `None` tryb zabezpieczeń. Ten tryb nie jest zabezpieczony i jest udostępniany tylko do celów debugowania. Jeśli punkt końcowy usługi został wdrożony z <xref:System.ServiceModel.WSFederationHttpBinding> trybem zabezpieczeń ustawionym na `None` , wyniki powiązania klienta (generowane przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)) są <xref:System.ServiceModel.WSHttpBinding> z trybem zabezpieczeń `None` .

     W przeciwieństwie do innych powiązań dostarczonych przez system nie trzeba wybierać typu poświadczeń klienta podczas korzystania z `WSFederationHttpBinding` . Wynika to z faktu, że typ poświadczeń klienta jest zawsze wystawiony token. Usługa WCF uzyskuje token od określonego wystawcy i przedstawia ten token usłudze w celu uwierzytelnienia klienta.

2. Na klientach federacyjnych Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> Właściwość na adres URL usługi tokenu zabezpieczającego. Ustaw wartość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> na powiązanie, które ma być używane do komunikacji z usługą tokenu zabezpieczającego.

3. Opcjonalny. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Właściwość na Uniform Resource Identifier (URI) typu tokenu. W obszarze Usługi federacyjne Określ typ tokenu oczekiwany przez usługę. W przypadku klientów federacyjnych Określ token typu żądania klientów z usługi tokenu zabezpieczającego.

     Jeśli typ tokenu nie zostanie określony, klienci generują tokeny zabezpieczające żądania WS-Trust (RSTs) bez identyfikatora URI typu tokenu, a usługi domyślnie oczekują na uwierzytelnianie klienta przy użyciu tokenu potwierdzeń zabezpieczeń (SAML) 1,1.

     Identyfikator URI dla tokenu SAML 1,1 to `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .

4. Opcjonalny. W usługach federacyjnych Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> Właściwość na adres URL metadanych usługi tokenu zabezpieczającego. Punkt końcowy metadanych umożliwia klientom usługi wybór odpowiedniej pary powiązań/punktów końcowych, jeśli usługa jest skonfigurowana do publikowania metadanych. Aby uzyskać więcej informacji na temat publikowania metadanych, zobacz [Publikowanie metadanych](publishing-metadata.md).

 Można również ustawić inne właściwości, w tym typ klucza używany jako klucz dowodu w wystawionym tokenie, pakiet algorytmów, który ma być używany między klientem a usługą, czy ma być negocjowane lub jawnie określone poświadczenie usługi, wszelkie specyficzne oświadczenia usługi oczekują, że wystawiony token zawiera, i wszelkie dodatkowe elementy XML, które należy dodać do żądania wysyłanego przez klienta do usługi tokenu zabezpieczające

> [!NOTE]
> `NegotiateServiceCredential`Właściwość ma zastosowanie tylko wtedy, gdy `SecurityMode` jest ustawiona na `Message` . Jeśli `SecurityMode` jest ustawiona na `TransportWithMessageCredential` , `NegotiateServiceCredential` Właściwość jest ignorowana.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Aby skonfigurować WSFederationHttpBinding w kodzie

1. Utwórz wystąpienie elementu <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Ustaw <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> Właściwość na <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub zgodnie z <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> wymaganiami. Jeśli pakiet algorytmów inny niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> jest wymagany, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> Właściwość na wartość pobieraną z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .

3. Ustaw właściwość stosownie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> potrzeb.

4. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> Właściwość na <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` lub.`AsymmetricKey` zgodnie z potrzebami.

5. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Właściwość na odpowiednią wartość. Jeśli wartość nie jest ustawiona, program WCF domyślnie `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` określa tokeny SAML 1,1.

6. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz element zawierający <xref:System.ServiceModel.EndpointAddress> Informacje o adresie i tożsamości usługi tokenu zabezpieczającego i przypisz <xref:System.ServiceModel.EndpointAddress> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwości.

7. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. Utwórz <xref:System.ServiceModel.Channels.Binding> dla `SecurityTokenService` i przypisz <xref:System.ServiceModel.Channels.Binding> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> właściwości.

8. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz <xref:System.ServiceModel.EndpointAddress> wystąpienie metadanych usługi tokenu zabezpieczającego i przypisz je do `IssuerMetadataAddress` właściwości.

9. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj jedno lub więcej <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> wystąpień do kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> Właściwość.

10. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj jedno lub więcej <xref:System.Xml.XmlElement> wystąpień do kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> Właściwość.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Aby utworzyć federacyjny punkt końcowy w konfiguracji

1. Utwórz [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako element podrzędny [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracyjnym aplikacji.

2. Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element jako obiekt podrzędny [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i ustaw `name` odpowiednią wartość atrybutu.

3. Utwórz `<security>` element jako obiekt podrzędny [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu.

4. Ustaw `mode` atrybut dla elementu na `<security>` wartość `Message` lub `TransportWithMessageCredential` , zgodnie z potrzebami.

5. Utwórz `<message>` element jako obiekt podrzędny `<security>` elementu.

6. Opcjonalny. Ustaw `algorithmSuite` atrybut dla `<message>` elementu z odpowiednią wartością. Wartość domyślna to `Basic256`.

7. Opcjonalny. Jeśli klucz dowodu asymetrycznego jest wymagany, ustaw `issuedKeyType` atrybut `<message>` elementu na `AsymmetricKey` . Wartość domyślna to `SymmetricKey`.

8. Opcjonalny. Ustaw `issuedTokenType` atrybut w `<message>` elemencie.

9. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz `<issuer>` element jako obiekt podrzędny `<message>` elementu.

10. Ustaw `address` atrybut na `<issuer>` element i określ adres, pod którym usługa tokenu zabezpieczającego akceptuje żądania tokenów.

11. Opcjonalny. Dodawanie `<identity>` elementu podrzędnego i Określanie tożsamości usługi tokenu zabezpieczającego

12. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](service-identity-and-authentication.md).

13. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. Utwórz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element w sekcji powiązań, którego można użyć do komunikowania się z usługą tokenu zabezpieczającego. Aby uzyskać więcej informacji na temat tworzenia powiązań, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).

14. Określ powiązanie utworzone w poprzednim kroku, ustawiając `binding` `bindingConfiguration` atrybuty i `<issuer>` elementu.

15. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz `<issuerMetadata>` element jako obiekt podrzędny `message`> <elementu. Następnie w `address` atrybucie `<issuerMetadata>` elementu Określ adres, pod którym usługa tokenu zabezpieczającego ma publikować swoje metadane. Opcjonalnie Dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.

16. Opcjonalne zarówno na kliencie, jak i w usłudze. Dodaj `<claimTypeRequirements>` element jako obiekt podrzędny `<message>` elementu. Określ wymagane i opcjonalne oświadczenia, na których opiera się usługa przez dodanie [\<add>](../../configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementów do `<claimTypeRequirements>` elementu i określenie typu oświadczenia z `claimType` atrybutem. Określ, czy podane żądanie jest wymagane, czy opcjonalne, ustawiając `isOptional` atrybut.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje kod służący do samodzielnego konfigurowania `WSFederationHttpBinding` .

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Zobacz też

- [Federacja](federation.md)
- [Federacja — przykład](../samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
