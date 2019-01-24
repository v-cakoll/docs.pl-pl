---
title: Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: f85b45186c7cbc299e68f6f914f591f337aa3993
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517075"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
Umożliwia certyfikaty w Windows Communication Foundation (WCF) z zabezpieczeń wiadomości warstwy (SOAP) oprócz transport layer security (TLS) za pośrednictwem protokołu HTTPS (HTTP) lub TCP. W tym temacie opisano różnice w sposobie takie certyfikaty są weryfikowane.  
  
## <a name="validation-of-https-client-certificates"></a>Sprawdzanie poprawności certyfikatów klientów protokołu HTTPS  
 Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikatu używanego przez klienta do uwierzytelnienia w usłudze musi obsługiwać łańcucha zaufania. Oznacza to, że jej musi zostać połączony zaufany główny urząd certyfikacji. Jeśli nie, wywołuje warstwę HTTP <xref:System.Net.WebException> z komunikatem "serwer zdalny zwrócił błąd: (403) zabroniony." Usługi WCF wydobywa informacje dotyczące tego wyjątku, ponieważ <xref:System.ServiceModel.Security.MessageSecurityException>.  
  
## <a name="validation-of-https-service-certificates"></a>Sprawdzanie poprawności protokołu HTTPS usług certyfikatów  
 Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikat, który uwierzytelnia serwer z musi obsługiwać łańcuch zaufania domyślnie. Oznacza to, że jej musi zostać połączony zaufany główny urząd certyfikacji. Aby zobaczyć, czy certyfikat został odwołany odbywa się nie kontroli w trybie online. Zachowanie to można zastąpić, rejestrując <xref:System.Net.Security.RemoteCertificateValidationCallback> wywołanie zwrotne, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 gdzie podpis dla `ValidateServerCertificate` jest następująca:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementowanie `ValidateServerCertificate` można wykonać wszystkie testy, Deweloper aplikacji klienta jeśli uzna, że wymagane na potrzeby weryfikacji certyfikatu usługi.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Sprawdzanie poprawności certyfikatów klientów SSL przez TCP i zabezpieczeniach SOAP  
 Jeśli przy użyciu protokołu Secure Sockets Layer (SSL) za pośrednictwem protokołu TCP lub zabezpieczenia komunikatów (SOAP), certyfikaty klienta są weryfikowane zgodnie z opisem w <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości. Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Sprawdzanie poprawności certyfikatu usługi SSL przez TCP i zabezpieczeniach SOAP  
 Przy użyciu protokołu SSL przez TCP lub (SOAP) zabezpieczeń wiadomości, usługa certyfikaty są weryfikowane zgodnie z opisem w <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości.  
  
 Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
