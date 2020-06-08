---
title: Używanie asynchronicznego gniazda klienta
description: Ten przykład pokazuje asynchroniczne gniazdo klienta. .NET Framework programowanie asynchroniczne umożliwia kontynuowanie uruchamiania aplikacji podczas przetwarzania połączenia.
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
ms.openlocfilehash: 9cf46e9519bcecf4d7a20ff99b86fa5f66af2087
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502044"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="b2be3-104">Używanie asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="b2be3-104">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="b2be3-105">Asynchroniczne gniazdo klienta nie wstrzymuje aplikacji podczas oczekiwania na ukończenie operacji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="b2be3-105">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="b2be3-106">Zamiast tego używa standardowego modelu programowania .NET Framework, aby przetwarzać połączenie sieciowe w jednym wątku, gdy aplikacja nadal działa w oryginalnym wątku.</span><span class="sxs-lookup"><span data-stu-id="b2be3-106">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="b2be3-107">Gniazda asynchroniczne są odpowiednie dla aplikacji, które intensywnie wykorzystują sieć lub nie mogą czekać na ukończenie operacji sieciowych przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="b2be3-107">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="b2be3-108"><xref:System.Net.Sockets.Socket>Klasa jest zgodna ze wzorcem nazewnictwa .NET Framework dla metod asynchronicznych, na przykład <xref:System.Net.Sockets.Socket.Receive%2A> metoda synchroniczna odnosi się do metod asynchronicznych <xref:System.Net.Sockets.Socket.BeginReceive%2A> i <xref:System.Net.Sockets.Socket.EndReceive%2A> .</span><span class="sxs-lookup"><span data-stu-id="b2be3-108">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="b2be3-109">Operacje asynchroniczne wymagają metody wywołania zwrotnego do zwrócenia wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="b2be3-109">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="b2be3-110">Jeśli aplikacja nie musi znać wyniku, nie jest wymagana żadna metoda wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b2be3-110">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="b2be3-111">W przykładowym kodzie w tej sekcji pokazano, jak rozpocząć łączenie się z urządzeniem sieciowym i metoda wywołania zwrotnego, aby zakończyć połączenie, metodę, aby rozpocząć wysyłanie danych i metodę wywołania zwrotnego w celu ukończenia wysyłania, oraz metodę, aby rozpocząć pobieranie danych i metodę wywołania zwrotnego, aby zakończyć pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="b2be3-111">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="b2be3-112">Gniazda asynchroniczne używają wielu wątków z puli wątków systemowych do przetwarzania połączeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="b2be3-112">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="b2be3-113">Jeden wątek jest odpowiedzialny za Inicjowanie wysyłania lub otrzymywania danych; inne wątki ukończą połączenie z urządzeniem sieciowym i wysyłają lub odbierają dane.</span><span class="sxs-lookup"><span data-stu-id="b2be3-113">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="b2be3-114">W poniższych przykładach wystąpienia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> klasy są używane do wstrzymania wykonywania głównego wątku i sygnału, gdy wykonanie może być kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="b2be3-114">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="b2be3-115">W poniższym przykładzie, aby połączyć gniazdo asynchroniczne z urządzeniem sieciowym, `Connect` Metoda inicjuje **gniazdo** , a następnie wywołuje <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> metodę, przekazując zdalny punkt końcowy reprezentujący urządzenie sieciowe, metodę połączenia wywołania zwrotnego i obiekt stanu ( **gniazdo**klienta), który jest używany do przekazywania informacji o stanie między wywołaniami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="b2be3-115">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="b2be3-116">Przykład implementuje metodę, `Connect` Aby połączyć określone **gniazdo** z określonym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b2be3-116">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="b2be3-117">Przyjęto założenie, że Global **ManualResetEvent** o nazwie `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="b2be3-117">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-118">Metoda Connect wywołania zwrotnego `ConnectCallback` implementuje <xref:System.AsyncCallback> delegata.</span><span class="sxs-lookup"><span data-stu-id="b2be3-118">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="b2be3-119">Nawiązuje połączenie z urządzeniem zdalnym, gdy urządzenie zdalne jest dostępne, a następnie sygnalizuje wątek aplikacji, że połączenie zostało ukończone przez ustawienie **ManualResetEvent** `connectDone` .</span><span class="sxs-lookup"><span data-stu-id="b2be3-119">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="b2be3-120">Poniższy kod implementuje `ConnectCallback` metodę.</span><span class="sxs-lookup"><span data-stu-id="b2be3-120">The following code implements the `ConnectCallback` method.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-121">Przykładowa Metoda `Send` koduje określone dane ciągu w formacie ASCII i wysyła je asynchronicznie do urządzenia sieciowego reprezentowanego przez określone gniazdo.</span><span class="sxs-lookup"><span data-stu-id="b2be3-121">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="b2be3-122">Poniższy przykład implementuje `Send` metodę.</span><span class="sxs-lookup"><span data-stu-id="b2be3-122">The following example implements the `Send` method.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-123">Metoda wysyłania wywołania zwrotnego `SendCallback` implementuje <xref:System.AsyncCallback> delegata.</span><span class="sxs-lookup"><span data-stu-id="b2be3-123">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="b2be3-124">Wysyła dane, gdy urządzenie sieciowe jest gotowe do odebrania.</span><span class="sxs-lookup"><span data-stu-id="b2be3-124">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="b2be3-125">Poniższy przykład pokazuje implementację `SendCallback` metody.</span><span class="sxs-lookup"><span data-stu-id="b2be3-125">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="b2be3-126">Przyjęto założenie, że Global **ManualResetEvent** o nazwie `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="b2be3-126">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-127">Odczytywanie danych z gniazda klienta wymaga obiektu stanu, który przekazuje wartości między wywołaniami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="b2be3-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="b2be3-128">Poniżej przedstawiono klasę przykładowego obiektu stanu do odbioru danych z gniazda klienta.</span><span class="sxs-lookup"><span data-stu-id="b2be3-128">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="b2be3-129">Zawiera pole dla gniazda klienta, bufor dla odebranych danych i obiekt <xref:System.Text.StringBuilder> do przechowywania przychodzącego ciągu danych.</span><span class="sxs-lookup"><span data-stu-id="b2be3-129">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="b2be3-130">Umieszczenie tych pól w obiekcie State pozwala zachować ich wartości między wieloma wywołaniami odczytu danych z gniazda klienta.</span><span class="sxs-lookup"><span data-stu-id="b2be3-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-131">Przykładowa `Receive` Metoda konfiguruje obiekt stanu, a następnie wywołuje metodę **BeginReceive** , aby odczytywać dane z gniazda klienta asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="b2be3-131">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="b2be3-132">Poniższy przykład implementuje `Receive` metodę.</span><span class="sxs-lookup"><span data-stu-id="b2be3-132">The following example implements the `Receive` method.</span></span>  
  
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
  
 <span data-ttu-id="b2be3-133">Metoda odbierania wywołania zwrotnego `ReceiveCallback` implementuje delegata **AsyncCallback** .</span><span class="sxs-lookup"><span data-stu-id="b2be3-133">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="b2be3-134">Odbiera dane z urządzenia sieciowego i kompiluje ciąg komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b2be3-134">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="b2be3-135">Odczytuje on co najmniej jeden bajt danych z sieci do bufora danych, a następnie ponownie wywołuje metodę **BeginReceive** do momentu ukończenia danych wysyłanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b2be3-135">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="b2be3-136">Po odczytaniu wszystkich danych z klienta program `ReceiveCallback` sygnalizuje wątek aplikacji, że dane zostały ukończone przez ustawienie **ManualResetEvent** `sendDone` .</span><span class="sxs-lookup"><span data-stu-id="b2be3-136">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="b2be3-137">Poniższy przykładowy kod implementuje `ReceiveCallback` metodę.</span><span class="sxs-lookup"><span data-stu-id="b2be3-137">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="b2be3-138">Przyjęto założenie, że ciąg globalny o nazwie `response` zawiera otrzymany ciąg i globalną **ManualResetEvent** o nazwie `receiveDone` .</span><span class="sxs-lookup"><span data-stu-id="b2be3-138">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="b2be3-139">Serwer musi bezpiecznie zamknąć gniazdo klienta, aby zakończyć sesję sieciową.</span><span class="sxs-lookup"><span data-stu-id="b2be3-139">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2be3-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2be3-140">See also</span></span>

- [<span data-ttu-id="b2be3-141">Używanie synchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="b2be3-141">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="b2be3-142">Nasłuchiwanie przy użyciu gniazd</span><span class="sxs-lookup"><span data-stu-id="b2be3-142">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="b2be3-143">Przykład asynchronicznego gniazda klienta</span><span class="sxs-lookup"><span data-stu-id="b2be3-143">Asynchronous Client Socket Example</span></span>](asynchronous-client-socket-example.md)
