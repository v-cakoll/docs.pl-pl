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
# <a name="using-udp-services"></a><span data-ttu-id="779b7-102">Stosowanie usług UDP</span><span class="sxs-lookup"><span data-stu-id="779b7-102">Using UDP Services</span></span>
<span data-ttu-id="779b7-103"><xref:System.Net.Sockets.UdpClient> Klasy komunikuje się z usługami sieciowymi przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="779b7-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="779b7-104">Właściwości i metod <xref:System.Net.Sockets.UdpClient> klasy abstrakcyjnej szczegółowe informacje o tworzeniu <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="779b7-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="779b7-105">Protokołu UDP (User Datagram) to prosty protokół, który sprawia, że najlepszy nakład pracy do dostarczania danych do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="779b7-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="779b7-106">Jednak ponieważ protokołu UDP jest przesyłanie protokołu, datagramy protokołu UDP wysyłane do zdalnego punktu końcowego nie dotrą do celu ani ich dotrą do celu w tej samej kolejności, w której są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="779b7-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="779b7-107">Aplikacje, które używają protokołu UDP musi być przygotowana do obsługi brakujące, zduplikowane i poza sekwencji datagramów.</span><span class="sxs-lookup"><span data-stu-id="779b7-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="779b7-108">Aby wysłać datagram przy użyciu protokołu UDP, trzeba znać adres sieciowy urządzenia sieciowego, hostingu usług, których potrzebujesz i numer portu UDP, używanymi przez usługę do komunikowania się.</span><span class="sxs-lookup"><span data-stu-id="779b7-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="779b7-109">Internet Assigned Numbers Authority (Iana) definiuje numery portów dla usług common (zobacz [nazwę usługi i rejestru numer portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="779b7-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="779b7-110">Usługi nie ma na liście Iana może mieć numery portów z zakresu od 1024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="779b7-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="779b7-111">Adresy sieciowe specjalne są używane do obsługi komunikatów emisji protokołu UDP w sieciach opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="779b7-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="779b7-112">Następujące dyskusji używa wersji 4 Rodzina adresów IP używanych w Internecie, na przykład.</span><span class="sxs-lookup"><span data-stu-id="779b7-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="779b7-113">W wersji 4 adresów użyj 32-bitowy, aby określić adres sieciowy.</span><span class="sxs-lookup"><span data-stu-id="779b7-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="779b7-114">Dla adresów klasy C za pomocą masek podsieci 255.255.255.0 bity te są podzielone na czterech oktetów.</span><span class="sxs-lookup"><span data-stu-id="779b7-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="779b7-115">Gdy wyrażona w zapisie dziesiętnym, cztery oktety tworzą znanej notacji czterema kropkami, takich jak 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="779b7-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="779b7-116">Pierwsze dwa oktety (192.168 w tym przykładzie) tworzą numer sieci, trzeci oktet (100) definiuje podsieć i końcowe octet (2) jest identyfikatorem hosta.</span><span class="sxs-lookup"><span data-stu-id="779b7-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="779b7-117">Ustawienie wszystkich bitów adresu IP do co najmniej 255.255.255.255, stanowi ograniczone adres emisji.</span><span class="sxs-lookup"><span data-stu-id="779b7-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="779b7-118">Wysyłanie UDP datagram na ten adres dostarcza wiadomość dla każdego hosta w segmencie sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="779b7-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="779b7-119">Ponieważ routerów nigdy nie przekazuje komunikaty wysyłane na ten adres, tylko hosty w segmencie sieci komunikat emisji.</span><span class="sxs-lookup"><span data-stu-id="779b7-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="779b7-120">Emisje może zostać skierowany do określonych części sieci, ustawiając wszystkie bity identyfikator hosta.</span><span class="sxs-lookup"><span data-stu-id="779b7-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="779b7-121">Na przykład aby wysyłać emisji do wszystkich hostów w sieci, identyfikowanych na podstawie adresów IP, począwszy od 192.168.1, należy użyć adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="779b7-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="779b7-122">Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do nasłuchiwania pod kątem wysłane na adres ukierunkowanej emisji 192.168.1.255 na porcie 11 000 datagramy protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="779b7-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="779b7-123">Klient odbiera ciąg wiadomości i zapisuje komunikat do konsoli.</span><span class="sxs-lookup"><span data-stu-id="779b7-123">The client receives a message string and writes the message to the console.</span></span>  
  
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
  
 <span data-ttu-id="779b7-124">Poniższy przykład kodu wykorzystuje <xref:System.Net.Sockets.UdpClient> do przesyłania datagramów protokołu UDP na adres ukierunkowanej emisji 192.168.1.255, przy użyciu portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="779b7-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="779b7-125">Klient wysyła określone w wierszu polecenia ciąg wiadomości.</span><span class="sxs-lookup"><span data-stu-id="779b7-125">The client sends the message string specified on the command line.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="779b7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="779b7-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
