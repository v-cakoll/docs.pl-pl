---
title: 'Porady: tworzenie WSFederationHttpBinding'
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
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f03734babf27ac4350580e7bed03645f3049c956
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Porady: tworzenie WSFederationHttpBinding
W [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], <xref:System.ServiceModel.WSFederationHttpBinding> klasy ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w konfiguracji) zapewnia mechanizm udostępnianie usługi federacyjnej. Oznacza to, że usługa, która wymaga od klientów uwierzytelniania za pomocą tokenu zabezpieczającego wydanego przez usługę tokenu zabezpieczającego. W tym temacie przedstawiono sposób konfigurowania <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie i konfiguracji. Po utworzeniu powiązania punktu końcowego można skonfigurować do używania tego powiązania.  
  
 Podstawowe kroki przedstawione poniżej:  
  
1.  Wybierz tryb zabezpieczeń. <xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje `Message`, nawet przez kilka przeskoków, która umożliwia zabezpieczeń na trasie na poziomie komunikatu i `TransportWithMessageCredential`, który zapewnia lepszą wydajność w przypadku, gdy klient i usługa ułatwia bezpośrednie połączenie za pośrednictwem PROTOKÓŁ HTTPS.  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.WSFederationHttpBinding> Obsługuje również `None` jako tryb zabezpieczeń. Ten tryb nie jest bezpieczna i jest dostępne tylko do celów debugowania. Jeśli punkt końcowy usługi jest wdrażany z <xref:System.ServiceModel.WSFederationHttpBinding> z jej ustawić tryb zabezpieczeń `None`, wynikowy klienta powiązania (generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) jest <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z tryb zabezpieczeń `None`.  
  
     W przeciwieństwie do innych powiązania dostarczane przez system nie jest konieczne wybieranie typu poświadczeń klienta przy użyciu `WSFederationHttpBinding`. Jest tak, ponieważ typ poświadczeń klienta jest zawsze wystawionego tokenu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uzyskuje token z określonego wystawcę i przedstawia tokenu usługi do uwierzytelniania klienta.  
  
2.  Na klientach federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwość adres URL usługi tokenu zabezpieczającego. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> do powiązania w celu użycia do komunikowania się z usługi tokenu zabezpieczającego.  
  
3.  Opcjonalny. Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> właściwości do jednolity identyfikator zasobów (URI) typu tokenu. Na usług federacyjnych Określ typ tokenu, który oczekuje usługi. Na klientach federacyjnych Określ typ tokenu żądania klienta z usługi tokenu zabezpieczającego.  
  
     Jeśli nie tokenu określono typu, klientów generuje tokeny zabezpieczające żądania WS-Trust (RSTs) bez tokenu typu identyfikatora URI i usług spodziewać się uwierzytelnianie klientów za pomocą tokenu zabezpieczeń potwierdzenia Markup Language (SAML) 1.1 domyślnie.  
  
     Identyfikator URI dla tokenu SAML 1.1 jest "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".  
  
4.  Opcjonalny. W usługach federacyjnych, należy ustawić <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> właściwość adres URL metadanych usługi tokenu zabezpieczającego. Punkt końcowy metadanych umożliwia klientom usługi wybierz para powiązanie odpowiednie/punktu końcowego, jeśli usługa jest skonfigurowana do publikowania metadanych. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Publikowanie metadanych, zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
 Można również ustawić inne właściwości, takich jak typ klucz używany jako dowód klucza wystawionego tokenu, pakiet algorytmów do użycia między klientem a usługą, czy do negocjowania lub jawnie określ poświadczenia usługi, szczególne oświadczeń usługi oczekuje wystawiony token zawierał i wszelkie dodatkowe elementy XML dodane do żądania, które klient wysyła do usługi tokenu zabezpieczającego.  
  
> [!NOTE]
>  `NegotiateServiceCredential` Właściwość ma zastosowanie tylko podczas `SecurityMode` ma ustawioną wartość `Message`. Jeśli `SecurityMode` ustawiono `TransportWithMessageCredential`, a następnie `NegotiateServiceCredential` właściwość jest ignorowana.  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Aby skonfigurować WSFederationHttpBinding w kodzie  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding>.  
  
2.  Ustaw <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> właściwości <xref:System.ServiceModel.WSFederationHttpSecurityMode> lub <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> zgodnie z wymaganiami. Jeśli pakiet algorytmów innych niż <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> jest wymagane, ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> właściwości na wartość pobranych z <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
3.  Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości zależnie od potrzeb.  
  
