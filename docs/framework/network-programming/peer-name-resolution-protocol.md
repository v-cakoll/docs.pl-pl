---
title: Protokół PNRP
description: Dowiedz się więcej na temat protokołu PNRP (Peer Name Resolution Protocol), bezpiecznej, skalowalnej i dynamicznej rejestracji nazw oraz protokołu rozpoznawania nazw.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502226"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="6dc86-103">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="6dc86-103">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="6dc86-104">W środowiskach komunikacji równorzędnej elementy równorzędne używają określonych systemów rozpoznawania nazw do rozwiązywania wszystkich lokalizacji sieciowych (adresów, protokołów i portów) z nazw lub innych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="6dc86-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="6dc86-105">W przeszłości rozpoznawanie nazw elementów równorzędnych zostało skomplikowane przez niezależną łączność przejściową, a także inne braki w ramach systemu nazw domen (DNS).</span><span class="sxs-lookup"><span data-stu-id="6dc86-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="6dc86-106">Platforma sieci równorzędnej Microsoft® Windows® rozwiązuje ten problem z protokołem rozpoznawania nazw równorzędnych (PNRP), bezpieczną, skalowalną i dynamiczną rejestracją nazw oraz protokołem rozpoznawania nazw, które zostały wcześniej opracowane dla systemu Windows XP, a następnie uaktualnione w™ systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="6dc86-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="6dc86-107">Protokół PNRP działa bardzo inaczej niż tradycyjne systemy rozpoznawania nazw, otwierając nowe możliwości dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dc86-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="6dc86-108">W przypadku protokołu PNRP nazwy elementów równorzędnych mogą być stosowane do komputera lub do poszczególnych aplikacji lub usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6dc86-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="6dc86-109">Rozpoznawanie nazw elementów równorzędnych obejmuje adres, port i prawdopodobnie rozszerzony ładunek.</span><span class="sxs-lookup"><span data-stu-id="6dc86-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="6dc86-110">Zalety tego systemu obejmują odporność na uszkodzenia, brak wąskich gardeł i rozdzielczości nazw, które nigdy nie zwracają starych adresów; uczynienie protokołu doskonałym rozwiązaniem do lokalizowania użytkowników mobilnych.</span><span class="sxs-lookup"><span data-stu-id="6dc86-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="6dc86-111">Pod względem zabezpieczeń nazwy elementów równorzędnych mogą być publikowane jako zabezpieczone (chronione) lub niezabezpieczone (niechronione).</span><span class="sxs-lookup"><span data-stu-id="6dc86-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="6dc86-112">Protokół PNRP używa kryptografii klucza publicznego do ochrony bezpiecznych nazw elementów równorzędnych przed fałszowaniem. zarówno komputery, jak i usługi mogą być nazwane przy użyciu protokołu PNRP.</span><span class="sxs-lookup"><span data-stu-id="6dc86-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="6dc86-113">Protokół rozpoznawania nazw równorzędnych demonstruje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6dc86-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="6dc86-114">Rozpowszechniane i niemal całkowicie bezserwerowe.</span><span class="sxs-lookup"><span data-stu-id="6dc86-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="6dc86-115">Serwery są wymagane tylko dla procesu uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="6dc86-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="6dc86-116">Publikacja z bezpieczną nazwą bez zaangażowania stron trzecich.</span><span class="sxs-lookup"><span data-stu-id="6dc86-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="6dc86-117">W przeciwieństwie do publikacji nazw DNS publikacja nazw PNRP jest natychmiastowa i bez kosztu finansowego.</span><span class="sxs-lookup"><span data-stu-id="6dc86-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="6dc86-118">Aktualizacje protokołu PNRP w czasie rzeczywistym, które uniemożliwiają rozpoznawanie starych adresów.</span><span class="sxs-lookup"><span data-stu-id="6dc86-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="6dc86-119">Rozpoznawanie nazw za pośrednictwem protokołu PNRP wykracza poza komputery, umożliwiając także rozpoznawanie nazw usług.</span><span class="sxs-lookup"><span data-stu-id="6dc86-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="6dc86-120">Przestrzeń nazw System .NET. PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="6dc86-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="6dc86-121">Funkcja PNRP jest definiowana przez <xref:System.Net.PeerToPeer> przestrzeń nazw w .NET Framework w wersji 3,5.</span><span class="sxs-lookup"><span data-stu-id="6dc86-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="6dc86-122">Zawiera zestaw typów, których można użyć do rejestrowania i rozpoznawania nazw elementów równorzędnych z dostępną usługą PNRP.</span><span class="sxs-lookup"><span data-stu-id="6dc86-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="6dc86-123">(Protokół PNRP i niestandardowe rozpoznawania elementów równorzędnych można utworzyć i utworzyć przy użyciu typów dostarczonych w <xref:System.ServiceModel.PeerResolvers> przestrzeni nazw).</span><span class="sxs-lookup"><span data-stu-id="6dc86-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="6dc86-124">Podstawowe typy używane do rejestrowania i rozpoznawania nazw z dostępną usługą PNRP są następujące:</span><span class="sxs-lookup"><span data-stu-id="6dc86-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="6dc86-125"><xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępną chmurę PNRP, w tym jej zakres.</span><span class="sxs-lookup"><span data-stu-id="6dc86-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="6dc86-126"><xref:System.Net.PeerToPeer.PeerName>: Definiuje nazwę elementu równorzędnego, który może służyć do rejestrowania i rozpoznawania elementów równorzędnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="6dc86-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="6dc86-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definiuje rekord w chmurze PNRP zawierający informacje o rejestracji dla elementu równorzędnego, który obejmuje punkty końcowe sieci, w których można skontaktować się z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="6dc86-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="6dc86-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji dla nazwy elementu równorzędnego, w tym metody uruchamiania i zatrzymywania rejestracji nazw elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="6dc86-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="6dc86-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazwy równorzędnej do jej punktów końcowych sieci, w tym metod synchronicznych i asynchronicznych do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6dc86-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc86-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dc86-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="6dc86-131">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="6dc86-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
