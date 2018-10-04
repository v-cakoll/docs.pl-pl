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
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266434"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="9ab1a-102">Za pomocą asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="9ab1a-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="9ab1a-103">Server asynchronicznego gniazda używają modelu programowania asynchronicznego środowiska .NET Framework do przetwarzania żądania usługi sieci.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="9ab1a-104"><xref:System.Net.Sockets.Socket> Klasy postępuje zgodnie ze standardowym .NET Framework asynchroniczny wzorzec nazewnictwa; na przykład synchronicznego <xref:System.Net.Sockets.Socket.Accept%2A> metody odpowiada asynchroniczną <xref:System.Net.Sockets.Socket.BeginAccept%2A> i <xref:System.Net.Sockets.Socket.EndAccept%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="9ab1a-105">Asynchronicznego gniazda serwera wymaga metodę, aby zacząć akceptować żądań połączeń od sieci, metody wywołania zwrotnego do obsługi żądań połączenia i zacząć odbierać dane z sieci i metody wywołania zwrotnego do końca odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="9ab1a-106">Wszystkie te metody zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="9ab1a-107">W poniższym przykładzie, aby rozpocząć, akceptując żądania połączenia z siecią, Metoda `StartListening` inicjuje **gniazda** , a następnie używa **BeginAccept** zacznij akceptować nowe metody połączenia.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="9ab1a-108">Akceptuj metody wywołania zwrotnego jest wywoływana, gdy zostanie odebrane żądanie nowego połączenia gniazda.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="9ab1a-109">Odpowiada za pobieranie **gniazda** wystąpienia, która będzie obsługiwać połączenia oraz przekazywanie, **gniazda** wyłączony do wątku, który będzie przetwarzał żądanie.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="9ab1a-110">Implementuje metody wywołania zwrotnego Akceptuj <xref:System.AsyncCallback> delegować; zwraca wartość typu void i przyjmuje jeden parametr typu <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="9ab1a-111">Poniższy przykład jest powłoka Akceptuj metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-112">**BeginAccept** metoda przyjmuje dwa parametry **AsyncCallback** delegat, który wskazuje na metody wywołania zwrotnego Akceptuj i obiekt, który jest używany do przekazywania informacji o stanie do metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="9ab1a-113">W poniższym przykładzie nasłuchiwania **gniazda** jest przekazywany do metody wywołania zwrotnego za pośrednictwem *stanu* parametru.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="9ab1a-114">Ten przykład tworzy **AsyncCallback** delegata i rozpoczyna się akceptować połączenia z siecią.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-115">Asynchronicznego gniazda używają wątków z puli wątków systemu do przetwarzania połączenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="9ab1a-116">Jeden wątek jest odpowiedzialny za akceptowanie połączeń, inny wątek jest używana do obsługi każdego połączenia przychodzące i inny wątek jest odpowiedzialna za odbieranie danych z połączenia.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="9ab1a-117">Mogą to być tym samym wątku, w zależności od tego, który wątek jest przypisywany przez puli wątków.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="9ab1a-118">W poniższym przykładzie <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy zawiesza wykonywanie wątku głównego i sygnalizuje, można kontynuować wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="9ab1a-119">Poniższy przykład przedstawia metodę asynchroniczną, która tworzy asynchronicznego gniazda TCP/IP na komputerze lokalnym i zaczyna akceptować połączenia.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="9ab1a-120">Przyjęto założenie, że dostępna jest globalna **ManualResetEvent** o nazwie `allDone`, że metoda jest składową klasy o nazwie `SocketListener`, i metodę wywołania zwrotnego o nazwie `acceptCallback` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-121">Metoda wywołania zwrotnego Akceptuj (`acceptCallback` w powyższym przykładzie) odpowiada za sygnalizowanie wątku głównego aplikacji, aby kontynuować przetwarzanie, podczas nawiązywania połączenia z klientem i uruchamianie asynchronicznego odczytu danych z klienta.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="9ab1a-122">Poniższy przykład jest pierwszą częścią implementacji `acceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="9ab1a-123">Ta sekcja metody sygnały w wątku głównym aplikacji, aby kontynuować przetwarzanie i nawiązuje połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="9ab1a-124">Przyjęto założenie, globalną **ManualResetEvent** o nazwie `allDone`.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-125">Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołania asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="9ab1a-126">Poniższy przykład implementuje obiektu stanu do odbierania ciąg przez klienta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="9ab1a-127">Zawiera on pola dla gniazda klienta, bufor danych do odbierania danych, a <xref:System.Text.StringBuilder> tworzenia ciągu danych wysyłany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="9ab1a-128">Wprowadzenie do tych pól w obiekcie stanu umożliwia ich wartości, które mają być zachowane w wielu wywołań do odczytywania danych z gniazda klienta.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-129">W sekcji `acceptCallback` metodę, która zacznie otrzymywać dane z gniazda klienta najpierw inicjuje wystąpienie `StateObject` klasy, a następnie wywołania <xref:System.Net.Sockets.Socket.BeginReceive%2A> metodę, aby rozpocząć odczyt danych z gniazda klienta asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="9ab1a-130">W poniższym przykładzie pokazano pełne `acceptCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="9ab1a-131">Przyjęto założenie, że dostępna jest globalna **ManualResetEvent** o nazwie `allDone,` , `StateObject` klasa jest zdefiniowana, a `readCallback` metoda jest zdefiniowana w klasie o nazwie `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="9ab1a-132">Ostatnią metodę, która musi zostać wdrożone dla asynchronicznego gniazda serwera jest metoda odczytu wywołania zwrotnego, która zwraca dane wysyłane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="9ab1a-133">Podobnie jak metody wywołania zwrotnego accept, metody wywołania zwrotnego odczytu jest **AsyncCallback** delegować.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="9ab1a-134">Ta metoda odczytuje bajtów co najmniej jeden z gniazda klienta do bufora danych, a następnie wywołuje **BeginReceive** metoda ponownie do czasu dane wysyłane przez klienta zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="9ab1a-135">Gdy cały komunikat został odczytany z klientem, ciąg jest wyświetlany w konsoli i gniazda serwera obsługi połączenie z klientem zostało zamknięte.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="9ab1a-136">Następujące przykładowe implementuje `readCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="9ab1a-137">Założono, że `StateObject` klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="9ab1a-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ab1a-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ab1a-138">See Also</span></span>  
 [<span data-ttu-id="9ab1a-139">Używanie synchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="9ab1a-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="9ab1a-140">Przykład asynchronicznego gniazda serwera</span><span class="sxs-lookup"><span data-stu-id="9ab1a-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="9ab1a-141">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="9ab1a-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="9ab1a-142">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="9ab1a-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
