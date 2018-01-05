---
title: "Usługa PNRP chmury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a><span data-ttu-id="13ffa-102">Usługa PNRP chmury</span><span class="sxs-lookup"><span data-stu-id="13ffa-102">PNRP Clouds</span></span>
<span data-ttu-id="13ffa-103">PNRP "chmura" reprezentuje zestaw węzłów, które mogą komunikować się ze sobą za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="13ffa-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="13ffa-104">Termin "chmura" jest tożsame z "siatki równorzędnej" i "peer-to-peer wykresu".</span><span class="sxs-lookup"><span data-stu-id="13ffa-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="13ffa-105">Komunikacja między węzłami nigdy nie powinien przechodzą z jednej chmury do innej.</span><span class="sxs-lookup"><span data-stu-id="13ffa-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="13ffa-106">A <xref:System.Net.PeerToPeer.Cloud> wystąpienia jest unikatowo identyfikowana przez jego nazwę, która jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="13ffa-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="13ffa-107">Pojedynczego elementu równorzędnego lub węzeł może być połączone do więcej niż jednej chmury.</span><span class="sxs-lookup"><span data-stu-id="13ffa-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="13ffa-108">Chmury są bardzo ściśle powiązane z interfejsów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="13ffa-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="13ffa-109">Na maszynie wieloadresowego z dwóch kart sieciowych, dołączone do różnych podsieci zostanie zwrócony trzy chmury: jeden dla poszczególnych adresów lokalnych łącza na interfejs i w chmurze pojedynczy zakres globalny.</span><span class="sxs-lookup"><span data-stu-id="13ffa-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="13ffa-110">Usługa PNRP używa trzech chmury "zakresy", w których zakres to grupa komputerów, które są w stanie odnajdować:</span><span class="sxs-lookup"><span data-stu-id="13ffa-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="13ffa-111">Globalne chmury odpowiada zasięg globalny adres IPv6 i adresy globalne i reprezentuje wszystkie komputery w całej Internet IPv6.</span><span class="sxs-lookup"><span data-stu-id="13ffa-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="13ffa-112">Istnieje tylko jeden chmury globalnej.</span><span class="sxs-lookup"><span data-stu-id="13ffa-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="13ffa-113">Link-local chmury odpowiada zakres adresów IPv6 połączenia lokalnego i adresów połączenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="13ffa-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="13ffa-114">Chmury połączenia lokalnego jest przeznaczony dla określonego łącza, które zwykle jest taka sama jak lokalnie dołączone podsieci.</span><span class="sxs-lookup"><span data-stu-id="13ffa-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="13ffa-115">Może istnieć wiele chmur połączenia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="13ffa-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="13ffa-116">Trzeci chmury, chmury specyficzne dla lokacji, odnosi się do witryny IPv6 zakres adresów i adresy lokacji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="13ffa-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="13ffa-117">Ta chmura jest przestarzałe, mimo że nadal jest obsługiwany w protokole PNRP.</span><span class="sxs-lookup"><span data-stu-id="13ffa-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="13ffa-118">Chmury</span><span class="sxs-lookup"><span data-stu-id="13ffa-118">Clouds</span></span>  
 <span data-ttu-id="13ffa-119">Usługa PNRP chmury są reprezentowane przez wystąpienia <xref:System.Net.PeerToPeer.Cloud> klasy.</span><span class="sxs-lookup"><span data-stu-id="13ffa-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="13ffa-120">Grupy chmur używane elementu równorzędnego są reprezentowane przez wystąpień wyliczenia <xref:System.Net.PeerToPeer.CloudCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="13ffa-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="13ffa-121">Kolekcje chmur PNRP znane dla bieżącego elementu równorzędnego można uzyskać przez wywołanie metody statycznych <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13ffa-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="13ffa-122">Poszczególne chmury mają unikatowe nazwy, reprezentowany jako ciąg Unicode 256 znaków.</span><span class="sxs-lookup"><span data-stu-id="13ffa-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="13ffa-123">Te nazwy, wraz z wyżej zakresu, są używane do utworzenia unikatowych wystąpień klasy chmury.</span><span class="sxs-lookup"><span data-stu-id="13ffa-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="13ffa-124">Te wystąpienia można serializować i odtworzyć trwałe użycia.</span><span class="sxs-lookup"><span data-stu-id="13ffa-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="13ffa-125">Po wystąpienia chmury jest utworzyć lub uzyskać, można zarejestrować nazwy elementów równorzędnych z go w celu utworzenia siatkę znanych elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="13ffa-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ffa-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ffa-126">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Cloud>  
 [<span data-ttu-id="13ffa-127">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="13ffa-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
