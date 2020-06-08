---
title: Stosowanie usług TCP
description: Klasa TcpClient jest abstrakcyjna, aby utworzyć gniazdo do żądania i odbierania danych przy użyciu protokołu TCP. Funkcja obsługi strumienia .NET Framework umożliwia odczytywanie i zapisywanie danych.
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
ms.openlocfilehash: 329701e8f11ca7f87c40ee8b2cc6a337435242b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501966"
---
# <a name="using-tcp-services"></a><span data-ttu-id="6a0aa-104">Stosowanie usług TCP</span><span class="sxs-lookup"><span data-stu-id="6a0aa-104">Using TCP Services</span></span>

<span data-ttu-id="6a0aa-105"><xref:System.Net.Sockets.TcpClient>Klasa żąda danych z zasobu internetowego przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-105">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="6a0aa-106">Metody i właściwości **TcpClient** są abstrakcyjne szczegóły dotyczące tworzenia <xref:System.Net.Sockets.Socket> żądania i otrzymywania danych przy użyciu protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-106">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="6a0aa-107">Ponieważ połączenie z urządzeniem zdalnym jest reprezentowane jako strumień, dane mogą być odczytywane i zapisywane przy użyciu technik obsługi strumienia .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-107">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="6a0aa-108">Protokół TCP nawiązuje połączenie ze zdalnym punktem końcowym, a następnie używa tego połączenia do wysyłania i odbierania pakietów danych.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-108">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="6a0aa-109">Protokół TCP jest odpowiedzialny za zapewnienie, że pakiety danych są wysyłane do punktu końcowego i zmontowane w odpowiedniej kolejności po nadejściu.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-109">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="6a0aa-110">Aby nawiązać połączenie TCP, musisz znać adres urządzenia sieciowego, którego potrzebujesz, i musisz znać port TCP, którego usługa używa do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-110">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="6a0aa-111">Organizacja Internet Assigned Numbers Authority (IANA) definiuje numery portów dla typowych usług (patrz [nazwa usługi i rejestr numeru portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="6a0aa-111">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="6a0aa-112">Usługi, które nie znajdują się na liście Iana, mogą mieć numery portów z zakresu od 1 024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-112">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="6a0aa-113">W poniższym przykładzie pokazano, jak skonfigurować **TcpClient** do nawiązywania połączenia z serwerem czasu na porcie TCP 13:</span><span class="sxs-lookup"><span data-stu-id="6a0aa-113">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

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

<span data-ttu-id="6a0aa-114"><xref:System.Net.Sockets.TcpListener>służy do monitorowania portu TCP dla żądań przychodzących, a następnie tworzenia **gniazda** lub **TcpClient** , który zarządza połączeniem z klientem.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-114"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="6a0aa-115"><xref:System.Net.Sockets.TcpListener.Start%2A>Metoda umożliwia nasłuchiwanie, a <xref:System.Net.Sockets.TcpListener.Stop%2A> Metoda wyłącza nasłuchiwanie na porcie.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-115">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="6a0aa-116"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A>Metoda akceptuje żądania połączenia przychodzącego i tworzy **TcpClient** do obsługi żądania, a <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> Metoda akceptuje żądania połączeń przychodzących i tworzy **gniazdo** do obsługi żądania.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-116">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="6a0aa-117">Poniższy przykład ilustruje tworzenie serwera czasu sieci przy użyciu **TcpListener** do monitorowania portu TCP 13.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-117">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="6a0aa-118">Po zaakceptowaniu przychodzącego żądania połączenia serwer czasu reaguje na bieżącą datę i godzinę z serwera hosta.</span><span class="sxs-lookup"><span data-stu-id="6a0aa-118">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

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
