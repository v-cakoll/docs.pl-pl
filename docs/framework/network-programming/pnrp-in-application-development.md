---
title: "Usługa PNRP w aplikacjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 752b354df897fa37bc45c1bbd1969cf93aac87ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="b01be-102">Usługa PNRP w aplikacjach</span><span class="sxs-lookup"><span data-stu-id="b01be-102">PNRP in Application Development</span></span>
<span data-ttu-id="b01be-103">W systemie Windows Vista sieci aplikacje mają dostęp do nazwy publikacji i funkcji rozpoznawania za pomocą uproszczonego PNRP interfejsu programowania aplikacji (API).</span><span class="sxs-lookup"><span data-stu-id="b01be-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="b01be-104">Implementacja protokołu rozpoznawania nazw równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b01be-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="b01be-105">Z uproszczony interfejs API PNRP chmury nie są jawnie określone zarejestrować z nazwą i adresami; składnik PNRP automatycznie określa odpowiednich chmur sprzężenia i adresów do publikowania w ramach chmury.</span><span class="sxs-lookup"><span data-stu-id="b01be-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="b01be-106">Bardzo uproszczonego rozpoznawania nazw PNRP w systemie Windows Vista nazw PNRP są teraz zintegrowane getaddrinfo() funkcji Windows Sockets.</span><span class="sxs-lookup"><span data-stu-id="b01be-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="b01be-107">Aby rozwiązać nazwę na adres IPv6 przy użyciu usługi PNRP, umożliwia aplikacjom funkcja getaddrinfo() rozwiązać name.prnp.net pełni kwalifikowanej domeny nazwę (FQDN), w których nazwa jest rozwiązywany nazwa elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="b01be-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="b01be-108">Domena pnrp.net jest domeną zastrzeżonego w systemie Windows Vista do rozpoznawania nazw PNRP.</span><span class="sxs-lookup"><span data-stu-id="b01be-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="b01be-109">Przekazywanie między aplikacjami PeerToPeer komunikat nadal jest obsługiwany przez podstawowej architektury, takie jak PeerChannel i WCF [duże ilości danych i przesyłania strumieniowego](http://go.microsoft.com/fwlink/?LinkID=179652).</span><span class="sxs-lookup"><span data-stu-id="b01be-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](http://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01be-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b01be-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
