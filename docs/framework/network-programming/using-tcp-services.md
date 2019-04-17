---
title: Stosowanie usług TCP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: d9b3c9975c4d10649bdecd6f63cf362a2b2a2738
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611955"
---
# <a name="using-tcp-services"></a><span data-ttu-id="1c2d9-102">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="1c2d9-102">Using TCP Services</span></span>

<span data-ttu-id="1c2d9-103"><xref:System.Net.Sockets.TcpClient> Klasy żąda danych od zasobu w Internecie przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="1c2d9-104">Metody i właściwości **TcpClient** abstrakcji szczegółowe informacje dotyczące tworzenia <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="1c2d9-105">Ponieważ połączenie z urządzeniem zdalnym jest reprezentowany jako strumień, dane można czytać i napisane przy użyciu techniki obsługi strumienia środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>  
  
 <span data-ttu-id="1c2d9-106">Protokół TCP nawiązuje połączenie ze zdalnego punktu końcowego, a następnie używa tego połączenia do wysyłania i odbierania pakietów danych.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="1c2d9-107">TCP jest odpowiedzialny za zagwarantowanie, że pakiety danych są wysyłane do punktu końcowego i zebranych w odpowiedniej kolejności, po ich nadejściu.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>  
  
 <span data-ttu-id="1c2d9-108">Do nawiązywania połączeń TCP, musisz znać adres urządzenia sieciowego, obsługujący usługę, czego potrzebujesz, i musi znać port TCP używany przez usługę do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="1c2d9-109">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="1c2d9-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="1c2d9-110">Usługi nie ma na liście Iana może mieć numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="1c2d9-111">W poniższym przykładzie pokazano ustawienie zapasowej **TcpClient** nawiązać połączenia z serwerem czasu na porcie TCP 13.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="1c2d9-112"><xref:System.Net.Sockets.TcpListener> Służy do monitorowania port TCP dla żądań przychodzących, a następnie utwórz jedną **gniazda** lub **TcpClient** który zarządza połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="1c2d9-113"><xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umożliwia nasłuchiwania i <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda wyłącza nasłuchuje na porcie.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="1c2d9-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda akceptuje przychodzące żądania połączeń i tworzy **TcpClient** obsłużyć żądania oraz <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda akceptuje przychodzące żądania połączeń i tworzy **gniazda**obsłużyć żądania.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>  
  
 <span data-ttu-id="1c2d9-115">W poniższym przykładzie pokazano tworzenie sieci serwera przy użyciu **TcpListener** monitorowanie portu TCP 13.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="1c2d9-116">Po zaakceptowaniu żądań połączenia przychodzących, serwer czasu odpowiada aktualnej daty i godziny od serwera hosta.</span><span class="sxs-lookup"><span data-stu-id="1c2d9-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```
