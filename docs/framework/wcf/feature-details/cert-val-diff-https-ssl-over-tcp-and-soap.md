---
title: "Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
Można użyć certyfikatów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] z zabezpieczeń wiadomości warstwy (SOAP) oprócz transport layer security (TLS) za pośrednictwem protokołu HTTP (HTTPS) lub TCP. W tym temacie opisano różnice w taki sposób, który takie certyfikaty są weryfikowane.  
  
## <a name="validation-of-https-client-certificates"></a>Weryfikacja certyfikatów klienta protokołu HTTPS  
 Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikat używany przez klienta do uwierzytelniania w usłudze musi obsługiwać łańcuch zaufania. Oznacza to, że należy łańcucha do zaufanego głównego urzędu certyfikacji. Jeśli nie, wywołuje warstwę HTTP <xref:System.Net.WebException> z komunikatem "serwer zdalny zwrócił błąd: (403) zabroniony." [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Wyświetla ten wyjątek jako <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Weryfikacja certyfikatów usługi protokołu HTTPS  
 Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikatu, który uwierzytelnia serwer z musi obsługiwać łańcuch zaufania domyślnie. Oznacza to, że należy łańcucha do zaufanego głównego urzędu certyfikacji. Nie online jest sprawdzane aby zobaczyć, czy certyfikat został odwołany. To zachowanie można przesłonić, rejestrując <xref:System.Net.Security.RemoteCertificateValidationCallback> wywołania zwrotnego, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 gdzie podpis dla `ValidateServerCertificate` wygląda następująco:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementowanie `ValidateServerCertificate` można wykonać żadnych testów, że deweloper aplikacji klienta uzna za wymagane do weryfikacji certyfikatu usługi.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Sprawdzanie poprawności klienta certyfikaty SSL przez TCP i zabezpieczeniach SOAP  
 Kiedy za pośrednictwem protokołu TCP lub zabezpieczenia komunikatów (SOAP), certyfikaty klienta przy użyciu protokołu Secure Sockets Layer (SSL) są zatwierdzane zgodnie z <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jeden z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości. Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jeden z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Sprawdzanie poprawności certyfikatu usługi SSL przez TCP i zabezpieczeniach SOAP  
 Korzystając z protokołu SSL za pośrednictwem zabezpieczeń wiadomości TCP lub (SOAP), usługa certyfikaty są weryfikowane zgodnie z <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jeden z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości.  
  
 Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jeden z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
