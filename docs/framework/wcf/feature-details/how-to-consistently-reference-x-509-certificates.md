---
title: 'Instrukcje: Spójne odwoływanie się do certyfikatów X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: efc4fb399224de7f03c6bffb606178184de1d467
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="f99cf-102">Instrukcje: Spójne odwoływanie się do certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="f99cf-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="f99cf-103">Można zidentyfikować certyfikatu na kilka sposobów: przez skrót certyfikatu, wystawcy i numer seryjny lub identyfikator klucza podmiotu (SKI).</span><span class="sxs-lookup"><span data-stu-id="f99cf-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="f99cf-104">SKI zawiera unikatowy identyfikator dla klucz publiczny podmiotu certyfikatu i jest często używany podczas pracy z XML podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="f99cf-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="f99cf-105">Wartość SKI zwykle jest częścią certyfikatu X.509 jako *rozszerzenia certyfikatów X.509*.</span><span class="sxs-lookup"><span data-stu-id="f99cf-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="f99cf-106">Windows Communication Foundation (WCF) ma wartość domyślną *odwołuje się do stylu* które używa wystawcy i numer seryjny, jeśli rozszerzenie SKI brakuje certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f99cf-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="f99cf-107">Jeśli certyfikat zawiera rozszerzenia SKI, domyślne odwołanie do stylu używa SKI do punktu z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="f99cf-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="f99cf-108">Jeśli pośredniej sposób tworzenia aplikacji, można zmienić za pomocą certyfikatów, które nie korzystają z rozszerzenia SKI certyfikaty, które było używane rozszerzenie SKI, zmieniają się także odwołujący się styl używany w wiadomościach generowanych przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f99cf-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="f99cf-109">Jeśli stylu odwołujący się spójne jest wymagany niezależnie od obecności rozszerzenia SKI, jest możliwe do skonfigurowania żądany styl odwołujący się, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f99cf-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99cf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f99cf-110">Example</span></span>  
 <span data-ttu-id="f99cf-111">Poniższy przykład tworzy niestandardowe zabezpieczeń element powiązania, który używa pojedynczy styl odwołujący się zgodne, nazwa wystawcy i numer seryjny.</span><span class="sxs-lookup"><span data-stu-id="f99cf-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f99cf-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f99cf-112">Compiling the Code</span></span>  
 <span data-ttu-id="f99cf-113">Następujących przestrzeni nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="f99cf-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="f99cf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f99cf-114">See Also</span></span>  
 [<span data-ttu-id="f99cf-115">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="f99cf-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
