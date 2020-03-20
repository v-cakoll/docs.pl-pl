---
title: PNRP w projektowaniu aplikacji
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428206"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="fd47e-102">PNRP w projektowaniu aplikacji</span><span class="sxs-lookup"><span data-stu-id="fd47e-102">PNRP in Application Development</span></span>
<span data-ttu-id="fd47e-103">W systemie Windows Vista aplikacje sieciowe mogą uzyskiwać dostęp do funkcji publikowania nazw i rozpoznawania nazw za pośrednictwem uproszczonego interfejsu programowania aplikacji PNRP (API).</span><span class="sxs-lookup"><span data-stu-id="fd47e-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="fd47e-104">Implementowanie protokołu rozpoznawania nazw elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="fd47e-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="fd47e-105">Za pomocą uproszczonego interfejsu API PNRP chmury nie są jawnie określone w celu zarejestrowania nazwy i adresów; Składnik PNRP automatycznie określa odpowiednie chmury do przyłączenia i adresy do opublikowania w chmurach.</span><span class="sxs-lookup"><span data-stu-id="fd47e-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="fd47e-106">W przypadku wysoce uproszczonej rozpoznawania nazw PNRP w systemie Windows Vista nazwy PNRP są teraz zintegrowane z funkcją getaddrinfo() Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="fd47e-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="fd47e-107">Aby użyć protokołu PNRP do rozpoznania nazwy adresu IPv6, aplikacje mogą użyć funkcji getaddrinfo() do rozpoznawania name.prnp.net w pełni kwalifikowanej nazwy domeny (FQDN), w której nazwa jest rozpoznawana.</span><span class="sxs-lookup"><span data-stu-id="fd47e-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="fd47e-108">Domena pnrp.net jest domeną zastrzeżoną w systemie Windows Vista dla rozpoznawania nazw PNRP.</span><span class="sxs-lookup"><span data-stu-id="fd47e-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="fd47e-109">Przekazywanie wiadomości między aplikacjami PeerToPeer jest nadal obsługiwane przez podstawowe architektury, takie jak PeerChannel i WCF [Large Data i Streaming](../wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="fd47e-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd47e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd47e-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
