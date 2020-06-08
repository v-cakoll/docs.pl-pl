---
title: Używanie synchronicznego gniazda klienta
description: W tym przykładzie pokazano synchroniczne gniazdo klienta w .NET Framework, które wstrzymuje program aplikacji podczas kończenia operacji sieciowej.
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
ms.openlocfilehash: ef682af33c10cf06ffc398c22e4a7dc1adf8290e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502070"
---
# <a name="using-a-synchronous-client-socket"></a>Używanie synchronicznego gniazda klienta
Synchroniczne gniazdo klienta zawiesza program aplikacji podczas kończenia operacji sieciowej. Gniazda synchroniczne nie są odpowiednie dla aplikacji, które intensywnie wykorzystują sieć do ich obsługi, ale mogą zapewnić prosty dostęp do usług sieciowych dla innych aplikacji.  
  
 Aby wysłać dane, Przekaż tablicę bajtową do jednej z <xref:System.Net.Sockets.Socket> metod wysyłania danych klasy ( <xref:System.Net.Sockets.Socket.Send%2A> i <xref:System.Net.Sockets.Socket.SendTo%2A> ). Poniższy przykład koduje ciąg w buforze tablicy bajtów przy użyciu <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> właściwości, a następnie przesyła bufor do urządzenia sieciowego przy użyciu metody **send** . Metoda **send** zwraca liczbę bajtów wysłanych do urządzenia sieciowego.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 Metoda **send** usuwa bajty z buforu i kolejkuje je za pomocą interfejsu sieciowego do wysłania do urządzenia sieciowego. Interfejs sieciowy może nie wysłać danych natychmiast, ale zostanie on wysłany ostatecznie, o ile połączenie zostanie normalnie zamknięte przy użyciu <xref:System.Net.Sockets.Socket.Shutdown%2A> metody.  
  
 Aby odbierać dane z urządzenia sieciowego, należy przekazać bufor do jednej z metod odbioru danych klasy **gniazda** ( <xref:System.Net.Sockets.Socket.Receive%2A> i <xref:System.Net.Sockets.Socket.ReceiveFrom%2A> ). Gniazda synchroniczne zawieszają aplikację do momentu odebrania bajtów z sieci lub do momentu zamknięcia gniazda. Poniższy przykład odbiera dane z sieci, a następnie wyświetla je w konsoli programu. W przykładzie założono, że dane pochodzące z sieci są tekstem zakodowanym w formacie ASCII. Metoda **Receive** zwraca liczbę bajtów odebranych z sieci.  
  
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
  
 Gdy gniazdo nie jest już potrzebne, należy je zwolnić, wywołując <xref:System.Net.Sockets.Socket.Shutdown%2A> metodę, a następnie wywołując metodę **Close** . Poniższy przykład zwalnia **gniazdo**. <xref:System.Net.Sockets.SocketShutdown>Wyliczenie definiuje stałe wskazujące, czy gniazdo powinno być zamknięte do wysłania, do odbioru lub dla obu.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie asynchronicznego gniazda klienta](using-an-asynchronous-client-socket.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
- [Przykład synchronicznego gniazda klienta](synchronous-client-socket-example.md)
