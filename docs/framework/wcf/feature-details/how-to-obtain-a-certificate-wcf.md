---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 468298c7a0ea673a90e0cde9d481333fad60e4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="b77c8-102">Instrukcje: Uzyskiwanie certyfikatu (WCF)</span><span class="sxs-lookup"><span data-stu-id="b77c8-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="b77c8-103">Aby użyć dowolnego z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje, które korzystają z certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="b77c8-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="b77c8-104">Aby uzyskać certyfikat X.509</span><span class="sxs-lookup"><span data-stu-id="b77c8-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="b77c8-105">Wybierz jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="b77c8-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="b77c8-106">Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="b77c8-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="b77c8-107">Skonfiguruj usługi certyfikatów i mieć podpisywania certyfikatów urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="b77c8-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="b77c8-108">, Systemu Windows Server 2000, Windows 2000 Server Datacenter i systemu Windows 2000 Server Datacenter uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI).</span><span class="sxs-lookup"><span data-stu-id="b77c8-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="b77c8-109">W systemie Windows Server 2008, należy użyć [usługi certyfikatów Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="b77c8-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="b77c8-110">Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.</span><span class="sxs-lookup"><span data-stu-id="b77c8-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b77c8-111">Sposób należy wykonać, odbiorca żądania SOAP, który zawiera certyfikat X.509 musi traktować jako zaufany certyfikat X.509.</span><span class="sxs-lookup"><span data-stu-id="b77c8-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="b77c8-112">Oznacza to, że certyfikat X.509 lub wystawców w łańcuchu certyfikatów jest w magazynie certyfikatów zaufanych osób i że certyfikatu X.509 nie jest w magazynie certyfikatów niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="b77c8-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77c8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b77c8-113">See Also</span></span>  
 [<span data-ttu-id="b77c8-114">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="b77c8-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="b77c8-115">Porady: Tworzenie certyfikatów tymczasowych do użytku w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="b77c8-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
