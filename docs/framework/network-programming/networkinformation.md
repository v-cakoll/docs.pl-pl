---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: de8cb03e6205a83d2cc93ee300eb3fcac1ac5b74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497173"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Przestrzeń nazw umożliwia zbieranie informacji na temat zdarzeń w sieci, zmiany, statystyk i właściwości. Możesz również określić, czy zdalny host jest osiągalny, za pomocą <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> klasy.  
  
## <a name="network-availability-and-events"></a>Dostępność sieci i zdarzenia  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Klasy umożliwia określenie, czy adres sieciowy lub dostępności został zmieniony. Aby użyć tej klasy, należy utworzyć program obsługi zdarzeń, aby przetworzyć zmiany i powiąż ją z <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> lub <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Aby uzyskać więcej informacji, zobacz [jak: Wykrywanie dostępności sieci i zmian adresów](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Właściwości i statystyki sieci  
 Będzie możliwe dalsze zbieranie statystyk sieciowych i właściwości na podstawie interfejsu lub protokołu. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, I <xref:System.Net.NetworkInformation.PhysicalAddress> klasy podać informacje dotyczące konkretnego interfejsu sieciowego, podczas gdy <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, i <xref:System.Net.NetworkInformation.UdpStatistics> klasy podają informacje temat warstwy 3 i 4 pakietów w warstwie. Aby uzyskać więcej informacji, zobacz [jak: Interfejs i informacji o protokole](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Określa, czy zdalny Host jest osiągalne  
 Możesz użyć <xref:System.Net.NetworkInformation.Ping> klasę, aby określić, czy zdalny Host jest w górę, w sieci i jest dostępny. Aby uzyskać więcej informacji, zobacz [jak: Polecenie ping do hosta](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Zobacz także
- [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)
- [Przykład technologii informacje o sieci](https://go.microsoft.com/fwlink/?LinkID=179564)
- [Przykład technologii NetStat narzędzia](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Przykład technologii ping klienta](https://go.microsoft.com/fwlink/?LinkID=179565)
