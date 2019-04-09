---
title: PNRP w projektowaniu aplikacji
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 4cd0d739e58cd252213e8d5c16d29cc612338df6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178142"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="93c70-102">PNRP w projektowaniu aplikacji</span><span class="sxs-lookup"><span data-stu-id="93c70-102">PNRP in Application Development</span></span>
<span data-ttu-id="93c70-103">W systemie Windows Vista sieci aplikacje mają dostęp do nazwy publikacji i funkcji rozpoznawania za pomocą uproszczonego PNRP interfejsu programowania aplikacji (API).</span><span class="sxs-lookup"><span data-stu-id="93c70-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="93c70-104">Implementacja protokołu rozpoznawania nazw równorzędnych</span><span class="sxs-lookup"><span data-stu-id="93c70-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="93c70-105">Uproszczony interfejs API PNRP chmury nie są jawnie określone zarejestrować nazwą i adresami; składnik PNRP automatycznie określa odpowiedniej chmury sprzężenia i adresy do opublikowania w ramach chmury.</span><span class="sxs-lookup"><span data-stu-id="93c70-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="93c70-106">Bardzo uproszczone rozpoznawania nazw PNRP w Windows Vista nazw PNRP są teraz zintegrowane getaddrinfo() funkcji Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="93c70-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="93c70-107">Aby rozpoznać nazwy adresu IPv6 za pomocą PNRP, aplikacje mogą korzystać funkcja getaddrinfo() rozpoznać name.prnp.net w pełni kwalifikowanej domeny nazwę (FQDN), w których nazwa jest nazwą elementu równorzędnego rozwiązywany.</span><span class="sxs-lookup"><span data-stu-id="93c70-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="93c70-108">Domena pnrp.net jest domeny zastrzeżonej w Windows Vista do rozpoznawania nazw PNRP.</span><span class="sxs-lookup"><span data-stu-id="93c70-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="93c70-109">Przekazywanie pomiędzy aplikacjami PeerToPeer komunikatów nadal jest obsługiwany przez podstawowych architektur, takich jak PeerChannel i WCF [duże ilości danych i przesyłanie strumieniowe](https://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="93c70-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c70-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93c70-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
