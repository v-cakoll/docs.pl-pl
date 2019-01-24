---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: f58d4dd9e0d3be8813cb9b08394cb084a9f66f88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684103"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="747a8-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="747a8-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="747a8-103">Wymagany jest certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="747a8-103">Client certificate is required.</span></span> <span data-ttu-id="747a8-104">Nie znaleziono certyfikatu w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="747a8-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="747a8-105">Opis</span><span class="sxs-lookup"><span data-stu-id="747a8-105">Description</span></span>  
 <span data-ttu-id="747a8-106">Ślad wskazuje, czy odbiornik HTTPS odebrane żądanie HTTPS, który nie został skojarzony z certyfikatem klienta.</span><span class="sxs-lookup"><span data-stu-id="747a8-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="747a8-107">Ponieważ odbiornik został skonfigurowany, aby wymagać certyfikaty klienta dla wszystkich żądań HTTPS, odbiornik nie można zweryfikować autentyczności klienta.</span><span class="sxs-lookup"><span data-stu-id="747a8-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747a8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="747a8-108">See also</span></span>
- [<span data-ttu-id="747a8-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="747a8-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="747a8-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="747a8-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="747a8-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="747a8-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
