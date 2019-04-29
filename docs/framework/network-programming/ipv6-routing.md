---
title: Routing IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 0f0fbce84caf096770e49ab47fb1de5b23b44b33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642233"
---
# <a name="ipv6-routing"></a><span data-ttu-id="b59f3-102">Routing IPv6</span><span class="sxs-lookup"><span data-stu-id="b59f3-102">IPv6 Routing</span></span>
<span data-ttu-id="b59f3-103">Elastyczny mechanizm routingu jest to korzyść protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="b59f3-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="b59f3-104">Ze względu na sposób, w których IPv4 zostały identyfikatory sieci i nie są przydzielone, duże tabele routingu muszą być przechowywane przez routery, które znajdują się na szkieletowymi Internet.</span><span class="sxs-lookup"><span data-stu-id="b59f3-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="b59f3-105">Te routery musi znać wszystkie trasy, aby przekazywać pakiety, które są potencjalnie skierowany do dowolnego węzła w Internecie.</span><span class="sxs-lookup"><span data-stu-id="b59f3-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="b59f3-106">Zdolność do agregacji adresów IPv6 umożliwia elastyczne adresowania i znacząco zmniejsza rozmiar tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="b59f3-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="b59f3-107">W tej nowej architektury adresowania routery pośrednie musi śledzić tylko lokalnej części sieci w celu przekazywania wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b59f3-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="b59f3-108">Odnajdywanie sąsiadujących</span><span class="sxs-lookup"><span data-stu-id="b59f3-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="b59f3-109">Niektóre z funkcji oferowanych przez funkcję odnajdowania sąsiadów to:</span><span class="sxs-lookup"><span data-stu-id="b59f3-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="b59f3-110">Odnajdywanie routera.</span><span class="sxs-lookup"><span data-stu-id="b59f3-110">Router discovery.</span></span> <span data-ttu-id="b59f3-111">To pozwala hostom na identyfikację lokalne routery.</span><span class="sxs-lookup"><span data-stu-id="b59f3-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="b59f3-112">Adres rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="b59f3-112">Address resolution.</span></span> <span data-ttu-id="b59f3-113">Dzięki temu węzłów do rozpoznania adresu warstwy linku, aby uzyskać odpowiedni adres następnego przeskoku (wymiana Address Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="b59f3-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="b59f3-114">Adres automatycznej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b59f3-114">Address auto-configuration.</span></span> <span data-ttu-id="b59f3-115">Dzięki temu hosty automatycznie skonfigurować adresów lokalnych i globalnych.</span><span class="sxs-lookup"><span data-stu-id="b59f3-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="b59f3-116">Odnajdywanie sąsiadujących używa Internet Control Message Protocol dla IPv6 (ICMPv6) wiadomości, które obejmują:</span><span class="sxs-lookup"><span data-stu-id="b59f3-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="b59f3-117">Anons routera.</span><span class="sxs-lookup"><span data-stu-id="b59f3-117">Router advertisement.</span></span> <span data-ttu-id="b59f3-118">Wysyłany przez router pseudolosowego okresowo lub w odpowiedzi na żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="b59f3-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="b59f3-119">Routery IPv6 użyć anonse routera, aby anonsować ich dostępności, prefiksów adresów i inne parametry.</span><span class="sxs-lookup"><span data-stu-id="b59f3-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="b59f3-120">Żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="b59f3-120">Router solicitation.</span></span> <span data-ttu-id="b59f3-121">Wysyłany przez hosta, by zażądać, routery łącze natychmiast wysyłać anons routera.</span><span class="sxs-lookup"><span data-stu-id="b59f3-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="b59f3-122">Żądanie sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="b59f3-122">Neighbor solicitation.</span></span> <span data-ttu-id="b59f3-123">Wysyłane przez węzły do rozpoznawania adresów, wykrywanie powtarzających się adresów, lub sprawdź, czy sąsiada jest nadal dostępny.</span><span class="sxs-lookup"><span data-stu-id="b59f3-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="b59f3-124">Anons sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="b59f3-124">Neighbor advertisement.</span></span> <span data-ttu-id="b59f3-125">Wysyłane przez węzły, aby odpowiedzieć na żądanie sąsiadów lub powiadamiania sąsiadów zmianę adresu warstwy linku.</span><span class="sxs-lookup"><span data-stu-id="b59f3-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="b59f3-126">Przekierowanie.</span><span class="sxs-lookup"><span data-stu-id="b59f3-126">Redirect.</span></span> <span data-ttu-id="b59f3-127">Wysyłane przez routery, aby wskazać, lepsze adres następnego przeskoku do określonego miejsca docelowego dla wysyłania węzła.</span><span class="sxs-lookup"><span data-stu-id="b59f3-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59f3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b59f3-128">See also</span></span>

- [<span data-ttu-id="b59f3-129">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="b59f3-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="b59f3-130">Gniazda</span><span class="sxs-lookup"><span data-stu-id="b59f3-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
