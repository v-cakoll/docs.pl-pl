---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428232"
---
# <a name="networkinformation"></a><span data-ttu-id="8d086-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="8d086-102">NetworkInformation</span></span>
<span data-ttu-id="8d086-103">Obszar <xref:System.Net.NetworkInformation> nazw umożliwia zbieranie informacji o zdarzeniach sieciowych, zmianach, statystykach i właściwościach.</span><span class="sxs-lookup"><span data-stu-id="8d086-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="8d086-104">Można również określić, czy host zdalny <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> jest osiągalny przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="8d086-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="8d086-105">Dostępność sieci i wydarzenia</span><span class="sxs-lookup"><span data-stu-id="8d086-105">Network Availability and Events</span></span>  
 <span data-ttu-id="8d086-106">Klasa <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umożliwia określenie, czy adres sieciowy lub dostępność uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="8d086-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="8d086-107">Aby użyć tej klasy, utwórz program obsługi zdarzeń, <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> aby <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>przetworzyć zmianę i skojarzyć ją z programem .</span><span class="sxs-lookup"><span data-stu-id="8d086-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="8d086-108">Aby uzyskać więcej informacji, zobacz [Jak: Wykrywanie dostępności sieci i zmiany adresu](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="8d086-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="8d086-109">Statystyki i właściwości sieci</span><span class="sxs-lookup"><span data-stu-id="8d086-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="8d086-110">Statystyki sieciowe i właściwości można zbierać na podstawie interfejsu lub protokołu.</span><span class="sxs-lookup"><span data-stu-id="8d086-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="8d086-111">Klasy <xref:System.Net.NetworkInformation.NetworkInterface> <xref:System.Net.NetworkInformation.NetworkInterfaceType>, <xref:System.Net.NetworkInformation.PhysicalAddress> i klasy dają informacje o określonym <xref:System.Net.NetworkInformation.IPInterfaceProperties> <xref:System.Net.NetworkInformation.IPGlobalProperties>interfejsie sieciowym, podczas gdy , , <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>i <xref:System.Net.NetworkInformation.UdpStatistics> klasy dają informacje o pakietach warstwy 3 i warstwy 4.</span><span class="sxs-lookup"><span data-stu-id="8d086-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="8d086-112">Aby uzyskać więcej informacji, zobacz [Jak: Pobierz informacje o interfejsie i protokole](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="8d086-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="8d086-113">Określanie, czy host zdalny jest osiągalny</span><span class="sxs-lookup"><span data-stu-id="8d086-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="8d086-114">Za pomocą <xref:System.Net.NetworkInformation.Ping> tej klasy można określić, czy host zdalny jest w sieci, i osiągalne.</span><span class="sxs-lookup"><span data-stu-id="8d086-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="8d086-115">Aby uzyskać więcej informacji, zobacz [Jak: Ping hosta](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="8d086-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d086-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d086-116">See also</span></span>

- [<span data-ttu-id="8d086-117">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="8d086-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
