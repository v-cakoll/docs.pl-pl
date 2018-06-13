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
ms.openlocfilehash: 5c33c26043d90d99c295b2e066c897e2cdad32d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496974"
---
# <a name="how-to-create-a-federated-client"></a>Instrukcje: Tworzenie klienta federacyjnego
W konsoli Windows Communication Foundation (WCF) tworzy klienta dla *usługa* składa się z trzech głównych kroków:  
  
1.  Skonfiguruj [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub podobne niestandardowego powiązania. Aby uzyskać więcej informacji o tworzeniu powiązanie odpowiednie, zobacz [porady: tworzenie WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Można również uruchomić [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wobec usługi federacyjnej, aby wygenerować plik konfiguracji do komunikowania się z usługi federacyjnej i co najmniej jeden punkt końcowy metadanych usługi tokenu zabezpieczeń.  
  
2.  Ustawianie właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> steruje różnych aspektów interakcji klienta z usługi tokenu zabezpieczającego.  
  
3.  Ustawianie właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, dzięki czemu certyfikaty wymagane do bezpiecznego komunikowania się z daną punktów końcowych, takie jak usługi tokenu zabezpieczeń.  
  
> [!NOTE]
>  A <xref:System.Security.Cryptography.CryptographicException> może zostać zgłoszony, gdy klient użyje poświadczeń personifikowanej <xref:System.ServiceModel.WSFederationHttpBinding> powiązanie lub token wystawiony niestandardowe i klucze asymetryczne. Klucze asymetryczne są używane z <xref:System.ServiceModel.WSFederationHttpBinding> powiązania i wydane niestandardowe tokenów gdy <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> i <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> właściwości, są odpowiednio ustawione na <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>. <xref:System.Security.Cryptography.CryptographicException> Jest generowany, gdy klient próbuje wysłać wiadomość i profilu użytkownika nie istnieje dla tożsamości, która jest personifikacji klienta. Aby zminimalizować ten problem, zaloguj się na komputerze klienckim lub wywołanie `LoadUserProfile` przed wysłaniem wiadomości.  
  
 Ten temat zawiera szczegółowe informacje na temat tych procedur. Aby uzyskać więcej informacji o tworzeniu powiązanie odpowiednie, zobacz [porady: tworzenie WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Aby uzyskać więcej informacji na temat działania usługi federacyjnej, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Aby wygenerować i sprawdzić jego konfigurację usługi federacyjnej  
  
1.  Uruchom [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) adres URL metadanych usługi jako parametru wiersza polecenia.  
  
2.  Otwórz plik konfiguracji wygenerowanych w odpowiedniego edytora.  
  
3.  Sprawdź, czy atrybuty i treści każdego wygenerowany [ \<wystawcy >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) i [ \<issuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) elementów. Te znajdują się w [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) elementy [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub elementy niestandardowego powiązania. Upewnij się, że adresy zawierają nazwy domeny oczekiwanego lub inne informacje o adresie. Należy sprawdzić te informacje, ponieważ klient jest uwierzytelniany na te adresy i może ujawnić informacje, takie jak pary nazwa/hasło użytkownika. Jeśli adres nie jest oczekiwany adres, może to spowodować ujawnienie informacji do właściwego adresata.  
  
4.  Sprawdź wszelkie dodatkowe [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) elementy wewnątrz komentarze limit <`alternativeIssuedTokenParameters`> elementu. Podczas korzystania z narzędzia Svcutil.exe do generowania konfiguracji dla usługi federacyjnej, jeśli usługi federacyjnej lub wszystkie usługi tokenu zabezpieczeń pośredniego adres wystawcy nie jest określony, ale raczej Określ adres metadanych usługi tokenu zabezpieczającego, który ujawnia wiele punktów końcowych, wynikowy plik konfiguracji odnosi się do pierwszego punktu końcowego. Dodatkowe punkty końcowe znajdują się w pliku konfiguracyjnym jako poza komentarzem <`alternativeIssuedTokenParameters`> elementów.  
  
     Określenia, czy jest to jeden z tych <`issuedTokenParameters`> jest ten, który znajduje się już w konfiguracji. Na przykład klienta może chcieć uwierzytelniać z usługą tokenu zabezpieczeń przy użyciu systemu Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token zamiast pary nazwa/hasło użytkownika.  
  
    > [!NOTE]
    >  Gdzie wykorzystywana wielu usługi tokenu zabezpieczeń przed komunikacji z usługą, możliwe jest dla usługi tokenu zabezpieczającego pośredniego, na przekierować klienta do usługi tokenu zabezpieczającego niepoprawne. W związku z tym, upewnij się, że punktu końcowego usługi tokenu zabezpieczającego w [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) jest usługi tokenu zabezpieczającego oczekiwany, a nie nieznany usługi tokenu zabezpieczającego.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Aby skonfigurować IssuedTokenClientCredential w kodzie  
  
1.  Dostęp <xref:System.ServiceModel.Security.IssuedTokenClientCredential> za pośrednictwem <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> właściwość <xref:System.ServiceModel.Description.ClientCredentials> klasy (zwrócony przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy, lub za pomocą <xref:System.ServiceModel.ChannelFactory> klasy), jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2.  Jeśli buforowanie tokenu nie jest wymagane, ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> właściwości `false`. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> Formantów właściwości czy takie tokeny od zabezpieczeń tokenu usługi są buforowane. Jeśli ta właściwość jest ustawiona na `false`, klient żąda nowy token z usługi tokenu zabezpieczającego przy każdym ponownym musi uwierzytelniać się do usługi federacyjnej, niezależnie od tego, czy poprzednim tokenem jest nadal ważny. Jeśli ta właściwość jest ustawiona na `true`, klient ponownie używa tokenu istniejących zawsze, gdy musi ponownie uwierzytelniać się do usługi federacyjnej (o ile nie wygasł token). Wartość domyślna to `true`.  
  
3.  Jeśli limit czasu jest wymagane w pamięci podręcznej tokenów, należy ustawić <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> właściwości <xref:System.TimeSpan> wartość. Właściwość określa, jak długo token mogą być buforowane. Po upływie określonego okresu, token jest usuwany z pamięci podręcznej klienta. Domyślnie tokeny są buforowane w nieskończoność. Poniższy przykład ustawia zakres czasu do 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4.  Opcjonalna. Ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> na wartość procentową. Wartość domyślna to 60 (w procentach). Właściwość określa procent okresu ważności tokenu. Na przykład, jeśli wystawiony token jest ważny przez 10 godzin i <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> ma wartość 80, a następnie token jest odnawiany po ośmiu godzinach. Poniższy przykład ustawia wartość do 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interwał odnawiania określana przez okres ważności tokenu i `IssuedTokenRenewalThresholdPercentage` wartość zostanie zastąpiona przez `MaxIssuedTokenCachingTime` wartości w przypadkach, gdy czas buforowania jest krótszy niż czas próg odnawiania. Na przykład jeśli iloczyn `IssuedTokenRenewalThresholdPercentage` i czas trwania tokenu jest osiem godzin i `MaxIssuedTokenCachingTime` wartość to 10 minut, klient kontaktuje się z usługą tokenu zabezpieczeń zaktualizowano tokenu co 10 minut.  
  
5.  Jeśli Tryb entropii klucza innych niż <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> jest wymagane dla powiązania, które nie korzystają z zabezpieczeń wiadomości lub transportu (np zabezpieczeń z poświadczeniami komunikatu. Powiązanie nie ma <xref:System.ServiceModel.Channels.SecurityBindingElement>) ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> właściwości odpowiednią wartość. *Entropii* tryb Określa, czy klucze symetryczne można kontrolować przy użyciu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> właściwości. Jest to ustawienie domyślne <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>, gdzie zarówno klient, jak i Wystawca tokenów zapewnia dane, które są łączone do tworzenia rzeczywistego klucza. Inne wartości są <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> i <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, co oznacza, że cały klucz jest odpowiednio określone przez klienta lub serwera. Poniższy przykład ustawia właściwość do użycia tylko dane z serwera dla klucza.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    >  Jeśli <xref:System.ServiceModel.Channels.SecurityBindingElement> znajduje się w usługi tokenu zabezpieczającego lub powiązanie usługi <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> ustawiać <xref:System.ServiceModel.Security.IssuedTokenClientCredential> jest zastępowana <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> właściwość `SecurityBindingElement`.  
  
6.  Skonfiguruj dowolne zachowania punktu końcowego specyficzne dla wystawcy, dodając je do kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Aby skonfigurować IssuedTokenClientCredential w konfiguracji  
  
1.  Utwórz [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element jako element podrzędny [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element zachowanie punktu końcowego.  
  
2.  Jeśli buforowanie tokenu nie jest wymagane, ustaw `cacheIssuedTokens` atrybutu (z <`issuedToken`> element) do `false`.  
  
3.  Jeśli limit czasu jest wymagane w pamięci podręcznej tokenów, należy ustawić `maxIssuedTokenCachingTime` atrybutu <`issuedToken`> element odpowiednią wartość. Na przykład:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4.  Jeśli wartość inna niż domyślna jest preferowana, ustaw `issuedTokenRenewalThresholdPercentage` atrybutu <`issuedToken`> element do odpowiedniej wartości, na przykład:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5.  Jeśli Tryb entropii klucza innych niż `CombinedEntropy` znajduje się na powiązania, który wykonuje zabezpieczeń nie używany do zabezpieczenia komunikatów lub transportu z poświadczeniami komunikatu (na przykład powiązanie nie ma `SecurityBindingElement`) ustaw `defaultKeyEntropyMode` atrybutu `<issuedToken>` Element jednej `ServerEntropy` lub `ClientEntropy` zgodnie z wymaganiami.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6.  Opcjonalna. Skonfiguruj jakiekolwiek zachowanie punktu końcowego niestandardowych specyficzne dla wystawcy, tworząc <`issuerChannelBehaviors`> element jako element podrzędny <`issuedToken`> elementu. Dla każdego zachowanie, należy utworzyć <`add`> element jako element podrzędny <`issuerChannelBehaviors`> elementu. Określ adres wystawcy zachowania, ustawiając `issuerAddress` atrybutu <`add`> elementu. Określ zachowanie się przez ustawienie `behaviorConfiguration` atrybutu <`add`> elementu.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Aby skonfigurować X509CertificateRecipientClientCredential w kodzie  
  
1.  Dostęp <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> za pośrednictwem <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy lub <xref:System.ServiceModel.ChannelFactory> właściwości.  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2.  Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie jest dostępne dla certyfikatu dla danego punktu końcowego, należy użyć <xref:System.Collections.Generic.ICollection%601.Add%2A> metody kolekcji zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości.  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3.  Jeśli <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> wystąpienie nie jest dostępna, należy użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Aby skonfigurować X509CertificateRecipientClientCredential w konfiguracji  
  
1.  Utwórz [ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md) element jako element podrzędny [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element, który jest elementem podrzędnym [ \< clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element zachowanie punktu końcowego.  
  
2.  Utwórz `<add>` element jako element podrzędny `<scopedCertificates>` elementu. Określ wartości dla `storeLocation`, `storeName`, `x509FindType`, i `findValue` atrybuty do odwoływania się do odpowiedniego certyfikatu. Ustaw `targetUri` atrybut na wartość, która dostarcza adres punktu końcowego, który certyfikat ma być używany, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykładowy kod konfiguruje wystąpienia <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy w kodzie.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby zapobiec ujawnieniu informacji możliwe, klienci, w których są uruchomione narzędzia Svcutil.exe do przetworzenia metadanych z punktów końcowych federacyjnych powinien zapewnić wynikowy adresy usługi tokenu zabezpieczeń co oczekiwane. Jest to szczególnie ważne w przypadku usługi tokenu zabezpieczającego udostępnia wiele punktów końcowych, ponieważ z narzędzia Svcutil.exe generuje wynikowy plik konfiguracji do użycia pierwszy takie punktu końcowego, który może nie być powinien być używany przez klienta.  
  
## <a name="localissuer-required"></a>LocalIssuer wymagane  
 Jeśli klienci powinni zawsze używaj wystawcy lokalnego, należy uwzględnić następujące informacje: domyślnego wyjścia Svcutil.exe skutkuje wystawcy lokalnego nie są używane, jeśli usługi tokenu zabezpieczeń na sekundę do ostatniego w łańcuchu Określa adres wystawcy lub adres metadanych Wystawca.  
  
 Aby uzyskać więcej informacji o ustawieniu <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>, i <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> , zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certyfikaty zakresami  
 Jeśli certyfikaty usługi musi być określona dla komunikacji z dowolnej usługi tokenu zabezpieczeń, zwykle ponieważ negocjowanie certyfikatu nie jest używany, ich można określić za pomocą <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy. <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Ma metodę <xref:System.Uri> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> jako parametry. Określony certyfikat jest używany podczas komunikacji z punktami końcowymi na określony identyfikator URI. Alternatywnie można użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metody, aby dodać certyfikat do kolekcji zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości.  
  
> [!NOTE]
>  Pomysł klienta certyfikatów, które należą do danego identyfikatora URI zakresu dotyczy tylko aplikacji, które wychodzących połączeń do usług, które udostępniają punkty końcowe w tych identyfikatorów URI. Nie ma zastosowania do certyfikatów, które są używane do podpisywania wystawionych tokenów, takich jak zasoby konfigurowane na serwerze w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Instrukcje: bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
