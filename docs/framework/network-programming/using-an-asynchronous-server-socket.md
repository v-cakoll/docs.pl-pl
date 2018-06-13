---
title: Przy użyciu gniazda serwera asynchroniczne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396610"
---
# <a name="using-an-asynchronous-server-socket"></a>Przy użyciu gniazda serwera asynchroniczne
Gniazda asynchroniczne serwera umożliwia asynchroniczne model programowania .NET Framework przetworzyć żądania usługi sieci. <xref:System.Net.Sockets.Socket> Klasy następuje standardowego asynchroniczny wzorzec nazewnictwa .NET Framework; na przykład synchroniczne <xref:System.Net.Sockets.Socket.Accept%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginAccept%2A> i <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.  
  
 Gniazda asynchroniczne serwera wymaga metody, aby rozpocząć, akceptując żądania połączenia od sieci, metody wywołania zwrotnego do obsługi żądań połączenia i rozpocząć odbieranie danych z sieci i metody wywołania zwrotnego do końca odbiera dane. Wszystkie te metody są omówione w tej sekcji.  
  
 W poniższym przykładzie, aby rozpocząć, akceptując żądania połączenia z siecią, Metoda `StartListening` inicjuje **gniazda** , a następnie używa **BeginAccept** metodę, aby uruchomić akceptować nowych połączenia. Metoda wywołania zwrotnego Akceptuj jest wywoływana po odebraniu nowego żądania połączenia w gnieździe. Odpowiada za pobieranie **gniazda** wystąpienie, które będą obsługiwać połączenia oraz przekazywanie, który **gniazda** wyłączone w wątku, który ma przetwarzać żądania. Implementuje metody wywołania zwrotnego Akceptuj <xref:System.AsyncCallback> delegata; zwraca typ void i przyjmuje jeden parametr typu <xref:System.IAsyncResult>. Poniższy przykład jest powłoki Akceptuj metody wywołania zwrotnego.  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 **BeginAccept** metoda przyjmuje dwa parametry **AsyncCallback** delegata, który wskazuje metodę wywołania zwrotnego Akceptuj i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego. W poniższym przykładzie nasłuchiwania **gniazda** jest przekazywany do metody wywołania zwrotnego za pośrednictwem *stanu* parametru. Ten przykład tworzy **AsyncCallback** delegata i zaczyna akceptować połączenia z siecią.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 Asynchroniczne sockets Użyj wątków z puli wątków systemu do przetwarzania przychodzących połączeń. Jeden wątek jest odpowiedzialny za akceptowanie połączeń, inny wątek jest używane do obsługi każdego połączenia przychodzące i inny wątek jest odpowiedzialny za odbieranie danych z połączenia. Mogą to być tym samym wątku, w zależności od wątku jest przypisywany przez puli wątków. W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy wstrzymuje wykonywanie wątku głównego i sygnalizuje, gdy można kontynuować wykonywania.  
  
 W poniższym przykładzie przedstawiono metodę asynchroniczną, które tworzy asynchroniczne gniazda protokołu TCP/IP na komputerze lokalnym i zaczyna akceptować połączenia. Przyjęto założenie, że istnieje globalnym **ManualResetEvent** o nazwie `allDone`, że metoda jest elementem członkowskim klasy o nazwie `SocketListener`, oraz że metoda wywołania zwrotnego o nazwie `acceptCallback` jest zdefiniowany.  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 Metoda wywołania zwrotnego Akceptuj (`acceptCallback` w poprzednim przykładzie) jest odpowiedzialny sygnalizowania wątku głównego aplikacji, aby kontynuować przetwarzanie, nawiązywania połączenia z klientem i uruchamianie asynchroniczną odczytać danych z klienta. Poniższy przykład jest pierwszą częścią implementacja `acceptCallback` metody. Ta sekcja metody sygnały wątku głównego aplikacji, aby kontynuować przetwarzanie i nawiązuje połączenie z klienta. Przyjęto założenie, globalnym **ManualResetEvent** o nazwie `allDone`.  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 Odczyt danych z gniazda klienta wymaga przesyłane wartości między asynchroniczne wywołania obiektu stanu. Poniższy przykład implementuje obiekt stanu w celu odbierania ciąg z klientami zdalnymi. Plik zawiera pól dla gniazda klienta, a bufor danych na odbieranie danych, a <xref:System.Text.StringBuilder> dla tworzenia ciągu dane wysyłane przez klienta. Umieszczenie tych pól w obiekt stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań można odczytać danych z gniazda klienta.  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 W sekcji `acceptCallback` metody, która rozpoczyna się odbierania danych z gniazda klienta najpierw inicjuje wystąpienie klasy `StateObject` klasy, a następnie wywołania <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodę, aby rozpocząć odczyt danych z gniazda klienta asynchronicznie.  
  
 W poniższym przykładzie przedstawiono pełną `acceptCallback` metody. Przyjęto założenie, że istnieje globalnym **ManualResetEvent** o nazwie `allDone,` który `StateObject` zdefiniowana jest klasa oraz że `readCallback` metoda jest zdefiniowana w klasie o nazwie `SocketListener`.  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 Metodę końcową, który musi zostać wdrożone dla serwera gniazda asynchroniczne jest metoda odczytu wywołania zwrotnego, która zwraca dane wysyłane przez klienta. Podobnie jak metody wywołania zwrotnego Akceptuj, metody wywołania zwrotnego odczytu jest **AsyncCallback** delegowanie. Ta metoda odczytuje bajtów co najmniej jeden z gniazda klienta do buforu danych, a następnie wywołuje **BeginReceive** zakończeniu metody ponownie do czasu dane wysyłane przez klienta. Po przeczytaniu cały komunikat z klienta ciąg jest wyświetlana w konsoli i gniazda serwera obsługi połączenie klienta jest zamknięty.  
  
 Następujące przykładowe implementuje `readCallback` metody. Przy założeniu, że `StateObject` klasa jest zdefiniowana.  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie synchronicznego gniazda serwera](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Przykład asynchronicznego gniazda serwera](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Nasłuchiwanie przy użyciu gniazd](../../../docs/framework/network-programming/listening-with-sockets.md)
