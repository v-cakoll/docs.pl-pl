---
title: Protokół PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428223"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="6fc50-102">Protokół PNRP</span><span class="sxs-lookup"><span data-stu-id="6fc50-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="6fc50-103">W środowiskach równorzędnych elementy równorzędne używają określonych systemów rozpoznawania nazw do rozpoznawania swoich lokalizacji sieciowych (adresów, protokołów i portów) z nazw lub innych typów identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="6fc50-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="6fc50-104">W przeszłości rozpoznawanie nazw równorzędnych było skomplikowane przez z natury przejściową łączność, a także inne niedociągnięcia w systemie nazw domen (DNS).</span><span class="sxs-lookup"><span data-stu-id="6fc50-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="6fc50-105">Microsoft® Windows® Platforma sieci peer-to-peer rozwiązuje ten problem za pomocą protokołu PNRP (PnRP), bezpiecznego, skalowalnego i dynamicznego protokołu rejestracji nazw i rozpoznawania nazw opracowanego najpierw dla systemu Windows XP, a następnie uaktualnionego w Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="6fc50-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="6fc50-106">PNRP działa zupełnie inaczej niż tradycyjne systemy rozpoznawania nazw, otwierając nowe, ekscytujące możliwości dla twórców aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fc50-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="6fc50-107">Za pomocą PNRP nazwy równorzędne mogą być stosowane do maszyny lub poszczególnych aplikacji lub usług na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6fc50-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="6fc50-108">Rozpoznawanie nazw elementów równorzędnych zawiera adres, port i ewentualnie rozszerzony ładunek.</span><span class="sxs-lookup"><span data-stu-id="6fc50-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="6fc50-109">Zalety tego systemu obejmują odporność na uszkodzenia, brak wąskich gardeł i rozpoznawania nazw, które nigdy nie zwracają starych adresów; co protokół jest doskonałym rozwiązaniem dla lokalizowania użytkowników mobilnych.</span><span class="sxs-lookup"><span data-stu-id="6fc50-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="6fc50-110">Pod względem bezpieczeństwa nazwy równorzędne mogą być publikowane jako zabezpieczone (chronione) lub niezabezpieczone (niezabezpieczone).</span><span class="sxs-lookup"><span data-stu-id="6fc50-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="6fc50-111">PNRP używa kryptografii klucza publicznego do ochrony bezpiecznych nazw elementów równorzędnych przed fałszowaniem; zarówno komputery, jak i usługi mogą być nazwane za pomocą PNRP.</span><span class="sxs-lookup"><span data-stu-id="6fc50-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="6fc50-112">Protokół rozpoznawania nazw elementów równorzędnych pokazuje następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6fc50-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="6fc50-113">Rozproszone i prawie całkowicie bezserwerowe.</span><span class="sxs-lookup"><span data-stu-id="6fc50-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="6fc50-114">Serwery są wymagane tylko dla procesu boottrappingu.</span><span class="sxs-lookup"><span data-stu-id="6fc50-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="6fc50-115">Bezpieczne publikowanie nazw bez udziału osób trzecich.</span><span class="sxs-lookup"><span data-stu-id="6fc50-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="6fc50-116">W przeciwieństwie do publikacji nazw DNS publikacja nazwy PNRP jest natychmiastowa i bez kosztów finansowych.</span><span class="sxs-lookup"><span data-stu-id="6fc50-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="6fc50-117">PnRP aktualizuje się w czasie rzeczywistym, co uniemożliwia rozpoznawanie starych adresów.</span><span class="sxs-lookup"><span data-stu-id="6fc50-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="6fc50-118">Rozpoznawanie nazw za pośrednictwem PNRP wykracza poza komputery, umożliwiając również rozpoznawanie nazw usług.</span><span class="sxs-lookup"><span data-stu-id="6fc50-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="6fc50-119">Obszar nazw System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="6fc50-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="6fc50-120">Funkcja PNRP jest definiowana przez obszar <xref:System.Net.PeerToPeer> nazw w wersji .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="6fc50-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="6fc50-121">Zawiera zestaw typów, które mogą służyć do rejestrowania i rozpoznawania nazw elementów równorzędnych za pomocą dostępnej usługi PNRP.</span><span class="sxs-lookup"><span data-stu-id="6fc50-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="6fc50-122">(PNRP i niestandardowe programy rozpoznawania nazw elementów równorzędnych można tworzyć i tworzyć wystąpienia przy użyciu typów podanych w obszarze <xref:System.ServiceModel.PeerResolvers> nazw).</span><span class="sxs-lookup"><span data-stu-id="6fc50-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="6fc50-123">Podstawowe typy używane do rejestrowania i rozpoznawania nazw za pomocą dostępnej usługi PNRP są następujące:</span><span class="sxs-lookup"><span data-stu-id="6fc50-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="6fc50-124"><xref:System.Net.PeerToPeer.Cloud>: Definiuje informacje opisujące dostępną chmurę PNRP, w tym jej zakres.</span><span class="sxs-lookup"><span data-stu-id="6fc50-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="6fc50-125"><xref:System.Net.PeerToPeer.PeerName>: Definiuje nazwę elementu równorzędnego, który może służyć do rejestrowania, a następnie rozwiązać element równorzędny w chmurze.</span><span class="sxs-lookup"><span data-stu-id="6fc50-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="6fc50-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definiuje rekord w chmurze PNRP, który zawiera informacje rejestracyjne dla elementu równorzędnego, który obejmuje punkty końcowe sieci, w których można skontaktować się z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="6fc50-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="6fc50-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definiuje proces rejestracji nazwy elementu równorzędnego, w tym metody uruchamiania i zatrzymywania rejestracji nazw równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="6fc50-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="6fc50-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definiuje proces rozpoznawania nazwy elementu równorzędnego do jego punktu końcowego sieci, w tym zarówno synchroniczne i asynchroniczne metody rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="6fc50-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc50-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fc50-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="6fc50-130">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="6fc50-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
