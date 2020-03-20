---
title: Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 0e82d1898bec7cda474a5a92958b5af1b30c9de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185406"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
Certyfikaty w programie Windows Communication Foundation (WCF) z zabezpieczeniami warstwy wiadomości (SOAP) oprócz zabezpieczeń warstwy transportu (TLS) za pośrednictwem protokołu HTTP (HTTPS) lub TCP. W tym temacie opisano różnice w sposobie sprawdzania poprawności takich certyfikatów.  
  
## <a name="validation-of-https-client-certificates"></a>Sprawdzanie poprawności certyfikatów klienta HTTPS  
 Podczas korzystania z protokołu HTTPS do komunikowania się między klientem a usługą, certyfikat używany przez klienta do uwierzytelniania w usłudze musi obsługiwać zaufanie łańcucha. Oznacza to, że musi łańcuch do zaufanego głównego urzędu certyfikacji. Jeśli nie, warstwa HTTP <xref:System.Net.WebException> podnosi a z komunikatem "Serwer zdalny zwrócił błąd: (403) Zabronione." WCF powierzchni tego wyjątku <xref:System.ServiceModel.Security.MessageSecurityException>jako .  
  
## <a name="validation-of-https-service-certificates"></a>Sprawdzanie poprawności certyfikatów usługi HTTPS  
 Podczas korzystania z protokołu HTTPS do komunikowania się między klientem a usługą, certyfikat, który serwer uwierzytelnia się z musi obsługiwać zaufanie łańcucha domyślnie. Oznacza to, że musi łańcuch do zaufanego głównego urzędu certyfikacji. Nie jest przeprowadzana kontrola online, aby sprawdzić, czy certyfikat został odwołany. To zachowanie można zastąpić, rejestrując <xref:System.Net.Security.RemoteCertificateValidationCallback> wywołanie zwrotne, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 w przypadku `ValidateServerCertificate` gdy podpis jest następujący:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementacja `ValidateServerCertificate` może wykonywać wszelkie kontrole, które deweloper aplikacji klienckiej uzna za niezbędne do sprawdzania poprawności certyfikatu usługi.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Sprawdzanie poprawności certyfikatów klientów w SSL za demotek TCP lub SOAP  
 W przypadku korzystania z secure sockets layer (SSL) za pośrednictwem zabezpieczeń TCP <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> lub message <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> (SOAP) certyfikaty klienta są sprawdzane zgodnie z wartością właściwości klasy. Właściwość jest ustawiona <xref:System.ServiceModel.Security.X509CertificateValidationMode> na jedną z wartości. Sprawdzanie odwołania jest wykonywane zgodnie z wartościami <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> wartości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> właściwości klasy. Właściwość jest ustawiona <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> na jedną z wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Sprawdzanie poprawności certyfikatu usługi w ssl za 10 TCP i SOAP Security  
 W przypadku korzystania z protokołu SSL za pośrednictwem protokołu TCP <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> lub (SOAP) zabezpieczenia komunikatów, certyfikaty usług są sprawdzane zgodnie z wartością właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona <xref:System.ServiceModel.Security.X509CertificateValidationMode> na jedną z wartości.  
  
 Sprawdzanie odwołania jest wykonywane zgodnie z wartościami <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> wartości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> właściwości klasy. Właściwość jest ustawiona <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> na jedną z wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
