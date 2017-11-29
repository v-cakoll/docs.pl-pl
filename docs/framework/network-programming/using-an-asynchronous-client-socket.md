---
title: "Przy użyciu gniazda asynchroniczne klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 263d8a82bf70ac86e776f28d660ef08c58a33384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynchronous-client-socket"></a>Przy użyciu gniazda asynchroniczne klienta
Gniazdo klienta asynchronicznego nie wstrzymuje aplikacji podczas oczekiwania na zakończenie operacji sieciowych. Zamiast tego używa standardowych model programowania asynchronicznego .NET Framework do przetwarzania połączenia sieciowego w jednym wątku, gdy aplikacja nadal działa w oryginalnym wątku. Gniazda asynchroniczne są odpowiednie dla aplikacji, która w znacznym stopniu wykorzystywane w sieci lub który nie może czekać na zakończenie przed kontynuowaniem operacji sieciowych.  
  
 <xref:System.Net.Sockets.Socket> Następujące klasy wzorzec nazewnictwa .NET Framework dla metod asynchronicznych; na przykład synchroniczne <xref:System.Net.Sockets.Socket.Receive%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginReceive%2A> i <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.  
  
 Operacje asynchroniczne wymagają Metoda wywołania zwrotnego zwracają wyniki operacji. Jeśli aplikacja nie trzeba znać wynik, brak metody wywołania zwrotnego jest wymagana. Przykład kodu w tej sekcji przedstawiono uruchamiania nawiązywania połączenia z urządzeniem sieciowym a metody wywołania zwrotnego, aby zakończyć połączenie, metody, aby rozpocząć wysyłanie danych i metoda wywołania zwrotnego do ukończenia wysyłania i metody, aby rozpocząć odbieranie danych przy użyciu metody i Metoda wywołania zwrotnego do końca odbierania danych.  
  
 Asynchroniczne sockets umożliwia wiele wątków z puli wątków systemu procesu połączeń sieciowych. Jeden wątek jest odpowiedzialny za inicjowanie wysyłania i odbierania danych. inne wątki nawiązać połączenie z urządzeniem sieciowym i wysyłać ani odbierać dane. W poniższych przykładach wystąpienia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy służą do Wstrzymaj wykonywanie wątku głównego i sygnału, gdy można kontynuować wykonywania.  
  
 W poniższym przykładzie nawiązywania połączenia z urządzeniem sieciowym asynchroniczne gniazda `Connect` inicjuje metody **gniazda** , a następnie wywołuje <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> jest metoda zdalny punkt końcowy, który reprezentuje urządzenie sieciowe , metody wywołania zwrotnego connect i obiektu stanu (klient **gniazda**), który jest używany do przekazywania informacji o stanie między wywołania asynchroniczne. Przykład implementuje `Connect` metodę, aby połączyć z określonym **gniazda** do określonego punktu końcowego. Przyjęto założenie, globalnym **ManualResetEvent** o nazwie `connectDone`.  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,   
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 Metoda wywołania zwrotnego connect `ConnectCallback` implementuje <xref:System.AsyncCallback> delegowanie. Po udostępnieniu urządzenie zdalne i następnie sygnały wątku aplikacji połączenie zostało wykonane przez ustawienie łączy do urządzenia zdalnego **ManualResetEvent** `connectDone`. Poniższy kod implementuje `ConnectCallback` metody.  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Przykładowa metoda `Send` koduje danych określonego ciągu w formacie ASCII i wysyła je asynchronicznie na urządzeniu sieci reprezentowany przez określony gniazda. Poniższy przykład implementuje `Send` metody.  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 Metoda wywołania zwrotnego wysyłania `SendCallback` implementuje <xref:System.AsyncCallback> delegowanie. Gdy urządzenie sieciowe jest gotowa do odbioru, wysyła dane. Poniższy przykład przedstawia implementację `SendCallback` metody. Przyjęto założenie, globalnym **ManualResetEvent** o nazwie `sendDone`.  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Odczyt danych z gniazda klienta wymaga przesyłane wartości między asynchroniczne wywołania obiektu stanu. Następujące klasy jest przykład obiekt stanu do odbierania danych z gniazda klienta. Zawiera on pole dla gniazda klienta, buforu dla odebranych danych i <xref:System.Text.StringBuilder> do przechowywania przychodzącego ciągu danych. Umieszczenie tych pól w obiekt stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań można odczytać danych z gniazda klienta.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing   
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte   
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 Przykład `Receive` metoda konfiguruje obiekt stanu, a następnie wywołuje **BeginReceive** metodę, aby odczytać danych z gniazda klienta asynchronicznie. Poniższy przykład implementuje `Receive` metody.  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Metody wywołania zwrotnego receive `ReceiveCallback` implementuje **AsyncCallback** delegowanie. Odbiera dane z urządzenia sieciowego, a kompilacje ciąg komunikatu. Odczytuje jeden lub więcej bajtów danych z sieci do buforu danych, a następnie wywołuje **BeginReceive** zakończeniu metody ponownie do czasu dane wysyłane przez klienta. Gdy wszystkie dane są odczytywane z klienta, `ReceiveCallback` wątku aplikacji sygnalizuje, że dane są kompletne przez ustawienie **ManualResetEvent** `sendDone`.  
  
 Poniższy przykładowy kod implementuje `ReceiveCallback` metody. Przyjęto założenie, globalne ciągu o nazwie `response` przechowuje odebranego ciągu i globalną **ManualResetEvent** o nazwie `receiveDone`. Serwer musi zamykany gniazdo klienta, aby zakończyć sesję sieci.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket   
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket   
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu gniazda synchroniczne klienta](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Nasłuchiwanie z gniazda](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [Przykład gniazda asynchroniczne klienta](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
