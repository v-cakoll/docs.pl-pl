---
title: 'Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 5bfea40a500dc1355b439ae7d949b0d96d3ab08c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej
W systemie Windows Communication Foundation (WCF), tworzenie usługi federacyjnej składa się z następujących procedur głównego:  
  
1.  Konfigurowanie <xref:System.ServiceModel.WSFederationHttpBinding> lub podobne niestandardowego powiązania. Aby uzyskać więcej informacji o tworzeniu powiązanie odpowiednie, zobacz [porady: tworzenie WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2.  Konfigurowanie <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> steruje jak wystawionych tokenów prezentowane z usługą uwierzytelniania.  
  
 Ten temat zawiera szczegółowe informacje o drugim krokiem. Aby uzyskać więcej informacji na temat działania usługi federacyjnej, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Aby ustawić właściwości IssuedTokenServiceCredential w kodzie  
  
1.  Użyj <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> właściwość <xref:System.ServiceModel.Description.ServiceCredentials> zwraca odwołanie do klasy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> wystąpienia. Właściwość jest dostępny z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwość <xref:System.ServiceModel.ServiceHostBase> klasy.  
  
2.  Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> właściwości `true` Jeśli własnym wystawionych tokenów, takich jak [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty są uwierzytelnienia. Wartość domyślna to `false`.  
  
3.  Wypełnianie kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwości wystąpieniami <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy. Każde wystąpienie reprezentuje wystawcy, z którego usługa będzie się uwierzytelniał tokenów.  
  
    > [!NOTE]
    >  W przeciwieństwie do kolekcji po stronie klienta zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwość kolekcji znanych certyfikatów nie jest kolekcją kluczem. Usługa akceptuje tokeny wystawiać certyfikaty określonego niezależnie od adresów klienta, który wysłał wiadomość zawierającą wystawionego tokenu (warunki ograniczające dodatkowe, które są opisane w dalszej części tego tematu).  
  
4.  Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> jedną z właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości wyliczenia. Można to zrobić tylko w kodzie. Wartość domyślna to <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5.  Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, przypisz wystąpienie niestandardowego <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy do <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości.  
  
6.  Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> ustawiono `ChainTrust` lub `PeerOrChainTrust`ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> właściwości odpowiednią wartość z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wyliczenia. Należy pamiętać, że tryb odwołania nie jest używany w `PeerTrust` lub `Custom` tryby sprawdzania poprawności.  
  
7.  W razie potrzeby przypisać wystąpienia niestandardowego <xref:System.IdentityModel.Tokens.SamlSerializer> klasy do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> właściwości. Niestandardowy serializator zabezpieczeń potwierdzenia Markup Language (SAML) jest potrzebny, na przykład do analizowania niestandardowych potwierdzenia SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Aby ustawić właściwości IssuedTokenServiceCredential w konfiguracji  
  
1.  Utwórz `<issuedTokenAuthentication>` element jako element podrzędny <`serviceCredentials`> elementu.  
  
2.  Ustaw `allowUntrustedRsaIssuers` atrybutu `<issuedTokenAuthentication>` elementu `true` Jeśli uwierzytelniania samodzielnie wystawionego tokenu, takich jak [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty.  
  
3.  Utwórz `<knownCertificates>` element jako element podrzędny `<issuedTokenAuthentication>` elementu.  
  
4.  Utwórz zero lub więcej `<add>` elementy jako elementy podrzędne `<knownCertificates>` element i określ, w jaki można znaleźć certyfikatu przy użyciu `storeLocation`, `storeName`, `x509FindType`, i `findValue` atrybutów.  
  
5.  W razie potrzeby ustaw `samlSerializer` atrybut <`issuedTokenAuthentication`> element na nazwę typu niestandardowego <xref:System.IdentityModel.Tokens.SamlSerializer> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia właściwości <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> w kodzie.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby usługi federacyjnej do uwierzytelnienia klienta, wymaga spełnienia następujących warunków o wystawionego tokenu:  
  
-   Jeśli podpis cyfrowy wystawiony token używa identyfikatora klucza zabezpieczeń RSA, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> właściwość musi być `true`.  
  
-   Gdy wystawiony token podpisu używa numeru seryjnego wystawcy X.509, identyfikator klucza podmiotu X.509 lub identyfikator zabezpieczeń palca certyfikatu X.509, wystawionego tokenu musi być podpisany przez certyfikatu w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwości <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>klasy.  
  
-   Gdy wystawiony token jest podpisany przy użyciu certyfikatu X.509, certyfikat musi zostać sprawdzony na semantykę określony przez wartość <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwości, niezależnie od tego, czy certyfikat został wysłany do jednostki uzależnionej jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> lub uzyskano z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwości. Aby uzyskać więcej informacji o walidacji certyfikatu X.509, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Na przykład ustawienie <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> może uwierzytelniać dowolnego wystawionego tokenu, którego certyfikat podpisywania znajduje się w `TrustedPeople` magazynu certyfikatów. W takim przypadku ustawić <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> właściwości albo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> lub <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Możesz wybrać inne tryby, w tym <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Gdy `Custom` jest zaznaczone, należy przypisać wystąpienia <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> właściwości. Niestandardowego modułu weryfikacji można sprawdzić poprawność certyfikatów przy użyciu dowolnego kryterium, które potrzeby. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi korzystającej z niestandardowego moduł weryfikacji certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
