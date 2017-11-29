---
title: IPv6 Routing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 21edbfee91a759b0b48f9dd6c0c9e900cdff93f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-routing"></a><span data-ttu-id="5610e-102">IPv6 Routing</span><span class="sxs-lookup"><span data-stu-id="5610e-102">IPv6 Routing</span></span>
<span data-ttu-id="5610e-103">Elastyczne mechanizm routingu przynosi IPv6.</span><span class="sxs-lookup"><span data-stu-id="5610e-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="5610e-104">Ze względu na sposób, w których IPv4 identyfikatory sieci były i są przydzielone, dużych tabel routingu muszą być obsługiwane za routerów, które znajdują się na szkieletowymi Internet.</span><span class="sxs-lookup"><span data-stu-id="5610e-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="5610e-105">Te routery musi znać wszystkich tras, aby przekazywać pakiety, które są potencjalnie skierowany do dowolnego węzła w Internecie.</span><span class="sxs-lookup"><span data-stu-id="5610e-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="5610e-106">Zdolność do agregacji adresów IPv6 umożliwia elastyczne adresowania i znacząco zmniejsza rozmiar tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="5610e-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="5610e-107">W tej nowej architekturze adresowania routerów pośrednich musi śledzić tylko lokalnej części sieci do przekazywania wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="5610e-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="5610e-108">Odnajdowania sąsiadów</span><span class="sxs-lookup"><span data-stu-id="5610e-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="5610e-109">Niektóre funkcje oferowane przez funkcję odnajdowania sąsiadów są:</span><span class="sxs-lookup"><span data-stu-id="5610e-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="5610e-110">Odnajdowanie routera.</span><span class="sxs-lookup"><span data-stu-id="5610e-110">Router discovery.</span></span> <span data-ttu-id="5610e-111">To pozwala hostom na identyfikację routerów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="5610e-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="5610e-112">Adres rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="5610e-112">Address resolution.</span></span> <span data-ttu-id="5610e-113">Dzięki temu węzłów do rozpoznania adresu warstwy linku, aby uzyskać odpowiedni adres następnego przeskoku (wymiana Address Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="5610e-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="5610e-114">Adres automatycznej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5610e-114">Address auto-configuration.</span></span> <span data-ttu-id="5610e-115">Dzięki temu hostów automatycznie skonfigurować adresy globalne i lokalne lokacji.</span><span class="sxs-lookup"><span data-stu-id="5610e-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="5610e-116">Odnajdowania sąsiadów używa Internet Control Message Protocol dla IPv6 (ICMPv6) wiadomości, które obejmują:</span><span class="sxs-lookup"><span data-stu-id="5610e-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="5610e-117">Anons routera.</span><span class="sxs-lookup"><span data-stu-id="5610e-117">Router advertisement.</span></span> <span data-ttu-id="5610e-118">Wysyłane przez router artykule okresowo lub w odpowiedzi na żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="5610e-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="5610e-119">Routery IPv6 używają anonse routera anonsowanie ich dostępności, prefiksy adresów i innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5610e-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="5610e-120">Żądanie routera.</span><span class="sxs-lookup"><span data-stu-id="5610e-120">Router solicitation.</span></span> <span data-ttu-id="5610e-121">Wysyłany przez hosta do żądania routery Link bezpośrednio wysyłać anons routera.</span><span class="sxs-lookup"><span data-stu-id="5610e-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="5610e-122">Żądanie sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="5610e-122">Neighbor solicitation.</span></span> <span data-ttu-id="5610e-123">Wysyłane przez węzły do rozpoznawania adresów, zduplikowany adres wykrywania, lub sprawdź, czy sąsiada jest nadal dostępny.</span><span class="sxs-lookup"><span data-stu-id="5610e-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="5610e-124">Anons sąsiadów.</span><span class="sxs-lookup"><span data-stu-id="5610e-124">Neighbor advertisement.</span></span> <span data-ttu-id="5610e-125">Wysyłane przez węzły, aby odpowiedzieć na żądanie sąsiada lub powiadamiania sąsiadów zmiany adresu warstwy linku.</span><span class="sxs-lookup"><span data-stu-id="5610e-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="5610e-126">Przekierowania.</span><span class="sxs-lookup"><span data-stu-id="5610e-126">Redirect.</span></span> <span data-ttu-id="5610e-127">Wysyłane przez routery, aby wskazać lepsze adres następnego przeskoku do określonego miejsca docelowego dla węzła wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5610e-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5610e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5610e-128">See Also</span></span>  
 [<span data-ttu-id="5610e-129">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="5610e-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="5610e-130">Gniazda</span><span class="sxs-lookup"><span data-stu-id="5610e-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
