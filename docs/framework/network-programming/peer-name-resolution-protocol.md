---
title: Protokół PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70c49198c0198610eaa5001971b7de7efd2951aa
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969866"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="3cbd5-102">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="3cbd5-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="3cbd5-103">W środowiskach peer-to-peer elementów równorzędnych użyć systemy rozpoznawania nazw określonych w ustalaniu siebie nawzajem lokalizacje sieciowe (adresy, protokoły i porty) na podstawie nazw lub innych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="3cbd5-104">W przeszłości rozpoznawania nazw równorzędnych ma zostały skomplikowane natury przejściowy łączność, a także innych braków w ramach systemu nazw domen (DNS).</span><span class="sxs-lookup"><span data-stu-id="3cbd5-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="3cbd5-105">Platforma sieci Peer-to-Peer Microsoft® Windows® rozwiązuje ten problem za pomocą rozpoznawania protokołu PNRP (Peer Name), bezpieczne, skalowalne i dynamicznego rejestrowania nazw oraz protokołu rozpoznawania nazw, zaprojektowane dla Windows XP, a następnie uaktualnienia w Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="3cbd5-106">Protokół PNRP działa bardzo inaczej od tradycyjnych protokołów rozpoznawania nazw, otwierając ekscytujące nowe możliwości dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="3cbd5-107">Z PNRP nazwy elementów równorzędnych może być stosowane do komputera, lub poszczególne aplikacje lub usługi na maszynie.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="3cbd5-108">Rozpoznawania nazw równorzędnych zawiera adres, port i prawdopodobnie Ładunek rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="3cbd5-109">Ten system zalety odporności na uszkodzenia, nie wąskich gardeł i nazwę rozwiązania, które nigdy nie będzie zwracać stare adresy; Wprowadzanie protokołu idealnym rozwiązaniem służącym do lokalizowania użytkowników urządzeń przenośnych.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="3cbd5-110">Pod względem zabezpieczeń, nazwy elementów równorzędnych może być publikowane jako zabezpieczone (chroniony) lub niezabezpieczone (bez ochrony).</span><span class="sxs-lookup"><span data-stu-id="3cbd5-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="3cbd5-111">Protokół PNRP używa kryptografii klucza publicznego do ochrony nazwy bezpiecznego elementów równorzędnych przed fałszowaniem; zarówno komputerów, jak i usług może być nazwany przy użyciu protokołu PNRP.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
-   <span data-ttu-id="3cbd5-112">Peer Name Resolution Protocol pokazuje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3cbd5-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="3cbd5-113">Rozproszone i niemal całkowicie bez użycia serwera.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="3cbd5-114">Serwery są tylko wymagane dla bootstrapping procesu.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="3cbd5-115">Bezpieczne publikowanie nazw bez angażowania osób trzecich.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="3cbd5-116">W przeciwieństwie do publikacji nazwę DNS PNRP nazwa publikacji jest natychmiastowe i bez ponoszenia kosztów finansowych.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="3cbd5-117">Protokół PNRP aktualizacje w w czasie rzeczywistym, co uniemożliwia rozpoznawanie stare adresy.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="3cbd5-118">Rozpoznawanie nazw za pośrednictwem protokołu PNRP wykracza poza komputerów, umożliwiając również rozpoznawania nazw dla usług.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="3cbd5-119">Namespace System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="3cbd5-119">The System.Net.PeerToPeer Namespace</span></span>  
  
-   <span data-ttu-id="3cbd5-120">Funkcje PNRP jest definiowany przez <xref:System.Net.PeerToPeer> przestrzeni nazw w ramach platformy .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="3cbd5-121">Zapewnia ona zestaw typów, które może służyć do rejestrowania i rozpoznawania nazw równorzędnych za pomocą usługi dostępne PNRP.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-  
  
-   <span data-ttu-id="3cbd5-122">(PNRP i mechanizmy rozpoznawania elementów równorzędnych niestandardowe można tworzyć i utworzona przy użyciu typów podawany <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw.)</span><span class="sxs-lookup"><span data-stu-id="3cbd5-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-  
  
-   <span data-ttu-id="3cbd5-123">Podstawowe typy, które są używane do rejestrowania i rozpoznawania nazw za pomocą usługi PNRP dostępne są następujące:</span><span class="sxs-lookup"><span data-stu-id="3cbd5-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-  
  
-   <span data-ttu-id="3cbd5-124"><xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępne chmury PNRP, łącznie z jego zakres.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <span data-ttu-id="3cbd5-125"><xref:System.Net.PeerToPeer.PeerName>: Określa nazwę elementu równorzędnego, który może służyć do rejestrowania i następnie rozpoznawania elementu równorzędnego w chmurze.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <span data-ttu-id="3cbd5-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definiuje rekordu w chmurze PNRP, który zawiera informacje o rejestracji dla elementu równorzędnego, która zawiera punkty końcowe sieci, w których równorzędną można nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <span data-ttu-id="3cbd5-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje procesu rejestracji dla nazwy elementów równorzędnych, włączając w to metody, uruchamianie i zatrzymywanie rejestrowania nazw elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <span data-ttu-id="3cbd5-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazw równorzędnych do swojej sieci punkty końcowe:, w tym synchroniczne i asynchroniczne metody dla rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="3cbd5-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
-  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="3cbd5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3cbd5-129">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [<span data-ttu-id="3cbd5-130">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="3cbd5-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="3cbd5-131">Przykład technologii PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="3cbd5-131">PeerToPeer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179571)
