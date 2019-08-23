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
ms.openlocfilehash: 988fc79f71b670f5eaed1a305f54cc90374e4b17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950627"
---
# <a name="how-to-create-a-federated-client"></a>Instrukcje: tworzenie klienta federacyjnego
W programie Windows Communication Foundation (WCF) tworzenie klienta dla *usługi federacyjnej* składa się z trzech głównych kroków:  
  
1. Skonfiguruj > WSFederationHttpBinding lub podobne niestandardowe powiązanie. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Aby uzyskać więcej informacji na temat tworzenia odpowiednich powiązań, [zobacz How to: Utwórz element WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Alternatywnie Uruchom narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem punktu końcowego metadanych usługi federacyjnej, aby wygenerować plik konfiguracji do komunikacji z usługą federacyjną i co najmniej jedną usługą tokenów zabezpieczających.  
  
2. Ustawianie właściwości <xref:System.ServiceModel.Security.IssuedTokenClientCredential> kontrolujących różne aspekty interakcji klienta z usługą tokenu zabezpieczającego.  
  
3. Ustaw właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>, które umożliwiają certyfikatom wymaganie bezpiecznego komunikowania się z poszczególnymi punktami końcowymi, takimi jak usługi tokenu zabezpieczającego.  
  
> [!NOTE]
> Może zostać zgłoszony <xref:System.ServiceModel.WSFederationHttpBinding> , gdy klient używa personifikowanych poświadczeń, powiązania lub tokenu wystawionego niestandardowo oraz kluczy asymetrycznych. <xref:System.Security.Cryptography.CryptographicException> Klucze <xref:System.ServiceModel.WSFederationHttpBinding> asymetryczne są używane z tokenami powiązania i wystawiane niestandardowo, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> gdy właściwości i <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> są odpowiednio ustawione <xref:System.IdentityModel.Tokens.SecurityKeyType.AsymmetricKey>na. <xref:System.Security.Cryptography.CryptographicException> Jest zgłaszany, gdy klient próbuje wysłać komunikat, a profil użytkownika nie istnieje dla tożsamości, która personifikuje klienta. Aby wyeliminować ten problem, zaloguj się na komputerze klienckim lub wywołaj `LoadUserProfile` przed wysłaniem wiadomości.  
  
 Ten temat zawiera szczegółowe informacje dotyczące tych procedur. Aby uzyskać więcej informacji na temat tworzenia odpowiednich powiązań, [zobacz How to: Utwórz element WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md). Aby uzyskać więcej informacji na temat działania usługi federacyjnej, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-generate-and-examine-the-configuration-for-a-federated-service"></a>Aby wygenerować i przeanalizować konfigurację usługi federacyjnej  
  
1. Uruchom [Narzędzie metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z adresem URL metadanych usługi jako parametrem wiersza polecenia.  
  
2. Otwórz wygenerowany plik konfiguracji w odpowiednim edytorze.  
  
3. Przejrzyj atrybuty i zawartość dowolnego wygenerowanego [ \<wystawcy >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) i [ \<elementów > IssuerMetadata](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) . Znajdują się one w obszarze [ \<> zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) dla [ \<elementów > WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) lub niestandardowych powiązań. Upewnij się, że adresy zawierają oczekiwane nazwy domen lub inne informacje o adresie. Ważne jest, aby sprawdzić te informacje, ponieważ klient uwierzytelnia się na tych adresach i może ujawnić takie informacje, jak pary nazwa użytkownika i hasło. Jeśli adres nie jest oczekiwanym adresem, może to spowodować ujawnienie informacji osobie nieprzeznaczonej odbiorcy.  
  
4. Zapoznaj się z dodatkowymi`alternativeIssuedTokenParameters` [ \<elementami issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) wewnątrz elementu z komentarzem < >. Przy użyciu narzędzia Svcutil. exe do generowania konfiguracji dla usługi federacyjnej, jeśli usługa federacyjna lub wszystkie pośrednie usługi tokenów zabezpieczających nie określają adresu wystawcy, ale zamiast tego Określ adres metadanych dla usługi tokenu zabezpieczającego, która ujawnia wiele punktów końcowych, otrzymany plik konfiguracji odwołuje się do pierwszego punktu końcowego. Dodatkowe punkty końcowe znajdują się w pliku konfiguracji jako komentarz <`alternativeIssuedTokenParameters`> elementy.  
  
     Ustal, czy jeden z tych`issuedTokenParameters`< > jest preferowany dla tej, która jest już obecna w konfiguracji. Na przykład klient może preferować uwierzytelnienie w usłudze tokenu zabezpieczającego przy użyciu tokenu Windows CardSpace zamiast pary nazwa użytkownika i hasło.  
  
    > [!NOTE]
    > W przypadku, gdy wiele usług tokenów zabezpieczających musi być przepływających przed komunikowaniem się z usługą, istnieje możliwość, że pośrednia usługa tokenu zabezpieczającego kieruje klienta do nieprawidłowej usługi tokenu zabezpieczającego. W związku z tym upewnij się, że punkt końcowy usługi tokenu zabezpieczającego w [ \<issuedTokenParameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md) to oczekiwana usługa tokenu zabezpieczającego, a nie nieznana usługa tokenu zabezpieczającego.  
  
### <a name="to-configure-an-issuedtokenclientcredential-in-code"></a>Aby skonfigurować IssuedTokenClientCredential w kodzie  
  
1. <xref:System.ServiceModel.Security.IssuedTokenClientCredential> Uzyskujdostęp<xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> do <xref:System.ServiceModel.ChannelFactory> właściwości klasy (zwracanej przez właściwość klasylubprzezklasę),jakpokazanowponiższymprzykładziekodu.<xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
2. Jeśli buforowanie tokenu nie jest wymagane, ustaw <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> właściwość na. `false` Właściwość <xref:System.ServiceModel.Security.IssuedTokenClientCredential.CacheIssuedTokens%2A> określa, czy takie tokeny z usługi tokenu zabezpieczającego są buforowane. Jeśli ta właściwość jest ustawiona na `false`, klient żąda nowego tokenu z usługi tokenu zabezpieczającego za każdym razem, gdy musi ponownie uwierzytelnić się w usłudze federacyjnej, bez względu na to, czy poprzedni token jest nadal ważny. Jeśli ta właściwość jest ustawiona na `true`, klient ponownie używa istniejącego tokenu przy każdym ponownym uwierzytelnieniu w usłudze federacyjnej (o ile token nie wygasł). Wartość domyślna to `true`.  
  
3. Jeśli w buforowanych tokenach jest wymagany limit czasu, należy <xref:System.ServiceModel.Security.IssuedTokenClientCredential.MaxIssuedTokenCachingTime%2A> ustawić właściwość <xref:System.TimeSpan> na wartość. Właściwość określa, jak długo token może być buforowany. Po upływie określonego przedziału czasu token zostanie usunięty z pamięci podręcznej klienta. Domyślnie tokeny są buforowane w nieskończoność. Poniższy przykład ustawia przedział czasu na 10 minut.  
  
     [!code-csharp[c_CreateSTS#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#15)]
     [!code-vb[c_CreateSTS#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#15)]  
  
4. Opcjonalny. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> Ustaw wartość procentową. Wartość domyślna to 60 (procent). Właściwość określa wartość procentową okresu ważności tokenu. Na przykład jeśli wystawiony token jest ważny przez 10 godzin i <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuedTokenRenewalThresholdPercentage%2A> jest ustawiony na 80, token jest odnawiany po ośmiu godzinach. Poniższy przykład ustawia wartość na 80 procent.  
  
     [!code-csharp[c_CreateSTS#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#16)]
     [!code-vb[c_CreateSTS#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#16)]  
  
     Interwał odnawiania określony przez okres ważności tokenu i `IssuedTokenRenewalThresholdPercentage` wartość jest zastępowana `MaxIssuedTokenCachingTime` przez wartość w przypadkach, gdy czas buforowania jest krótszy niż czas progu odnawiania. Na przykład jeśli produkt `IssuedTokenRenewalThresholdPercentage` i czas trwania tokenu wynosi osiem godzin, `MaxIssuedTokenCachingTime` a wartość wynosi 10 minut, klient programu kontaktuje się z usługą tokenu zabezpieczającego dla zaktualizowanego tokenu co 10 minut.  
  
5. Jeśli w powiązaniu, które nie <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy> korzysta z zabezpieczeń komunikatów lub zabezpieczeń transportu z poświadczeniami komunikatów, jest wymagany inny tryb entropii klucza niż jest to potrzebne. powiązanie nie ma elementu <xref:System.ServiceModel.Channels.SecurityBindingElement>), <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> ustaw właściwość na odpowiednią wartość. Tryb *entropii* określa, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> czy klucze symetryczne można kontrolować za pomocą właściwości. Ta wartość domyślna <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.CombinedEntropy>to, w której zarówno klient, jak i wystawca tokenów dostarczają dane połączone w celu utworzenia rzeczywistego klucza. Inne wartości to <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ClientEntropy> i <xref:System.ServiceModel.Security.SecurityKeyEntropyMode.ServerEntropy>, co oznacza, że cały klucz jest określony przez klienta lub serwer. Poniższy przykład ustawia właściwość, aby używać tylko danych serwera dla klucza.  
  
     [!code-csharp[c_CreateSTS#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#17)]
     [!code-vb[c_CreateSTS#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#17)]  
  
    > [!NOTE]
    > <xref:System.ServiceModel.Security.IssuedTokenClientCredential> <xref:System.ServiceModel.Security.IssuedTokenClientCredential.DefaultKeyEntropyMode%2A> `SecurityBindingElement` <xref:System.ServiceModel.Channels.SecurityBindingElement.KeyEntropyMode%2A> Jeśli występuje w usłudze tokenu zabezpieczającego lub w powiązaniu usługi, zestaw na jest zastępowany przez właściwość. <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
6. Skonfiguruj wszelkie zachowania punktu końcowego specyficzne dla wystawcy, dodając je do kolekcji <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A> zwróconej przez właściwość.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-issuedtokenclientcredential-in-configuration"></a>Aby skonfigurować IssuedTokenClientCredential w konfiguracji  
  
1. Utwórz element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) issuedToken > jako obiekt podrzędny elementu issuedToken > w zachowaniu punktu końcowego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)  
  
2. Jeśli buforowanie tokenu nie jest wymagane, należy ustawić `cacheIssuedTokens` atrybut (elementu > <`issuedToken`) na `false`.  
  
3. Jeśli w buforowanych tokenach jest wymagany limit czasu, należy `maxIssuedTokenCachingTime` ustawić atrybut na <`issuedToken`> elementu na odpowiednią wartość. Na przykład:  
    `<issuedToken maxIssuedTokenCachingTime='00:10:00' />`  
  
4. Jeśli preferowana jest wartość inna niż domyślna, należy ustawić `issuedTokenRenewalThresholdPercentage` atrybut w <`issuedToken`> elementu na odpowiednią wartość, na przykład:  
  
    ```xml  
    <issuedToken issuedTokenRenewalThresholdPercentage = "80" />  
    ```  
  
5. Jeśli tryb entropii klucza inny niż `CombinedEntropy` znajduje się w powiązaniu, które nie korzysta z zabezpieczeń komunikatów lub zabezpieczeń transportu z poświadczeniami wiadomości (na przykład powiązanie nie `SecurityBindingElement`ma), `<issuedToken>` Ustaw `defaultKeyEntropyMode` atrybut na należy do elementu `ServerEntropy` lub `ClientEntropy` , jeśli jest to wymagane.  
  
    ```xml  
    <issuedToken defaultKeyEntropyMode = "ServerEntropy" />  
    ```  
  
6. Opcjonalny. Skonfiguruj niestandardowe zachowanie punktu końcowego określonego przez wystawcę, tworząc <`issuerChannelBehaviors`> element jako element podrzędny elementu <`issuedToken`>. Dla każdego zachowania Utwórz <`add`element > jako obiekt podrzędny <`issuerChannelBehaviors`> elementu. Określ adres wystawcy zachowania przez ustawienie `issuerAddress` atrybutu dla elementu <`add`>. Określ samo zachowanie, ustawiając `behaviorConfiguration` atrybut w <`add`> elementu.  
  
    ```xml  
    <issuerChannelBehaviors>  
    <add issuerAddress="http://fabrikam.org/sts" behaviorConfiguration="FabrikamSTS" />  
    </issuerChannelBehaviors>  
    ```  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-code"></a>Aby skonfigurować X509CertificateRecipientClientCredential w kodzie  
  
1. Dostępdo<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>przezwłaściwość klasylub<xref:System.ServiceModel.ChannelFactory> właściwości. <xref:System.ServiceModel.ClientBase%601>  
  
     [!code-csharp[c_CreateSTS#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#18)]
     [!code-vb[c_CreateSTS#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#18)]  
  
2. Jeśli wystąpienie jest dostępne dla certyfikatu dla danego punktu końcowego, <xref:System.Collections.Generic.ICollection%601.Add%2A> Użyj metody kolekcji zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwość. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>  
  
     [!code-csharp[c_CreateSTS#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#19)]
     [!code-vb[c_CreateSTS#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#19)]  
  
3. Jeśli wystąpienie jest niedostępne, <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> Użyj metody <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy, jak pokazano w poniższym przykładzie. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>  
  
     [!code-csharp[c_CreateSTS#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#20)]
     [!code-vb[c_CreateSTS#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#20)]  
  
### <a name="to-configure-an-x509certificaterecipientclientcredential-in-configuration"></a>Aby skonfigurować X509CertificateRecipientClientCredential w konfiguracji  
  
1. Utwórz element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) scopedCertificates > jako obiekt podrzędny elementu serviceCertificate >, który jest samym elementem podrzędnym elementu ClientCredentials > w zachowaniu punktu końcowego. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)  
  
2. Utwórz element jako obiekt podrzędny `<scopedCertificates>` elementu. `<add>` Określ wartości `storeLocation`atrybutów, `storeName`, `x509FindType`i `findValue` , aby odwołać się do odpowiedniego certyfikatu. `targetUri` Ustaw atrybut na wartość, która dostarcza adres punktu końcowego, którego certyfikat ma być używany, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy przykład kodu konfiguruje wystąpienie <xref:System.ServiceModel.Security.IssuedTokenClientCredential> klasy w kodzie.  
  
 [!code-csharp[c_FederatedClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedclient/cs/source.cs#2)]
 [!code-vb[c_FederatedClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedclient/vb/source.vb#2)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby zapobiec ujawnieniu informacji, Klienci uruchamiający narzędzie Svcutil. exe mogą przetwarzać metadane z federacyjnych punktów końcowych, powinny mieć pewność, że otrzymane adresy usługi tokenu zabezpieczającego są oczekiwane. Jest to szczególnie ważne, gdy usługa tokenów zabezpieczających ujawnia wiele punktów końcowych, ponieważ narzędzie Svcutil. exe generuje plik konfiguracji, aby użyć pierwszego takiego punktu końcowego, który może nie być używany przez klienta.  
  
## <a name="localissuer-required"></a>LocalIssuer wymagane  
 Jeśli klienci mają zawsze używać wystawcy lokalnego, należy zwrócić uwagę na następujące kwestie: domyślne dane wyjściowe programu Svcutil. exe nie są używane, jeśli w łańcuchu określono adres wystawcy lub adres metadanych wydawcy.  
  
 Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>ustawiania <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>właściwości, <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> <xref:System.ServiceModel.Security.IssuedTokenClientCredential> , i klasy, zobacz [How to: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="scoped-certificates"></a>Certyfikaty o określonym zakresie  
 Jeśli należy określić certyfikaty usługi do komunikacji z dowolnymi usługami tokenów zabezpieczających, zwykle ponieważ negocjowanie certyfikatu nie jest używane, można je określić przy użyciu <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> klasy. Metoda przyjmuje parametry<xref:System.Security.Cryptography.X509Certificates.X509Certificate2>iAS. <xref:System.Uri> <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetDefaultCertificate%2A> Określony certyfikat jest używany podczas komunikowania się z punktami końcowymi o określonym identyfikatorze URI. Alternatywnie możesz użyć <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.SetScopedCertificate%2A> metody, aby dodać certyfikat do kolekcji zwróconej <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> przez właściwość.  
  
> [!NOTE]
> Pomysł klienta dotyczący certyfikatów należących do zakresu danego identyfikatora URI dotyczy tylko aplikacji, które powodują wywołania wychodzące do usług, które uwidaczniają punkty końcowe dla tych identyfikatorów URI. Nie dotyczy certyfikatów, które są używane do podpisywania wystawionych tokenów, takich jak te skonfigurowane na serwerze w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasę. Aby uzyskać więcej informacji, zobacz [jak: Skonfiguruj poświadczenia na usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznych sesji na WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: Utwórz WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Zagadnienia dotyczące zabezpieczeń obejmujące metadane](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Instrukcje: Bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
