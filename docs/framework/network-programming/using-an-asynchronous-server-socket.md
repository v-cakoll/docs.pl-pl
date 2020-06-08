---
title: Używanie asynchronicznego gniazda serwera
description: Ten przykład pokazuje asynchroniczne gniazdo serwera. Klasa Socket używa programowania asynchronicznego .NET Framework, aby przetwarzać żądania obsługi sieci.
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
ms.openlocfilehash: 8b85afb3ffdf69973eff37ccbb067b470ed44e3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502031"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="3f67c-104">Używanie asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="3f67c-104">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="3f67c-105">Asynchroniczne gniazda serwera używają .NET Framework asynchronicznego modelu programowania do przetwarzania żądań obsługi sieci.</span><span class="sxs-lookup"><span data-stu-id="3f67c-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="3f67c-106"><xref:System.Net.Sockets.Socket>Klasa jest zgodna ze standardowym wzorcem nazewnictwa asynchronicznego .NET Framework, na przykład <xref:System.Net.Sockets.Socket.Accept%2A> metoda synchroniczna odnosi się do metod asynchronicznych <xref:System.Net.Sockets.Socket.BeginAccept%2A> i <xref:System.Net.Sockets.Socket.EndAccept%2A> .</span><span class="sxs-lookup"><span data-stu-id="3f67c-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="3f67c-107">Asynchroniczne gniazdo serwera wymaga metody do rozpoczęcia akceptowania żądań połączenia z sieci, metody wywołania zwrotnego do obsługi żądań połączeń i rozpoczęcia odbierania danych z sieci oraz metody wywołania zwrotnego, która ma kończyć pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="3f67c-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="3f67c-108">Wszystkie te metody zostały omówione w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f67c-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="3f67c-109">W poniższym przykładzie, aby rozpocząć akceptowanie żądań połączeń z sieci, Metoda `StartListening` inicjuje **gniazdo** , a następnie używa metody **BeginAccept** w celu rozpoczęcia przyjmowania nowych połączeń.</span><span class="sxs-lookup"><span data-stu-id="3f67c-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="3f67c-110">Metoda akceptowania wywołania zwrotnego jest wywoływana, gdy w gnieździe zostanie odebrane nowe żądanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f67c-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="3f67c-111">Jest on odpowiedzialny za pobieranie wystąpienia **gniazda** , które będzie obsługiwać połączenie i przekazanie tego **gniazda** do wątku, który będzie przetwarzać żądanie.</span><span class="sxs-lookup"><span data-stu-id="3f67c-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="3f67c-112">Metoda akceptowania wywołania zwrotnego implementuje <xref:System.AsyncCallback> delegata; zwraca wartość void i przyjmuje jeden parametr typu <xref:System.IAsyncResult> .</span><span class="sxs-lookup"><span data-stu-id="3f67c-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="3f67c-113">Poniższy przykład to powłoka metody akceptowania wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3f67c-113">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="3f67c-114">Metoda **BeginAccept** przyjmuje dwa parametry, delegat elementu **AsyncCallback** wskazujący na metodę Accept wywołania zwrotnego i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3f67c-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="3f67c-115">W poniższym przykładzie **gniazdo** nasłuchiwania jest przesyłane do metody wywołania zwrotnego za pomocą parametru *State* .</span><span class="sxs-lookup"><span data-stu-id="3f67c-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="3f67c-116">Ten przykład tworzy delegata **AsyncCallback** i zaczyna akceptować połączenia z sieci.</span><span class="sxs-lookup"><span data-stu-id="3f67c-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="3f67c-117">Gniazda asynchroniczne używają wątków z puli wątków systemowych do przetwarzania połączeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="3f67c-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="3f67c-118">Jeden wątek jest odpowiedzialny za akceptowanie połączeń, drugi wątek jest używany do obsługi każdego połączenia przychodzącego, a drugi wątek jest odpowiedzialny za odbieranie danych z połączenia.</span><span class="sxs-lookup"><span data-stu-id="3f67c-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="3f67c-119">Może to być ten sam wątek, w zależności od tego, który wątek jest przypisywany przez pulę wątków.</span><span class="sxs-lookup"><span data-stu-id="3f67c-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="3f67c-120">W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa wstrzymuje wykonywanie głównego wątku i sygnalizuje, kiedy wykonywanie może być kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="3f67c-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="3f67c-121">Poniższy przykład przedstawia metodę asynchroniczną, która tworzy asynchroniczne gniazdo TCP/IP na komputerze lokalnym i rozpoczyna akceptowanie połączeń.</span><span class="sxs-lookup"><span data-stu-id="3f67c-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="3f67c-122">Przyjęto założenie, że istnieje globalna **ManualResetEvent** o nazwie `allDone` , która jest elementem członkowskim klasy o nazwie `SocketListener` i że określono metodę wywołania zwrotnego o nazwie `AcceptCallback` .</span><span class="sxs-lookup"><span data-stu-id="3f67c-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="3f67c-123">Metoda akceptowania wywołania zwrotnego ( `AcceptCallback` w poprzednim przykładzie) jest odpowiedzialna za sygnalizowanie wątku głównego aplikacji w celu kontynuowania przetwarzania, ustanowienia połączenia z klientem i uruchomienia asynchronicznego odczytu danych z klienta.</span><span class="sxs-lookup"><span data-stu-id="3f67c-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="3f67c-124">Poniższy przykład jest pierwszą częścią implementacji `AcceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="3f67c-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="3f67c-125">Ta sekcja metody informuje główny wątek aplikacji, aby kontynuować przetwarzanie i ustanawia połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="3f67c-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="3f67c-126">Przyjęto założenie, że Global **ManualResetEvent** o nazwie `allDone` .</span><span class="sxs-lookup"><span data-stu-id="3f67c-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="3f67c-127">Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołaniami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="3f67c-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="3f67c-128">Poniższy przykład implementuje obiekt stanu do odbioru ciągu z klienta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="3f67c-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="3f67c-129">Zawiera pola dla gniazda klienta, bufor danych służący do odbioru danych oraz <xref:System.Text.StringBuilder> do tworzenia ciągów danych wysyłanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3f67c-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="3f67c-130">Umieszczenie tych pól w obiekcie State pozwala zachować ich wartości między wieloma wywołaniami odczytu danych z gniazda klienta.</span><span class="sxs-lookup"><span data-stu-id="3f67c-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="3f67c-131">Sekcja `AcceptCallback` metody, która rozpoczyna pobieranie danych z gniazda klienta, najpierw Inicjuje wystąpienie `StateObject` klasy, a następnie wywołuje <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodę, aby rozpocząć odczytywanie danych z gniazda klienta asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="3f67c-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="3f67c-132">Poniższy przykład przedstawia `AcceptCallback` metodę Complete.</span><span class="sxs-lookup"><span data-stu-id="3f67c-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="3f67c-133">Przyjęto założenie, że istnieje globalna **ManualResetEvent** o nazwie, `allDone,` że `StateObject` Klasa jest zdefiniowana i że `ReadCallback` Metoda jest zdefiniowana w klasie o nazwie `SocketListener` .</span><span class="sxs-lookup"><span data-stu-id="3f67c-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="3f67c-134">Ostatnia metoda, która musi być zaimplementowana dla asynchronicznego serwera gniazd, to metoda wywołania zwrotnego odczytu, która zwraca dane wysyłane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3f67c-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="3f67c-135">Podobnie jak Metoda akceptowania wywołania zwrotnego, Metoda odczytu wywołania zwrotnego jest delegatem **AsyncCallback** .</span><span class="sxs-lookup"><span data-stu-id="3f67c-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="3f67c-136">Ta metoda odczytuje jeden lub więcej bajtów z gniazda klienta do bufora danych, a następnie ponownie wywołuje metodę **BeginReceive** do momentu ukończenia danych wysyłanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3f67c-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="3f67c-137">Po odczytaniu całego komunikatu z klienta ciąg jest wyświetlany w konsoli programu, a gniazdo serwera obsługujące połączenie z klientem jest zamknięte.</span><span class="sxs-lookup"><span data-stu-id="3f67c-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="3f67c-138">Poniższy przykład implementuje `ReadCallback` metodę.</span><span class="sxs-lookup"><span data-stu-id="3f67c-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="3f67c-139">Przyjęto założenie, że `StateObject` Klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3f67c-139">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f67c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f67c-140">See also</span></span>

- [<span data-ttu-id="3f67c-141">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="3f67c-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="3f67c-142">Przykład asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="3f67c-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="3f67c-143">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="3f67c-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="3f67c-144">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="3f67c-144">Listening with Sockets</span></span>](listening-with-sockets.md)
