---
title: 'Instrukcje: tworzenie gniazda'
description: Dowiedz się, jak zainicjować gniazdo do komunikowania się z urządzeniami zdalnymi. Użyj klasy Socket, aby określić rodzinę adresów, typ gniazda i typ protokołu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502551"
---
# <a name="how-to-create-a-socket"></a>Instrukcje: tworzenie gniazda
Aby można było używać gniazda do komunikowania się z urządzeniami zdalnymi, gniazdo musi być zainicjowane przy użyciu informacji o protokole i adresie sieciowym. Konstruktor dla <xref:System.Net.Sockets.Socket> klasy ma parametry, które określają rodzinę adresów, typ gniazda i typ protokołu, który jest wykorzystywany przez gniazdo do nawiązywania połączeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy gniazdo, którego można użyć do komunikowania się w sieci opartej na protokole TCP/IP, na przykład w Internecie.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Aby użyć protokołu UDP zamiast TCP, należy zmienić typ protokołu, tak jak w poniższym przykładzie:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily>Wyliczenie określa rodziny adresów standardowych używane przez klasę **Socket** do rozpoznawania adresów sieciowych (na przykład członek **AddressFamily. Internetwork** określa rodzinę adresów IP w wersji 4).  
  
 <xref:System.Net.Sockets.SocketType>Wyliczenie określa typ gniazda (na przykład, członek **gniazda. Stream** wskazuje standardowe gniazdo do wysyłania i otrzymywania danych za pomocą sterowania przepływem).  
  
 <xref:System.Net.Sockets.ProtocolType>Wyliczenie określa protokół sieciowy, który ma być używany podczas komunikacji w **gnieździe** (na przykład **ProtocolType. TCP** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType. UDP** wskazuje, że gniazdo używa protokołu UDP.  
  
 Po utworzeniu **gniazda** można zainicjować połączenie ze zdalnym punktem końcowym lub odebrać połączenia z urządzeń zdalnych.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie gniazd klientów](using-client-sockets.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
