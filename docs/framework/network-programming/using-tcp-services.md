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
ms.openlocfilehash: 11b0082630fb41823173a87160344d2dfff5482e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193399"
---
# <a name="using-tcp-services"></a>Stosowanie usług TCP
<xref:System.Net.Sockets.TcpClient> Klasy żąda danych od zasobu w Internecie przy użyciu protokołu TCP. Metody i właściwości **TcpClient** abstrakcji szczegółowe informacje dotyczące tworzenia <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu TCP. Ponieważ połączenie z urządzeniem zdalnym jest reprezentowany jako strumień, dane można czytać i napisane przy użyciu techniki obsługi strumienia środowiska .NET Framework.  
  
 Protokół TCP nawiązuje połączenie ze zdalnego punktu końcowego, a następnie używa tego połączenia do wysyłania i odbierania pakietów danych. TCP jest odpowiedzialny za zagwarantowanie, że pakiety danych są wysyłane do punktu końcowego i zebranych w odpowiedniej kolejności, po ich nadejściu.  
  
 Do nawiązywania połączeń TCP, musisz znać adres urządzenia sieciowego, obsługujący usługę, czego potrzebujesz, i musi znać port TCP używany przez usługę do komunikowania się. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Usługi nie ma na liście Iana może mieć numery portów z zakresu od 1024 do 65 535.  
  
 W poniższym przykładzie pokazano ustawienie zapasowej **TcpClient** nawiązać połączenia z serwerem czasu na porcie TCP 13.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> Służy do monitorowania port TCP dla żądań przychodzących, a następnie utwórz jedną **gniazda** lub **TcpClient** który zarządza połączenie z klientem. <xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umożliwia nasłuchiwania i <xref:System.Net.Sockets.TcpListener.Stop%2A> metoda wyłącza nasłuchuje na porcie. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda akceptuje przychodzące żądania połączeń i tworzy **TcpClient** obsłużyć żądania oraz <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda akceptuje przychodzące żądania połączeń i tworzy **gniazda**obsłużyć żądania.  
  
 W poniższym przykładzie pokazano tworzenie sieci serwera przy użyciu **TcpListener** monitorowanie portu TCP 13. Po zaakceptowaniu żądań połączenia przychodzących, serwer czasu odpowiada aktualnej daty i godziny od serwera hosta.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 
