---
title: "Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP"
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
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="2adea-102">Różnice dotyczące weryfikacji certyfikatów w protokołach HTTPS, SSL przez TCP i zabezpieczeniach SOAP</span><span class="sxs-lookup"><span data-stu-id="2adea-102">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>
<span data-ttu-id="2adea-103">Można użyć certyfikatów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] z zabezpieczeń wiadomości warstwy (SOAP) oprócz transport layer security (TLS) za pośrednictwem protokołu HTTP (HTTPS) lub TCP.</span><span class="sxs-lookup"><span data-stu-id="2adea-103">You can use certificates in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="2adea-104">W tym temacie opisano różnice w taki sposób, który takie certyfikaty są weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="2adea-104">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="2adea-105">Weryfikacja certyfikatów klienta protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="2adea-105">Validation of HTTPS Client Certificates</span></span>  
 <span data-ttu-id="2adea-106">Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikat używany przez klienta do uwierzytelniania w usłudze musi obsługiwać łańcuch zaufania.</span><span class="sxs-lookup"><span data-stu-id="2adea-106">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="2adea-107">Oznacza to, że należy łańcucha do zaufanego głównego urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2adea-107">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="2adea-108">Jeśli nie, wywołuje warstwę HTTP <xref:System.Net.WebException> z komunikatem "serwer zdalny zwrócił błąd: (403) zabroniony."</span><span class="sxs-lookup"><span data-stu-id="2adea-108">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2adea-109">Wyświetla ten wyjątek jako <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="2adea-109"> surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="2adea-110">Weryfikacja certyfikatów usługi protokołu HTTPS</span><span class="sxs-lookup"><span data-stu-id="2adea-110">Validation of HTTPS Service Certificates</span></span>  
 <span data-ttu-id="2adea-111">Przy użyciu protokołu HTTPS do komunikacji między klientem a usługą, certyfikatu, który uwierzytelnia serwer z musi obsługiwać łańcuch zaufania domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2adea-111">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="2adea-112">Oznacza to, że należy łańcucha do zaufanego głównego urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2adea-112">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="2adea-113">Nie online jest sprawdzane aby zobaczyć, czy certyfikat został odwołany.</span><span class="sxs-lookup"><span data-stu-id="2adea-113">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="2adea-114">To zachowanie można przesłonić, rejestrując <xref:System.Net.Security.RemoteCertificateValidationCallback> wywołania zwrotnego, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2adea-114">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="2adea-115">gdzie podpis dla `ValidateServerCertificate` wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="2adea-115">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="2adea-116">Implementowanie `ValidateServerCertificate` można wykonać żadnych testów, że deweloper aplikacji klienta uzna za wymagane do weryfikacji certyfikatu usługi.</span><span class="sxs-lookup"><span data-stu-id="2adea-116">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="2adea-117">Sprawdzanie poprawności klienta certyfikaty SSL przez TCP i zabezpieczeniach SOAP</span><span class="sxs-lookup"><span data-stu-id="2adea-117">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  
 <span data-ttu-id="2adea-118">Kiedy za pośrednictwem protokołu TCP lub zabezpieczenia komunikatów (SOAP), certyfikaty klienta przy użyciu protokołu Secure Sockets Layer (SSL) są zatwierdzane zgodnie z <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="2adea-118">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="2adea-119">Właściwość jest ustawiona na jeden z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="2adea-119">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="2adea-120">Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="2adea-120">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="2adea-121">Właściwość jest ustawiona na jeden z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="2adea-121">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="2adea-122">Sprawdzanie poprawności certyfikatu usługi SSL przez TCP i zabezpieczeniach SOAP</span><span class="sxs-lookup"><span data-stu-id="2adea-122">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  
 <span data-ttu-id="2adea-123">Korzystając z protokołu SSL za pośrednictwem zabezpieczeń wiadomości TCP lub (SOAP), usługa certyfikaty są weryfikowane zgodnie z <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="2adea-123">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="2adea-124">Właściwość jest ustawiona na jeden z <xref:System.ServiceModel.Security.X509CertificateValidationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="2adea-124">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="2adea-125">Sprawdzanie odwołań odbywa się zgodnie z wartościami <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> wartość właściwości <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="2adea-125">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="2adea-126">Właściwość jest ustawiona na jeden z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="2adea-126">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2adea-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2adea-127">See Also</span></span>  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [<span data-ttu-id="2adea-128">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2adea-128">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
