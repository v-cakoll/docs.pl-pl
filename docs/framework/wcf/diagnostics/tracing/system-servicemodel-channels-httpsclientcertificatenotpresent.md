---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 3e3bedca7a46f147ee3d9e143cea7e57095c99d1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602047"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="0f633-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="0f633-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>
<span data-ttu-id="0f633-103">Wymagany jest certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="0f633-103">Client certificate is required.</span></span> <span data-ttu-id="0f633-104">W żądaniu nie znaleziono żadnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="0f633-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f633-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0f633-105">Description</span></span>  
 <span data-ttu-id="0f633-106">Ten ślad wskazuje, że odbiornik protokołu HTTPS otrzymał żądanie HTTPS, które nie zostało skojarzone z certyfikatem klienta.</span><span class="sxs-lookup"><span data-stu-id="0f633-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="0f633-107">Ponieważ odbiornik został skonfigurowany tak, aby wymagał certyfikatów klienta na wszystkich żądaniach HTTPS, odbiornik nie mógł zweryfikować autentyczności klienta.</span><span class="sxs-lookup"><span data-stu-id="0f633-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f633-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f633-108">See also</span></span>

- [<span data-ttu-id="0f633-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0f633-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="0f633-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0f633-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0f633-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0f633-111">Administration and Diagnostics</span></span>](../index.md)
