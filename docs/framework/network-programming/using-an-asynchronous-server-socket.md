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
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="03ca7-102">Przy użyciu gniazda serwera asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="03ca7-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="03ca7-103">Gniazda asynchroniczne serwera umożliwia asynchroniczne model programowania .NET Framework przetworzyć żądania usługi sieci.</span><span class="sxs-lookup"><span data-stu-id="03ca7-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="03ca7-104"><xref:System.Net.Sockets.Socket> Klasy następuje standardowego asynchroniczny wzorzec nazewnictwa .NET Framework; na przykład synchroniczne <xref:System.Net.Sockets.Socket.Accept%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginAccept%2A> i <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="03ca7-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="03ca7-105">Gniazda asynchroniczne serwera wymaga metody, aby rozpocząć, akceptując żądania połączenia od sieci, metody wywołania zwrotnego do obsługi żądań połączenia i rozpocząć odbieranie danych z sieci i metody wywołania zwrotnego do końca odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="03ca7-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="03ca7-106">Wszystkie te metody są omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="03ca7-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="03ca7-107">W poniższym przykładzie, aby rozpocząć, akceptując żądania połączenia z siecią, Metoda `StartListening` inicjuje **gniazda** , a następnie używa **BeginAccept** metodę, aby uruchomić akceptować nowych połączenia.</span><span class="sxs-lookup"><span data-stu-id="03ca7-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="03ca7-108">Metoda wywołania zwrotnego Akceptuj jest wywoływana po odebraniu nowego żądania połączenia w gnieździe.</span><span class="sxs-lookup"><span data-stu-id="03ca7-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="03ca7-109">Odpowiada za pobieranie **gniazda** wystąpienie, które będą obsługiwać połączenia oraz przekazywanie, który **gniazda** wyłączone w wątku, który ma przetwarzać żądania.</span><span class="sxs-lookup"><span data-stu-id="03ca7-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="03ca7-110">Implementuje metody wywołania zwrotnego Akceptuj <xref:System.AsyncCallback> delegata; zwraca typ void i przyjmuje jeden parametr typu <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="03ca7-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="03ca7-111">Poniższy przykład jest powłoki Akceptuj metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03ca7-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-112">**BeginAccept** metoda przyjmuje dwa parametry **AsyncCallback** delegata, który wskazuje metodę wywołania zwrotnego Akceptuj i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03ca7-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="03ca7-113">W poniższym przykładzie nasłuchiwania **gniazda** jest przekazywany do metody wywołania zwrotnego za pośrednictwem *stanu* parametru.</span><span class="sxs-lookup"><span data-stu-id="03ca7-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="03ca7-114">Ten przykład tworzy **AsyncCallback** delegata i zaczyna akceptować połączenia z siecią.</span><span class="sxs-lookup"><span data-stu-id="03ca7-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-115">Asynchroniczne sockets Użyj wątków z puli wątków systemu do przetwarzania przychodzących połączeń.</span><span class="sxs-lookup"><span data-stu-id="03ca7-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="03ca7-116">Jeden wątek jest odpowiedzialny za akceptowanie połączeń, inny wątek jest używane do obsługi każdego połączenia przychodzące i inny wątek jest odpowiedzialny za odbieranie danych z połączenia.</span><span class="sxs-lookup"><span data-stu-id="03ca7-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="03ca7-117">Mogą to być tym samym wątku, w zależności od wątku jest przypisywany przez puli wątków.</span><span class="sxs-lookup"><span data-stu-id="03ca7-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="03ca7-118">W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy wstrzymuje wykonywanie wątku głównego i sygnalizuje, gdy można kontynuować wykonywania.</span><span class="sxs-lookup"><span data-stu-id="03ca7-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="03ca7-119">W poniższym przykładzie przedstawiono metodę asynchroniczną, które tworzy asynchroniczne gniazda protokołu TCP/IP na komputerze lokalnym i zaczyna akceptować połączenia.</span><span class="sxs-lookup"><span data-stu-id="03ca7-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="03ca7-120">Przyjęto założenie, że istnieje globalnym **ManualResetEvent** o nazwie `allDone`, że metoda jest elementem członkowskim klasy o nazwie `SocketListener`, oraz że metoda wywołania zwrotnego o nazwie `acceptCallback` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="03ca7-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-121">Metoda wywołania zwrotnego Akceptuj (`acceptCallback` w poprzednim przykładzie) jest odpowiedzialny sygnalizowania wątku głównego aplikacji, aby kontynuować przetwarzanie, nawiązywania połączenia z klientem i uruchamianie asynchroniczną odczytać danych z klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="03ca7-122">Poniższy przykład jest pierwszą częścią implementacja `acceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="03ca7-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="03ca7-123">Ta sekcja metody sygnały wątku głównego aplikacji, aby kontynuować przetwarzanie i nawiązuje połączenie z klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="03ca7-124">Przyjęto założenie, globalnym **ManualResetEvent** o nazwie `allDone`.</span><span class="sxs-lookup"><span data-stu-id="03ca7-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-125">Odczyt danych z gniazda klienta wymaga przesyłane wartości między asynchroniczne wywołania obiektu stanu.</span><span class="sxs-lookup"><span data-stu-id="03ca7-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="03ca7-126">Poniższy przykład implementuje obiekt stanu w celu odbierania ciąg z klientami zdalnymi.</span><span class="sxs-lookup"><span data-stu-id="03ca7-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="03ca7-127">Plik zawiera pól dla gniazda klienta, a bufor danych na odbieranie danych, a <xref:System.Text.StringBuilder> dla tworzenia ciągu dane wysyłane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="03ca7-128">Umieszczenie tych pól w obiekt stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań można odczytać danych z gniazda klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-129">W sekcji `acceptCallback` metody, która rozpoczyna się odbierania danych z gniazda klienta najpierw inicjuje wystąpienie klasy `StateObject` klasy, a następnie wywołania <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodę, aby rozpocząć odczyt danych z gniazda klienta asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="03ca7-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="03ca7-130">W poniższym przykładzie przedstawiono pełną `acceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="03ca7-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="03ca7-131">Przyjęto założenie, że istnieje globalnym **ManualResetEvent** o nazwie `allDone,` który `StateObject` zdefiniowana jest klasa oraz że `readCallback` metoda jest zdefiniowana w klasie o nazwie `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="03ca7-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="03ca7-132">Metodę końcową, który musi zostać wdrożone dla serwera gniazda asynchroniczne jest metoda odczytu wywołania zwrotnego, która zwraca dane wysyłane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="03ca7-133">Podobnie jak metody wywołania zwrotnego Akceptuj, metody wywołania zwrotnego odczytu jest **AsyncCallback** delegowanie.</span><span class="sxs-lookup"><span data-stu-id="03ca7-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="03ca7-134">Ta metoda odczytuje bajtów co najmniej jeden z gniazda klienta do buforu danych, a następnie wywołuje **BeginReceive** zakończeniu metody ponownie do czasu dane wysyłane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="03ca7-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="03ca7-135">Po przeczytaniu cały komunikat z klienta ciąg jest wyświetlana w konsoli i gniazda serwera obsługi połączenie klienta jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="03ca7-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="03ca7-136">Następujące przykładowe implementuje `readCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="03ca7-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="03ca7-137">Przy założeniu, że `StateObject` klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="03ca7-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03ca7-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03ca7-138">See Also</span></span>  
 [<span data-ttu-id="03ca7-139">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="03ca7-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="03ca7-140">Przykład asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="03ca7-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="03ca7-141">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="03ca7-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="03ca7-142">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="03ca7-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