4.  Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> właściwości <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` lub.`AsymmetricKey` co jest wymagane.  
  
5.  Ustaw <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> na odpowiednią wartość. Jeśli wartość nie jest ustawiona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wartość domyślna to "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1", które wskazuje tokeny SAML 1.1.  
  
6.  Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; Opcjonalnie w usłudze. Utwórz <xref:System.ServiceModel.EndpointAddress> zawierający informacje o adres i tożsamość usługi tokenu zabezpieczającego i przypisz <xref:System.ServiceModel.EndpointAddress> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> właściwości.  
  
7.  Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; nie są używane w usłudze. Utwórz <xref:System.ServiceModel.Channels.Binding> dla `SecurityTokenService` i przypisz <xref:System.ServiceModel.Channels.Binding> wystąpienie do <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> właściwości.  
  
8.  Nie jest używany na komputerze klienckim; Opcjonalnie w usłudze. Utwórz <xref:System.ServiceModel.EndpointAddress> wystąpienie metadanych usługi tokenu zabezpieczeń i przypisz go do `IssuerMetadataAddress` właściwości.  
  
9. Opcjonalnie zarówno klient, jak i usługi. Utwórz i Dodaj jeden lub więcej <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> właściwości.  
  
10. Opcjonalnie zarówno klient, jak i usługi. Utwórz i Dodaj jeden lub więcej <xref:System.Xml.XmlElement> wystąpień kolekcji zwróconej przez <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> właściwości.  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a>Aby utworzyć punkt końcowy federacyjnych w konfiguracji  
  
1.  Utwórz [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) jako element podrzędny [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu w pliku konfiguracyjnym aplikacji.  
  
2.  Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) element jako element podrzędny [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i ustaw `name` atrybutu odpowiednią wartość.  
  
3.  Utwórz `<security>` element jako element podrzędny [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.  
  
4.  Ustaw `mode` atrybutu `<security>` elementu na wartość `Message` lub `TransportWithMessageCredential`, co jest wymagane.  
  
5.  Utwórz `<message>` element jako element podrzędny `<security>` elementu.  
  
6.  Opcjonalny. Ustaw `algorithmSuite` atrybutu `<message>` element odpowiednią wartość. Wartość domyślna to `Basic256`.  
  
7.  Opcjonalny. Jeśli klucz asymetryczny potwierdzającego jest wymagane, ustaw `issuedKeyType` atrybutu `<message>` elementu `AsymmetricKey`. Wartość domyślna to `SymmetricKey`.  
  
8.  Opcjonalny. Ustaw `issuedTokenType` atrybutu `<message>` elementu.  
  
9. Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; Opcjonalnie w usłudze. Utwórz `<issuer>` element jako element podrzędny `<message>` elementu.  
  
10. Ustaw `address` atrybutu `<issuer>` element i określ adres, pod którym usługa tokenu zabezpieczającego akceptuje żądania tokenu.  
  
11. Opcjonalny. Dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczeń  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Usługi uwierzytelnianie i tożsamość](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
13. Wymagany na kliencie, jeśli określono nie wystawcy lokalnego; nie są używane w usłudze. Utwórz [ \<powiązania >](../../../../docs/framework/misc/binding.md) w sekcji powiązania, który może służyć do komunikacji z usługą tokenu zabezpieczeń. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie powiązania, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
14. Określanie powiązania utworzony w poprzednim kroku, ustawiając `binding` i `bindingConfiguration` atrybuty `<issuer>` elementu.  
  
15. Nie jest używany na komputerze klienckim; Opcjonalnie w usłudze. Utwórz `<issuerMetadata>` element jako element podrzędny <`message`> elementu. Następnie w `address` atrybutu `<issuerMetadata>` elementu, określ adres, pod którym usługi tokenu zabezpieczającego Publikowanie metadanych. Opcjonalnie dodaj `<identity>` element podrzędny i określ tożsamość usługi tokenu zabezpieczającego.  
  
16. Opcjonalnie zarówno klient, jak i usługi. Dodaj `<claimTypeRequirements>` element jako element podrzędny `<message>` elementu. Określ wymaganych i opcjonalnych oświadczeń korzystający usługi przez dodanie [ \<Dodaj >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementy `<claimTypeRequirements>` element i określając oświadczenie typu z `claimType` atrybutu. Określ, czy dany oświadczenia jest wymagany lub opcjonalny przez ustawienie `isOptional` atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kodu do konfigurowania `WSFederationHttpBinding` imperatively.  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Federacyjna](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Porady: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
