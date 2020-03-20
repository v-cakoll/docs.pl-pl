---
title: Routing IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047789"
---
# <a name="ipv6-routing"></a><span data-ttu-id="d78ea-102">Routing IPv6</span><span class="sxs-lookup"><span data-stu-id="d78ea-102">IPv6 Routing</span></span>
<span data-ttu-id="d78ea-103">Elastyczny mechanizm routingu jest zaletą protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="d78ea-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="d78ea-104">Ze względu na sposób, w jaki identyfikatory sieci IPv4 były i są przydzielane, duże tabele routingu muszą być obsługiwane przez routery, które znajdują się w szkieletach internetowych.</span><span class="sxs-lookup"><span data-stu-id="d78ea-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="d78ea-105">Routery te muszą znać wszystkie trasy, aby przesyłać dalej pakiety, które są potencjalnie kierowane do dowolnego węzła w Internecie.</span><span class="sxs-lookup"><span data-stu-id="d78ea-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="d78ea-106">Dzięki możliwości agregowania adresów IPv6 umożliwia elastyczne adresowanie i drastycznie zmniejsza rozmiar tabel routingu.</span><span class="sxs-lookup"><span data-stu-id="d78ea-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="d78ea-107">W tej nowej architekturze adresowania routery pośrednie muszą śledzić tylko lokalną część swojej sieci, aby odpowiednio przesyłać dalej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d78ea-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="d78ea-108">Odnajdowanie sąsiada</span><span class="sxs-lookup"><span data-stu-id="d78ea-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="d78ea-109">Niektóre funkcje dostarczone przez Odnajdywanie sąsiadów to:</span><span class="sxs-lookup"><span data-stu-id="d78ea-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="d78ea-110">Odnajdowanie routera.</span><span class="sxs-lookup"><span data-stu-id="d78ea-110">Router discovery.</span></span> <span data-ttu-id="d78ea-111">Dzięki temu hosty mogą identyfikować routery lokalne.</span><span class="sxs-lookup"><span data-stu-id="d78ea-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="d78ea-112">Rozdzielczość adresu.</span><span class="sxs-lookup"><span data-stu-id="d78ea-112">Address resolution.</span></span> <span data-ttu-id="d78ea-113">Dzięki temu węzły mogą rozpoznawać adres warstwy łącza dla odpowiedniego adresu następnego przeskoku (zastąpienie protokołu rozpoznawania adresów [ARP]).</span><span class="sxs-lookup"><span data-stu-id="d78ea-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="d78ea-114">Automatyczna konfiguracja adresu.</span><span class="sxs-lookup"><span data-stu-id="d78ea-114">Address auto-configuration.</span></span> <span data-ttu-id="d78ea-115">Dzięki temu hosty mogą automatycznie konfigurować adresy lokalne i globalne lokacji.</span><span class="sxs-lookup"><span data-stu-id="d78ea-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="d78ea-116">Odnajdowanie sąsiadów używa protokołu internetowego komunikatów sterujących dla komunikatów IPv6 (ICMPv6), które zawierają:</span><span class="sxs-lookup"><span data-stu-id="d78ea-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="d78ea-117">Anons routera.</span><span class="sxs-lookup"><span data-stu-id="d78ea-117">Router advertisement.</span></span> <span data-ttu-id="d78ea-118">Wysyłane przez router pseudo-okresowe lub w odpowiedzi na żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="d78ea-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="d78ea-119">Routery IPv6 używają anonsów routera do reklamowania ich dostępności, prefiksów adresów i innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d78ea-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="d78ea-120">Pozyskiwanie routera.</span><span class="sxs-lookup"><span data-stu-id="d78ea-120">Router solicitation.</span></span> <span data-ttu-id="d78ea-121">Wysłane przez hosta, aby zażądać, aby routery na linku natychmiast wysłać anons routera.</span><span class="sxs-lookup"><span data-stu-id="d78ea-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="d78ea-122">Nagabywanie sąsiada.</span><span class="sxs-lookup"><span data-stu-id="d78ea-122">Neighbor solicitation.</span></span> <span data-ttu-id="d78ea-123">Wysyłane przez węzły w celu rozpoznawania adresów, wykrywania zduplikowanych adresów lub sprawdzenia, czy sąsiad jest nadal osiągalny.</span><span class="sxs-lookup"><span data-stu-id="d78ea-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="d78ea-124">Reklama sąsiada.</span><span class="sxs-lookup"><span data-stu-id="d78ea-124">Neighbor advertisement.</span></span> <span data-ttu-id="d78ea-125">Wysyłane przez węzły w celu udzielenia odpowiedzi na żądanie sąsiada lub powiadomienia sąsiadów o zmianie adresu warstwy łącza.</span><span class="sxs-lookup"><span data-stu-id="d78ea-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="d78ea-126">Przekierowanie.</span><span class="sxs-lookup"><span data-stu-id="d78ea-126">Redirect.</span></span> <span data-ttu-id="d78ea-127">Wysyłane przez routery w celu wskazania lepszego adresu następnego przeskoku do określonego miejsca docelowego dla węzła wysyłającego.</span><span class="sxs-lookup"><span data-stu-id="d78ea-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78ea-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d78ea-128">See also</span></span>

- [<span data-ttu-id="d78ea-129">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="d78ea-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="d78ea-130">Gniazda</span><span class="sxs-lookup"><span data-stu-id="d78ea-130">Sockets</span></span>](sockets.md)
