---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 65b15e61acaa39c9bfc4e0bd81b26f5a211bd1f1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047547"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Przestrzeń nazw umożliwia gromadzenie informacji o zdarzeniach, zmianach, statystykach i właściwościach sieci. Można również określić, czy host zdalny jest osiągalny za pomocą <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> klasy.  
  
## <a name="network-availability-and-events"></a>Dostępność i zdarzenia sieci  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Klasa umożliwia określenie, czy adres sieciowy lub dostępność uległy zmianie. Aby użyć tej klasy, należy utworzyć procedurę obsługi zdarzeń w celu przetworzenia zmiany i skojarzyć ją z <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>lub. Aby uzyskać więcej informacji, zobacz [jak: Wykrywaj zmiany](how-to-detect-network-availability-and-address-changes.md)dostępności i adresów sieci.  
  
## <a name="network-statistics-and-properties"></a>Statystyka i właściwości sieci  
 Można zbierać dane statystyczne i właściwości sieci w interfejsie lub protokole. <xref:System.Net.NetworkInformation.IPGlobalProperties> <xref:System.Net.NetworkInformation.UdpStatistics> <xref:System.Net.NetworkInformation.IPGlobalStatistics> <xref:System.Net.NetworkInformation.TcpStatistics>Klasy <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>i zawierają<xref:System.Net.NetworkInformation.PhysicalAddress> informacje okonkretnyminterfejsiesieciowym,natomiastklasy,,<xref:System.Net.NetworkInformation.IPInterfaceProperties>, i zawierają informacje Informacje o pakietach warstwy 3 i 4. Aby uzyskać więcej informacji, zobacz [jak: Pobierz informacje o](how-to-get-interface-and-protocol-information.md)interfejsie i protokole.  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Określanie, czy host zdalny jest osiągalny  
 <xref:System.Net.NetworkInformation.Ping> Klasy można użyć do określenia, czy host zdalny jest w sieci i osiągalny. Aby uzyskać więcej informacji, zobacz [jak: Wyślij polecenie ping](how-to-ping-a-host.md)do hosta.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady programowania sieciowego](network-programming-samples.md)
- [Przykładowa technologia informacyjna sieci](https://go.microsoft.com/fwlink/?LinkID=179564)
- [Przykład technologii narzędzia netstat](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Przykład polecenia ping dla technologii klienta](https://go.microsoft.com/fwlink/?LinkID=179565)
