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
ms.openlocfilehash: 05f35bbb7dbb34cd4067c407578038cbb4eff70f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599148"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej
W programie Windows Communication Foundation (WCF) Tworzenie usługi federacyjnej obejmuje następujące główne procedury:  
  
1. Konfigurowanie <xref:System.ServiceModel.WSFederationHttpBinding> lub podobne niestandardowe powiązanie. Aby uzyskać więcej informacji na temat tworzenia odpowiednich powiązań, zobacz [How to: Create a WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md).  
  
2. Skonfigurowanie <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> usługi, która kontroluje sposób uwierzytelniania wystawionych tokenów w usłudze.  
  
 Ten temat zawiera szczegółowe informacje o drugim kroku. Aby uzyskać więcej informacji na temat działania usługi federacyjnej, zobacz [Federacja](federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Aby ustawić właściwości IssuedTokenServiceCredential w kodzie  
  
1. Użyj <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> właściwości <xref:System.ServiceModel.Description.ServiceCredentials> klasy, aby zwrócić odwołanie do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> wystąpienia. Właściwość jest dostępna z <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości <xref:System.ServiceModel.ServiceHostBase> klasy.  
  
2. Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> Właściwość na `true` , jeśli tokeny wystawione przez siebie, takie jak karta CardSpace, mają być uwierzytelniane. Wartość domyślna to `false`.  
  
3. Wypełnij kolekcję zwróconą przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> Właściwość z wystąpieniami <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy. Każde wystąpienie reprezentuje wystawcę, z którego usługa będzie uwierzytelniać tokeny.  
  
    > [!NOTE]
    > W przeciwieństwie do kolekcji po stronie klienta zwróconej przez <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> Właściwość, znana kolekcja certyfikatów nie jest kolekcją z systemem. Usługa akceptuje tokeny, które wystawiane przez określone certyfikaty niezależnie od adresu klienta, który wysłał komunikat zawierający wystawiony token (z zastrzeżeniem dalszych ograniczeń, które są opisane w dalszej części tego tematu).  
  
4. Ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Właściwość na jedną z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości wyliczenia. Można to zrobić tylko w kodzie. Wartość domyślna to <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Właściwość jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> , przypisz wystąpienie <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy niestandardowej do <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości.  
  
6. Jeśli <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> jest ustawiona na `ChainTrust` lub `PeerOrChainTrust` , ustaw <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> Właściwość na odpowiednią wartość z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wyliczenia. Należy zauważyć, że tryb odwołania nie jest używany w trybie `PeerTrust` `Custom` walidacji.  
  
7. W razie potrzeby Przypisz wystąpienie <xref:System.IdentityModel.Tokens.SamlSerializer> klasy niestandardowej do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> właściwości. Wymagany jest serializator niestandardowego języka Markup Language (SAML). na przykład do analizowania niestandardowych zatwierdzeń SAML.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Aby ustawić właściwości IssuedTokenServiceCredential w konfiguracji  
  
1. Utwórz `<issuedTokenAuthentication>` element jako obiekt podrzędny `serviceCredentials` elementu> <.  
  
2. Ustaw `allowUntrustedRsaIssuers` atrybut `<issuedTokenAuthentication>` elementu na `true` , jeśli uwierzytelniany jest token wystawiony automatycznie, taki jak karta CardSpace.  
  
3. Utwórz `<knownCertificates>` element jako obiekt podrzędny `<issuedTokenAuthentication>` elementu.  
  
4. Utwórz zero lub więcej `<add>` elementów jako elementy podrzędne `<knownCertificates>` elementu i określ sposób lokalizowania certyfikatu przy użyciu `storeLocation` atrybutów,, `storeName` `x509FindType` i `findValue` .  
  
5. W razie potrzeby ustaw `samlSerializer` atrybut <`issuedTokenAuthentication`> elementu na nazwę typu <xref:System.IdentityModel.Tokens.SamlSerializer> klasy niestandardowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ustawia właściwości <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> w kodzie.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Aby usługa federacyjna mogła uwierzytelnić klienta, następujące elementy muszą mieć wartość true dotyczącą wystawionego tokenu:  
  
- Gdy podpis cyfrowy wystawionego tokenu używa identyfikatora klucza zabezpieczeń RSA, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> Właściwość musi mieć wartość `true` .  
  
- Gdy podpis wystawionego tokenu używa numeru seryjnego wystawcy X. 509, identyfikatora klucza podmiotu X. 509 lub identyfikatora zabezpieczeń odcisku palca X. 509, wystawiony token musi być podpisany przez certyfikat w kolekcji zwróconej przez <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> Właściwość <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy.  
  
- Gdy wystawiony token jest podpisany przy użyciu certyfikatu X. 509, certyfikat musi być zweryfikowany zgodnie z semantyką określoną przez wartość <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwości, niezależnie od tego, czy certyfikat został wysłany do jednostki uzależnionej jako <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> lub uzyskany z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> właściwości. Aby uzyskać więcej informacji na temat weryfikacji certyfikatu X. 509, zobacz [Praca z certyfikatami](working-with-certificates.md).  
  
 Na przykład ustawienie na wartość <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> spowoduje uwierzytelnienie dowolnego wystawionego tokenu, którego certyfikat podpisywania znajduje się w `TrustedPeople` magazynie certyfikatów. W takim przypadku należy ustawić <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> Właściwość na <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> lub <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine> . Można wybrać inne tryby, w tym <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> . Gdy `Custom` jest zaznaczone, należy przypisać wystąpienie <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy do <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> właściwości. Niestandardowy moduł sprawdzania poprawności może weryfikować certyfikaty przy użyciu dowolnych kryteriów, które polubią. Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Zobacz też

- [Federacja](federation.md)
- [Federacja i zaufanie](federation-and-trust.md)
- [Federacja — przykład](../samples/federation-sample.md)
- [Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
- [Instrukcje: tworzenie klienta federacyjnego](how-to-create-a-federated-client.md)
- [Praca z certyfikatami](working-with-certificates.md)
- [Tryby uwierzytelniania elementu SecurityBindingElement](securitybindingelement-authentication-modes.md)
