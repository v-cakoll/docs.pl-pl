---
title: Używanie gniazd klientów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046956"
---
# <a name="using-client-sockets"></a>Używanie gniazd klientów
Przed rozpoczęciem konwersacji <xref:System.Net.Sockets.Socket>za pośrednictwem programów należy utworzyć potok danych między aplikacją a urządzeniem zdalnym. Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć połączenie TCP/IP z usługą zdalną.  
  
 Protokół TCP/IP używa adresu sieciowego i numeru portu usługi do jednoznacznej identyfikacji usługi. Adres sieciowy identyfikuje określone urządzenie w sieci; numer portu identyfikuje określoną usługę na tym urządzeniu, z którą ma się łączyć. Połączenie adresu sieciowego i portu usługi jest nazywany punktem końcowym, który <xref:System.Net.EndPoint> jest reprezentowany w programie .NET Framework przez klasę. Element podrzędny **programu EndPoint** jest zdefiniowany dla każdej obsługiwanej rodziny adresów; dla rodziny adresów IP, <xref:System.Net.IPEndPoint>klasa jest .  
  
 Klasa <xref:System.Net.Dns> udostępnia usługi nazw domen aplikacjom korzystającym z usług internetowych TCP/IP. Metoda <xref:System.Net.Dns.Resolve%2A> wysyła zapytanie do serwera DNS o mapowanie przyjaznej dla użytkownika nazwy domeny (takiej jak "host.contoso.com") na numeryczny adres internetowy (na przykład 192.168.1.1). **Resolve** zwraca <xref:System.Net.IPHostEntry> listę adresów i aliasów żądanej nazwy. W większości przypadków można użyć pierwszego adresu <xref:System.Net.IPHostEntry.AddressList%2A> zwróconego w tablicy. Poniższy kod <xref:System.Net.IPAddress> otrzymuje adres IP serwera host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych (aby uzyskać więcej informacji, zobacz [Rejestracja numeru portu usługi i protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Inne usługi mogą mieć zarejestrowane numery portów w zakresie od 1024 do 65 535. Poniższy kod łączy adres IP dla host.contoso.com z numerem portu w celu utworzenia zdalnego punktu końcowego dla połączenia.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po określeniu adresu urządzenia zdalnego i wybraniu portu do użycia dla połączenia, aplikacja może podjąć próbę nawiązania połączenia z urządzeniem zdalnym. Poniższy przykład używa istniejącego **ipendpoint** do łączenia się z urządzeniem zdalnym i połowy wszelkich wyjątków, które są generowane.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Używanie synchronicznego gniazda klienta](using-a-synchronous-client-socket.md)
- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Instrukcje: tworzenie gniazda](how-to-create-a-socket.md)
- [Gniazda](sockets.md)
