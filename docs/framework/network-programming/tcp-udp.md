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
manager: markl
ms.openlocfilehash: 30630f397d491a6a5f251ddac14a4db90e53b999
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394608"
---
# <a name="tcp-udp"></a>TCP I UDP
Aplikacje mogą używać usług Transmission Control Protocol (TCP) i protokół UDP (User Datagram) z <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasy. Te klasy protokołu są wbudowane nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy a zajmie się szczegóły transferu danych.  
  
 Klasy protokołu Użyj metod synchronicznych **gniazda** klasa umożliwia proste i bezpośrednie dostęp do usług sieciowych bez zwiększania utrzymywanie informacji o stanie i wiedzy o szczegóły konfiguracji oparte na protokole gniazda. Aby używać asynchronicznych **gniazda** metod, można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasy. Dostępu do funkcji z **gniazda** klasy nie jest udostępniany przez protokół klasy, należy użyć **gniazda** klasy.  
  
 **TcpClient** i **TcpListener** reprezentują sieci za pomocą funkcji **Strumień NetworkStream** klasy. Możesz użyć <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodę, aby zwrócić strumień sieci, a następnie wywołać strumienia <xref:System.Net.Sockets.NetworkStream.Read%2A> i <xref:System.Net.Sockets.NetworkStream.Write%2A> metody. **Strumień NetworkStream** nie jest właścicielem podstawowej gniazda z klas protokołu, więc jego zamknięciem nie wpływa na gniazdo.  
  
 **UdpClient** klasa korzysta z tablicy bajtów do przechowywania datagramów protokołu UDP. Możesz użyć <xref:System.Net.Sockets.UdpClient.Send%2A> do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metodę, aby odbierać przychodzące datagramów.  
  
## <a name="see-also"></a>Zobacz też  
 [Stosowanie usług TCP](../../../docs/framework/network-programming/using-tcp-services.md)  
 [Stosowanie usług UDP](../../../docs/framework/network-programming/using-udp-services.md)  
 [Stosowanie strumieni w sieci](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Używanie asynchronicznego gniazda klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Korzystanie z protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
