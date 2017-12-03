---
title: "Instrukcje: Używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 312a4b854cb527e63d6866247d4147720ce0710c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Instrukcje: Używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania
W tym temacie przedstawiono sposób konfigurowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] korzystanie z różnych certyfikatów komunikat podpisywania i szyfrowania na kliencie i usługi.  
  
 Aby włączyć osobnych certyfikatów służący do podpisywania i szyfrowania, niestandardowe klienta lub usługi poświadczeń (lub obie) należy utworzyć ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie zapewnia interfejsu API, aby ustawić wiele certyfikatów klienta lub usługi. Ponadto zabezpieczeń Menedżer tokenów należy podać wykorzystać informacje wiele certyfikatów i utworzyć dostawcę tokenu zabezpieczeń odpowiednich dla określony klucza kierunku użycia i komunikatu.  
  
 Na poniższym diagramie przedstawiono główne klasy używane, klasy dziedziczą z (się za pomocą strzałki wskazującej w górę) i typy zwracane niektórych metod i właściwości.  
  
-   `MyClientCredentials`to niestandardowe implementacja <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Właściwości wyświetlane na diagramie zwracany wszystkie wystąpienia <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Metody <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> Zwraca wystąpienie klasy `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager`to niestandardowe implementacja <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Metody <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> Zwraca wystąpienie klasy <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Wykres przedstawiający sposób używania poświadczeń klienta](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz niestandardowych poświadczeń [wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Ponadto należy utworzyć weryfikatora tożsamość niestandardowa i połączyć elementu powiązania zabezpieczeń, do niestandardowego powiązania. Należy również użyć niestandardowych poświadczeń zamiast domyślnych poświadczeń.  
  
 Na poniższym diagramie przedstawiono klasy zaangażowane w niestandardowego powiązania i jak weryfikatora tożsamość niestandardowa jest połączony. Istnieje kilka elementów wiązania zaangażowany, które dziedziczą z <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Ma <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> właściwość, która zwraca wystąpienie klasy <xref:System.ServiceModel.Security.IdentityVerifier>, z którego `MyIdentityVerifier` jest dostosowana.  
  
 ![Wykres przedstawiający element niestandardowego powiązania](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie weryfikatora tożsamość niestandardowa, zobacz jak: [porady: Tworzenie niestandardowego weryfikator tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Korzystanie z osobnych certyfikatów podpisywania i szyfrowania  
  
1.  Zdefiniuj nową klasę poświadczeń klienta, która dziedziczy <xref:System.ServiceModel.Description.ClientCredentials> klasy. Implementowanie czterech nowych właściwości do wielu specyfikacji certyfikaty: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, i `ServiceEncryptingCertificate`. Także zastępować <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> sposób zwrócenia wystąpienia klasy dostosowywane <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy, która jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Zdefiniuj nowy Menedżer tokenów klienta zabezpieczeń, która dziedziczy <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> klasy. Zastąpienie <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, aby utworzyć dostawcę tokenu odpowiednich ustawień zabezpieczeń. `requirement` Parametr ( <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) udostępnia użycia kierunku i klucz wiadomości.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Zdefiniuj nową klasę poświadczenia usługi, która dziedziczy <xref:System.ServiceModel.Description.ServiceCredentials> klasy. Implementowanie czterech nowych właściwości do wielu specyfikacji certyfikaty: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, i `ServiceEncryptingCertificate`. Także zastępować <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> sposób zwrócenia wystąpienia klasy dostosowywane <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy, która jest zdefiniowana w następnym kroku.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Zdefiniuj nowy Menedżer tokenów usługi zabezpieczeń, która dziedziczy <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> klasy. Zastąpienie <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodę, aby utworzyć dostawcę tokenu zabezpieczeń odpowiednich podany komunikat przekazany w kierunku i klucz użycia.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Korzystanie z wielu certyfikatów na komputerze klienckim  
  
1.  Tworzenie niestandardowego powiązania. Element powiązania zabezpieczeń musi działać w trybie duplex umożliwia zabezpieczeń innego dostawcy tokenów obecności dla żądań i odpowiedzi. Aby wykonać to użycia obsługą dupleks transportu lub użyj <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak pokazano w poniższym kodzie. Link dostosowywane <xref:System.ServiceModel.Security.IdentityVerifier> który jest zdefiniowany w następnym kroku do elementu powiązania zabezpieczeń. Zastąpić domyślne poświadczenia klienta przy użyciu poświadczeń klienta dostosowanego wcześniej utworzony.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Definiowanie niestandardowego <xref:System.ServiceModel.Security.IdentityVerifier>. Usługa ma wiele tożsamości, ponieważ różne certyfikaty są używane do żądania szyfrowania i podpisywania odpowiedzi.  
  
    > [!NOTE]
    >  W poniższym przykładzie weryfikatora podana tożsamość niestandardowa nie wykonuje sprawdzanie dla celów demonstracyjnych tożsamości punktu końcowego. Nie jest to zalecane praktyki kodzie produkcyjnym.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Korzystanie z wielu certyfikatów w usłudze  
  
1.  Tworzenie niestandardowego powiązania. Element powiązania zabezpieczeń musi działać w trybie duplex umożliwia zabezpieczeń innego dostawcy tokenów obecności dla żądań i odpowiedzi. Zgodnie z klientem, należy użyć obsługą dupleks transportu lub <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak pokazano w poniższym kodzie. Zastąpić domyślne poświadczenia usługi przy użyciu poświadczeń usług niestandardowych wcześniej utworzony.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
