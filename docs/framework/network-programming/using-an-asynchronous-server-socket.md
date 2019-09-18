---
title: Używanie asynchronicznego gniazda serwera
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
ms.openlocfilehash: 11ed53a4e51ba6993fd4e240116b0e1de910a01e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047047"
---
# <a name="using-an-asynchronous-server-socket"></a>Używanie asynchronicznego gniazda serwera
Asynchroniczne gniazda serwera używają .NET Framework asynchronicznego modelu programowania do przetwarzania żądań obsługi sieci. Klasa <xref:System.Net.Sockets.Socket> jest zgodna ze standardowym wzorcem nazewnictwa asynchronicznego .NET Framework, na przykład <xref:System.Net.Sockets.Socket.Accept%2A> metoda synchroniczna odnosi się <xref:System.Net.Sockets.Socket.BeginAccept%2A> do <xref:System.Net.Sockets.Socket.EndAccept%2A> metod asynchronicznych i.  
  
 Asynchroniczne gniazdo serwera wymaga metody do rozpoczęcia akceptowania żądań połączenia z sieci, metody wywołania zwrotnego do obsługi żądań połączeń i rozpoczęcia odbierania danych z sieci oraz metody wywołania zwrotnego, która ma kończyć pobieranie danych. Wszystkie te metody zostały omówione w dalszej części tej sekcji.  
  
 W poniższym przykładzie, aby rozpocząć akceptowanie żądań połączeń z sieci, Metoda `StartListening` inicjuje **gniazdo** , a następnie używa metody **BeginAccept** w celu rozpoczęcia przyjmowania nowych połączeń. Metoda akceptowania wywołania zwrotnego jest wywoływana, gdy w gnieździe zostanie odebrane nowe żądanie połączenia. Jest on odpowiedzialny za pobieranie wystąpienia **gniazda** , które będzie obsługiwać połączenie i przekazanie tego **gniazda** do wątku, który będzie przetwarzać żądanie. Metoda akceptowania wywołania zwrotnego <xref:System.AsyncCallback> implementuje delegata; zwraca wartość void i przyjmuje jeden parametr typu. <xref:System.IAsyncResult> Poniższy przykład to powłoka metody akceptowania wywołania zwrotnego.  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 Metoda **BeginAccept** przyjmuje dwa parametry, delegat elementu **AsyncCallback** wskazujący na metodę Accept wywołania zwrotnego i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego. W poniższym przykładzie **gniazdo** nasłuchiwania jest przesyłane do metody wywołania zwrotnego za pomocą parametru *State* . Ten przykład tworzy delegata **AsyncCallback** i zaczyna akceptować połączenia z sieci.  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 Gniazda asynchroniczne używają wątków z puli wątków systemowych do przetwarzania połączeń przychodzących. Jeden wątek jest odpowiedzialny za akceptowanie połączeń, drugi wątek jest używany do obsługi każdego połączenia przychodzącego, a drugi wątek jest odpowiedzialny za odbieranie danych z połączenia. Może to być ten sam wątek, w zależności od tego, który wątek jest przypisywany przez pulę wątków. W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa wstrzymuje wykonywanie głównego wątku i sygnalizuje, kiedy wykonywanie może być kontynuowane.  
  
 Poniższy przykład przedstawia metodę asynchroniczną, która tworzy asynchroniczne gniazdo TCP/IP na komputerze lokalnym i rozpoczyna akceptowanie połączeń. Przyjęto założenie, że istnieje globalna `allDone`ManualResetEvent o nazwie, która jest elementem członkowskim klasy o nazwie `SocketListener`i że określono metodę wywołania zwrotnego `AcceptCallback` o nazwie.  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
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
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try 
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 Metoda akceptowania wywołania zwrotnego (`AcceptCallback` w poprzednim przykładzie) jest odpowiedzialna za sygnalizowanie wątku głównego aplikacji w celu kontynuowania przetwarzania, ustanowienia połączenia z klientem i uruchomienia asynchronicznego odczytu danych z klienta. Poniższy przykład jest pierwszą częścią implementacji `AcceptCallback` metody. Ta sekcja metody informuje główny wątek aplikacji, aby kontynuować przetwarzanie i ustanawia połączenie z klientem. Przyjęto założenie , że `allDone`Global ManualResetEvent o nazwie.  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar) 
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołaniami asynchronicznymi. Poniższy przykład implementuje obiekt stanu do odbioru ciągu z klienta zdalnego. Zawiera pola dla gniazda klienta, bufor danych służący do odbioru danych oraz <xref:System.Text.StringBuilder> do tworzenia ciągów danych wysyłanych przez klienta. Umieszczenie tych pól w obiekcie State pozwala zachować ich wartości między wieloma wywołaniami odczytu danych z gniazda klienta.  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject 
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 Sekcja `AcceptCallback` metody, która rozpoczyna pobieranie danych z gniazda klienta, najpierw Inicjuje wystąpienie `StateObject` <xref:System.Net.Sockets.Socket.BeginReceive%2A> klasy, a następnie wywołuje metodę, aby rozpocząć odczytywanie danych z gniazda klienta asynchronicznie.  
  
 Poniższy przykład przedstawia metodę Complete `AcceptCallback` . Przyjęto założenie, że istnieje globalna `allDone,` ManualResetEvent o `StateObject` nazwie, że `ReadCallback` Klasa jest zdefiniowana i że metoda jest zdefiniowana w klasie o `SocketListener`nazwie.  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 Ostatnia metoda, która musi być zaimplementowana dla asynchronicznego serwera gniazd, to metoda wywołania zwrotnego odczytu, która zwraca dane wysyłane przez klienta. Podobnie jak Metoda akceptowania wywołania zwrotnego, Metoda odczytu wywołania zwrotnego jest delegatem **AsyncCallback** . Ta metoda odczytuje jeden lub więcej bajtów z gniazda klienta do bufora danych, a następnie ponownie wywołuje metodę **BeginReceive** do momentu ukończenia danych wysyłanych przez klienta. Po odczytaniu całego komunikatu z klienta ciąg jest wyświetlany w konsoli programu, a gniazdo serwera obsługujące połączenie z klientem jest zamknięte.  
  
 Poniższy przykład implementuje `ReadCallback` metodę. Przyjęto założenie `StateObject` , że Klasa jest zdefiniowana.  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    } 
    else 
    {  
        if (state.sb.Length > 1) 
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie synchronicznego gniazda serwera](using-a-synchronous-server-socket.md)
- [Przykład asynchronicznego gniazda serwera](asynchronous-server-socket-example.md)
- [Wątkowość](../../standard/threading/index.md)
- [Nasłuchiwanie przy użyciu gniazd](listening-with-sockets.md)
