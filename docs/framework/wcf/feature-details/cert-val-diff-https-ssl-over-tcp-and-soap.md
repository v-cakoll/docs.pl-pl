---
title: Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
description: Dowiedz się więcej o certyfikatach z zabezpieczeniami w warstwie komunikatów (SOAP), które są oferowane przez usługi WCF oprócz protokołu HTTPS lub TCP oraz jak usługa WCF weryfikuje takie certyfikaty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 97d51e5b65ebf20e80a69512370b68a51eeb28a7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245274"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP
Za pomocą protokołu HTTP (HTTPS) lub TCP (TLS) można używać certyfikatów w programie Windows Communication Foundation (WCF) z zabezpieczeniami warstwy komunikatów (SOAP). W tym temacie opisano różnice w sposobie, w jaki takie certyfikaty zostały zweryfikowane.  
  
## <a name="validation-of-https-client-certificates"></a>Sprawdzanie poprawności certyfikatów klienta HTTPS  
 W przypadku komunikacji między klientem a usługą przy użyciu protokołu HTTPS certyfikat używany przez klienta do uwierzytelniania w usłudze musi obsługiwać zaufanie łańcucha. Oznacza to, że musi być powiązany z zaufanym głównym urzędem certyfikacji. W przeciwnym razie warstwa HTTP zgłasza <xref:System.Net.WebException> komunikat "serwer zdalny zwrócił błąd: (403) zabronione". Platforma WCF wyświetla ten wyjątek jako <xref:System.ServiceModel.Security.MessageSecurityException> .  
  
## <a name="validation-of-https-service-certificates"></a>Sprawdzanie poprawności certyfikatów usługi HTTPS  
 W przypadku komunikacji między klientem a usługą przy użyciu protokołu HTTPS certyfikat, który jest uwierzytelniany przez serwer, musi obsługiwać domyślnie zaufanie do łańcucha. Oznacza to, że musi być powiązany z zaufanym głównym urzędem certyfikacji. Nie jest przeprowadzane sprawdzanie online, aby sprawdzić, czy certyfikat został odwołany. To zachowanie można zastąpić przez zarejestrowanie <xref:System.Net.Security.RemoteCertificateValidationCallback> wywołania zwrotnego, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 gdzie sygnatura `ValidateServerCertificate` jest następująca:  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 Implementacja `ValidateServerCertificate` może wykonać wszelkie sprawdzenia, czy Deweloper aplikacji klienta uzna za niezbędne do zweryfikowania certyfikatu usługi.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>Sprawdzanie poprawności certyfikatów klienta w protokole SSL za pośrednictwem protokołu TCP lub SOAP Security  
 W przypadku korzystania z SSL (SSL) za pośrednictwem protokołu TCP lub komunikatów (SOAP) certyfikaty klienta są weryfikowane zgodnie z <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> wartością właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości. Sprawdzanie odwołania jest wykonywane zgodnie z wartościami <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>Sprawdzanie poprawności certyfikatu usługi w protokole SSL przez TCP i zabezpieczenia SOAP  
 W przypadku korzystania z protokołu SSL przez TCP lub (SOAP), certyfikaty usług są weryfikowane zgodnie z <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> wartością właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości.  
  
 Sprawdzanie odwołania jest wykonywane zgodnie z wartościami <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy. Właściwość jest ustawiona na jedną z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [Praca z certyfikatami](working-with-certificates.md)
