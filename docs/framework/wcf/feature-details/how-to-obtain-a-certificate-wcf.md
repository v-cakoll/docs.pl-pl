---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="d940b-102">Instrukcje: Uzyskiwanie certyfikatu (WCF)</span><span class="sxs-lookup"><span data-stu-id="d940b-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="d940b-103">Aby użyć dowolnego z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje, które korzystają z certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="d940b-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="d940b-104">Aby uzyskać certyfikat X.509</span><span class="sxs-lookup"><span data-stu-id="d940b-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="d940b-105">Wybierz jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="d940b-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="d940b-106">Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="d940b-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="d940b-107">Skonfiguruj usługi certyfikatów i mieć podpisywania certyfikatów urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d940b-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="d940b-108">, Systemu Windows Server 2000, Windows 2000 Server Datacenter i systemu Windows 2000 Server Datacenter uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI).</span><span class="sxs-lookup"><span data-stu-id="d940b-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="d940b-109">W systemie Windows Server 2008, należy użyć [usługi certyfikatów Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d940b-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="d940b-110">Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.</span><span class="sxs-lookup"><span data-stu-id="d940b-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d940b-111">Sposób należy wykonać, odbiorca żądania SOAP, który zawiera certyfikat X.509 musi traktować jako zaufany certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="d940b-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="d940b-112">Oznacza to, że certyfikat X.509 lub wystawców w łańcuchu certyfikatów jest w magazynie certyfikatów zaufanych osób i że certyfikatu X.509 nie jest w magazynie certyfikatów niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="d940b-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d940b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d940b-113">See Also</span></span>  
 [<span data-ttu-id="d940b-114">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="d940b-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d940b-115">Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="d940b-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
