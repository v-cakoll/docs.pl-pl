---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 368401d91aa2a83110631d583660d6ccebf8d4fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="2fa4a-102">Instrukcje: Uzyskiwanie certyfikatu (WCF)</span><span class="sxs-lookup"><span data-stu-id="2fa4a-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="2fa4a-103">Pod kątem używania dowolnych Windows Communication Foundation (WCF) funkcje tego używać certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="2fa4a-104">Aby uzyskać certyfikat X.509</span><span class="sxs-lookup"><span data-stu-id="2fa4a-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="2fa4a-105">Wybierz jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="2fa4a-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="2fa4a-106">Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="2fa4a-107">Skonfiguruj usługi certyfikatów i mieć podpisywania certyfikatów urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="2fa4a-108">, Systemu Windows Server 2000, Windows 2000 Server Datacenter i systemu Windows 2000 Server Datacenter uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI).</span><span class="sxs-lookup"><span data-stu-id="2fa4a-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="2fa4a-109">W systemie Windows Server 2008, należy użyć [usługi certyfikatów Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="2fa4a-110">Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2fa4a-111">Sposób należy wykonać, odbiorca żądania SOAP, który zawiera certyfikat X.509 musi traktować jako zaufany certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="2fa4a-112">Oznacza to, że certyfikat X.509 lub wystawców w łańcuchu certyfikatów jest w magazynie certyfikatów zaufanych osób i że certyfikatu X.509 nie jest w magazynie certyfikatów niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="2fa4a-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa4a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa4a-113">See Also</span></span>  
 [<span data-ttu-id="2fa4a-114">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2fa4a-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2fa4a-115">Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="2fa4a-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
