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
# <a name="networkinformation"></a>NetworkInformation
Obszar <xref:System.Net.NetworkInformation> nazw umożliwia zbieranie informacji o zdarzeniach sieciowych, zmianach, statystykach i właściwościach. Można również określić, czy host zdalny <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> jest osiągalny przy użyciu klasy.  
  
## <a name="network-availability-and-events"></a>Dostępność sieci i wydarzenia  
 Klasa <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umożliwia określenie, czy adres sieciowy lub dostępność uległy zmianie. Aby użyć tej klasy, utwórz program obsługi zdarzeń, <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> aby <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>przetworzyć zmianę i skojarzyć ją z programem . Aby uzyskać więcej informacji, zobacz [Jak: Wykrywanie dostępności sieci i zmiany adresu](how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Statystyki i właściwości sieci  
 Statystyki sieciowe i właściwości można zbierać na podstawie interfejsu lub protokołu. Klasy <xref:System.Net.NetworkInformation.NetworkInterface> <xref:System.Net.NetworkInformation.NetworkInterfaceType>, <xref:System.Net.NetworkInformation.PhysicalAddress> i klasy dają informacje o określonym <xref:System.Net.NetworkInformation.IPInterfaceProperties> <xref:System.Net.NetworkInformation.IPGlobalProperties>interfejsie sieciowym, podczas gdy , , <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>i <xref:System.Net.NetworkInformation.UdpStatistics> klasy dają informacje o pakietach warstwy 3 i warstwy 4. Aby uzyskać więcej informacji, zobacz [Jak: Pobierz informacje o interfejsie i protokole](how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Określanie, czy host zdalny jest osiągalny  
 Za pomocą <xref:System.Net.NetworkInformation.Ping> tej klasy można określić, czy host zdalny jest w sieci, i osiągalne. Aby uzyskać więcej informacji, zobacz [Jak: Ping hosta](how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady programowania sieciowego](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
