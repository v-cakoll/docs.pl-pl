---
title: Za pomocą synchronicznego gniazda klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: 8036421f937385edbaefb8df4ee3915798084c64
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147234"
---
# <a name="using-a-synchronous-client-socket"></a>Za pomocą synchronicznego gniazda klienta
Synchronicznego gniazda klienta zawiesza program aplikacji podczas wykonywania operacji sieciowej. Synchronicznego gniazda nie są odpowiednie dla aplikacji, które intensywnie korzystają z sieci do ich działania, ale mogą one umożliwiać prosty dostęp do usług sieciowych dla innych aplikacji.  
  
 Aby wysyłać dane, należy przekazać tablicy typu byte do jednej z <xref:System.Net.Sockets.Socket> metod wysyłania danych klasy (<xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.SendTo%2A>). Poniższy przykład koduje ciąg w użyciu bufor tablicy bajtów <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości i następnie przesyła bufor do urządzenia sieciowego za pomocą **wysyłania** metody. **Wysyłania** metoda zwraca liczbę bajtów wysłanych z urządzeniem sieciowym.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Wysyłania** metoda usuwa bajtów z bufora i kolejki je z interfejsem sieciowym do wysłania do urządzenia sieciowego. Interfejs sieciowy nie może wysłać dane od razu, ale wysyła on po pewnym czasie tak długo, jak połączenie jest zamknięte zwykle z <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.  
  
 Odbieranie danych z urządzenia sieciowego, należy przekazać do jednego z buforu **gniazda** metod odbierania danych klasy (<xref:System.Net.Sockets.Socket.Receive%2A> i <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Synchronicznego gniazda zostanie zawieszone aplikacji, dopóki nie są odbierane z sieci, lub do czasu zamknięcia gniazda. Poniższy przykład odbiera dane z sieci i wyświetla go w konsoli. W przykładzie założono, że dane pochodzące z sieci należy tekstowymi w formacie ASCII. **Receive** metoda zwraca liczbę bajtów odebranych z sieci.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Gdy gniazda nie jest już potrzebny, musisz zwolnić go przez wywołanie metody <xref:System.Net.Sockets.Socket.Shutdown%2A> metody, a następnie wywołując **Zamknij** metody. Poniższy przykład zwalnia **gniazda**. <xref:System.Net.Sockets.SocketShutdown> Wyliczenie definiuje stałe, które wskazują, czy gniazda powinien zostać zamknięty, wysyłanie, odbieranie lub dla obu.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie asynchronicznego gniazda klienta](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [Przykład synchronicznego gniazda klienta](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
