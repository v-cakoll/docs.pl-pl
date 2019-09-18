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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046956"
---
# <a name="using-client-sockets"></a>Używanie gniazd klientów
Aby można było zainicjować konwersację za pomocą <xref:System.Net.Sockets.Socket>programu, należy utworzyć potok danych między aplikacją a urządzeniem zdalnym. Chociaż istnieją inne rodziny i protokoły adresów sieciowych, w tym przykładzie pokazano, jak utworzyć połączenie TCP/IP z usługą zdalną.  
  
 Protokół TCP/IP używa adresu sieciowego i numeru portu usługi do unikatowego identyfikowania usługi. Adres sieciowy identyfikuje określone urządzenie w sieci; Numer portu identyfikuje konkretną usługę na tym urządzeniu, z którą ma zostać nawiązane połączenie. Kombinacja adresu sieciowego i portu usługi nosi nazwę punktu końcowego, który jest reprezentowany w .NET Framework przez <xref:System.Net.EndPoint> klasę. Element podrzędny **punktu końcowego** jest zdefiniowany dla każdej obsługiwanej rodziny adresów; w przypadku rodziny adresów IP Klasa jest <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Klasa zapewnia usługi nazw domen dla aplikacji, które korzystają z usług internetowych TCP/IP. <xref:System.Net.Dns.Resolve%2A> Metoda wysyła zapytanie do serwera DNS w celu zamapowania przyjaznej dla użytkownika nazwy domeny (takiej jak "host.contoso.com") na liczbowy adres internetowy (na przykład 192.168.1.1). Funkcja **Rozwiązuj** zwraca <xref:System.Net.IPHostEntry> element zawierający listę adresów i aliasów dla żądanej nazwy. W większości przypadków można użyć pierwszego adresu zwróconego w <xref:System.Net.IPHostEntry.AddressList%2A> tablicy. Poniższy kod pobiera <xref:System.Net.IPAddress> zawierający adres IP serwera Host.contoso.com.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Urząd IANA (Internet Assigned Numbers Authority) definiuje numery portów dla typowych usług (Aby uzyskać więcej informacji, zobacz [rejestr numerów portów i protokołów transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Inne usługi mogą mieć zarejestrowane numery portów z zakresu od 1 024 do 65 535. Poniższy kod łączy adres IP host.contoso.com z numerem portu, aby utworzyć zdalny punkt końcowy dla połączenia.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po ustaleniu adresu urządzenia zdalnego i wybraniu portu do użycia w ramach połączenia aplikacja może próbować nawiązać połączenie z urządzeniem zdalnym. Poniższy przykład używa istniejącej **IPEndPoint** do nawiązywania połączenia z urządzeniem zdalnym i przechwytuje wszystkie zgłoszone wyjątki.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Używanie synchronicznego gniazda klienta](using-a-synchronous-client-socket.md)
- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Instrukcje: Utwórz gniazdo](how-to-create-a-socket.md)
- [Gniazda](sockets.md)
