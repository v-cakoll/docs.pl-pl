---
title: 'Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: f95274861f58d1581e4c5439861ebf186b1b3489
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332563"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania
W tym temacie przedstawiono sposób konfigurowania Windows Communication Foundation (WCF) do użycia różnych certyfikatów do podpisywania komunikatów i szyfrowania w klienta i usługi.  
  
 Aby włączyć oddzielnych certyfikatów służący do podpisywania i szyfrowania, niestandardowe klienta lub usługę poświadczeń (lub obie) należy utworzyć ponieważ WCF nie zapewnia interfejsu API, aby ustawić wielu certyfikatów klienta lub usługę. Ponadto zabezpieczeń Menedżera tokenu należy podać może wykorzystać informacje wiele certyfikatów i utworzyć dostawcę tokenu zabezpieczeń odpowiednich dla określonego klucza kierunku użycia i komunikatu.  
  
 Na poniższym diagramie przedstawiono główne klasy używane, klasy mogą dziedziczyć (reprezentowany przez strzałkę skierowaną w górę) i zwracane typy niektórych metod i właściwości.  
  
-   `MyClientCredentials` jest niestandardową implementację <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Właściwości wyświetlane na diagramie zwracany wszystkie wystąpienia elementu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Jego metoda <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> Zwraca wystąpienie `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager` jest niestandardową implementację <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Jego metoda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> Zwraca wystąpienie <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Wykres przedstawiający sposób użycia poświadczeń klienta](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 Aby uzyskać więcej informacji na temat niestandardowych poświadczeń, zobacz [instruktażu: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Ponadto należy utworzyć weryfikatora tożsamości niestandardowej i połączyć elementu powiązania zabezpieczeń, w niestandardowym powiązaniu. Należy również użyć niestandardowych poświadczeniach, zamiast domyślnych poświadczeń.  
  
 Na poniższym diagramie przedstawiono klasy zaangażowanych w niestandardowego powiązania i jak jest połączony weryfikatora tożsamości niestandardowej. Istnieje kilka elementów wiązania zaangażowani, które dziedziczą z <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Ma <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> właściwość, która zwraca wystąpienie <xref:System.ServiceModel.Security.IdentityVerifier>, z którego `MyIdentityVerifier` dostosowany.  
  
 ![Wykres przedstawiający element niestandardowego powiązania](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 Aby uzyskać więcej informacji na temat tworzenia weryfikatora tożsamości niestandardowej, zobacz jak: [Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Aby użyć oddzielnych certyfikatów podpisywania i szyfrowania  
  
1. Zdefiniuj nową klasę poświadczeń klienta, która dziedziczy <xref:System.ServiceModel.Description.ClientCredentials> klasy. Implementowanie cztery nowe właściwości, aby zezwolić wielu specyfikacji certyfikaty: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, i `ServiceEncryptingCertificate`. Także Przesłoń <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> metodę, aby zwrócić wystąpienia dostosowane <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy, która jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2. Zdefiniuj nowy Menedżer tokenów klienta zabezpieczeń, która dziedziczy z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy. Zastąp <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, aby utworzyć dostawcę tokenu usługi odpowiednie zabezpieczenia. `requirement` Parametru ( <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) udostępnia komunikat użycia kierunku i klucz.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3. Zdefiniuj nową klasę poświadczenia usługi, która dziedziczy <xref:System.ServiceModel.Description.ServiceCredentials> klasy. Implementowanie cztery nowe właściwości, aby zezwolić wielu specyfikacji certyfikaty: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, i `ServiceEncryptingCertificate`. Także Przesłoń <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> metodę, aby zwrócić wystąpienia dostosowane <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy, która jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4. Zdefiniuj nowy Menedżer tokenów usługi zabezpieczeń, który dziedziczy z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy. Zastąp <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę w celu utworzenia dostawcy tokenów zabezpieczeń odpowiednich, biorąc pod uwagę użycie kierunku i klucz przekazany w wiadomości.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Aby korzystać z wielu certyfikatów na komputerze klienckim  
  
1. Tworzenie niestandardowego powiązania. Elementu powiązania zabezpieczeń musi działać w tryb dupleks, aby umożliwić zabezpieczeń dostawcy tokenów obecności dla żądań i odpowiedzi. Jednym ze sposobów, aby zrobić to użyj transportu obsługą duplex lub użyć <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak pokazano w poniższym kodzie. Link dostosowane <xref:System.ServiceModel.Security.IdentityVerifier> który jest zdefiniowany w następnym kroku do elementu powiązania zabezpieczeń. Zastąp domyślne poświadczenia klienta przy użyciu poświadczeń klienta niestandardowe utworzone wcześniej.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2. Definiowanie niestandardowego <xref:System.ServiceModel.Security.IdentityVerifier>. Usługa ma wiele tożsamości, ponieważ różne certyfikaty są używane do szyfrowania żądania i zaloguj się w odpowiedzi.  
  
    > [!NOTE]
    >  W poniższym przykładzie weryfikatora podana tożsamość niestandardowa nie wykonuje żadnych tożsamość punktu końcowego sprawdzanie dla celów demonstracyjnych. Nie jest to zalecane praktyki dla kodu produkcyjnego.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Aby korzystać z wielu certyfikatów w usłudze  
  
1. Tworzenie niestandardowego powiązania. Elementu powiązania zabezpieczeń musi działać w tryb dupleks, aby umożliwić zabezpieczeń dostawcy tokenów obecności dla żądań i odpowiedzi. Jak za pomocą klienta, należy użyć obsługą dupleks transportu lub <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak pokazano w poniższym kodzie. Zastąp domyślne poświadczenia usługi przy użyciu poświadczeń usług niestandardowych utworzone wcześniej.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Przewodnik: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
