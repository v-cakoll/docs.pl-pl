---
title: Protokół PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428223"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="e17a3-102">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="e17a3-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="e17a3-103">W środowiskach komunikacji równorzędnej elementy równorzędne używają określonych systemów rozpoznawania nazw do rozwiązywania wszystkich lokalizacji sieciowych (adresów, protokołów i portów) z nazw lub innych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="e17a3-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="e17a3-104">W przeszłości rozpoznawanie nazw elementów równorzędnych zostało skomplikowane przez niezależną łączność przejściową, a także inne braki w ramach systemu nazw domen (DNS).</span><span class="sxs-lookup"><span data-stu-id="e17a3-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="e17a3-105">Platforma sieci równorzędnej Microsoft® Windows® rozwiązuje ten problem z protokołem rozpoznawania nazw równorzędnych (PNRP), bezpieczną, skalowalną i dynamiczną rejestracją nazw oraz protokołem rozpoznawania nazw, które zostały wcześniej opracowane dla systemu Windows XP, a następnie uaktualnione w programie ™ Systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="e17a3-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="e17a3-106">Protokół PNRP działa bardzo inaczej niż tradycyjne systemy rozpoznawania nazw, otwierając nowe możliwości dla deweloperów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e17a3-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="e17a3-107">W przypadku protokołu PNRP nazwy elementów równorzędnych mogą być stosowane do komputera lub do poszczególnych aplikacji lub usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e17a3-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="e17a3-108">Rozpoznawanie nazw elementów równorzędnych obejmuje adres, port i prawdopodobnie rozszerzony ładunek.</span><span class="sxs-lookup"><span data-stu-id="e17a3-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="e17a3-109">Zalety tego systemu obejmują odporność na uszkodzenia, brak wąskich gardeł i rozdzielczości nazw, które nigdy nie zwracają starych adresów; uczynienie protokołu doskonałym rozwiązaniem do lokalizowania użytkowników mobilnych.</span><span class="sxs-lookup"><span data-stu-id="e17a3-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="e17a3-110">Pod względem zabezpieczeń nazwy elementów równorzędnych mogą być publikowane jako zabezpieczone (chronione) lub niezabezpieczone (niechronione).</span><span class="sxs-lookup"><span data-stu-id="e17a3-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="e17a3-111">Protokół PNRP używa kryptografii klucza publicznego do ochrony bezpiecznych nazw elementów równorzędnych przed fałszowaniem. zarówno komputery, jak i usługi mogą być nazwane przy użyciu protokołu PNRP.</span><span class="sxs-lookup"><span data-stu-id="e17a3-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="e17a3-112">Protokół rozpoznawania nazw równorzędnych demonstruje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e17a3-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="e17a3-113">Rozpowszechniane i niemal całkowicie bezserwerowe.</span><span class="sxs-lookup"><span data-stu-id="e17a3-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="e17a3-114">Serwery są wymagane tylko dla procesu uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e17a3-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="e17a3-115">Publikacja z bezpieczną nazwą bez zaangażowania stron trzecich.</span><span class="sxs-lookup"><span data-stu-id="e17a3-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="e17a3-116">W przeciwieństwie do publikacji nazw DNS publikacja nazw PNRP jest natychmiastowa i bez kosztu finansowego.</span><span class="sxs-lookup"><span data-stu-id="e17a3-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="e17a3-117">Aktualizacje protokołu PNRP w czasie rzeczywistym, które uniemożliwiają rozpoznawanie starych adresów.</span><span class="sxs-lookup"><span data-stu-id="e17a3-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="e17a3-118">Rozpoznawanie nazw za pośrednictwem protokołu PNRP wykracza poza komputery, umożliwiając także rozpoznawanie nazw usług.</span><span class="sxs-lookup"><span data-stu-id="e17a3-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="e17a3-119">Przestrzeń nazw System .NET. PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="e17a3-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="e17a3-120">Funkcja PNRP jest definiowana przez przestrzeń nazw <xref:System.Net.PeerToPeer> w .NET Framework wersji 3,5.</span><span class="sxs-lookup"><span data-stu-id="e17a3-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="e17a3-121">Zawiera zestaw typów, których można użyć do rejestrowania i rozpoznawania nazw elementów równorzędnych z dostępną usługą PNRP.</span><span class="sxs-lookup"><span data-stu-id="e17a3-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="e17a3-122">(Protokół PNRP i niestandardowe rozpoznawania elementów równorzędnych można utworzyć i utworzyć przy użyciu typów podanych w przestrzeni nazw <xref:System.ServiceModel.PeerResolvers>).</span><span class="sxs-lookup"><span data-stu-id="e17a3-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="e17a3-123">Podstawowe typy używane do rejestrowania i rozpoznawania nazw z dostępną usługą PNRP są następujące:</span><span class="sxs-lookup"><span data-stu-id="e17a3-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="e17a3-124"><xref:System.Net.PeerToPeer.Cloud>: definiuje informacje opisujące dostępną chmurę PNRP, w tym jej zakres.</span><span class="sxs-lookup"><span data-stu-id="e17a3-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="e17a3-125"><xref:System.Net.PeerToPeer.PeerName>: Określa nazwę elementu równorzędnego, który może służyć do rejestrowania i rozpoznawania elementów równorzędnych w chmurze.</span><span class="sxs-lookup"><span data-stu-id="e17a3-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="e17a3-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: określa rekord w chmurze PNRP zawierający informacje o rejestracji elementu równorzędnego, który obejmuje punkty końcowe sieci, w których można skontaktować się z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="e17a3-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="e17a3-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: definiuje proces rejestracji dla nazwy elementu równorzędnego, w tym metody uruchamiania i zatrzymywania rejestracji nazw elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="e17a3-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="e17a3-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: definiuje proces rozpoznawania nazwy elementu równorzędnego do jego punktów końcowych sieci, w tym metod synchronicznych i asynchronicznych do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e17a3-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17a3-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e17a3-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="e17a3-130">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="e17a3-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
