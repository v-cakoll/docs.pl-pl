---
title: 'Porady: Tworzenie gniazda'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24ec39798f5f31cf20cc5c84714efaae6ccbed52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-socket"></a>Porady: Tworzenie gniazda
Zanim użyjesz gniazda komunikację z urządzeniami zdalnego gniazda musi zostać zainicjowany z informacjami o adresie protokołu i sieci. Konstruktor <xref:System.Net.Sockets.Socket> klasa ma następujące parametry określające rodziny adresów, typ gniazda i typ protokołu, który używa gniazda do nawiązania połączenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy gniazda, który może służyć do komunikacji w sieci opartych na protokole TCP/IP, takich jak Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Aby użyć UDP zamiast protokołu TCP, należy zmienić typ protokołu, jak w poniższym przykładzie:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> Wyliczenie określa rodzin standardowy adres używany przez **gniazda** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** elementu członkowskiego Określa adres IP Rodzina adresów IPv4).  
  
 <xref:System.Net.Sockets.SocketType> Wyliczenie Określa typ gniazda (na przykład **SocketType.Stream** Członkowskie wskazuje standardowe gniazda do wysyłania i odbierania danych za pomocą sterowania przepływem).  
  
 <xref:System.Net.Sockets.ProtocolType> Wyliczenie Określa protokół do użycia przy komunikacji na **gniazda** (na przykład **ProtocolType.Tcp** wskazuje, że gniazda używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazda używa protokołu UDP).  
  
 Po **gniazda** jest tworzony, go można inicjować połączenie zdalnego punktu końcowego lub odbierania połączeń z urządzeń zdalnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie gniazd klientów](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
