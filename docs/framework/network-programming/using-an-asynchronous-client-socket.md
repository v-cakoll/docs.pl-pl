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
ms.openlocfilehash: 22e7c670f93293bd37edcb181c8130cdbe9ceb26
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047062"
---
# <a name="using-an-asynchronous-client-socket"></a>Używanie asynchronicznego gniazda klienta
Asynchroniczne gniazdo klienta nie wstrzymuje aplikacji podczas oczekiwania na ukończenie operacji sieciowych. Zamiast tego używa standardowego modelu programowania .NET Framework, aby przetwarzać połączenie sieciowe w jednym wątku, gdy aplikacja nadal działa w oryginalnym wątku. Gniazda asynchroniczne są odpowiednie dla aplikacji, które intensywnie wykorzystują sieć lub nie mogą czekać na ukończenie operacji sieciowych przed kontynuowaniem.  
  
 Klasa <xref:System.Net.Sockets.Socket> jest zgodna ze wzorcem nazewnictwa .NET Framework dla metod asynchronicznych, na przykład <xref:System.Net.Sockets.Socket.Receive%2A> metoda synchroniczna odnosi się <xref:System.Net.Sockets.Socket.BeginReceive%2A> do <xref:System.Net.Sockets.Socket.EndReceive%2A> metod asynchronicznych i.  
  
 Operacje asynchroniczne wymagają metody wywołania zwrotnego do zwrócenia wyniku operacji. Jeśli aplikacja nie musi znać wyniku, nie jest wymagana żadna metoda wywołania zwrotnego. W przykładowym kodzie w tej sekcji pokazano, jak rozpocząć łączenie się z urządzeniem sieciowym i metoda wywołania zwrotnego, aby zakończyć połączenie, metodę, aby rozpocząć wysyłanie danych i metodę wywołania zwrotnego w celu ukończenia wysyłania, oraz metodę, aby rozpocząć pobieranie danych i Metoda wywołania zwrotnego kończąca pobieranie danych.  
  
 Gniazda asynchroniczne używają wielu wątków z puli wątków systemowych do przetwarzania połączeń sieciowych. Jeden wątek jest odpowiedzialny za Inicjowanie wysyłania lub otrzymywania danych; inne wątki ukończą połączenie z urządzeniem sieciowym i wysyłają lub odbierają dane. W poniższych przykładach wystąpienia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy są używane do wstrzymania wykonywania głównego wątku i sygnału, gdy wykonanie może być kontynuowane.  
  
 W poniższym przykładzie, aby połączyć gniazdo asynchroniczne z urządzeniem sieciowym, `Connect` Metoda inicjuje **gniazdo** , <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> a następnie wywołuje metodę, przekazując zdalny punkt końcowy reprezentujący urządzenie sieciowe, wywołanie zwrotne połączenia Metoda i obiekt stanu ( **gniazdo**klienta), który jest używany do przekazywania informacji o stanie między wywołaniami asynchronicznymi. Przykład implementuje metodę, `Connect` aby połączyć określone **gniazdo** z określonym punktem końcowym. Przyjęto założenie , że `connectDone`Global ManualResetEvent o nazwie.  
  
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
  
 Metoda `ConnectCallback` Connect wywołania zwrotnego <xref:System.AsyncCallback> implementuje delegata. Nawiązuje połączenie z urządzeniem zdalnym, gdy urządzenie zdalne jest dostępne, a następnie sygnalizuje wątek aplikacji, że połączenie zostało ukończone przez ustawienie **ManualResetEvent** `connectDone`. Poniższy kod implementuje `ConnectCallback` metodę.  
  
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
  
 Przykładowa Metoda `Send` koduje określone dane ciągu w formacie ASCII i wysyła je asynchronicznie do urządzenia sieciowego reprezentowanego przez określone gniazdo. Poniższy przykład implementuje `Send` metodę.  
  
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
  
 Metoda `SendCallback` wysyłania wywołania zwrotnego <xref:System.AsyncCallback> implementuje delegata. Wysyła dane, gdy urządzenie sieciowe jest gotowe do odebrania. Poniższy przykład pokazuje implementację `SendCallback` metody. Przyjęto założenie , że `sendDone`Global ManualResetEvent o nazwie.  
  
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
  
 Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołaniami asynchronicznymi. Poniżej przedstawiono klasę przykładowego obiektu stanu do odbioru danych z gniazda klienta. Zawiera pole dla gniazda klienta, bufor dla odebranych danych i obiekt <xref:System.Text.StringBuilder> do przechowywania przychodzącego ciągu danych. Umieszczenie tych pól w obiekcie State pozwala zachować ich wartości między wieloma wywołaniami odczytu danych z gniazda klienta.  
  
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
  
 Przykładowa `Receive` Metoda konfiguruje obiekt stanu, a następnie wywołuje metodę **BeginReceive** , aby odczytywać dane z gniazda klienta asynchronicznie. Poniższy przykład implementuje `Receive` metodę.  
  
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
  
 Metoda `ReceiveCallback` odbierania wywołania zwrotnego implementuje delegata **AsyncCallback** . Odbiera dane z urządzenia sieciowego i kompiluje ciąg komunikatu. Odczytuje on co najmniej jeden bajt danych z sieci do bufora danych, a następnie ponownie wywołuje metodę **BeginReceive** do momentu ukończenia danych wysyłanych przez klienta. Po odczytaniu wszystkich danych z klienta program `ReceiveCallback` sygnalizuje wątek aplikacji, że dane zostały ukończone przez ustawienie **ManualResetEvent** `sendDone`.  
  
 Poniższy przykładowy kod implementuje `ReceiveCallback` metodę. Przyjęto założenie, że `response` ciąg globalny o nazwie zawiera otrzymany ciąg i globalną `receiveDone` **ManualResetEvent** o nazwie. Serwer musi bezpiecznie zamknąć gniazdo klienta, aby zakończyć sesję sieciową.  
  
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

- [Używanie synchronicznego gniazda klienta](using-a-synchronous-client-socket.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
- [Przykład asynchronicznego gniazda klienta](asynchronous-client-socket-example.md)
