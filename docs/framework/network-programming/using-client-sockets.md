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
ms.openlocfilehash: 42cea87576ca4c5cbca685c6d71272649eabb844
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562855"
---
# <a name="using-client-sockets"></a>Używanie gniazd klientów
Przed rozpoczęciem konwersacji za pośrednictwem <xref:System.Net.Sockets.Socket>, należy utworzyć potok danych między aplikacją i urządzenie zdalne. Mimo że istnieją inne rodziny adresów sieciowych i protokołów, w tym przykładzie pokazano, jak utworzyć połączenie TCP/IP do usługi zdalnej.  
  
 Protokół TCP/IP używa adresu sieciowego i numer portu usługi do unikatowego identyfikowania usługi. Adres sieciowy identyfikuje konkretnym urządzeniu w sieci. numer portu identyfikuje określonej usługi na tym urządzeniu, aby nawiązać połączenie. Kombinacja portu adresu i usługi sieciowej jest nazywana punktu końcowego, która jest reprezentowana w .NET Framework według <xref:System.Net.EndPoint> klasy. Element podrzędny **punktu końcowego** jest zdefiniowana dla każdego obsługiwane rodziny adresów; Rodzina adresów IP, klasa jest <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Klasa udostępnia usługi nazwy domeny dla aplikacji korzystających z usług internetowych TCP/IP. <xref:System.Net.Dns.Resolve%2A> Metoda odpytuje serwer DNS, aby zamapować nazwę przyjazną dla użytkownika domeny (na przykład "host.contoso.com") do numerycznego adresu internetowego (np. 192.168.1.1). **Rozwiąż** zwraca <xref:System.Net.IPHostEntry> zawierający listę adresów i aliasy dla żądanej nazwy. W większości przypadków można użyć pierwszego adresu zwracane w <xref:System.Net.IPHostEntry.AddressList%2A> tablicy. Poniższy kod pobiera <xref:System.Net.IPAddress> zawierające adres IP dla host.contoso.com serwera.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (Aby uzyskać więcej informacji, zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Inne usługi można zarejestrowano numery portów z zakresu od 1024 do 65 535. Poniższy kod łączy adres IP dla host.contoso.com z numerem portu, aby utworzyć zdalnego punktu końcowego połączenia.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Po określająca adres urządzenia zdalnego, a następnie wybierając port do użycia na potrzeby połączenia, aplikacja może próbować nawiązać połączenie z urządzeniem zdalnym. W poniższym przykładzie użyto istniejącej **IPEndPoint** nawiązać połączenia z urządzeniem zdalnym i przechwytuje wszystkie wyjątki, które są generowane.  
  
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
- [Używanie synchronicznego gniazda klienta](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Używanie asynchronicznego gniazda klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Instrukcje: Tworzenie gniazda](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [Gniazda](../../../docs/framework/network-programming/sockets.md)
