---
title: Automatyczna konfiguracja IPv6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0332bca146041aa955ea000cfeee78d3f5287036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="c5152-102">Automatyczna konfiguracja IPv6</span><span class="sxs-lookup"><span data-stu-id="c5152-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="c5152-103">Co ważne celu dla protokołu IPv6 jest obsługuje węzła typu Plug and Play.</span><span class="sxs-lookup"><span data-stu-id="c5152-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="c5152-104">Oznacza to, że powinno być możliwe Podłącz węzła do sieci IPv6 i została ona skonfigurowana automatycznie bez interwencji człowieka.</span><span class="sxs-lookup"><span data-stu-id="c5152-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="c5152-105">Typ automatycznej konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c5152-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="c5152-106">Protokół IPv6 obsługuje następujące typy automatycznej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="c5152-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="c5152-107">**Stanowe automatycznej konfiguracji**.</span><span class="sxs-lookup"><span data-stu-id="c5152-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="c5152-108">Ten typ konfiguracji wymaga pewnego poziomu udziału człowieka, ponieważ wymaga Dynamic Host Configuration Protocol dla IPv6 (DHCPv6) serwera dla instalacji i administracji węzłów.</span><span class="sxs-lookup"><span data-stu-id="c5152-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="c5152-109">Serwer DHCPv6 przechowuje listę węzłów, do których podaje informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c5152-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="c5152-110">Zachowuje również informacje o stanie, aby serwer żądał, jak długo każdy adres jest używany, a gdy mogą być dostępne do ponownego przypisania.</span><span class="sxs-lookup"><span data-stu-id="c5152-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="c5152-111">**Bezstanowej konfiguracji automatycznej**.</span><span class="sxs-lookup"><span data-stu-id="c5152-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="c5152-112">Ten typ konfiguracji jest odpowiednie dla małych organizacje i pojedyncze osoby.</span><span class="sxs-lookup"><span data-stu-id="c5152-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="c5152-113">W takim przypadku każdy host Określa jej adresy z zawartości anonsów routera odebrane.</span><span class="sxs-lookup"><span data-stu-id="c5152-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="c5152-114">Aby zdefiniować identyfikator sieci części adresu przy użyciu standardu IEEE EUI-64, jest można założyć unikatowości adres hosta łącze.</span><span class="sxs-lookup"><span data-stu-id="c5152-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="c5152-115">Niezależnie od tego, jak określić adres węzła należy sprawdzić, czy adres potencjalnych jest unikatowy dla łącza lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c5152-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="c5152-116">Jest to, wysyłając żądanie sąsiada wiadomość na adres potencjalnych.</span><span class="sxs-lookup"><span data-stu-id="c5152-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="c5152-117">Jeśli węzeł odbiera odpowiedzi, wie to, czy adres jest już w użyciu, a następnie określić inny adres.</span><span class="sxs-lookup"><span data-stu-id="c5152-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="c5152-118">Mobilność IPv6</span><span class="sxs-lookup"><span data-stu-id="c5152-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="c5152-119">Mnożenie urządzeń przenośnych została wprowadzona nowe wymaganie: urządzenie musi mieć możliwość arbitralnie zmiana lokalizacji w Internecie IPv6 i zachować istniejące połączenia.</span><span class="sxs-lookup"><span data-stu-id="c5152-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="c5152-120">Do tej funkcji, przenośnych węzła jest przypisany adres domowy, w którym go zawsze można połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="c5152-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="c5152-121">Jeśli węzeł przenośny w domu, łączy się link do strony głównej i używa adresu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="c5152-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="c5152-122">Gdy węzeł przenośny jest witryną, agenta macierzystego, który jest zazwyczaj router, przekazuje wiadomości między węzeł przenośny i węzłów, z którymi jest komunikacji.</span><span class="sxs-lookup"><span data-stu-id="c5152-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5152-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5152-123">See Also</span></span>  
 [<span data-ttu-id="c5152-124">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="c5152-124">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="c5152-125">Gniazda</span><span class="sxs-lookup"><span data-stu-id="c5152-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
