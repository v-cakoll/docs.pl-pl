---
title: TCP I UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b3e39b952b37f70513b3a84ce6b6059b85e01c28
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080867"
---
# <a name="tcp-udp"></a>TCP I UDP
Aplikacje mogą używać usług Transmission Control Protocol (TCP) i protokołu UDP (User Datagram) za pomocą <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasy. W ramach tych zajęć protokołu są wbudowane w górnej części <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy i zadbać o szczegółach transferu danych.  
  
 Klasy protokołu Użyj metod synchronicznych **gniazda** klasy w celu zapewnienia niezwykle proste dostępu do usług sieciowych bez konieczności utrzymywania informacji o stanie lub wiedząc, szczegółowe informacje o konfigurowaniu gniazda specyficzne dla protokołu. Aby używać asynchronicznych **gniazda** metody, można użyć metod asynchronicznych, dostarczone przez <xref:System.Net.Sockets.NetworkStream> klasy. Dostępu do funkcji z **gniazda** klasy nie jest udostępniany przez protokół klasy, należy użyć **gniazda** klasy.  
  
 **TcpClient** i **TcpListener** reprezentują sieci za pomocą funkcji **Strumień NetworkStream** klasy. Możesz użyć <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodę, aby zwrócić strumień sieci, a następnie wywołaj strumienia <xref:System.Net.Sockets.NetworkStream.Read%2A> i <xref:System.Net.Sockets.NetworkStream.Write%2A> metody. **Strumień NetworkStream** nie jest właścicielem gniazdo podstawowej z klas protokołu, zamykając go nie ma wpływu na gniazda.  
  
 **UdpClient** klasy wykorzystuje tablicę bajtów zawierającą UDP datagram. Możesz użyć <xref:System.Net.Sockets.UdpClient.Send%2A> metodę, aby wysyłać dane do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metodę, aby otrzymywać datagram przychodzących.  
  
## <a name="see-also"></a>Zobacz też  
 [Stosowanie usług TCP](../../../docs/framework/network-programming/using-tcp-services.md)  
 [Stosowanie usług UDP](../../../docs/framework/network-programming/using-udp-services.md)  
 [Stosowanie strumieni w sieci](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Używanie asynchronicznego gniazda klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
