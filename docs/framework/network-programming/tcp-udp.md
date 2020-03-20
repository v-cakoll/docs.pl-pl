---
title: TCP-UDP
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
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047114"
---
# <a name="tcp-udp"></a>TCP-UDP
Aplikacje mogą korzystać z usług Protokołu TCP (Transmission Control <xref:System.Net.Sockets.TcpClient>Protocol) i User Datagram Protocol (UDP) z programem <xref:System.Net.Sockets.TcpListener>, i <xref:System.Net.Sockets.UdpClient> klasami. Te klasy protokołu są zbudowane <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> na szczycie klasy i dbać o szczegóły przesyłania danych.  
  
 Klasy protokołu używają synchronicznych metod **Socket** klasy, aby zapewnić prosty i prosty dostęp do usług sieciowych bez narzutu z utrzymaniem informacji o stanie lub znając szczegóły konfigurowania gniazd specyficznych dla protokołu. Aby użyć metod asynchronii **Socket,** można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasę. Aby uzyskać dostęp do funkcji **Socket** klasy nie są udostępniane przez klasy protokołu, należy użyć **Socket** klasy.  
  
 **TcpClient** i **TcpListener** reprezentują sieć przy użyciu klasy **NetworkStream.** Metoda służy <xref:System.Net.Sockets.TcpClient.GetStream%2A> do zwracania strumienia sieciowego, a <xref:System.Net.Sockets.NetworkStream.Read%2A> <xref:System.Net.Sockets.NetworkStream.Write%2A> następnie wywołać strumień i metody. **NetworkStream** nie jest właścicielem gniazda podstawowej klas protokołu, więc zamknięcie nie wpływa na gniazdo.  
  
 **Klasa UdpClient** używa tablicy bajtów do przechowywania datagramu UDP. Metoda wysyłania <xref:System.Net.Sockets.UdpClient.Send%2A> danych do sieci służy <xref:System.Net.Sockets.UdpClient.Receive%2A> do wysyłania danych, a metoda odbierania przychodzącego datagramu.  
  
## <a name="see-also"></a>Zobacz też

- [Stosowanie usług TCP](using-tcp-services.md)
- [Stosowanie usług UDP](using-udp-services.md)
- [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
