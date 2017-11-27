---
title: TCP I UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a>TCP I UDP
Aplikacje mogą używać usług Transmission Control Protocol (TCP) i protokół UDP (User Datagram) z <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasy. Te klasy protokołu są wbudowane nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy a zajmie się szczegóły transferu danych.  
  
 Klasy protokołu Użyj metod synchronicznych **gniazda** klasa umożliwia proste i bezpośrednie dostęp do usług sieciowych bez zwiększania utrzymywanie informacji o stanie i wiedzy o szczegóły konfiguracji oparte na protokole gniazda. Aby używać asynchronicznych **gniazda** metod, można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasy. Dostępu do funkcji z **gniazda** klasy nie jest udostępniany przez protokół klasy, należy użyć **gniazda** klasy.  
  
 **TcpClient** i **TcpListener** reprezentują sieci za pomocą funkcji **Strumień NetworkStream** klasy. Możesz użyć <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodę, aby zwrócić strumień sieci, a następnie wywołać strumienia <xref:System.Net.Sockets.NetworkStream.Read%2A> i <xref:System.Net.Sockets.NetworkStream.Write%2A> metody. **Strumień NetworkStream** nie jest właścicielem podstawowej gniazda z klas protokołu, więc jego zamknięciem nie wpływa na gniazdo.  
  
 **UdpClient** klasa korzysta z tablicy bajtów do przechowywania datagramów protokołu UDP. Możesz użyć <xref:System.Net.Sockets.UdpClient.Send%2A> do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metodę, aby odbierać przychodzące datagramów.  
  
## <a name="see-also"></a>Zobacz też  
 [Za pomocą usług TCP](../../../docs/framework/network-programming/using-tcp-services.md)  
 [Za pomocą usług UDP](../../../docs/framework/network-programming/using-udp-services.md)  
 [W sieci za pomocą strumieni](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Przy użyciu gniazda serwera asynchroniczne](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Przy użyciu gniazda asynchroniczne klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Przy użyciu protokołów aplikacji](../../../docs/framework/network-programming/using-application-protocols.md)
