---
title: 'Instrukcje: Tworzenie klienta federacyjnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 56ece47e-98bf-4346-b92b-fda1fc3b4d9c
ms.openlocfilehash: a9213d8cbbafaaa1fffa3a1db0d6936c2fc6544f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185041"
---
# <a name="how-to-create-a-federated-client"></a>Instrukcje: Tworzenie klienta federacyjnego
W programie Windows Communication Foundation (WCF) tworzenie klienta dla *usługi federacyjnej* składa się z trzech głównych kroków:  
  
1. Konfigurowanie [ \<powiązania niestandardowego wsFederationHttpBinding>lub](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) podobne powiązanie niestandardowe. Aby uzyskać więcej informacji na temat tworzenia odpowiedniego powiązania, zobacz [Jak: Tworzenie powiązania WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternatywnie uruchom [Narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem punktu końcowego metadanych usługi federacyjnej, aby wygenerować plik konfiguracyjny do komunikowania się z usługą federacyjnymi i jedną lub kilkoma usługami tokenu zabezpieczającego.  
  
2. Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential> właściwości, które kontroluje różne aspekty interakcji klienta z usługą tokenu zabezpieczającego.  
  
3. Ustaw właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>programu , który umożliwia certyfikaty potrzebne do bezpiecznej komunikacji z określonymi punktami końcowymi, takimi jak usługi tokenów zabezpieczających.  
  
> [!NOTE]
> A <xref:System.Security.Cryptography.CryptographicException> może zostać zgłoszony, gdy klient używa <xref:System.ServiceModel.WSFederationHttpBinding> personifikowanych poświadczeń, powiązania lub tokenu wystawionego na zamówienie i kluczy asymetrycznych. Klucze asymetryczne <xref:System.ServiceModel.WSFederationHttpBinding> są używane z tokenami wiązania <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i niestandardowymi, gdy właściwości <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>i właściwości są ustawione odpowiednio na . Jest <xref:System.Security.Cryptography.CryptographicException> generowany, gdy klient próbuje wysłać wiadomość, a profil użytkownika nie istnieje dla tożsamości, że klient jest personifikacji. Aby rozwiązać ten problem, zaloguj się do `LoadUserProfile` komputera klienckiego lub zadzwoń przed wysłaniem wiadomości.  
  
 Ten temat zawiera szczegółowe informacje na temat tych procedur. Aby uzyskać więcej informacji na temat tworzenia odpowiedniego powiązania, zobacz [Jak: Tworzenie powiązania WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Aby uzyskać więcej informacji o tym, jak działa usługa federacyjnej, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Aby wygenerować i sprawdzić konfigurację usługi federacyjnej  
  
1. Uruchom [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z adresem adresu URL metadanych usługi jako parametru wiersza polecenia.  
  
2. Otwórz wygenerowany plik konfiguracyjny w odpowiednim edytorze.  
  
3. Sprawdź atrybuty i zawartość wszelkich wygenerowanych [ \<>wystawców](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) i [ \<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementów. Znajdują się one w [ \<elementach zabezpieczeń>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) dla [ \<elementów wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub niestandardowych powiązań. Upewnij się, że adresy zawierają oczekiwane nazwy domen lub inne informacje adresowe. Ważne jest, aby sprawdzić te informacje, ponieważ klient uwierzytelnia się na tych adresach i może ujawnić informacje, takie jak pary nazwy użytkownika/hasła. Jeśli adres nie jest oczekiwanym adresem, może to spowodować ujawnienie informacji niezamierzonemu odbiorcy.  
  
4. Sprawdź wszelkie dodatkowe `alternativeIssuedTokenParameters` [ \<wydaneTokenParameters>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementy wewnątrz skomentowanego <> element. Podczas korzystania z narzędzia Svcutil.exe do generowania konfiguracji dla usługi federacyjnej, jeśli usługa federacyjne lub jakiekolwiek pośrednie usługi tokenu zabezpieczającego nie określają adresu wystawcy, ale raczej określają adres metadanych dla usługi tokenu zabezpieczającego, która udostępnia wiele punktów końcowych, wynikowy plik konfiguracyjny odnosi się do pierwszego punktu końcowego. Dodatkowe punkty końcowe znajdują się w pliku konfiguracyjnym jako skomentowane <`alternativeIssuedTokenParameters`> elementów.  
  
     Określ, czy jedna z `issuedTokenParameters` tych <> jest lepsza niż te, które są już obecne w konfiguracji. Na przykład klient może preferować uwierzytelnienie w usłudze tokenu zabezpieczającego przy użyciu tokenu Windows CardSpace, a nie pary nazwa użytkownika/hasło.  
  
    > [!NOTE]
    > W przypadku, gdy wiele usług tokenu zabezpieczającego musi być przenoszone przed komunikowaniem się z usługą, usługa pośredniego tokenu zabezpieczającego może skierować klienta do niepoprawnej usługi tokenu zabezpieczającego. W związku z tym upewnij się, że punkt końcowy dla usługi tokenu zabezpieczającego [ \<w issuedTokenParameters>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) jest oczekiwaną usługą tokenu zabezpieczającego, a nie nieznaną usługą tokenu zabezpieczającego.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Aby skonfigurować issuedTokenClientCredential w kodzie  
  
1. Dostęp <xref:System.ServiceModel.Security.IssuedTokenClientCredential> za <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> pośrednictwem właściwości <xref:System.ServiceModel.Description.ClientCredentials> klasy (zwrócone <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> przez <xref:System.ServiceModel.ClientBase%601> właściwość klasy <xref:System.ServiceModel.ChannelFactory> lub za pośrednictwem klasy), jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Jeśli buforowanie tokenów nie jest <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> wymagane, `false`ustaw właściwość na . Właściwość <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> określa, czy takie tokeny z usługi tokenu zabezpieczającego są buforowane. Jeśli ta właściwość `false`jest ustawiona na , klient żąda nowego tokenu z usługi tokenu zabezpieczającego, gdy musi ponownie uwierzytelnić się do usługi federacyjnej, niezależnie od tego, czy poprzedni token jest nadal prawidłowy. Jeśli ta właściwość `true`jest ustawiona na , klient ponownie używa istniejącego tokenu, gdy musi ponownie uwierzytelnić się do usługi federacyjnej (tak długo, jak token nie wygasł). Wartość domyślna to `true`.  
  
3. Jeśli limit czasu jest wymagany dla tokenów <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> buforowanych, <xref:System.TimeSpan> ustaw właściwość na wartość. Właściwość określa, jak długo token może być buforowany. Po upływie określonego przedziału czasu token jest usuwany z pamięci podręcznej klienta. Domyślnie tokeny są buforowane przez czas nieokreślony. W poniższym przykładzie ustawia przedział czasu do 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Element opcjonalny. Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> wartość procentową. Wartość domyślna to 60 (procent). Właściwość określa procent okresu ważności tokenu. Na przykład jeśli wystawiony token jest prawidłowy <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> przez 10 godzin i jest ustawiony na 80, token jest odnawiany po ośmiu godzinach. W poniższym przykładzie ustawia wartość na 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interwał odnawiania określony przez okres `IssuedTokenRenewalThresholdPercentage` ważności tokenu i `MaxIssuedTokenCachingTime` wartość jest zastępowane przez wartość w przypadkach, gdy czas buforowania jest krótszy niż czas progu odnowienia. Na przykład jeśli i `IssuedTokenRenewalThresholdPercentage` czas trwania tokenu wynosi osiem `MaxIssuedTokenCachingTime` godzin, a wartość wynosi 10 minut, klient kontaktuje się z usługą tokenu zabezpieczającego dla zaktualizowanego tokenu co 10 minut.  
  
5. Jeśli tryb entropii <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> klucza inny niż jest potrzebny w powiązaniu, które nie używa zabezpieczeń wiadomości lub zabezpieczeń transportu z poświadczeniami wiadomości (na przykład. powiązanie nie ma <xref:System.ServiceModel.Channels.SecurityBindingElement>a <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> ), ustawić właściwość na odpowiednią wartość. Tryb *entropii* określa, czy klucze symetryczne mogą być kontrolowane przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> właściwości. Ta wartość <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>domyślna to , gdzie zarówno klient, jak i wystawca tokenu dostarczają dane, które są łączone w celu wytworzenia rzeczywistego klucza. Inne wartości <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>są i , co oznacza, że cały klucz jest określony przez klienta lub serwera, odpowiednio. W poniższym przykładzie ustawia właściwość do używania tylko danych serwera dla klucza.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > Jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement> a jest obecny w tokenu zabezpieczającym <xref:System.ServiceModel.Security.IssuedTokenClientCredential> usługi lub powiązania <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> usługi, `SecurityBindingElement` <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> zestaw jest zastępowane przez właściwość . .  
  
6. Skonfiguruj wszelkie zachowania punktu końcowego specyficzne dla <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> wystawcy, dodając je do kolekcji zwróconej przez właściwość.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Aby skonfigurować program IssuedTokenClientCredential w konfiguracji  
  
1. Utwórz [ \<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element jako element podrzędny [ \<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element w zachowaniu punktu końcowego.  
  
2. Jeśli buforowanie tokenów nie jest `cacheIssuedTokens` wymagane, ustaw atrybut (<`issuedToken`> element) `false`na .  
  
3. Jeśli limit czasu jest wymagany dla tokenów `maxIssuedTokenCachingTime` buforowanych, ustaw atrybut `issuedToken` na <> element do odpowiedniej wartości. Przykład:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Jeśli preferowana jest wartość inna niż `issuedTokenRenewalThresholdPercentage` wartość domyślna, ustaw `issuedToken` atrybut <> element na odpowiednią wartość, na przykład:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Jeśli tryb entropii `CombinedEntropy` klucza inny niż jest na powiązanie, które nie używa zabezpieczeń wiadomości lub `SecurityBindingElement`zabezpieczeń transportu `defaultKeyEntropyMode` z poświadczeniami wiadomości (na przykład powiązanie nie ma), ustaw atrybut na `<issuedToken>` element albo `ServerEntropy` lub `ClientEntropy` zgodnie z wymaganiami.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Element opcjonalny. Skonfiguruj dowolne zachowanie niestandardowego punktu końcowego specyficzne dla wystawcy, tworząc `issuerChannelBehaviors` element `issuedToken` <> jako element podrzędny <> elementu. Dla każdego zachowania utwórz element `add` <> jako element podrzędny elementu `issuerChannelBehaviors`> <. Określ adres wystawcy zachowania, `issuerAddress` ustawiając atrybut w `add` <> element. Określ samo zachowanie, `behaviorConfiguration` ustawiając atrybut na `add` <> element.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Aby skonfigurować x509CertificateRecipientClientCredential w kodzie  
  
1. Dostęp <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> do <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> właściwości <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> klasy lub <xref:System.ServiceModel.ChannelFactory> obiektu można uzyskać za pośrednictwem obiektu.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie jest dostępne dla certyfikatu dla <xref:System.Collections.Generic.ICollection%601.Add%2A> danego punktu końcowego, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> należy użyć metody kolekcji zwróconej przez właściwość.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie nie jest <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> dostępne, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> należy użyć metody klasy, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Aby skonfigurować x509CertificateRecipientClientCredential w konfiguracji  
  
1. Tworzenie [ \<scopedCertificates>](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) element jako element podrzędny [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element, który sam jest elementem podrzędnym [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element w zachowaniu punktu końcowego.  
  
2. Utwórz `<add>` element jako element `<scopedCertificates>` podrzędny elementu. Określ wartości `storeLocation` `storeName`dla `x509FindType`, `findValue` , i atrybuty, aby odwołać się do odpowiedniego certyfikatu. Ustaw `targetUri` atrybut na wartość, która zawiera adres punktu końcowego, dla którego ma być używany certyfikat, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykładowy kod konfiguruje wystąpienie <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy w kodzie.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby zapobiec ujawnieniu informacji, klienci, którzy są uruchomione narzędzie Svcutil.exe do przetwarzania metadanych z federowanych punktów końcowych należy upewnić się, że wynikowe adresy usługi tokenu zabezpieczającego są to, czego oczekują. Jest to szczególnie ważne, gdy usługa tokenu zabezpieczającego udostępnia wiele punktów końcowych, ponieważ narzędzie Svcutil.exe generuje wynikowy plik konfiguracyjny do używania pierwszego takiego punktu końcowego, który może nie być tym, którego klient powinien używać.  
  
## <a name="localissuer-required"></a>Wymagany identyfikator lokalny  
 Jeśli oczekuje się, że klienci zawsze będą używać wystawcy lokalnego, należy zwrócić uwagę na następujące kwestie: domyślne dane wyjściowe programu Svcutil.exe powoduje, że lokalny wystawca nie jest używany, jeśli usługa tokenu zabezpieczającego przedostatniego w łańcuchu określa adres wystawcy lub adres metadanych wystawcy.  
  
 Aby uzyskać więcej <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>informacji <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>na <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> temat ustawiania , i właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy, zobacz [Jak: Konfigurowanie wystawcy lokalnego](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certyfikaty o określonym zakresie  
 Jeśli certyfikaty usług muszą być określone do komunikowania się z dowolnej usługi tokenu zabezpieczającego, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> zazwyczaj dlatego, że negocjacja certyfikatu nie jest używany, mogą być określone przy użyciu właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy. Metoda <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> przyjmuje <xref:System.Uri> a <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> i jako parametry. Określony certyfikat jest używany podczas komunikowania się z punktami końcowymi w określonym identyfikatorze URI. Alternatywnie można użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metody, aby dodać certyfikat do <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> kolekcji zwróconej przez właściwość.  
  
> [!NOTE]
> Pomysł klienta certyfikatów, które są ograniczone do danego identyfikatora URI ma zastosowanie tylko do aplikacji, które są wykonywanie wywołań wychodzących do usług, które uwidaczniają punkty końcowe w tych identyfikatorów URI. Nie ma zastosowania do certyfikatów, które są używane do podpisywania wystawionych tokenów, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> takich <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> jak te skonfigurowane na serwerze w kolekcji zwracanej przez klasę. Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie poświadczeń w usłudze federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz też

- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Instrukcje: bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
