---
title: Za pomocą asynchronicznego gniazda serwera
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
ms.openlocfilehash: f89bf9e3ea9f2b3c385d267cfc77a05ee8eb82d6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47436105"
---
# <a name="using-an-asynchronous-server-socket"></a>Za pomocą asynchronicznego gniazda serwera
Server asynchronicznego gniazda używają modelu programowania asynchronicznego środowiska .NET Framework do przetwarzania żądania usługi sieci. <xref:System.Net.Sockets.Socket> Klasy postępuje zgodnie ze standardowym .NET Framework asynchroniczny wzorzec nazewnictwa; na przykład synchronicznego <xref:System.Net.Sockets.Socket.Accept%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginAccept%2A> i <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.  
  
 Asynchronicznego gniazda serwera wymaga metodę, aby zacząć akceptować żądań połączeń od sieci, metody wywołania zwrotnego do obsługi żądań połączenia i zacząć odbierać dane z sieci i metody wywołania zwrotnego do końca odbiera dane. Wszystkie te metody zostały omówione w tej sekcji.  
  
 W poniższym przykładzie, aby rozpocząć, akceptując żądania połączenia z siecią, Metoda `StartListening` inicjuje **gniazda** , a następnie używa **BeginAccept** zacznij akceptować nowe metody połączenia. Akceptuj metody wywołania zwrotnego jest wywoływana, gdy zostanie odebrane żądanie nowego połączenia gniazda. Odpowiada za pobieranie **gniazda** wystąpienia, która będzie obsługiwać połączenia oraz przekazywanie, **gniazda** wyłączony do wątku, który będzie przetwarzał żądanie. Implementuje metody wywołania zwrotnego Akceptuj <xref:System.AsyncCallback> delegować; zwraca wartość typu void i przyjmuje jeden parametr typu <xref:System.IAsyncResult>. Poniższy przykład jest powłoka Akceptuj metody wywołania zwrotnego.  
  
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
  
 **BeginAccept** metoda przyjmuje dwa parametry **AsyncCallback** delegat, który wskazuje na metody wywołania zwrotnego Akceptuj i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego. W poniższym przykładzie nasłuchiwania **gniazda** jest przekazywany do metody wywołania zwrotnego za pośrednictwem *stanu* parametru. Ten przykład tworzy **AsyncCallback** delegata i rozpoczyna się akceptować połączenia z siecią.  
  
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
  
 Asynchronicznego gniazda używają wątków z puli wątków systemu do przetwarzania połączenia przychodzące. Jeden wątek jest odpowiedzialny za akceptowanie połączeń, inny wątek jest używana do obsługi każdego połączenia przychodzące i inny wątek jest odpowiedzialna za odbieranie danych z połączenia. Mogą to być tym samym wątku, w zależności od tego, który wątek jest przypisywany przez puli wątków. W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy zawiesza wykonywanie wątku głównego i sygnalizuje, można kontynuować wykonywania.  
  
 Poniższy przykład przedstawia metodę asynchroniczną, która tworzy asynchronicznego gniazda TCP/IP na komputerze lokalnym i zaczyna akceptować połączenia. Przyjęto założenie, że dostępna jest globalna **ManualResetEvent** o nazwie `allDone`, że metoda jest składową klasy o nazwie `SocketListener`, i metodę wywołania zwrotnego o nazwie `acceptCallback` jest zdefiniowana.  
  
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
  
 Metoda wywołania zwrotnego Akceptuj (`acceptCallback` w powyższym przykładzie) odpowiada za sygnalizowanie wątku głównego aplikacji, aby kontynuować przetwarzanie, podczas nawiązywania połączenia z klientem i uruchamianie asynchronicznego odczytu danych z klienta. Poniższy przykład jest pierwszą częścią implementacji `acceptCallback` metody. Ta sekcja metody sygnały w wątku głównym aplikacji, aby kontynuować przetwarzanie i nawiązuje połączenie z klientem. Przyjęto założenie, globalną **ManualResetEvent** o nazwie `allDone`.  
  
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
  
 Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołania asynchroniczne. Poniższy przykład implementuje obiektu stanu do odbierania ciąg przez klienta zdalnego. Zawiera on pola dla gniazda klienta, bufor danych do odbierania danych, a <xref:System.Text.StringBuilder> tworzenia ciągu danych wysyłany przez klienta. Wprowadzenie do tych pól w obiekcie stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań do odczytywania danych z gniazda klienta.  
  
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
  
 W sekcji `acceptCallback` metodę, która zacznie otrzymywać dane z gniazda klienta najpierw inicjuje wystąpienie `StateObject` klasy, a następnie wywołania <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodę, aby rozpocząć odczyt danych z gniazda klienta asynchronicznie.  
  
 W poniższym przykładzie pokazano pełne `acceptCallback` metody. Przyjęto założenie, że dostępna jest globalna **ManualResetEvent** o nazwie `allDone,` , `StateObject` klasa jest zdefiniowana, a `readCallback` metoda jest zdefiniowana w klasie o nazwie `SocketListener`.  
  
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
  
 Ostatnią metodę, która musi zostać wdrożone dla asynchronicznego gniazda serwera jest metoda odczytu wywołania zwrotnego, która zwraca dane wysyłane przez klienta. Podobnie jak metody wywołania zwrotnego accept, metody wywołania zwrotnego odczytu jest **AsyncCallback** delegować. Ta metoda odczytuje bajtów co najmniej jeden z gniazda klienta do bufora danych, a następnie wywołuje **BeginReceive** metoda ponownie do czasu dane wysyłane przez klienta zostało zakończone. Gdy cały komunikat został odczytany z klientem, ciąg jest wyświetlany w konsoli i gniazda serwera obsługi połączenie z klientem zostało zamknięte.  
  
 Następujące przykładowe implementuje `readCallback` metody. Założono, że `StateObject` klasa jest zdefiniowana.  
  
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
