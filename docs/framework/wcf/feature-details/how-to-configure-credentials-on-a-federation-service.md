---
title: 'Instrukcje: konfigurowanie poświadczeń usługi federacyjnej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 33df685b4d14130ae00d59012706b7637924c9be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295435"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Instrukcje: konfigurowanie poświadczeń usługi federacyjnej
W Windows Communication Foundation (WCF), tworzenia usługi federacyjnej składa się z następujących procedur głównego:  
  
1. Konfigurowanie <xref:System.ServiceModel.WSFederationHttpBinding> lub podobne niestandardowego powiązania. Aby uzyskać więcej informacji na temat tworzenia odpowiednie powiązanie, zobacz [jak: Tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Konfigurowanie <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sterującą jak wystawione tokeny, przedstawione z usługą uwierzytelniania.  
  
 Ten temat zawiera szczegółowe informacje o drugi etap. Aby uzyskać więcej informacji na temat współdziałania usługi federacyjnej, zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Aby ustawić właściwości IssuedTokenServiceCredential w kodzie  
  
1. Użyj <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> właściwość <xref:System.ServiceModel.Description.ServiceCredentials> klasy, aby zwrócić odwołanie do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> wystąpienia. Właściwość jest dostępny z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwość <xref:System.ServiceModel.ServiceHostBase> klasy.  
  
2. Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> właściwości `true` Jeśli samodzielnie wystawionych tokenów, takich jak [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty, to uwierzytelnianie. Wartość domyślna to `false`.  
  
3. Wypełnianie kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwość wystąpieniami <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy. Każde wystąpienie reprezentuje wystawcy, z której usługa uwierzytelnia tokenów.  
  
    > [!NOTE]
    >  W przeciwieństwie do kolekcji po stronie klienta, zwracany przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> właściwości kolekcji znanych certyfikatów nie jest kolekcją kluczem. Usługa akceptuje tokeny, które wystawiają certyfikaty określonego, niezależnie od adresów klienta, która wysłała komunikat zawierający wystawiony token (zależnie od dalszego ograniczenia, które są opisane w dalszej części tego tematu).  
  
4. Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> jedną z właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości wyliczenia. Można to zrobić tylko w przypadku kodu. Wartość domyślna to <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, przypisując wystąpienia niestandardowego <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości.  
  
6. Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> ustawiono `ChainTrust` lub `PeerOrChainTrust`ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> właściwość do odpowiedniej wartości z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wyliczenia. Należy zauważyć, że tryb odwołania nie jest używany w `PeerTrust` lub `Custom` tryby weryfikacji.  
  
7. Jeśli to konieczne, przypisz wystąpienie klasy niestandardowej <xref:System.IdentityModel.Tokens.SamlSerializer> klasy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> właściwości. Niestandardowy serializator zabezpieczeń potwierdzenia Markup Language (SAML) wymagane jest na przykład do analizowania niestandardowe twierdzenia SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Aby ustawić właściwości IssuedTokenServiceCredential konfigurację  
  
1. Tworzenie `<issuedTokenAuthentication>` element jako element podrzędny <`serviceCredentials`> element.  
  
2. Ustaw `allowUntrustedRsaIssuers` atrybutu `<issuedTokenAuthentication>` elementu `true` Jeśli uwierzytelnia własnym wystawiony token, taki jak [!INCLUDE[infocard](../../../../includes/infocard-md.md)] karty.  
  
3. Tworzenie `<knownCertificates>` element jako element podrzędny elementu `<issuedTokenAuthentication>` elementu.  
  
4. Utwórz zero lub więcej `<add>` elementy jako elementy podrzędne `<knownCertificates>` element i określ, jak można zlokalizować certyfikatu za pomocą `storeLocation`, `storeName`, `x509FindType`, i `findValue` atrybutów.  
  
5. Jeśli to konieczne, ustaw `samlSerializer` atrybut <`issuedTokenAuthentication`> element na nazwę typu niestandardowego <xref:System.IdentityModel.Tokens.SamlSerializer> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ustawiono właściwości <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> w kodzie.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby usługi federacyjnej do uwierzytelnienia klienta, wymaga spełnienia następujących warunków dotyczących wystawiony token:  
  
-   Jeśli podpis cyfrowy wystawiony token używa identyfikatora klucza zabezpieczeń RSA, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> właściwość musi być `true`.  
  
-   Jeśli podpis wystawiony token używa numeru seryjnego wystawcy X.509, identyfikator klucza podmiotu X.509 lub identyfikator zabezpieczeń odcisk palca X.509, wystawiony token musi być podpisany przy użyciu certyfikatu w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwość <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>klasy.  
  
-   Gdy wystawiony token jest podpisany przy użyciu certyfikatu X.509, certyfikat musi go zweryfikować na semantykę określony przez wartość <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwość, niezależnie od tego, czy certyfikat został wysłany do jednostki uzależnionej jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> lub zostały pobrane z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwości. Aby uzyskać więcej informacji dotyczących walidacji certyfikatu X.509, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Na przykład ustawienie <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> do <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> będzie uwierzytelnienia wszelkich wystawiony token, którego certyfikat podpisywania jest `TrustedPeople` magazynu certyfikatów. W takim przypadku należy ustawić <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> właściwości albo <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> lub <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Możesz wybrać inne tryby, w tym <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Gdy `Custom` jest zaznaczone, należy przypisać wystąpienie <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> właściwości. Niestandardowego modułu weryfikacji można sprawdzić poprawność certyfikatów przy użyciu dowolnego kryterium, które potrzeby. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Zobacz także

- [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: Tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
