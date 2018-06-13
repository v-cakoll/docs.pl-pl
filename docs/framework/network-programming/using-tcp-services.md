---
title: Za pomocą usług TCP
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d11566182cc9d0b4f2634350868ec94a0685d996
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397172"
---
# <a name="using-tcp-services"></a>Za pomocą usług TCP
<xref:System.Net.Sockets.TcpClient> Klasy żąda danych od zasobu internetowego za pomocą protokołu TCP. Metody i właściwości **TcpClient** abstrakcyjnej szczegółowe informacje dotyczące tworzenia <xref:System.Net.Sockets.Socket> żądania i odbierania danych za pomocą protokołu TCP. Ponieważ połączenie z urządzeniem zdalnym jest reprezentowana jako strumienia, dane można Odczyt i zapis techniki obsługi strumienia .NET Framework.  
  
 Protokół TCP ustanawia połączenie ze zdalnego punktu końcowego, a następnie używa tego połączenia w celu wysyłania i odbierania pakietów danych. Protokół TCP jest odpowiedzialny za zapewnienie, że pakiety danych są wysyłane do punktu końcowego i zebranych w odpowiedniej kolejności, po ich nadejściu.  
  
 Nawiązywania połączeń TCP, musisz znać adres urządzenia sieciowego obsługującego usługę, które są potrzebne, i musi znać port TCP używany przez usługę do komunikowania się. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (zobacz www.iana.org/assignments/port-numbers). Usługi nie ma na liście przez organizację Iana może mieć numeru portu z zakresu od 1024 do 65 535.  
  
 W poniższym przykładzie pokazano ustawienie się **TcpClient** nawiązać połączenia z serwerem czasu na porcie TCP 13.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> Służy do monitorowania port TCP dla żądań przychodzących, a następnie utworzyć albo **gniazda** lub **TcpClient** który zarządza połączenie z klientem. <xref:System.Net.Sockets.TcpListener.Start%2A> Metoda umożliwia nasłuchiwania i <xref:System.Net.Sockets.TcpListener.Stop%2A> metody wyłącza nasłuchiwanie na porcie. <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> Metoda akceptuje przychodzące żądania połączeń i tworzy **TcpClient** można obsłużyć żądania i <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> metoda akceptuje przychodzące żądania połączeń i tworzy **gniazda**obsłużyć żądanie.  
  
 W poniższym przykładzie pokazano tworzenie sieci czas serwera za pomocą **TcpListener** monitorować TCP port 13. Po zaakceptowaniu przychodzącego żądania połączenia czas server odpowie bieżącą datę i godzinę z serwera hosta.  
  
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
 
