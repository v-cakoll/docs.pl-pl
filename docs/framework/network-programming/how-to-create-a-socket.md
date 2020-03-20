---
title: 'Instrukcje: tworzenie gniazda'
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
ms.openlocfilehash: e71e7e235048361580c65bdb551919fe3038130b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180825"
---
# <a name="how-to-create-a-socket"></a>Instrukcje: tworzenie gniazda
Aby można było używać gniazda do komunikowania się z urządzeniami zdalnymi, gniazdo musi zostać zainicjowane z informacjami o protokole i adresie sieciowym. Konstruktor <xref:System.Net.Sockets.Socket> dla klasy ma parametry, które określają rodzinę adresów, typ gniazda i typ protokołu, którego gniazdo używa do nawiązywać połączenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy Socket, który może służyć do komunikowania się w sieci opartej na TCP/IP, takich jak Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Aby użyć protokołu UDP zamiast protokołu TCP, zmień typ protokołu, tak jak w poniższym przykładzie:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 Wyliczenie <xref:System.Net.Sockets.AddressFamily> określa standardowe rodziny adresów używane przez **Socket** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** element członkowski określa ip wersji 4 rodziny adresów rodziny).  
  
 Wyliczenie <xref:System.Net.Sockets.SocketType> określa typ gniazda (na przykład **SocketType.Stream** element członkowski wskazuje standardowe gniazdo do wysyłania i odbierania danych z kontrolą przepływu).  
  
 Wyliczenie <xref:System.Net.Sockets.ProtocolType> określa protokół sieciowy używany podczas komunikacji na **socket** (na przykład **ProtocolType.Tcp** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazdo używa UDP).  
  
 Po utworzeniu **socket** może zainicjować połączenie ze zdalnym punktem końcowym lub odbierać połączenia z urządzeń zdalnych.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie gniazd klientów](using-client-sockets.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
