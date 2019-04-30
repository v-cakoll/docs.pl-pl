---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 15ae13563cfcfb3765559cafb2d31bd6482df7b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767315"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="928fa-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="928fa-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="928fa-103">Wymagany jest certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="928fa-103">Client certificate is required.</span></span> <span data-ttu-id="928fa-104">Nie znaleziono certyfikatu w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="928fa-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="928fa-105">Opis</span><span class="sxs-lookup"><span data-stu-id="928fa-105">Description</span></span>  
 <span data-ttu-id="928fa-106">Ślad wskazuje, czy odbiornik HTTPS odebrane żądanie HTTPS, który nie został skojarzony z certyfikatem klienta.</span><span class="sxs-lookup"><span data-stu-id="928fa-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="928fa-107">Ponieważ odbiornik został skonfigurowany, aby wymagać certyfikaty klienta dla wszystkich żądań HTTPS, odbiornik nie można zweryfikować autentyczności klienta.</span><span class="sxs-lookup"><span data-stu-id="928fa-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928fa-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="928fa-108">See also</span></span>

- [<span data-ttu-id="928fa-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="928fa-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="928fa-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="928fa-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="928fa-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="928fa-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
