---
title: Używanie klienta gniazd
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-client-sockets"></a>Używanie klienta gniazd
Przed rozpoczęciem konwersacji za pośrednictwem <xref:System.Net.Sockets.Socket>, należy utworzyć potok danych pomiędzy aplikacją i urządzenia zdalnego. Mimo że istnieją inne rodziny adresów sieci i protokołów, w tym przykładzie pokazano, jak można utworzyć połączenia TCP/IP do zdalnej usługi.  
  
 Protokół TCP/IP używa adresu sieciowego i numer portu usługi do jednoznacznej identyfikacji usługi. Adres sieciowy identyfikuje konkretnym urządzeniu w sieci. numer portu identyfikuje określonej usługi na tym urządzeniu, aby nawiązać połączenie. Kombinacja portu adres i usługi sieci jest nazywana punktu końcowego, który jest reprezentowana w programie .NET Framework przez <xref:System.Net.EndPoint> klasy. Element podrzędny **punktu końcowego** jest zdefiniowany dla każdego obsługiwana Rodzina adresów; rodziny adresów IP jest klasa <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Klasa udostępnia usługi nazwy domeny do aplikacji, które używają usługi internetowe TCP/IP. <xref:System.Net.Dns.Resolve%2A> Metoda odpytuje serwer DNS, aby zamapować nazwę przyjazną dla użytkownika domeny (na przykład "host.contoso.com") do numerycznego adresu internetowego (na przykład 192.168.1.1). **Rozwiąż** zwraca <xref:System.Net.IPHostEntry> zawierający listę adresów i aliasów dla żądanej nazwy. W większości przypadków można użyć pierwszy zwrócony w adres <xref:System.Net.IPHostEntry.AddressList%2A> tablicy. Poniższy kod pobiera <xref:System.Net.IPAddress> zawierający adres IP dla host.contoso.com serwera.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (Aby uzyskać więcej informacji, zobacz www.iana.org/assignments/port-numbers). Inne usługi można zarejestrować numery portów z zakresu od 1024 do 65 535. Poniższy kod łączy adres IP host.contoso.com z numerem portu, aby utworzyć zdalny punkt końcowy dla połączenia.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po określania adresu urządzenie zdalne i wybierając port do użycia na potrzeby połączenia, aplikacja może próbować nawiązać połączenie z urządzeniem zdalnym. W poniższym przykładzie użyto istniejące **IPEndPoint** nawiązać połączenia z urządzeniem zdalnym i przechwytuje wszystkie wyjątki, które są zgłaszane.  
  
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
 [Używanie synchronicznego gniazda klienta](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Używanie asynchronicznego gniazda klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Instrukcje: tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
