---
title: Za pomocą usług UDP
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bc325a551afd0190ea71b46cc53a275de635bda3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-udp-services"></a>Za pomocą usług UDP
<xref:System.Net.Sockets.UdpClient> Klasy komunikuje się z usługami sieciowymi przy użyciu protokołu UDP. Właściwości i metod <xref:System.Net.Sockets.UdpClient> klasy abstrakcyjnej szczegółów tworzenia <xref:System.Net.Sockets.Socket> żądania i odbierania danych przy użyciu protokołu UDP.  
  
 Protokół UDP (User Datagram) to prosty protokół, który sprawia, że optymalnego do dostarczania danych do hosta zdalnego. Jednak ponieważ protokół UDP jest protokołem bez połączenia, datagramy protokołu UDP wysyłane do zdalnego punktu końcowego nie dotrą do celu ani ich dotrą do celu w takiej samej kolejności, w jakiej są wysyłane. Aplikacje, które korzystają z protokołu UDP muszą być przygotowane do obsługi Brak, zduplikowany i sekwencji datagramów.  
  
 Aby wysłać datagram przy użyciu protokołu UDP, musisz znać adres sieciowy urządzenia sieciowego hosting usług, które są potrzebne i numer portu UDP, używane przez usługę do komunikowania się. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (zobacz www.iana.org/assignments/port-numbers). Usługi nie ma na liście przez organizację Iana może mieć numeru portu z zakresu od 1024 do 65 535.  
  
 Adresów sieciowych są używane do obsługi komunikatów rozgłaszanych UDP w sieciach opartych na protokole IP. Następujące dyskusji używa wersji 4 adresów IP rodziny używanych w Internecie, na przykład.  
  
 Adresy IP w wersji 4 Użyj 32-bitowy, aby określić adresu sieciowego. Dla adresów klasy C za pomocą maski podsieci 255.255.255.0 bity te są podzielone na cztery oktety. Wyrażone w dziesiętnych, cztery oktety tworzą znanych notacji quad kropkami, na przykład 192.168.100.2. Pierwsze dwa oktety (192.168 w tym przykładzie) tworzą numer sieci, trzeci oktet (100) definiuje podsieć i końcowe octet (2) jest identyfikatorem hosta.  
  
 Ustawienie wszystkich bitów adresu IP na co najmniej 255.255.255.255, formularzy ograniczone adresu emisji. Wysyłanie datagramów protokołu UDP na ten adres dostarcza wiadomość dla każdego hosta w segmencie sieci lokalnej. Ponieważ routery nigdy nie przesyła komunikaty wysyłane na ten adres, tylko hosty w segmencie sieci komunikat emisji.  
  
 Emisje może zostać skierowany do określonej części sieci przez ustawienie wszystkich bitów identyfikator hosta. Na przykład aby wysłać emisji do wszystkich hostów w sieci identyfikowanych na podstawie adresów IP, począwszy od 192.168.1, należy użyć adresu 192.168.1.255.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do nasłuchiwania wysłane na adres ukierunkowanej emisji 192.168.1.255 na porcie 11 000 datagramy protokołu UDP. Klient odbiera ciąg z komunikatem i zapisuje komunikat do konsoli.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do przesyłania datagramów protokołu UDP na adres ukierunkowanej emisji 192.168.1.255, przy użyciu portu 11 000. Klient wysyła określone w wierszu polecenia ciąg komunikatu.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
