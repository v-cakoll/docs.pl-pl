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
ms.openlocfilehash: e464aff46f311ede1cd629fb459ade9a6e627d59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796958"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania

W tym temacie opisano sposób konfigurowania Windows Communication Foundation (WCF) do używania różnych certyfikatów do podpisywania i szyfrowania wiadomości na kliencie i w usłudze.

Aby umożliwić używanie oddzielnych certyfikatów do podpisywania i szyfrowania, należy utworzyć niestandardowe poświadczenia klienta lub usługi (lub oba), ponieważ usługa WCF nie udostępnia interfejsu API do ustawiania wielu certyfikatów klienta lub usługi. Ponadto należy podać Menedżera tokenów zabezpieczających, aby wykorzystać informacje o wielu certyfikatach i utworzyć odpowiedniego dostawcę tokenów zabezpieczających dla określonego użycia klucza i kierunku komunikatów.

Na poniższym diagramie przedstawiono główne klasy używane, klasy, z których dziedziczą (pokazane przez strzałkę w górę) i typy zwracane niektórych metod i właściwości.

- `MyClientCredentials`jest implementacją <xref:System.ServiceModel.Description.ClientCredentials>niestandardową.

  - Jego właściwości wyświetlane na diagramie zwracają wystąpienia elementu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.

  - Jego Metoda <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> zwraca wystąpienie elementu `MyClientCredentialsSecurityTokenManager`.

- `MyClientCredentialsSecurityTokenManager`jest implementacją <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>niestandardową.

  - Jego Metoda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> zwraca wystąpienie elementu <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.

![Wykres przedstawiający sposób użycia poświadczeń klienta](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")

Aby uzyskać więcej informacji o poświadczeniach niestandardowych [, zobacz Przewodnik: Tworzenie niestandardowych poświadczeń](walkthrough-creating-custom-client-and-service-credentials.md)klienta i usługi.

Ponadto należy utworzyć niestandardowego weryfikatora tożsamości i połączyć go z elementem powiązania zabezpieczeń w niestandardowym powiązaniu. Należy również użyć niestandardowych poświadczeń zamiast poświadczeń domyślnych.

Na poniższym diagramie przedstawiono klasy powiązane z powiązaniem niestandardowym oraz sposób powiązania niestandardowego weryfikatora tożsamości. Istnieje kilka elementów powiązania, z których wszystkie dziedziczą <xref:System.ServiceModel.Channels.BindingElement>. Zawiera właściwość, która zwraca wystąpienie `MyIdentityVerifier` , z którego jest dostosowane. <xref:System.ServiceModel.Security.IdentityVerifier> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>

![Wykres przedstawiający niestandardowy element powiązania](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")

Aby uzyskać więcej informacji na temat tworzenia niestandardowego weryfikatora tożsamości, zobacz How to: [Instrukcje: Utwórz niestandardowego weryfikatora](how-to-create-a-custom-client-identity-verifier.md)tożsamości klienta.

### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Aby używać oddzielnych certyfikatów do podpisywania i szyfrowania

1. Zdefiniuj nową klasę poświadczeń klienta, która dziedziczy z <xref:System.ServiceModel.Description.ClientCredentials> klasy. Zaimplementuj cztery nowe właściwości, aby umożliwić określenie wielu `ClientSigningCertificate`certyfikatów `ClientEncryptingCertificate`: `ServiceSigningCertificate`,, `ServiceEncryptingCertificate`i. Należy również zastąpić <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> metodę, aby zwrócić wystąpienie dostosowanej <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy zdefiniowanej w następnym kroku.

     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]

2. Zdefiniuj nowego menedżera tokenów zabezpieczających klienta, który dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> z klasy. Zastąp <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, aby utworzyć odpowiedniego dostawcę tokenów zabezpieczających. Parametr (a <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) zawiera kierunek wiadomości i użycie klucza. `requirement`

     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]

3. Zdefiniuj nową klasę poświadczeń usługi, która dziedziczy z <xref:System.ServiceModel.Description.ServiceCredentials> klasy. Zaimplementuj cztery nowe właściwości, aby umożliwić określenie wielu `ClientSigningCertificate`certyfikatów `ClientEncryptingCertificate`: `ServiceSigningCertificate`,, `ServiceEncryptingCertificate`i. Należy również zastąpić <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> metodę, aby zwrócić wystąpienie dostosowanej <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy zdefiniowanej w następnym kroku.

     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]

4. Zdefiniuj nowego menedżera tokenów zabezpieczeń usługi, który dziedziczy z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy. Zastąp <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę w celu utworzenia odpowiedniego dostawcy tokenów zabezpieczających, który ma przekazany kierunek komunikatu i użycie klucza.

     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]

### <a name="to-use-multiple-certificates-on-the-client"></a>Aby użyć wielu certyfikatów na kliencie

1. Tworzenie niestandardowego powiązania. Element powiązania zabezpieczeń musi działać w trybie dupleksu, aby zezwolić na obecność różnych dostawców tokenów zabezpieczających dla żądań i odpowiedzi. Jednym ze sposobów jest użycie transportu z obsługą dupleksu lub użycie <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> , jak pokazano w poniższym kodzie. Połącz dostosowany <xref:System.ServiceModel.Security.IdentityVerifier> element, który jest zdefiniowany w następnym kroku do elementu powiązania zabezpieczeń. Zastąp domyślne poświadczenia klienta przy użyciu niestandardowych poświadczeń klienta, które zostały wcześniej utworzone.

     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]

2. Zdefiniuj niestandardową <xref:System.ServiceModel.Security.IdentityVerifier>. Usługa ma wiele tożsamości, ponieważ do szyfrowania żądania służą różne certyfikaty i podpisanie odpowiedzi.

    > [!NOTE]
    > W poniższym przykładzie dostarczony niestandardowy weryfikator tożsamości nie sprawdza tożsamości punktu końcowego w celach demonstracyjnych. Nie jest to zalecane rozwiązanie w przypadku kodu produkcyjnego.

     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]

### <a name="to-use-multiple-certificates-on-the-service"></a>Aby użyć wielu certyfikatów w usłudze

1. Tworzenie niestandardowego powiązania. Element powiązania zabezpieczeń musi działać w trybie dupleksu, aby zezwolić na obecność różnych dostawców tokenów zabezpieczających dla żądań i odpowiedzi. Podobnie jak w przypadku klienta należy użyć transportu z obsługą dupleksu <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> lub użyć, jak pokazano w poniższym kodzie. Zastąp domyślne poświadczenia usługi przy użyciu wcześniej utworzonych poświadczeń usługi.

     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Przewodnik: Tworzenie niestandardowych poświadczeń klienta i usługi](walkthrough-creating-custom-client-and-service-credentials.md)
