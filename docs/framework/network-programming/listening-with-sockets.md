---
title: Nasłuchiwanie z gniazda
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f85b63b151bcc20db635f56ec1dfec8df6c92241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="listening-with-sockets"></a>Nasłuchiwanie z gniazda
Gniazda odbiornika lub serwera Otwórz port w sieci, a następnie poczekaj dla klienta połączyć się z tym portem. Mimo że istnieją inne rodziny adresów sieci i protokołów, w tym przykładzie pokazano, jak można utworzyć usługi zdalnej dla sieci TCP/IP.  
  
 Unikatowy adres usługi TCP/IP jest zdefiniowana przez połączenie adres IP hosta i numer portu usługi można utworzyć punktu końcowego usługi. <xref:System.Net.Dns> Klasa dostarcza metody, które zwracają informacje o adresy sieciowe obsługiwane przez urządzenie sieci lokalnej. Gdy urządzenie sieci lokalnej ma więcej niż jednego adresu sieciowego lub systemu lokalnego obsługuje więcej niż jednego urządzenia sieciowego, **Dns** klasy zwraca informacje o wszystkich adresów sieciowych, a aplikacji należy wybrać odpowiednią adres usługi. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (Aby uzyskać więcej informacji, zobacz www.iana.org/assignments/port-numbers). Inne usługi można zarejestrować numery portów z zakresu od 1024 do 65 535.  
  
 Poniższy przykład tworzy <xref:System.Net.IPEndPoint> dla serwera, łącząc pierwszy adres IP zwrócony przez **Dns** komputera-hosta z numerem portu wybrane z zakresu numerów portów zarejestrowany.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Po lokalny punkt końcowy jest określana, <xref:System.Net.Sockets.Socket> musi być skojarzony z tego punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> — metoda i zestawu do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Listen%2A> metody. **Powiąż** zgłasza wyjątek, jeśli konkretnym kombinacji adres i port jest już używana. W poniższym przykładzie pokazano kojarzenie **gniazda** z **IPEndPoint**.  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 **Nasłuchiwania** metoda przyjmuje jeden parametr, który określa liczbę oczekujących połączeń **gniazda** są dozwolone przed zwróceniem do klienta nawiązującego połączenie zajęty błąd serwera. W takim przypadku maksymalnie 100 klientami są umieszczane w kolejce połączenia przed zwróceniem do klienta o numerze 101 zajęty odpowiedź serwera.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie synchronicznego gniazda serwera](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Używanie gniazd klientów](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Instrukcje: tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
