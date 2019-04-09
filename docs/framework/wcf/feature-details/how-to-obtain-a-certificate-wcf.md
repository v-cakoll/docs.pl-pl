---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 03ee861f7eba8b2ecee6b4697c5b475eacf78c89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093907"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="2e471-102">Instrukcje: Uzyskiwanie certyfikatu (WCF)</span><span class="sxs-lookup"><span data-stu-id="2e471-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="2e471-103">Aby użyć dowolnego narzędzia Windows Communication Foundation (WCF) funkcji, które używają certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="2e471-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="2e471-104">Aby uzyskać certyfikat X.509</span><span class="sxs-lookup"><span data-stu-id="2e471-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="2e471-105">Wybierz jedną z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="2e471-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="2e471-106">Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="2e471-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="2e471-107">Skonfigurować usługi certyfikatów i podpisywania certyfikatów urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2e471-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="2e471-108">, Windows 2000 Server, Windows 2000 Server Datacenter oraz Windows 2000 Datacenter Server uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI).</span><span class="sxs-lookup"><span data-stu-id="2e471-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="2e471-109">W systemie Windows Server 2008, należy użyć [usług certyfikatów Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2e471-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="2e471-110">Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.</span><span class="sxs-lookup"><span data-stu-id="2e471-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e471-111">Niezależnie od tego podejścia, odbiorca żądania SOAP, który zawiera certyfikat X.509, muszą ufać certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="2e471-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="2e471-112">Oznacza to, że certyfikat X.509 lub wystawcy w łańcuchu certyfikatów znajduje się w magazynie certyfikatów zaufanych osób i że certyfikat X.509 nie znajduje się w magazynie certyfikatów niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="2e471-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e471-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e471-113">See also</span></span>

- [<span data-ttu-id="2e471-114">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="2e471-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2e471-115">Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania</span><span class="sxs-lookup"><span data-stu-id="2e471-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
