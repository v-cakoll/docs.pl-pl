---
title: 'Instrukcje: Tworzenie gniazda'
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
ms.openlocfilehash: e8f90d2a9e2f2e4bef8d1ab360bfe677bd2bf695
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589704"
---
# <a name="how-to-create-a-socket"></a>Instrukcje: Tworzenie gniazda
Zanim użyjesz gniazda do komunikowania się z urządzeniami zdalnymi gniazda musi zostać zainicjowany z informacjami o adresie protokołu i sieci. Konstruktor <xref:System.Net.Sockets.Socket> klasa ma parametry, które określają rodziny adresów, typ gniazda i typ protokołu, który gniazda używa do nawiązywania połączeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy gniazdo, który może służyć do komunikacji w sieci opartego na protokole IP, takich jak Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Aby użyć protokołu UDP, zamiast połączenia TCP, Zmień typ protokołu, jak w poniższym przykładzie:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> Wyliczenie określa rodzin standardowy adres używany przez **gniazda** klasy do rozpoznawania adresów sieciowych (na przykład **AddressFamily.InterNetwork** elementu członkowskiego Określa adres IP Rodzina adresów w wersji 4).  
  
 <xref:System.Net.Sockets.SocketType> Wyliczenie określa rodzaj gniazd (na przykład **SocketType.Stream** członka wskazuje standardowy gniazda do wysyłania i odbierania danych za pomocą sterowanie przepływem).  
  
 <xref:System.Net.Sockets.ProtocolType> Wyliczenie Określa protokół do użycia przy komunikacji na **gniazda** (na przykład **ProtocolType.Tcp** wskazuje, że gniazdo używa protokołu TCP; **ProtocolType.Udp** wskazuje, że gniazdo używa protokołu UDP).  
  
 Po **gniazda** jest utworzone, jego można inicjować połączenie w celu zdalnego punktu końcowego lub odbierania połączeń z urządzeniami zdalnymi.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie gniazd klientów](../../../docs/framework/network-programming/using-client-sockets.md)
- [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
