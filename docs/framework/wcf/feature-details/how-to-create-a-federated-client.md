---
title: 'Instrukcje: tworzenie klienta federacyjnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: 8de673fae16da8189589e20b6d9a66b96e1823ba
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487112"
---
# <a name="how-to-create-a-federated-client"></a>Instrukcje: tworzenie klienta federacyjnego
W Windows Communication Foundation (WCF), Tworzenie klienta dla *usługa federacyjna* składa się z trzech głównych kroków:  
  
1. Konfigurowanie [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub podobne niestandardowego powiązania. Aby uzyskać więcej informacji na temat tworzenia odpowiednie powiązanie, zobacz [jak: Tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Możesz też uruchomić [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wobec usługi federacyjnej, aby wygenerować plik konfiguracji do komunikowania się z usługi federacyjnej i co najmniej jeden punkt końcowy metadanych usługi tokenu zabezpieczeń.  
  
2. Ustawianie właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> sterującą różnymi aspektami interakcji z klientem za pomocą usługi tokenu zabezpieczającego.  
  
3. Ustawianie właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, co pozwala certyfikaty wymagane do bezpiecznego komunikowania się z podanych punktów końcowych, takich jak usługi tokenu zabezpieczeń.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> może być zgłaszany, gdy klient używa poświadczeń spersonifikowanego <xref:System.ServiceModel.WSFederationHttpBinding> powiązanie lub token wystawiony przez niestandardowe oraz kluczy asymetrycznych. Klucze asymetryczne są używane z <xref:System.ServiceModel.WSFederationHttpBinding> powiązania i wystawione niestandardowe tokenów gdy <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> i <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> właściwości ustawiono odpowiednio na <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> Jest zgłaszany, gdy klient próbuje wysłać wiadomość i profil użytkownika nie istnieje dla tożsamości, która jest personifikowania klienta. Aby rozwiązać ten problem, zaloguj się na komputerze klienckim lub wywołanie `LoadUserProfile` przed wysłaniem wiadomości.  
  
 Ten temat zawiera szczegółowe informacje na temat tych procedur. Aby uzyskać więcej informacji na temat tworzenia odpowiednie powiązanie, zobacz [jak: Tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Aby uzyskać więcej informacji na temat współdziałania usługi federacyjnej, zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Aby wygenerować i zbadania konfiguracyjne dla usługi federacyjnej  
  
1. Uruchom [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) przy użyciu adresu URL metadanych usługi jako parametr wiersza polecenia.  
  
2. Otwórz plik konfiguracyjny wygenerowanego w odpowiedniego edytora.  
  
3. Sprawdź atrybuty i zawartości dowolnego generowane [ \<issuer >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) i [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementów. Te znajdują się w [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elementy [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub powiązań niestandardowych elementów. Upewnij się, że adresy zawierają nazwy domen oczekiwanego i inne informacje o adresie. Należy sprawdzić te informacje, ponieważ klient uwierzytelnia się na te adresy i może ujawnić informacje, takie jak pary nazwa/hasło użytkownika. Jeśli adres nie jest oczekiwanego adresu, może to spowodować ujawnienie informacji do właściwego adresata.  
  
4. Sprawdź wszystkie dodatkowe [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementy wewnątrz skomentowanej się <`alternativeIssuedTokenParameters`> element. Podczas korzystania z narzędzia Svcutil.exe do generowania konfiguracji dla usługi federacyjnej, jeśli usługi federacyjnej lub dowolnej usługi tokenu zabezpieczeń pośrednich adres wystawcy nie jest określony, ale raczej Określ adres metadanych usługi tokenu zabezpieczającego, która udostępnia wiele punktów końcowych, wynikowy plik konfiguracji odnosi się do pierwszego punktu końcowego. Dodatkowe punkty końcowe są w pliku konfiguracyjnym jako zakomentowany <`alternativeIssuedTokenParameters`> elementy.  
  
     Określić, czy jest to jeden z nich <`issuedTokenParameters`> jest już obecny w konfiguracji jednego. Na przykład klient lepszym rozwiązaniem może być uwierzytelniania usługi tokenów zabezpieczeń przy użyciu tokenu Windows CardSpace zamiast pary nazwa/hasło użytkownika.  
  
    > [!NOTE]
    >  Gdzie wielu usługach tokenów zabezpieczeń należy te typy można przemierzać przed komunikacji z usługą, jest możliwe dla usługi tokenu zabezpieczającego pośrednich, na do kierowania klienta do usługi tokenu zabezpieczającego niepoprawne. W związku z tym, upewnij się, że punkt końcowy usługi tokenu zabezpieczającego w [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) usługę tokenu zabezpieczającego oczekiwanego i nie nieznany usługę tokenu zabezpieczającego.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Aby skonfigurować IssuedTokenClientCredential w kodzie  
  
1. Dostęp do <xref:System.ServiceModel.Security.IssuedTokenClientCredential> za pośrednictwem <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwość <xref:System.ServiceModel.Description.ClientCredentials> klasy (zwrócone przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy, lub za pomocą <xref:System.ServiceModel.ChannelFactory> klasy), jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Jeśli buforowaniem tokena nie jest wymagane, ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> właściwość `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Formantów właściwości tego, czy takie tokeny od zabezpieczeń tokenu usługi są buforowane. Jeśli ta właściwość jest ustawiona `false`, klient wysyła żądanie nowego tokenu z usługi tokenu zabezpieczającego zawsze wtedy, gdy ponownie musi uwierzytelniać się do usługi federacyjnej, niezależnie od tego, czy poprzedni token jest nadal ważny. Jeśli ta właściwość jest ustawiona `true`, klient używa istniejącego tokenu zawsze wtedy, gdy jej musi ponownie uwierzytelniać się usługi federacyjnej (o ile nie wygasł token). Wartość domyślna to `true`.  
  
3. Jeśli limit czasu jest wymagana w pamięci podręcznej tokenów, ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> właściwości <xref:System.TimeSpan> wartość. Właściwość określa, jak długo token może być buforowane. Po określonym czasie, token jest usuwany z pamięci podręcznej klienta. Domyślnie tokeny są buforowane przez czas nieokreślony. W poniższym przykładzie ustawiono przedział czasu do 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Opcjonalna. Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> na wartość procentową. Wartość domyślna to 60 (procent). Właściwość określa procent okresu ważności tokenu. Na przykład, jeśli wystawiony token jest ważny przez 10 godzin i <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> ustawiono 80, a następnie token jest odnawiany po ośmiu godzinach. W poniższym przykładzie ustawiono wartość do 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interwał odnawiania ustalany na podstawie okresu ważności tokenu i `IssuedTokenRenewalThresholdPercentage` wartość zostanie zastąpiona przez `MaxIssuedTokenCachingTime` wartości w przypadkach, gdy czas buforowania jest krótszy niż czas próg odnawiania. Na przykład jeśli wynikiem `IssuedTokenRenewalThresholdPercentage` i czas trwania tokenu to osiem godzin i `MaxIssuedTokenCachingTime` wartość wynosi 10 minut, klient kontaktuje się z usługą tokenu zabezpieczeń dla uaktualnionego tokenu co 10 minut.  
  
5. Jeśli w trybie entropii klucza w innych niż <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> jest wymagana dla powiązania, które nie korzystają z zabezpieczeń komunikatów lub transportu zabezpieczeń przy użyciu poświadczeń komunikatu (na przykład. nie ma powiązania <xref:System.ServiceModel.Channels.SecurityBindingElement>) ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> właściwość do odpowiedniej wartości. *Entropii* tryb Określa, czy klucze symetryczne mogą być kontrolowane za pomocą <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> właściwości. To ustawienie domyślne to <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, gdzie zarówno klient, jak i Wystawca tokenu dostarczania danych, które są łączone w celu wygenerowania klucza rzeczywistego. Inne wartości są <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> i <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, co oznacza, że cały klucz jest określony przez klienta lub serwera, odpowiednio. W poniższym przykładzie ustawiono właściwości używania tylko danych serwera dla klucza.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement> znajduje się w usługę tokenu zabezpieczającego lub powiązania usługi <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> nastavit <xref:System.ServiceModel.Security.IssuedTokenClientCredential> jest zastępowany przez <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> właściwość `SecurityBindingElement`.  
  
6. Konfigurowanie zachowania dowolnym punktem końcowym specyficznym dla wystawcy, dodając je do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Aby skonfigurować IssuedTokenClientCredential w konfiguracji  
  
1. Tworzenie [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element jako element podrzędny elementu [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) elementu w zachowanie punktu końcowego.  
  
2. Jeśli buforowaniem tokena nie jest wymagane, ustaw `cacheIssuedTokens` atrybut (z <`issuedToken`> element) na `false`.  
  
3. Jeśli limit czasu jest wymagana w pamięci podręcznej tokenów, ustaw `maxIssuedTokenCachingTime` atrybutu na <`issuedToken`> element do odpowiedniej wartości. Na przykład:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Jeśli wartość inną niż domyślna jest preferowana, ustaw `issuedTokenRenewalThresholdPercentage` atrybutu na <`issuedToken`> element do odpowiedniej wartości, na przykład:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Jeśli w trybie entropii klucza w innych niż `CombinedEntropy` znajduje się na powiązania, który wykonuje zabezpieczeń nie korzystanie z zabezpieczeń wiadomości lub transportu z poświadczeniami komunikatu (na przykład, nie ma powiązania `SecurityBindingElement`) ustaw `defaultKeyEntropyMode` atrybutu na `<issuedToken>` element do `ServerEntropy` lub `ClientEntropy` stosownie do potrzeb.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Opcjonalna. Konfigurowanie jakiekolwiek zachowanie punktu końcowego niestandardowe specyficzne dla wystawcy, tworząc <`issuerChannelBehaviors`> element jako element podrzędny <`issuedToken`> element. Każde działanie, można utworzyć <`add`> element jako element podrzędny <`issuerChannelBehaviors`> element. Określ adres wystawcy zachowanie przez ustawienie `issuerAddress` atrybutu na <`add`> element. Określ zachowanie przez ustawienie `behaviorConfiguration` atrybutu na <`add`> element.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Aby skonfigurować X509CertificateRecipientClientCredential w kodzie  
  
1. Dostęp do <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> za pośrednictwem <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy lub <xref:System.ServiceModel.ChannelFactory> właściwości.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie jest dostępne w przypadku certyfikatu dla danego punktu końcowego, należy użyć <xref:System.Collections.Generic.ICollection%601.Add%2A> metoda zbiorze zwróconym przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie jest niedostępne, należy użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Aby skonfigurować X509CertificateRecipientClientCredential w konfiguracji  
  
1. Tworzenie [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) element jako element podrzędny elementu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element, który jest elementem podrzędnym [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu w zachowanie punktu końcowego.  
  
2. Tworzenie `<add>` element jako element podrzędny elementu `<scopedCertificates>` elementu. Określ wartości dla `storeLocation`, `storeName`, `x509FindType`, i `findValue` atrybuty do odwoływania się do odpowiedniego certyfikatu. Ustaw `targetUri` atrybutu wartość, która zawiera adres punktu końcowego, który certyfikat ma być używane, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <scopedCertificates>  
     <add targetUri="http://fabrikam.com/sts"   
          storeLocation="CurrentUser"  
          storeName="TrustedPeople"  
          x509FindType="FindBySubjectName"  
          findValue="FabrikamSTS" />  
    </scopedCertificates>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu umożliwia skonfigurowanie wystąpienia <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy w kodzie.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby zapobiec ujawnieniu informacji możliwych, klienci, w których są uruchomione narzędzia Svcutil.exe do przetworzenia metadanych z punktów końcowych federacyjnego należy upewnij się, że wynikowy adresów usługi tokenu zabezpieczeń spełniają oczekiwane. Jest to szczególnie ważne w przypadku usługi tokenu zabezpieczającego udostępnia wiele punktów końcowych, ponieważ narzędzia Svcutil.exe generuje wynikowy plik konfiguracji do pierwszego użycia takich punktu końcowego, który może nie być powinien używać klient.  
  
## <a name="localissuer-required"></a>LocalIssuer wymagane  
 Jeśli klienci powinni zawsze używaj wystawcy lokalnego, należy pamiętać o następujących: domyślne dane wyjściowe Svcutil.exe powoduje powstanie wystawcy lokalnego nie jest używany, jeśli drugi do ostatniego usługę tokenu zabezpieczającego w łańcuchu określa wystawcy adres lub adres metadanych wystawcy.  
  
 Aby uzyskać więcej informacji o ustawieniu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, i <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>O określonym zakresie certyfikatów  
 Jeśli certyfikaty usługi musi być określona dla komunikacji z dowolnej usługi tokenu zabezpieczeń, zwykle negocjacji certyfikatu nie jest używany, mogą być określone przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Metoda przyjmuje <xref:System.Uri> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> jako parametry. Określony certyfikat jest używany podczas komunikacji z punktami końcowymi na określony identyfikator URI. Alternatywnie, można użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metodę, aby dodać certyfikat do kolekcji zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości.  
  
> [!NOTE]
>  Pomysł klienta certyfikatów, które są ograniczone do danego identyfikatora URI ma zastosowanie tylko do aplikacji, które wykorzystują połączenia wychodzące do usługi, które uwidaczniają punkty końcowe w tych identyfikatorów URI. Nie ma zastosowania do certyfikatów, które są używane do podpisywania wystawionych tokenów, takich jak skonfigurowane na serwerze w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: Tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Instrukcje: Bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
