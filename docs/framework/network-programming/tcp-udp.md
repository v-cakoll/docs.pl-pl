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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047114"
---
# <a name="tcp-udp"></a>TCP-UDP
Aplikacje mogą używać usług Transmission Control Protocol (TCP) i UDP (User Datagram Protocol) z <xref:System.Net.Sockets.TcpClient>klasami, <xref:System.Net.Sockets.TcpListener>i <xref:System.Net.Sockets.UdpClient> . Te klasy protokołów są zbudowane na podstawie <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy i należy wziąć pod uwagę Szczegóły transferu danych.  
  
 Klasy protokołu używają metod synchronicznych klasy **Socket** , aby zapewnić prosty i prosty dostęp do usług sieciowych bez konieczności utrzymywania informacji o stanie lub znajomości szczegółów dotyczących konfigurowania gniazd specyficznych dla protokołu. Aby użyć asynchronicznych metod **gniazda** , można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasę. Aby uzyskać dostęp do funkcji klasy **Socket** , które nie są uwidaczniane przez klasy protokołów, należy użyć klasy **Socket** .  
  
 **TcpClient** i **TcpListener** reprezentują sieć przy użyciu klasy **NetworkStream** . Używasz metody do zwrócenia strumienia sieciowego, a następnie wywołaj metody <xref:System.Net.Sockets.NetworkStream.Read%2A> strumienia i <xref:System.Net.Sockets.NetworkStream.Write%2A>. <xref:System.Net.Sockets.TcpClient.GetStream%2A> **NetworkStream** nie jest własnością gniazda bazowego klasy protokołów, dlatego zamknięcie nie ma wpływu na gniazdo.  
  
 Klasa **UdpClient** używa tablicy bajtów do przechowywania datagramu UDP. Używasz metody do wysyłania danych do sieci <xref:System.Net.Sockets.UdpClient.Receive%2A> i metody odbierania przychodzącego datagramu. <xref:System.Net.Sockets.UdpClient.Send%2A>  
  
## <a name="see-also"></a>Zobacz także

- [Stosowanie usług TCP](using-tcp-services.md)
- [Stosowanie usług UDP](using-udp-services.md)
- [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
