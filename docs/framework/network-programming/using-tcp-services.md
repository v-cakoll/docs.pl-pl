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
ms.openlocfilehash: 3678586647dcf9c47b4494197fbf56cab865b3d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039494"
---
# <a name="using-tcp-services"></a><span data-ttu-id="0e443-102">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="0e443-102">Using TCP Services</span></span>

<span data-ttu-id="0e443-103">Klasa <xref:System.Net.Sockets.TcpClient> żąda danych z zasobu internetowego przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="0e443-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="0e443-104">Metody i właściwości **TcpClient** abstrakcyjne szczegóły tworzenia <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="0e443-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="0e443-105">Ponieważ połączenie z urządzeniem zdalnym jest reprezentowane jako strumień, dane mogą być odczytywane i zapisywane za pomocą technik obsługi strumienia platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0e443-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="0e443-106">Protokół TCP ustanawia połączenie ze zdalnym punktem końcowym, a następnie używa tego połączenia do wysyłania i odbierania pakietów danych.</span><span class="sxs-lookup"><span data-stu-id="0e443-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="0e443-107">Protokół TCP jest odpowiedzialny za zapewnienie, że pakiety danych są wysyłane do punktu końcowego i montowane w odpowiedniej kolejności po ich przybyciu.</span><span class="sxs-lookup"><span data-stu-id="0e443-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="0e443-108">Aby ustanowić połączenie TCP, musisz znać adres urządzenia sieciowego obsługującego usługę, której potrzebujesz, i znać port TCP używany do komunikowania się przez usługę.</span><span class="sxs-lookup"><span data-stu-id="0e443-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="0e443-109">Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych (patrz [Nazwa usługi i Rejestr numerów portów protokołu transportu).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)</span><span class="sxs-lookup"><span data-stu-id="0e443-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="0e443-110">Usługi nienajmowe na liście Iana mogą mieć numery portów w zakresie od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="0e443-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="0e443-111">W poniższym przykładzie pokazano konfigurowanie **TcpClient** do łączenia się z serwerem czasu na porcie TCP 13:</span><span class="sxs-lookup"><span data-stu-id="0e443-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
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

    Overloads Public Shared Function Main(args As String()) As Integer
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
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="0e443-112"><xref:System.Net.Sockets.TcpListener>służy do monitorowania portu TCP pod kątem żądań **przychodzących,** a następnie do tworzenia gniazda lub **tcpClient,** który zarządza połączeniem z klientem.</span><span class="sxs-lookup"><span data-stu-id="0e443-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="0e443-113">Metoda <xref:System.Net.Sockets.TcpListener.Start%2A> umożliwia nasłuchiwanie, a <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda wyłącza nasłuchiwanie na porcie.</span><span class="sxs-lookup"><span data-stu-id="0e443-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="0e443-114">Metoda <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> akceptuje przychodzące żądania połączenia i tworzy **TcpClient** do <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> obsługi żądania, a metoda akceptuje przychodzące żądania połączenia i tworzy **Socket** do obsługi żądania.</span><span class="sxs-lookup"><span data-stu-id="0e443-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="0e443-115">W poniższym przykładzie pokazano tworzenie serwera czasu sieciowego przy użyciu **TcpListener** do monitorowania portu TCP 13.</span><span class="sxs-lookup"><span data-stu-id="0e443-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="0e443-116">Po zaakceptowaniu żądania połączenia przychodzącego serwer czasu odpowiada bieżącą datą i godziną z serwera hosta.</span><span class="sxs-lookup"><span data-stu-id="0e443-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

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
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
