---
title: 'Instrukcje: Stale odwołanie certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2468faabfbca57e7d905a592b6743c43cb2ccd56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731975"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="2b71f-102">Instrukcje: Stale odwołanie certyfikatu X.509</span><span class="sxs-lookup"><span data-stu-id="2b71f-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="2b71f-103">Można zidentyfikować certyfikatu na kilka sposobów: przez skrót certyfikatu, przez wystawcę i numer seryjny lub przez identyfikator klucza podmiotu (NARCIARSKIE).</span><span class="sxs-lookup"><span data-stu-id="2b71f-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="2b71f-104">NARCIARSKIE zawiera unikatowy identyfikator dla klucz publiczny podmiotu certyfikatu i jest często używana podczas pracy z XML cyfrowego podpisywania.</span><span class="sxs-lookup"><span data-stu-id="2b71f-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="2b71f-105">Wartość NARCIARSKIE jest zazwyczaj część certyfikatu X.509 jako *rozszerzenia certyfikatów X.509*.</span><span class="sxs-lookup"><span data-stu-id="2b71f-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="2b71f-106">Windows Communication Foundation (WCF) ma wartość domyślną *odwołanie do stylu* , jeżeli wystawcy i numer seryjny rozszerzenia NARCIARSKIE brakuje certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="2b71f-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="2b71f-107">Jeśli certyfikat zawiera rozszerzenie NARCIARSKIE, domyślne odwołanie do stylu używa NARCIARSKIE wskaż certyfikat.</span><span class="sxs-lookup"><span data-stu-id="2b71f-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="2b71f-108">Środku sposób przez proces tworzenia aplikacji, możesz przejść z korzystania z certyfikatów, które nie korzystają z rozszerzenia NARCIARSKIE certyfikaty, które mają rozszerzenie NARCIARSKIE, zmienia także odwołujący się styl używany w wiadomościach generowanych przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2b71f-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="2b71f-109">Jeśli jednolitego stylu odwołujący się jest wymagany niezależnie od obecności rozszerzenia NARCIARSKIE, jest możliwość skonfigurowania żądany styl odwołujący się, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2b71f-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b71f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b71f-110">Example</span></span>  
 <span data-ttu-id="2b71f-111">Poniższy przykład tworzy niestandardowe zabezpieczeń element powiązania, który używa pojedynczego jednolitego stylu odwołujący się, nazwy wystawcy i numer seryjny.</span><span class="sxs-lookup"><span data-stu-id="2b71f-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2b71f-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2b71f-112">Compiling the Code</span></span>  
 <span data-ttu-id="2b71f-113">Następujące przestrzenie nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="2b71f-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="2b71f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b71f-114">See also</span></span>
- [<span data-ttu-id="2b71f-115">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2b71f-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
