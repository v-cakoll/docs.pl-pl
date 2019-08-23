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
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912185"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Instrukcje: konfigurowanie poświadczeń usługi federacyjnej
W programie Windows Communication Foundation (WCF) Tworzenie usługi federacyjnej obejmuje następujące główne procedury:  
  
1. <xref:System.ServiceModel.WSFederationHttpBinding> Konfigurowanie lub podobne niestandardowe powiązanie. Aby uzyskać więcej informacji na temat tworzenia odpowiednich powiązań, [zobacz How to: Utwórz element WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Skonfigurowanie usługi <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> , która kontroluje sposób uwierzytelniania wystawionych tokenów w usłudze.  
  
 Ten temat zawiera szczegółowe informacje o drugim kroku. Aby uzyskać więcej informacji na temat działania usługi federacyjnej, zobacz [Federacja](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Aby ustawić właściwości IssuedTokenServiceCredential w kodzie  
  
1. Użyj właściwości klasy, <xref:System.ServiceModel.Description.ServiceCredentials> aby <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> zwrócić odwołanie do wystąpienia. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> Właściwość jest dostępna z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości <xref:System.ServiceModel.ServiceHostBase> klasy.  
  
2. Ustaw właściwość na `true` , jeśli tokeny wystawione przez siebie, takie jak karta CardSpace, mają być uwierzytelniane. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> Wartość domyślna to `false`.  
  
3. Wypełnij kolekcję zwróconą przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwość z wystąpieniami <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy. Każde wystąpienie reprezentuje wystawcę, z którego usługa będzie uwierzytelniać tokeny.  
  
    > [!NOTE]
    > W przeciwieństwie do kolekcji po stronie klienta zwróconej <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> przez właściwość, znana kolekcja certyfikatów nie jest kolekcją z systemem. Usługa akceptuje tokeny, które wystawiane przez określone certyfikaty niezależnie od adresu klienta, który wysłał komunikat zawierający wystawiony token (z zastrzeżeniem dalszych ograniczeń, które są opisane w dalszej części tego tematu).  
  
4. Ustaw właściwość na jedną z wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode> wyliczenia. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Można to zrobić tylko w kodzie. Wartość domyślna to <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Jeśli właściwość jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, przypisz wystąpienie klasy niestandardowej <xref:System.IdentityModel.Selectors.X509CertificateValidator> do <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>  
  
6. `ChainTrust` `PeerOrChainTrust`Jeśli jest ustawiona na lub, ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> właściwość na odpowiednią wartość z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wyliczenia. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Należy zauważyć, że tryb odwołania nie jest używany `PeerTrust` w `Custom` trybie walidacji.  
  
7. W razie potrzeby Przypisz wystąpienie klasy niestandardowej <xref:System.IdentityModel.Tokens.SamlSerializer> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> do właściwości. Wymagany jest serializator niestandardowego języka Markup Language (SAML). na przykład do analizowania niestandardowych zatwierdzeń SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Aby ustawić właściwości IssuedTokenServiceCredential w konfiguracji  
  
1. Utwórz element jako obiekt podrzędny elementu > <`serviceCredentials`. `<issuedTokenAuthentication>`  
  
2. `allowUntrustedRsaIssuers` Ustaw atrybut `<issuedTokenAuthentication>` elementu na`true` , jeśli uwierzytelniany jest token wystawiony automatycznie, taki jak karta CardSpace.  
  
3. Utwórz element jako obiekt podrzędny `<issuedTokenAuthentication>` elementu. `<knownCertificates>`  
  
4. Utwórz zero lub więcej `<add>` elementów jako elementy podrzędne `<knownCertificates>` elementu i określ sposób `storeLocation`lokalizowania `x509FindType`certyfikatu przy użyciu atrybutów, `storeName`, i `findValue` .  
  
5. W razie potrzeby ustaw `samlSerializer` atrybut <`issuedTokenAuthentication`> elementu na nazwę typu klasy niestandardowej <xref:System.IdentityModel.Tokens.SamlSerializer> .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia właściwości <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> w kodzie.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby usługa federacyjna mogła uwierzytelnić klienta, następujące elementy muszą mieć wartość true dotyczącą wystawionego tokenu:  
  
- Gdy podpis cyfrowy wystawionego tokenu używa identyfikatora klucza zabezpieczeń RSA, właściwość musi <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> mieć `true`wartość.  
  
- Gdy podpis wystawionego tokenu używa numeru seryjnego wystawcy x. 509, identyfikatora klucza podmiotu x. 509 lub identyfikatora zabezpieczeń odcisku palca x. 509, wystawiony token musi być podpisany przez certyfikat w <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> kolekcji zwróconej przez właściwość <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>Klasa.  
  
- Gdy wystawiony token jest podpisany przy użyciu certyfikatu X. 509, certyfikat musi być zweryfikowany zgodnie z semantyką określoną przez wartość <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwości, bez względu na to, czy certyfikat został wysłany do jednostki uzależnionej <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> jako lub uzyskany <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> z właściwości. Aby uzyskać więcej informacji na temat weryfikacji certyfikatu X. 509, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Na przykład ustawienie na wartość <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> spowoduje <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> uwierzytelnienie dowolnego wystawionego tokenu, którego certyfikat `TrustedPeople` podpisywania znajduje się w magazynie certyfikatów. W takim przypadku należy ustawić <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> Właściwość <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> na lub <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Można wybrać inne tryby, w tym <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Gdy `Custom` jest zaznaczone, należy przypisać wystąpienie <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> właściwości. Niestandardowy moduł sprawdzania poprawności może weryfikować certyfikaty przy użyciu dowolnych kryteriów, które polubią. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certyfikatów.  
  
## <a name="see-also"></a>Zobacz także

- [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznych sesji na WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: Utwórz WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
