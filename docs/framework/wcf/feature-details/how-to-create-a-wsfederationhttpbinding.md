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
ms.openlocfilehash: 9728c908331d5eabcff04d094e7fcbe42f636963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911219"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Instrukcje: tworzenie elementu WSFederationHttpBinding

W Windows Communication Foundation (WCF) <xref:System.ServiceModel.WSFederationHttpBinding> Klasa ([\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) zapewnia mechanizm ujawniania usługi federacyjnej. Oznacza to, że usługa, która wymaga od klientów uwierzytelnienia przy użyciu tokenu zabezpieczającego wystawionego przez usługę tokenu zabezpieczającego. <xref:System.ServiceModel.WSFederationHttpBinding> W tym temacie pokazano, jak skonfigurować zarówno kod, jak i konfigurację. Po utworzeniu powiązania można skonfigurować punkt końcowy do korzystania z tego powiązania.

 Podstawowe kroki zostały opisane w następujący sposób:

1. Wybierz tryb zabezpieczeń. Obsługa, która zapewnia kompleksowe zabezpieczenia na poziomie wiadomości, nawet w wielu przeskokach, i `TransportWithMessageCredential`, która zapewnia lepszą wydajność w przypadkach, gdy klient i usługa mogą nawiązać bezpośrednie połączenie `Message` <xref:System.ServiceModel.WSFederationHttpBinding> Schemat.

    > [!NOTE]
    > Program <xref:System.ServiceModel.WSFederationHttpBinding> obsługuje`None` również tryb zabezpieczeń. Ten tryb nie jest zabezpieczony i jest udostępniany tylko do celów debugowania. Jeśli punkt końcowy usługi został wdrożony z <xref:System.ServiceModel.WSFederationHttpBinding> trybem zabezpieczeń ustawionym na `None`, wyniki powiązania klienta (generowane przez narzędzie do obsługi <xref:System.ServiceModel.WSHttpBinding> [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) są z trybem `None`zabezpieczeń.

     W przeciwieństwie do innych powiązań dostarczonych przez system nie trzeba wybierać typu poświadczeń klienta podczas korzystania z `WSFederationHttpBinding`. Wynika to z faktu, że typ poświadczeń klienta jest zawsze wystawiony token. Usługa WCF uzyskuje token od określonego wystawcy i przedstawia ten token usłudze w celu uwierzytelnienia klienta.

2. Na klientach federacyjnych Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwość na adres URL usługi tokenu zabezpieczającego. Ustaw wartość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> na powiązanie, które ma być używane do komunikacji z usługą tokenu zabezpieczającego.

3. Opcjonalny. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Ustaw właściwość na Uniform Resource Identifier (URI) typu tokenu. W obszarze Usługi federacyjne Określ typ tokenu oczekiwany przez usługę. W przypadku klientów federacyjnych Określ token typu żądania klientów z usługi tokenu zabezpieczającego.

     Jeśli typ tokenu nie zostanie określony, klienci generują tokeny zabezpieczające żądania WS-Trust (RSTs) bez identyfikatora URI typu tokenu, a usługi domyślnie oczekują na uwierzytelnianie klienta przy użyciu tokenu potwierdzeń zabezpieczeń (SAML) 1,1.

     Identyfikator URI dla tokenu SAML 1,1 to `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcjonalny. W usługach federacyjnych Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> właściwość na adres URL metadanych usługi tokenu zabezpieczającego. Punkt końcowy metadanych umożliwia klientom usługi wybór odpowiedniej pary powiązań/punktów końcowych, jeśli usługa jest skonfigurowana do publikowania metadanych. Aby uzyskać więcej informacji na temat publikowania metadanych, zobacz [Publikowanie metadanych](publishing-metadata.md).

 Można również ustawić inne właściwości, w tym typ klucza używany jako klucz dowodu w wystawionym tokenie, pakiet algorytmów, który ma być używany między klientem a usługą, zarówno w przypadku negocjowania, jak i jawnego określenia poświadczeń usługi, wszelkich określonych oświadczeń usługi oczekuje, że wystawiony token zawiera, i wszelkie dodatkowe elementy XML, które należy dodać do żądania wysyłanego przez klienta do usługi tokenu zabezpieczającego.

> [!NOTE]
> Właściwość ma zastosowanie tylko wtedy, `SecurityMode` gdy jest ustawiona na `Message`. `NegotiateServiceCredential` Jeśli `SecurityMode` jest ustawiona na `TransportWithMessageCredential`, `NegotiateServiceCredential` właściwość jest ignorowana.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Aby skonfigurować WSFederationHttpBinding w kodzie

1. Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding>obiektu.

2. Ustaw właściwość <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> na <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> zgodnie z wymaganiami. Jeśli pakiet algorytmów inny niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> jest wymagany, należy <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> ustawić właściwość na wartość pobieraną z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Ustaw właściwość <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> stosownie do potrzeb.

4. <xref:System.IdentityModel.Tokens.SecurityKeyType> Ustaw właściwość na`SymmetricKey` lub. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A>`AsymmetricKey` zgodnie z potrzebami.

5. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> Ustaw właściwość na odpowiednią wartość. Jeśli wartość nie jest ustawiona, program WCF domyślnie `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`określa tokeny SAML 1,1.

6. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz element <xref:System.ServiceModel.EndpointAddress> zawierający informacje o adresie i tożsamości usługi tokenu zabezpieczającego i <xref:System.ServiceModel.EndpointAddress> Przypisz wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwości.

7. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. <xref:System.ServiceModel.Channels.Binding> Utwórz dla`SecurityTokenService` i<xref:System.ServiceModel.Channels.Binding> Przypisz wystąpienie do właściwości.<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>

8. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz wystąpienie metadanych usługi tokenu zabezpieczającego i przypisz je `IssuerMetadataAddress` do właściwości. <xref:System.ServiceModel.EndpointAddress>

9. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj jedno lub więcej <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> wystąpień do kolekcji zwróconej <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> przez właściwość.

10. Opcjonalne zarówno na kliencie, jak i w usłudze. Utwórz i Dodaj jedno lub więcej <xref:System.Xml.XmlElement> wystąpień do kolekcji zwróconej <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> przez właściwość.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Aby utworzyć federacyjny punkt końcowy w konfiguracji

1. Utwórz WSFederationHttpBinding > jako element podrzędny [ \<> powiązania](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) w pliku konfiguracyjnym aplikacji. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)

2. `name` [ Utwórzpowiązanie>elementujakoelementupodrzędnego>WSFederationHttpBindingi\<](../../../../docs/framework/misc/binding.md) Ustaw odpowiednią wartość atrybutu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)

3. Utwórz element jako obiekt podrzędny [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu. `<security>`

4. Ustaw atrybut dla elementu na wartość lub `TransportWithMessageCredential`, zgodnie z `Message` potrzebami. `<security>` `mode`

5. Utwórz element jako obiekt podrzędny `<security>` elementu. `<message>`

6. Opcjonalna. `algorithmSuite` Ustaw atrybut`<message>` dla elementu z odpowiednią wartością. Wartość domyślna to `Basic256`.

7. Opcjonalna. Jeśli klucz dowodu asymetrycznego jest wymagany, ustaw `issuedKeyType` atrybut `<message>` elementu na `AsymmetricKey`. Wartość domyślna to `SymmetricKey`.

8. Opcjonalna. `issuedTokenType` Ustaw atrybut`<message>` w elemencie.

9. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; opcjonalne w usłudze. Utwórz element jako obiekt podrzędny `<message>` elementu. `<issuer>`

10. `address` Ustaw atrybut`<issuer>` na element i określ adres, pod którym usługa tokenu zabezpieczającego akceptuje żądania tokenów.

11. Opcjonalny. Dodawanie elementu `<identity>` podrzędnego i Określanie tożsamości usługi tokenu zabezpieczającego

12. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](service-identity-and-authentication.md).

13. Wymagane na kliencie, jeśli nie określono żadnego lokalnego wystawcy; nieużywane w usłudze. Utwórz [powiązanie > elementu w sekcji powiązania, którego można użyć do komunikowania się z usługą tokenu zabezpieczającego. \<](../../../../docs/framework/misc/binding.md) Aby uzyskać więcej informacji na temat tworzenia powiązań, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Określ powiązanie utworzone w poprzednim kroku, ustawiając `binding` atrybuty `<issuer>` i `bindingConfiguration` elementu.

15. Nieużywane na kliencie; opcjonalne w usłudze. Utwórz element jako obiekt podrzędny > <`message`elementu. `<issuerMetadata>` Następnie w `address` atrybucie `<issuerMetadata>` elementu Określ adres, pod którym usługa tokenu zabezpieczającego ma publikować swoje metadane. Opcjonalnie Dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.

16. Opcjonalne zarówno na kliencie, jak i w usłudze. Dodaj element jako obiekt podrzędny `<message>` elementu. `<claimTypeRequirements>` Określ wymagane i opcjonalne oświadczenia, na których bazuje usługa, dodając [ \<Dodawanie >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementów do `<claimTypeRequirements>` elementu `claimType` i określając typ oświadczenia przy użyciu atrybutu. Określ, `isOptional` czy podane żądanie jest wymagane, czy opcjonalne, ustawiając atrybut.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje kod służący do samodzielnego `WSFederationHttpBinding` konfigurowania.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Federacja](federation.md)
- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznych sesji na WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
