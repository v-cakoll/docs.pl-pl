---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 964e76a008e1c18fe9f609f1dd63bce565e95d44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396324"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Przestrzeni nazw umożliwia zebranie informacji o sieci zdarzenia, zmiany statystyk i właściwości. Można również określić, czy zdalny host jest dostępny, za pomocą <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> klasy.  
  
## <a name="network-availability-and-events"></a>Dostępność sieci i zdarzeń  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Klasa umożliwia określenie, czy adres sieciowy lub dostępności został zmieniony. Aby korzystać z tej klasy, Tworzenie procedury obsługi zdarzeń do przetwarzania zmiany i skojarz ją z <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> lub <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Aby uzyskać więcej informacji, zobacz [porady: wykrywanie dostępności sieci i zmiany adresu](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Właściwości i statystyki sieci  
 Możesz zbierać właściwości i statystyki sieci na podstawie interfejsu lub protokołu. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, I <xref:System.Net.NetworkInformation.PhysicalAddress> klasy zapewniające informacje dotyczące konkretnego interfejsu sieciowego, podczas gdy <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, i <xref:System.Net.NetworkInformation.UdpStatistics> klasy zapewniające informacje o warstwy 3 i 4 pakietów warstwy. Aby uzyskać więcej informacji, zobacz [porady: Uzyskiwanie interfejsu i informacje protokołu](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Określa, czy Host zdalny jest osiągalne  
 Można użyć <xref:System.Net.NetworkInformation.Ping> klasę, aby określić, czy Host zdalny jest uruchomiona, w sieci i dostępny. Aby uzyskać więcej informacji, zobacz [porady: polecenie Ping przyjmujące](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Przykładowe technologii informacje o sieci](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [Narzędzie NetStat technologii próbki](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [Przykładowe technologii klienta ping](http://go.microsoft.com/fwlink/?LinkID=179565)
