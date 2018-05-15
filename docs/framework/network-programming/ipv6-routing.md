---
title: IPv6 Routing
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c3e2662eb444c70d2376a05e44ac84f472f27384
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ipv6-routing"></a><span data-ttu-id="21b96-102">IPv6 Routing</span><span class="sxs-lookup"><span data-stu-id="21b96-102">IPv6 Routing</span></span>
<span data-ttu-id="21b96-103">Elastyczne mechanizm routingu przynosi IPv6.</span><span class="sxs-lookup"><span data-stu-id="21b96-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="21b96-104">Ze względu na sposób, w których IPv4 identyfikatory sieci były i są przydzielone, dużych tabel routingu muszą być obsługiwane za routerów, które znajdują się na szkieletowymi Internet.</span><span class="sxs-lookup"><span data-stu-id="21b96-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="21b96-105">Te routery musi znać wszystkich tras, aby przekazywać pakiety, które są potencjalnie skierowany do dowolnego węzła w Internecie.</span><span class="sxs-lookup"><span data-stu-id="21b96-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="21b96-106">Zdolność do agregacji adresów IPv6 umożliwia elastyczne adresowania i znacząco zmniejsza rozmiar tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="21b96-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="21b96-107">W tej nowej architekturze adresowania routerów pośrednich musi śledzić tylko lokalnej części sieci do przekazywania wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="21b96-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="21b96-108">Odnajdowania sąsiadów</span><span class="sxs-lookup"><span data-stu-id="21b96-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="21b96-109">Niektóre funkcje oferowane przez funkcję odnajdowania sąsiadów są:</span><span class="sxs-lookup"><span data-stu-id="21b96-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="21b96-110">Odnajdowanie routera.</span><span class="sxs-lookup"><span data-stu-id="21b96-110">Router discovery.</span></span> <span data-ttu-id="21b96-111">To pozwala hostom na identyfikację routerów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="21b96-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="21b96-112">Adres rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="21b96-112">Address resolution.</span></span> <span data-ttu-id="21b96-113">Dzięki temu węzłów do rozpoznania adresu warstwy linku, aby uzyskać odpowiedni adres następnego przeskoku (wymiana Address Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="21b96-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="21b96-114">Adres automatycznej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="21b96-114">Address auto-configuration.</span></span> <span data-ttu-id="21b96-115">Dzięki temu hostów automatycznie skonfigurować adresy globalne i lokalne lokacji.</span><span class="sxs-lookup"><span data-stu-id="21b96-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="21b96-116">Odnajdowania sąsiadów używa Internet Control Message Protocol dla IPv6 (ICMPv6) wiadomości, które obejmują:</span><span class="sxs-lookup"><span data-stu-id="21b96-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="21b96-117">Anons routera.</span><span class="sxs-lookup"><span data-stu-id="21b96-117">Router advertisement.</span></span> <span data-ttu-id="21b96-118">Wysyłane przez router artykule okresowo lub w odpowiedzi na żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="21b96-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="21b96-119">Routery IPv6 używają anonse routera anonsowanie ich dostępności, prefiksy adresów i innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="21b96-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="21b96-120">Żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="21b96-120">Router solicitation.</span></span> <span data-ttu-id="21b96-121">Wysyłany przez hosta do żądania routery Link bezpośrednio wysyłać anons routera.</span><span class="sxs-lookup"><span data-stu-id="21b96-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="21b96-122">Żądanie sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="21b96-122">Neighbor solicitation.</span></span> <span data-ttu-id="21b96-123">Wysyłane przez węzły do rozpoznawania adresów, zduplikowany adres wykrywania, lub sprawdź, czy sąsiada jest nadal dostępny.</span><span class="sxs-lookup"><span data-stu-id="21b96-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="21b96-124">Anons sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="21b96-124">Neighbor advertisement.</span></span> <span data-ttu-id="21b96-125">Wysyłane przez węzły, aby odpowiedzieć na żądanie sąsiada lub powiadamiania sąsiadów zmiany adresu warstwy linku.</span><span class="sxs-lookup"><span data-stu-id="21b96-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="21b96-126">Przekierowania.</span><span class="sxs-lookup"><span data-stu-id="21b96-126">Redirect.</span></span> <span data-ttu-id="21b96-127">Wysyłane przez routery, aby wskazać lepsze adres następnego przeskoku do określonego miejsca docelowego dla węzła wysyłania.</span><span class="sxs-lookup"><span data-stu-id="21b96-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b96-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21b96-128">See Also</span></span>  
 [<span data-ttu-id="21b96-129">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="21b96-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="21b96-130">Gniazda</span><span class="sxs-lookup"><span data-stu-id="21b96-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
