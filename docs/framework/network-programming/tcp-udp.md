---
title: TCP-UDP
description: Dowiedz się, w jaki sposób klasy TcpClient, TcpListener i UdpClient obsługują protokoły TCP i UDP, które uwzględniają Szczegóły transferu danych w .NET Framework.
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
ms.openlocfilehash: ae6d2f9ced2235aa1b9b8fada8064d7e4be970a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502096"
---
# <a name="tcp-udp"></a>TCP-UDP
Aplikacje mogą używać usług Transmission Control Protocol (TCP) i UDP (User Datagram Protocol) z <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener> klasami, i <xref:System.Net.Sockets.UdpClient> . Te klasy protokołów są zbudowane na podstawie <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> klasy i należy wziąć pod uwagę Szczegóły transferu danych.  
  
 Klasy protokołu używają metod synchronicznych klasy **Socket** , aby zapewnić prosty i prosty dostęp do usług sieciowych bez konieczności utrzymywania informacji o stanie lub znajomości szczegółów dotyczących konfigurowania gniazd specyficznych dla protokołu. Aby użyć asynchronicznych metod **gniazda** , można użyć metod asynchronicznych dostarczonych przez <xref:System.Net.Sockets.NetworkStream> klasę. Aby uzyskać dostęp do funkcji klasy **Socket** , które nie są uwidaczniane przez klasy protokołów, należy użyć klasy **Socket** .  
  
 **TcpClient** i **TcpListener** reprezentują sieć przy użyciu klasy **NetworkStream** . Używasz <xref:System.Net.Sockets.TcpClient.GetStream%2A> metody do zwrócenia strumienia sieciowego, a następnie Wywołaj <xref:System.Net.Sockets.NetworkStream.Read%2A> metody strumienia i <xref:System.Net.Sockets.NetworkStream.Write%2A> . **NetworkStream** nie jest własnością gniazda bazowego klasy protokołów, dlatego zamknięcie nie ma wpływu na gniazdo.  
  
 Klasa **UdpClient** używa tablicy bajtów do przechowywania datagramu UDP. Używasz <xref:System.Net.Sockets.UdpClient.Send%2A> metody do wysyłania danych do sieci i <xref:System.Net.Sockets.UdpClient.Receive%2A> metody odbierania przychodzącego datagramu.  
  
## <a name="see-also"></a>Zobacz także

- [Stosowanie usług TCP](using-tcp-services.md)
- [Stosowanie usług UDP](using-udp-services.md)
- [Stosowanie strumieni w sieci](using-streams-on-the-network.md)
- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Korzystanie z protokołów aplikacji](using-application-protocols.md)
