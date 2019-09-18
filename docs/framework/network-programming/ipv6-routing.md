---
title: Routing IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047789"
---
# <a name="ipv6-routing"></a><span data-ttu-id="0affc-102">Routing IPv6</span><span class="sxs-lookup"><span data-stu-id="0affc-102">IPv6 Routing</span></span>
<span data-ttu-id="0affc-103">Elastyczny mechanizm routingu to korzyść z protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="0affc-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="0affc-104">Ze względu na sposób, w jaki identyfikatory sieci IPv4 zostały i są przydzielone, należy zachować duże tabele routingu na routerach, które są podłączone do Internetu.</span><span class="sxs-lookup"><span data-stu-id="0affc-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="0affc-105">Te routery muszą znać wszystkie trasy w celu przekazywania pakietów, które mogą być kierowane do dowolnego węzła w Internecie.</span><span class="sxs-lookup"><span data-stu-id="0affc-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="0affc-106">Dzięki możliwości agregowania adresów protokół IPv6 umożliwia elastyczne adresowanie, a radykalnie zmniejsza rozmiar tabel routingu.</span><span class="sxs-lookup"><span data-stu-id="0affc-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="0affc-107">W tej nowej architekturze, routery pośrednie muszą śledzić tylko lokalną część swojej sieci, aby zapewnić odpowiednie przesyłanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0affc-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="0affc-108">Odnajdywanie sąsiadów</span><span class="sxs-lookup"><span data-stu-id="0affc-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="0affc-109">Niektóre funkcje dostępne w ramach odnajdywania sąsiadów są następujące:</span><span class="sxs-lookup"><span data-stu-id="0affc-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="0affc-110">Odnajdywanie routerów.</span><span class="sxs-lookup"><span data-stu-id="0affc-110">Router discovery.</span></span> <span data-ttu-id="0affc-111">Pozwala to hostom na identyfikację routerów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0affc-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="0affc-112">Rozpoznawanie adresów.</span><span class="sxs-lookup"><span data-stu-id="0affc-112">Address resolution.</span></span> <span data-ttu-id="0affc-113">Pozwala to węzłom na rozpoznanie adresu warstwy łącza dla odpowiedniego adresu następnego przeskoku (zastępowanie protokołu ARP).</span><span class="sxs-lookup"><span data-stu-id="0affc-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="0affc-114">Automatycznej konfiguracji adresu.</span><span class="sxs-lookup"><span data-stu-id="0affc-114">Address auto-configuration.</span></span> <span data-ttu-id="0affc-115">Pozwala to hostom na automatyczne konfigurowanie adresów lokalnych i globalnych lokacji.</span><span class="sxs-lookup"><span data-stu-id="0affc-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="0affc-116">Funkcja odnajdywania sąsiadów korzysta z protokołu komunikatów sterowania Internetem dla protokołu IPv6 (ICMPv6), które obejmują:</span><span class="sxs-lookup"><span data-stu-id="0affc-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="0affc-117">Anons routera.</span><span class="sxs-lookup"><span data-stu-id="0affc-117">Router advertisement.</span></span> <span data-ttu-id="0affc-118">Wysyłany przez router na zasadzie okresowo lub w odpowiedzi na żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="0affc-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="0affc-119">Routery IPv6 używają anonsów routera do anonsowania dostępności, prefiksów adresów i innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="0affc-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="0affc-120">Żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="0affc-120">Router solicitation.</span></span> <span data-ttu-id="0affc-121">Wysyłany przez hosta w celu uzyskania natychmiastowego wysłania anonsu routera.</span><span class="sxs-lookup"><span data-stu-id="0affc-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="0affc-122">Żądanie sąsiada.</span><span class="sxs-lookup"><span data-stu-id="0affc-122">Neighbor solicitation.</span></span> <span data-ttu-id="0affc-123">Wysyłany przez węzły do rozpoznawania adresów, wykrywania zduplikowanych adresów lub do sprawdzenia, czy sąsiad jest nadal dostępny.</span><span class="sxs-lookup"><span data-stu-id="0affc-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="0affc-124">Anons sąsiada.</span><span class="sxs-lookup"><span data-stu-id="0affc-124">Neighbor advertisement.</span></span> <span data-ttu-id="0affc-125">Wysyłany przez węzły odpowiadające na żądanie sąsiada lub do powiadamiania sąsiadów o zmianie adresu warstwy łącza.</span><span class="sxs-lookup"><span data-stu-id="0affc-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="0affc-126">Przekierowania.</span><span class="sxs-lookup"><span data-stu-id="0affc-126">Redirect.</span></span> <span data-ttu-id="0affc-127">Wysyłany przez routery, aby wskazać lepszy adres następnego przeskoku do określonego miejsca docelowego dla węzła wysyłającego.</span><span class="sxs-lookup"><span data-stu-id="0affc-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0affc-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0affc-128">See also</span></span>

- [<span data-ttu-id="0affc-129">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="0affc-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="0affc-130">Gniazda</span><span class="sxs-lookup"><span data-stu-id="0affc-130">Sockets</span></span>](sockets.md)
