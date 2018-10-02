---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b5293afbda1bdf13db318b072696c597a12b8187
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48024840"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Przestrzeń nazw umożliwia zbieranie informacji na temat zdarzeń w sieci, zmiany, statystyk i właściwości. Możesz również określić, czy zdalny host jest osiągalny, za pomocą <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> klasy.  
  
## <a name="network-availability-and-events"></a>Dostępność sieci i zdarzenia  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Klasy umożliwia określenie, czy adres sieciowy lub dostępności został zmieniony. Aby użyć tej klasy, należy utworzyć program obsługi zdarzeń, aby przetworzyć zmiany i powiąż ją z <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> lub <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Aby uzyskać więcej informacji, zobacz [instrukcje: wykrywanie dostępności sieci i zmiany adresu](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Właściwości i statystyki sieci  
 Będzie możliwe dalsze zbieranie statystyk sieciowych i właściwości na podstawie interfejsu lub protokołu. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, I <xref:System.Net.NetworkInformation.PhysicalAddress> klasy podać informacje dotyczące konkretnego interfejsu sieciowego, podczas gdy <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, i <xref:System.Net.NetworkInformation.UdpStatistics> klasy podają informacje temat warstwy 3 i 4 pakietów w warstwie. Aby uzyskać więcej informacji, zobacz [porady: pobieranie interfejsu i informacji o protokole](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Określa, czy zdalny Host jest osiągalne  
 Możesz użyć <xref:System.Net.NetworkInformation.Ping> klasę, aby określić, czy zdalny Host jest w górę, w sieci i jest dostępny. Aby uzyskać więcej informacji, zobacz [jak: polecenie Ping do hosta](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykład technologii informacje o sieci](https://go.microsoft.com/fwlink/?LinkID=179564)  
 [Przykład technologii NetStat narzędzia](https://go.microsoft.com/fwlink/?LinkID=179562)  
 [Przykład technologii ping klienta](https://go.microsoft.com/fwlink/?LinkID=179565)
