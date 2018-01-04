---
title: "Instrukcje: Spójne odwoływanie się do certyfikatów X.509"
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
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cc313be8c3d6325630e57e0b0e845ad4902bd2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="819de-102">Instrukcje: Spójne odwoływanie się do certyfikatów X.509</span><span class="sxs-lookup"><span data-stu-id="819de-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="819de-103">Można zidentyfikować certyfikatu na kilka sposobów: przez skrót certyfikatu, wystawcy i numer seryjny lub identyfikator klucza podmiotu (SKI).</span><span class="sxs-lookup"><span data-stu-id="819de-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="819de-104">SKI zawiera unikatowy identyfikator dla klucz publiczny podmiotu certyfikatu i jest często używany podczas pracy z XML podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="819de-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="819de-105">Wartość SKI zwykle jest częścią certyfikatu X.509 jako *rozszerzenia certyfikatów X.509*.</span><span class="sxs-lookup"><span data-stu-id="819de-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="819de-106">ma wartość domyślną *odwołuje się do stylu* które używa wystawcy i numer seryjny, jeśli rozszerzenie SKI brakuje certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="819de-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="819de-107">Jeśli certyfikat zawiera rozszerzenia SKI, domyślne odwołanie do stylu używa SKI do punktu z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="819de-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="819de-108">Jeśli pośredniej sposób tworzenia aplikacji, można zmienić za pomocą certyfikatów, które nie korzystają z rozszerzenia SKI certyfikaty, które było używane rozszerzenie SKI, odwołujący się styl używany w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-wygenerowane wiadomości również zmiany.</span><span class="sxs-lookup"><span data-stu-id="819de-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="819de-109">Jeśli stylu odwołujący się spójne jest wymagany niezależnie od obecności rozszerzenia SKI, jest możliwe do skonfigurowania żądany styl odwołujący się, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="819de-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="819de-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="819de-110">Example</span></span>  
 <span data-ttu-id="819de-111">Poniższy przykład tworzy niestandardowe zabezpieczeń element powiązania, który używa pojedynczy styl odwołujący się zgodne, nazwa wystawcy i numer seryjny.</span><span class="sxs-lookup"><span data-stu-id="819de-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="819de-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="819de-112">Compiling the Code</span></span>  
 <span data-ttu-id="819de-113">Następujących przestrzeni nazw są wymagane, aby skompilować kod:</span><span class="sxs-lookup"><span data-stu-id="819de-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="819de-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="819de-114">See Also</span></span>  
 [<span data-ttu-id="819de-115">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="819de-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
