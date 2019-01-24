---
title: Nasłuchiwanie przy użyciu gniazd
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
ms.openlocfilehash: 763d1106a289e4aa6530eb07971d6ffb7e6095b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527851"
---
# <a name="listening-with-sockets"></a>Nasłuchiwanie przy użyciu gniazd
Gniazda odbiornika lub serwera Otwórz port w sieci, a następnie poczekaj klienta połączyć się z tym portem. Mimo że istnieją inne rodziny adresów sieciowych i protokołów, w tym przykładzie pokazano, jak utworzyć usługi zdalnej sieci TCP/IP.  
  
 Unikatowy adres usługi TCP/IP jest definiowany przez połączenie adres IP hosta i numer portu usługi do tworzenia punktu końcowego usługi. <xref:System.Net.Dns> Klasa dostarcza metody, które zwracają informacje dotyczące adresów sieciowych obsługiwanych przez urządzenie sieci lokalnej. Gdy urządzenie sieci lokalnej ma więcej niż jednego adresu sieciowego, lub jeśli lokalny system obsługuje więcej niż jednego urządzenia sieciowego, **Dns** klasy zwraca informacje o wszystkich adresów sieci i aplikacji, musisz wybrać prawidłowe adres usługi. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common; Aby uzyskać więcej informacji, zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/port-numbers). Inne usługi można zarejestrowano numery portów z zakresu od 1024 do 65 535.  
  
 Poniższy przykład tworzy <xref:System.Net.IPEndPoint> dla serwera, łącząc pierwszy adres IP zwrócony przez **Dns** dla komputera hosta, numer portu wybranego z zakresu numerów portów zarejestrowane.  
  
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
  
 Po lokalnym punktem końcowym jest określana, <xref:System.Net.Sockets.Socket> musi być skojarzony z tego punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> metody i zestawu do nasłuchiwania punktu końcowego za pomocą <xref:System.Net.Sockets.Socket.Listen%2A> metody. **Powiąż** zgłasza wyjątek, jeśli konkretny kombinacji adres i port jest już używana. W poniższym przykładzie pokazano kojarzenie **gniazda** z **IPEndPoint**.  
  
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
  
 **Nasłuchiwania** metoda przyjmuje jeden parametr, który określa liczbę oczekujących połączeń **gniazda** są dozwolone przed zwróceniem błąd zajęty serwera do klienta nawiązującego połączenie. W tym przypadku maksymalnie 100 klientami są umieszczane w kolejce połączenia zanim serwer zajęty odpowiedź jest zwracana do klienta o numerze 101.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie synchronicznego gniazda serwera](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)
- [Używanie asynchronicznego gniazda serwera](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [Używanie gniazd klientów](../../../docs/framework/network-programming/using-client-sockets.md)
- [Instrukcje: Tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [Gniazda](../../../docs/framework/network-programming/sockets.md)
