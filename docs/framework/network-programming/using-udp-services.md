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
# <a name="using-udp-services"></a><span data-ttu-id="d3899-102">Za pomocą usług UDP</span><span class="sxs-lookup"><span data-stu-id="d3899-102">Using UDP Services</span></span>
<span data-ttu-id="d3899-103"><xref:System.Net.Sockets.UdpClient> Klasy komunikuje się z usługami sieciowymi przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d3899-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="d3899-104">Właściwości i metod <xref:System.Net.Sockets.UdpClient> klasy abstrakcyjnej szczegółów tworzenia <xref:System.Net.Sockets.Socket> żądania i odbierania danych przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d3899-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="d3899-105">Protokół UDP (User Datagram) to prosty protokół, który sprawia, że optymalnego do dostarczania danych do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d3899-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="d3899-106">Jednak ponieważ protokół UDP jest protokołem bez połączenia, datagramy protokołu UDP wysyłane do zdalnego punktu końcowego nie dotrą do celu ani ich dotrą do celu w takiej samej kolejności, w jakiej są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="d3899-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="d3899-107">Aplikacje, które korzystają z protokołu UDP muszą być przygotowane do obsługi Brak, zduplikowany i sekwencji datagramów.</span><span class="sxs-lookup"><span data-stu-id="d3899-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="d3899-108">Aby wysłać datagram przy użyciu protokołu UDP, musisz znać adres sieciowy urządzenia sieciowego hosting usług, które są potrzebne i numer portu UDP, używane przez usługę do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="d3899-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="d3899-109">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług wspólnej (zobacz www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="d3899-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="d3899-110">Usługi nie ma na liście przez organizację Iana może mieć numeru portu z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="d3899-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="d3899-111">Adresów sieciowych są używane do obsługi komunikatów rozgłaszanych UDP w sieciach opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="d3899-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="d3899-112">Następujące dyskusji używa wersji 4 adresów IP rodziny używanych w Internecie, na przykład.</span><span class="sxs-lookup"><span data-stu-id="d3899-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="d3899-113">Adresy IP w wersji 4 Użyj 32-bitowy, aby określić adresu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="d3899-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="d3899-114">Dla adresów klasy C za pomocą maski podsieci 255.255.255.0 bity te są podzielone na cztery oktety.</span><span class="sxs-lookup"><span data-stu-id="d3899-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="d3899-115">Wyrażone w dziesiętnych, cztery oktety tworzą znanych notacji quad kropkami, na przykład 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="d3899-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="d3899-116">Pierwsze dwa oktety (192.168 w tym przykładzie) tworzą numer sieci, trzeci oktet (100) definiuje podsieć i końcowe octet (2) jest identyfikatorem hosta.</span><span class="sxs-lookup"><span data-stu-id="d3899-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="d3899-117">Ustawienie wszystkich bitów adresu IP na co najmniej 255.255.255.255, formularzy ograniczone adresu emisji.</span><span class="sxs-lookup"><span data-stu-id="d3899-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="d3899-118">Wysyłanie datagramów protokołu UDP na ten adres dostarcza wiadomość dla każdego hosta w segmencie sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d3899-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="d3899-119">Ponieważ routery nigdy nie przesyła komunikaty wysyłane na ten adres, tylko hosty w segmencie sieci komunikat emisji.</span><span class="sxs-lookup"><span data-stu-id="d3899-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="d3899-120">Emisje może zostać skierowany do określonej części sieci przez ustawienie wszystkich bitów identyfikator hosta.</span><span class="sxs-lookup"><span data-stu-id="d3899-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="d3899-121">Na przykład aby wysłać emisji do wszystkich hostów w sieci identyfikowanych na podstawie adresów IP, począwszy od 192.168.1, należy użyć adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="d3899-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="d3899-122">Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do nasłuchiwania wysłane na adres ukierunkowanej emisji 192.168.1.255 na porcie 11 000 datagramy protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="d3899-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="d3899-123">Klient odbiera ciąg z komunikatem i zapisuje komunikat do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3899-123">The client receives a message string and writes the message to the console.</span></span>  
  
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
  
 <span data-ttu-id="d3899-124">Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do przesyłania datagramów protokołu UDP na adres ukierunkowanej emisji 192.168.1.255, przy użyciu portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="d3899-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="d3899-125">Klient wysyła określone w wierszu polecenia ciąg komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d3899-125">The client sends the message string specified on the command line.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3899-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3899-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
