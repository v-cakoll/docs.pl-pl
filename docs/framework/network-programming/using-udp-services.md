---
title: Stosowanie usług UDP
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
ms.openlocfilehash: 8f0c34b2226863bc04800ac4558c07e969f02154
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191132"
---
# <a name="using-udp-services"></a>Stosowanie usług UDP
<xref:System.Net.Sockets.UdpClient> Klasy komunikuje się z usługami sieciowymi przy użyciu protokołu UDP. Właściwości i metod <xref:System.Net.Sockets.UdpClient> klasy abstrakcyjnej szczegółowe informacje o tworzeniu <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu UDP.  
  
 Protokołu UDP (User Datagram) to prosty protokół, który sprawia, że najlepszy nakład pracy do dostarczania danych do hosta zdalnego. Jednak ponieważ protokołu UDP jest przesyłanie protokołu, datagramy protokołu UDP wysyłane do zdalnego punktu końcowego nie dotrą do celu ani ich dotrą do celu w tej samej kolejności, w której są wysyłane. Aplikacje, które używają protokołu UDP musi być przygotowana do obsługi brakujące, zduplikowane i poza sekwencji datagramów.  
  
 Aby wysłać datagram przy użyciu protokołu UDP, trzeba znać adres sieciowy urządzenia sieciowego, hostingu usług, których potrzebujesz i numer portu UDP, używanymi przez usługę do komunikowania się. Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Usługi nie ma na liście Iana może mieć numery portów z zakresu od 1024 do 65 535.  
  
 Adresy sieciowe specjalne są używane do obsługi komunikatów emisji protokołu UDP w sieciach opartych na protokole IP. Następujące dyskusji używa wersji 4 Rodzina adresów IP używanych w Internecie, na przykład.  
  
 W wersji 4 adresów użyj 32-bitowy, aby określić adres sieciowy. Dla adresów klasy C za pomocą masek podsieci 255.255.255.0 bity te są podzielone na czterech oktetów. Gdy wyrażona w zapisie dziesiętnym, cztery oktety tworzą znanej notacji czterema kropkami, takich jak 192.168.100.2. Pierwsze dwa oktety (192.168 w tym przykładzie) tworzą numer sieci, trzeci oktet (100) definiuje podsieć i końcowe octet (2) jest identyfikatorem hosta.  
  
 Ustawienie wszystkich bitów adresu IP do co najmniej 255.255.255.255, stanowi ograniczone adres emisji. Wysyłanie UDP datagram na ten adres dostarcza wiadomość dla każdego hosta w segmencie sieci lokalnej. Ponieważ routerów nigdy nie przekazuje komunikaty wysyłane na ten adres, tylko hosty w segmencie sieci komunikat emisji.  
  
 Emisje może zostać skierowany do określonych części sieci, ustawiając wszystkie bity identyfikator hosta. Na przykład aby wysyłać emisji do wszystkich hostów w sieci, identyfikowanych na podstawie adresów IP, począwszy od 192.168.1, należy użyć adresu 192.168.1.255.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do nasłuchiwania pod kątem wysłane na adres ukierunkowanej emisji 192.168.1.255 na porcie 11 000 datagramy protokołu UDP. Klient odbiera ciąg wiadomości i zapisuje komunikat do konsoli.  
  
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
  
 Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do przesyłania datagramów protokołu UDP na adres ukierunkowanej emisji 192.168.1.255, przy użyciu portu 11 000. Klient wysyła określone w wierszu polecenia ciąg wiadomości.  
  
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
 
