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
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180741"
---
# <a name="listening-with-sockets"></a>Nasłuchiwanie przy użyciu gniazd
Gniazda odbiornika lub serwera otwierają port w sieci, a następnie czekają na połączenie klienta z tym portem. Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć usługę zdalną dla sieci TCP/IP.  
  
 Unikatowy adres usługi TCP/IP jest definiowany przez połączenie adresu IP hosta z numerem portu usługi w celu utworzenia punktu końcowego dla usługi. Klasa <xref:System.Net.Dns> zawiera metody, które zwracają informacje o adresach sieciowych obsługiwanych przez lokalne urządzenie sieciowe. Gdy lokalne urządzenie sieciowe ma więcej niż jeden adres sieciowy lub jeśli system lokalny obsługuje więcej niż jedno urządzenie sieciowe, klasa **Dns** zwraca informacje o wszystkich adresach sieciowych, a aplikacja musi wybrać odpowiedni adres usługi. Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych; Aby uzyskać więcej informacji, zobacz [Nazwa usługi i Rejestr numerów portów protokołu transportu](https://www.iana.org/assignments/port-numbers). Inne usługi mogą mieć zarejestrowane numery portów w zakresie od 1024 do 65 535.  
  
 Poniższy przykład <xref:System.Net.IPEndPoint> tworzy dla serwera przez połączenie pierwszego adresu IP zwróconego przez **dns** dla komputera-hosta z numerem portu wybranym z zakresu numerów zarejestrowanych portów.  
  
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
  
 Po określeniu lokalnego <xref:System.Net.Sockets.Socket> punktu końcowego musi być <xref:System.Net.Sockets.Socket.Bind%2A> skojarzony z tym punktem końcowym <xref:System.Net.Sockets.Socket.Listen%2A> przy użyciu metody i ustawić nasłuchiwać na punkt końcowy przy użyciu metody. **Bind** zgłasza wyjątek, jeśli określona kombinacja adresu i portu jest już używana. W poniższym przykładzie pokazano skojarzenie **socket** z **IPEndPoint**.  
  
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
  
 Listen **Listen** Metoda przyjmuje jeden parametr, który określa, ile oczekujących połączeń **do Gniazda** są dozwolone przed błąd zajęty serwera jest zwracany do klienta łączącego. W takim przypadku do 100 klientów są umieszczane w kolejce połączenia przed serwer zajęty odpowiedzi jest zwracany do numeru klienta 101.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie synchronicznego gniazda serwera](using-a-synchronous-server-socket.md)
- [Używanie asynchronicznego gniazda serwera](using-an-asynchronous-server-socket.md)
- [Używanie gniazd klientów](using-client-sockets.md)
- [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)
- [Gniazda](sockets.md)
