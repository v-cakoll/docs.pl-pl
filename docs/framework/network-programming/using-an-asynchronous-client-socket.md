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
ms.openlocfilehash: 748745ca6799005dccdbfcbcc37a8c2a38f2a88e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180650"
---
# <a name="using-an-asynchronous-client-socket"></a>Używanie asynchronicznego gniazda klienta
Gniazdo klienta asynchroniiowego nie zawiesza aplikacji podczas oczekiwania na zakończenie operacji sieciowych. Zamiast tego używa standardowego modelu programowania asynchroniowego programu .NET Framework do przetwarzania połączenia sieciowego w jednym wątku, podczas gdy aplikacja będzie nadal działać w oryginalnym wątku. Gniazda asynchroniczne są odpowiednie dla aplikacji, które intensywnie korzystają z sieci lub które nie mogą czekać na zakończenie operacji sieciowych przed kontynuowaniem.  
  
 Klasa <xref:System.Net.Sockets.Socket> jest zgodna z wzorcem nazewnictwa programu .NET Framework dla metod asynchronicznych; na przykład metoda synchroniczne <xref:System.Net.Sockets.Socket.Receive%2A> odpowiada asynchroniczne <xref:System.Net.Sockets.Socket.BeginReceive%2A> <xref:System.Net.Sockets.Socket.EndReceive%2A> i metody.  
  
 Operacje asynchroniczne wymagają metody wywołania zwrotnego, aby zwrócić wynik operacji. Jeśli aplikacja nie musi znać wynik, następnie nie jest wymagana metoda wywołania zwrotnego. Przykładowy kod w tej sekcji pokazuje przy użyciu metody, aby rozpocząć łączenie się z urządzeniem sieciowym i metody wywołania zwrotnego, aby zakończyć połączenie, metoda rozpoczęcia wysyłania danych i metody wywołania zwrotnego, aby zakończyć wysyłanie, a metoda, aby rozpocząć odbieranie danych i metody wywołania zwrotnego, aby zakończyć odbieranie danych.  
  
 Gniazda asynchroniczne używają wielu wątków z puli wątków systemowych do przetwarzania połączeń sieciowych. Jeden wątek jest odpowiedzialny za inicjowanie wysyłania lub odbierania danych; inne wątki kończą połączenie z urządzeniem sieciowym i wysyłają lub odbierają dane. W poniższych przykładach wystąpienia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy są używane do zawieszenia wykonywania wątku głównego i sygnału, gdy wykonywanie można kontynuować.  
  
 W `Connect` poniższym przykładzie, aby połączyć gniazdo asynchroniczne z urządzeniem sieciowym, metoda inicjuje **Socket,** a następnie wywołuje <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> metodę, przekazując zdalny punkt końcowy reprezentujący urządzenie sieciowe, metodę wywołania zwrotnego i obiekt stanu (gniazdo klienta), który jest używany do **przekazywania**informacji o stanie między wywołaniami asynchronizacyjnymi. W przykładzie `Connect` implementuje metodę, aby połączyć określony **Socket** do określonego punktu końcowego. Zakłada się, że globalny **ManualResetEvent** o nazwie `connectDone`.  
  
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
  
 Connect callback `ConnectCallback` metoda implementuje delegata. <xref:System.AsyncCallback> Łączy się z urządzeniem zdalnym, gdy urządzenie zdalne jest dostępne, a następnie sygnalizuje wątek aplikacji, że połączenie zostało zakończone, ustawiając **ManualResetEvent** `connectDone`. Poniższy kod implementuje `ConnectCallback` metodę.  
  
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
  
 Przykładowa `Send` metoda koduje określone dane ciągu w formacie ASCII i wysyła je asynchronicznie do urządzenia sieciowego reprezentowanego przez określone gniazdo. Poniższy przykład implementuje `Send` metodę.  
  
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
  
 Metoda `SendCallback` wywołania zwrotnego <xref:System.AsyncCallback> send implementuje pełnomocnika. Wysyła dane, gdy urządzenie sieciowe jest gotowe do odbioru. Poniższy przykład przedstawia implementację `SendCallback` metody. Zakłada się, że globalny **ManualResetEvent** o nazwie `sendDone`.  
  
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
  
 Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołaniami asynchronizacyjnymi. Następująca klasa jest przykładowym obiektem stanu do odbierania danych z gniazda klienta. Zawiera pole dla gniazda klienta, bufor dla odebranych <xref:System.Text.StringBuilder> danych i do przechowywania przychodzącego ciągu danych. Umieszczenie tych pól w obiekcie stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań do odczytu danych z gniazda klienta.  
  
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
  
 Przykładowa `Receive` metoda konfiguruje obiekt stanu, a następnie wywołuje **BeginReceive** metody do odczytu danych z gniazda klienta asynchronicznie. Poniższy przykład implementuje `Receive` metodę.  
  
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
  
 Metoda wywołania `ReceiveCallback` zwrotnego receive implementuje **delegata AsyncCallback.** Odbiera dane z urządzenia sieciowego i tworzy ciąg komunikatu. Odczytuje jeden lub więcej bajtów danych z sieci do buforu danych, a następnie wywołuje **BeginReceive** metody ponownie, aż do zakończenia danych wysyłanych przez klienta. Po odczytaniu wszystkich danych z `ReceiveCallback` klienta sygnalizuje wątek aplikacji, że dane są kompletne, ustawiając **ManualResetEvent** `sendDone`.  
  
 Poniższy przykładowy kod `ReceiveCallback` implementuje metodę. Przyjęto założenie, że `response` ciąg globalny o nazwie, który zawiera `receiveDone`odebrany ciąg i global **ManualResetEvent** o nazwie . Serwer musi bezpiecznie zamknąć gniazdo klienta, aby zakończyć sesję sieciową.  
  
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

- [Używanie synchronicznego gniazda klienta](using-a-synchronous-client-socket.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
- [Przykład asynchronicznego gniazda klienta](asynchronous-client-socket-example.md)
