---
title: Nasłuchiwanie przy użyciu gniazd
description: Dowiedz się, jak utworzyć usługę zdalną, w której gniazdo serwera otwiera port w sieci i czeka, aż klient nawiąże połączenie z tym portem.
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
ms.openlocfilehash: 0b6de67772bae397373e307ec02ce69a71b0542e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502317"
---
# <a name="listening-with-sockets"></a>Nasłuchiwanie przy użyciu gniazd
Odbiornik lub gniazda serwera otwierają port w sieci, a następnie czekają, aż klient nawiąże połączenie z tym portem. Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć usługę zdalną dla sieci TCP/IP.  
  
 Unikatowy adres usługi TCP/IP jest definiowany przez połączenie adresu IP hosta z numerem portu usługi, aby utworzyć punkt końcowy usługi. <xref:System.Net.Dns>Klasa zawiera metody, które zwracają informacje o adresach sieciowych obsługiwanych przez lokalne urządzenie sieciowe. Jeśli lokalne urządzenie sieciowe ma więcej niż jeden adres sieciowy lub jeśli system lokalny obsługuje więcej niż jedno urządzenie sieciowe, Klasa **DNS** zwraca informacje dotyczące wszystkich adresów sieciowych, a aplikacja musi wybrać właściwy adres dla usługi. Organizacja Internet Assigned Numbers Authority (IANA) definiuje numery portów dla wspólnych usług; Aby uzyskać więcej informacji, zobacz [rejestr numerów portów i protokołów transportu](https://www.iana.org/assignments/port-numbers). Inne usługi mogą mieć zarejestrowane numery portów z zakresu od 1 024 do 65 535.  
  
 Poniższy przykład tworzy <xref:System.Net.IPEndPoint> dla serwera przez połączenie pierwszego adresu IP zwróconego przez serwer **DNS** dla komputera hosta z numerem portu wybranym z zakresu zarejestrowanych numerów portów.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Po ustaleniu lokalnego punktu końcowego <xref:System.Net.Sockets.Socket> należy go skojarzyć z tym punktem końcowym za pomocą <xref:System.Net.Sockets.Socket.Bind%2A> metody i ustawić do nasłuchiwania na punkcie końcowym przy użyciu <xref:System.Net.Sockets.Socket.Listen%2A> metody. **Powiązanie** zgłasza wyjątek, jeśli określony kombinacja adresów i portów jest już w użyciu. Poniższy przykład demonstruje kojarzenie **gniazda** z **IPEndPoint**.  
  
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
  
 Metoda **Listen** przyjmuje jeden parametr, który określa, ile oczekujących połączeń z **gniazdem** jest dozwolonych przed zwróceniem błędu serwera do klienta nawiązującego połączenie. W takim przypadku do 100 klientów są umieszczane w kolejce połączeń przed zwróceniem odpowiedzi serwera na numer klienta 101.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie synchronicznego gniazda serwera](using-a-synchronous-server-socket.md)
- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Używanie gniazd klientów](using-client-sockets.md)
- [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)
- [Gniazda](sockets.md)
