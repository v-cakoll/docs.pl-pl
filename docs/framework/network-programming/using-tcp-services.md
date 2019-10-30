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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039494"
---
# <a name="using-tcp-services"></a>Stosowanie usług TCP

Klasa <xref:System.Net.Sockets.TcpClient> żąda danych z zasobu internetowego przy użyciu protokołu TCP. Metody i właściwości **TcpClient** są abstrakcyjne szczegóły dotyczące tworzenia <xref:System.Net.Sockets.Socket> do żądania i otrzymywania danych przy użyciu protokołu TCP. Ponieważ połączenie z urządzeniem zdalnym jest reprezentowane jako strumień, dane mogą być odczytywane i zapisywane przy użyciu technik obsługi strumienia .NET Framework.

Protokół TCP nawiązuje połączenie ze zdalnym punktem końcowym, a następnie używa tego połączenia do wysyłania i odbierania pakietów danych. Protokół TCP jest odpowiedzialny za zapewnienie, że pakiety danych są wysyłane do punktu końcowego i zmontowane w odpowiedniej kolejności po nadejściu.

Aby nawiązać połączenie TCP, musisz znać adres urządzenia sieciowego, którego potrzebujesz, i musisz znać port TCP, którego usługa używa do komunikacji. Organizacja Internet Assigned Numbers Authority (IANA) definiuje numery portów dla typowych usług (patrz [nazwa usługi i rejestr numeru portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Usługi, które nie znajdują się na liście Iana, mogą mieć numery portów z zakresu od 1 024 do 65 535.

W poniższym przykładzie pokazano, jak skonfigurować **TcpClient** do nawiązywania połączenia z serwerem czasu na porcie TCP 13:

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

<xref:System.Net.Sockets.TcpListener> służy do monitorowania portu TCP dla żądań przychodzących, a następnie tworzenia **gniazda** lub **TcpClient** , który zarządza połączeniem z klientem. Metoda <xref:System.Net.Sockets.TcpListener.Start%2A> umożliwia nasłuchiwanie, a metoda <xref:System.Net.Sockets.TcpListener.Stop%2A> wyłącza nasłuchiwanie na porcie. Metoda <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> akceptuje żądania połączeń przychodzących i tworzy **TcpClient** do obsługi żądania, a metoda <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> akceptuje przychodzące żądania połączenia i tworzy **gniazdo** do obsługi żądania.

Poniższy przykład ilustruje tworzenie serwera czasu sieci przy użyciu **TcpListener** do monitorowania portu TCP 13. Po zaakceptowaniu przychodzącego żądania połączenia serwer czasu reaguje na bieżącą datę i godzinę z serwera hosta.

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
