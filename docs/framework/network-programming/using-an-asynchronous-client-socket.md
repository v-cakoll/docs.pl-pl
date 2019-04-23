---
title: Używanie asynchronicznego gniazda klienta
ms.date: 03/30/2017
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
ms.openlocfilehash: 4d7020b6bc5049101ec08329d53d966771e38035
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168899"
---
# <a name="using-an-asynchronous-client-socket"></a>Używanie asynchronicznego gniazda klienta
Asynchronicznego gniazda klienta nie wstrzymuje aplikacji podczas oczekiwania na zakończenie operacji sieciowych. Zamiast tego używa standardowego modelu programowania asynchronicznego środowiska .NET Framework do przetwarzania połączenia sieciowego w jednym wątku, podczas gdy aplikacja będzie działać w oryginalnym wątku. Asynchronicznego gniazda są odpowiednie dla aplikacji, które intensywnie korzystają z sieci lub które nie może czekać na operacje sieciowe, które należy wykonać przed kontynuowaniem.  
  
 <xref:System.Net.Sockets.Socket> Następujące klasy .NET Framework nazwy wzorca w przypadku metod asynchronicznych; na przykład synchronicznego <xref:System.Net.Sockets.Socket.Receive%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginReceive%2A> i <xref:System.Net.Sockets.Socket.EndReceive%2A> metody.  
  
 Asynchroniczne operacje wymagają metodę wywołania zwrotnego do zwrócenia wyniku operacji. Jeśli aplikacja nie musi wiedzieć, wynik, brak metody wywołania zwrotnego jest wymagany. Przykładowy kod w tej sekcji pokazano, za pomocą innej metody, aby rozpocząć, nawiązywania połączenia z urządzeniem sieciowym a metody wywołania zwrotnego, aby zakończyć połączenie, metody, aby rozpocząć wysyłanie danych i metodę wywołania zwrotnego do ukończenia wysyłania i metodę, aby rozpocząć odbieranie danych i Metoda wywołania zwrotnego do końca odbierania danych.  
  
 Asynchronicznego gniazda umożliwia wielu wątków z puli wątków systemu procesu połączeń sieciowych. Jeden wątek jest odpowiedzialny za inicjowanie wysyłania lub odbierania danych. inne wątki nawiązać połączenie z urządzeniem sieciowym i wysyłania lub odbierania danych. W poniższych przykładach wystąpień <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy są używane w celu wstrzymania wykonywania wątku głównego i sygnał, gdy można kontynuować wykonywania.  
  
 W poniższym przykładzie, urządzenie sieciowe nawiązać połączenia asynchronicznego gniazda `Connect` inicjuje metodę **gniazda** , a następnie wywołuje <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> jest metoda zdalnego punktu końcowego, który reprezentuje urządzenie sieciowe , metody wywołania zwrotnego connect i obiektu stanu (klient **gniazda**), który jest używany do przekazywania informacji o stanie między wywołania asynchroniczne. Przykład implementuje `Connect` metodę, aby połączyć z określonym **gniazda** do określonego punktu końcowego. Przyjęto założenie, globalną **ManualResetEvent** o nazwie `connectDone`.  
  
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
  
 Metoda wywołania zwrotnego connect `ConnectCallback` implementuje <xref:System.AsyncCallback> delegować. Nawiązuje połączenie z urządzeniem zdalnym, gdy urządzenie zdalne jest dostępne i następnie sygnalizuje wątku aplikacji, że połączenie zostało wykonane przez ustawienie **ManualResetEvent** `connectDone`. Poniższy kod implementuje `ConnectCallback` metody.  
  
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
  
 Przykładowa metoda `Send` koduje danych określonego ciągu w formacie ASCII i asynchronicznie wysyła je do urządzenia sieciowego, reprezentowane przez określony gniazda. Poniższy przykład implementuje `Send` metody.  
  
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
  
 Metoda wywołania zwrotnego wysyłania `SendCallback` implementuje <xref:System.AsyncCallback> delegować. Wysyła dane, gdy urządzenie sieciowe jest gotowa do odbierania. W poniższym przykładzie pokazano implementację `SendCallback` metody. Przyjęto założenie, globalną **ManualResetEvent** o nazwie `sendDone`.  
  
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
  
 Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołania asynchroniczne. Następujące klasy jest przykładowy obiekt stanu do odbierania danych z gniazda klienta. Zawiera on pole dla gniazda klienta, bufor dla odebranych danych i <xref:System.Text.StringBuilder> do przechowywania przychodzącego ciągu danych. Wprowadzenie do tych pól w obiekcie stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań do odczytywania danych z gniazda klienta.  
  
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
  
 Przykład `Receive` metoda konfiguruje obiekt stanu, a następnie wywołuje **BeginReceive** metodę w celu odczytania danych z gniazda klienta asynchronicznie. Poniższy przykład implementuje `Receive` metody.  
  
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
  
 Metoda wywołania zwrotnego receive `ReceiveCallback` implementuje **AsyncCallback** delegować. Ona odbiera dane z urządzenia sieciowego i tworzy ciąg komunikatu. Odczytuje co najmniej jeden bajtów danych z sieci do buforów danych, a następnie wywołuje **BeginReceive** metoda ponownie do czasu dane wysyłane przez klienta zostało zakończone. Gdy wszystkie dane są odczytywane z poziomu klienta, `ReceiveCallback` wątku aplikacji sygnalizuje, że danych została zakończona, ustawiając **ManualResetEvent** `sendDone`.  
  
 Poniższy przykład kodu implementuje `ReceiveCallback` metody. Przyjęto założenie, globalne ciągu o nazwie `response` przechowuje odebranych ciągu i globalną **ManualResetEvent** o nazwie `receiveDone`. Serwer musi zamykany gniazda klienta, aby zakończyć sesję sieci.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Używanie synchronicznego gniazda klienta](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
- [Przykład asynchronicznego gniazda klienta](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
