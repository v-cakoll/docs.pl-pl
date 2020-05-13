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
ms.openlocfilehash: 5ff40e8759b1732d4ad228b1414f96f9c37e5ac5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209776"
---
# <a name="use-udp-services"></a><span data-ttu-id="37374-102">Korzystanie z usług UDP</span><span class="sxs-lookup"><span data-stu-id="37374-102">Use UDP services</span></span>

<span data-ttu-id="37374-103"><xref:System.Net.Sockets.UdpClient>Klasa komunikuje się z usługami sieciowymi przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="37374-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="37374-104">Właściwości i metody <xref:System.Net.Sockets.UdpClient> klasy są abstrakcyjne Szczegóły tworzenia <xref:System.Net.Sockets.Socket> żądania i otrzymywania danych przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="37374-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="37374-105">UDP (User Datagram Protocol) to prosty protokół, który najlepiej nadaje się do dostarczania danych do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="37374-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="37374-106">Ponieważ jednak protokół UDP jest protokołem bezpołączeni, datagramy UDP wysyłane do zdalnego punktu końcowego nie są gwarantowane, ani nie są gwarantowane w takiej samej kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="37374-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="37374-107">Aplikacje korzystające z protokołu UDP muszą być przygotowane do obsługi brakujących, zduplikowanych i nieaktualnych datagramów.</span><span class="sxs-lookup"><span data-stu-id="37374-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="37374-108">Aby wysłać datagram przy użyciu protokołu UDP, musisz znać adres sieciowy urządzenia sieciowego obsługującego potrzebną usługę oraz numer portu UDP, którego usługa używa do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="37374-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="37374-109">Organizacja Internet Assigned Numbers Authority (IANA) definiuje numery portów dla typowych usług (patrz [nazwa usługi i rejestr numeru portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="37374-109">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="37374-110">Usługi, które nie znajdują się na liście IANA, mogą mieć numery portów z zakresu od 1 024 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="37374-110">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="37374-111">Specjalne adresy sieciowe są używane do obsługi komunikatów emisji UDP w sieciach opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="37374-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="37374-112">W poniższej dyskusji użyto rodziny adresów IP w wersji 4 używanej w Internecie jako przykładu.</span><span class="sxs-lookup"><span data-stu-id="37374-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="37374-113">Adresy IP w wersji 4 używają 32 bitów do określenia adresu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="37374-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="37374-114">W przypadku adresów klasy C przy użyciu maski sieci 255.255.255.0 te bity są rozdzielone na cztery oktety.</span><span class="sxs-lookup"><span data-stu-id="37374-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="37374-115">W przypadku wartości wyrażonej w postaci dziesiętnej Cztery oktety tworzą dobrze znaną notację kropkowaną, taką jak 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="37374-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="37374-116">Pierwsze dwa oktety (192,168 w tym przykładzie) tworzą numer sieci, Trzeci oktet (100) definiuje podsieć, a końcowy oktet (2) jest identyfikatorem hosta.</span><span class="sxs-lookup"><span data-stu-id="37374-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="37374-117">Ustawienie wszystkich bitów adresu IP na jeden lub 255.255.255.255 powoduje ograniczenie adresu emisji.</span><span class="sxs-lookup"><span data-stu-id="37374-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="37374-118">Wysyłanie datagramu UDP na ten adres zawiera komunikat do dowolnego hosta w segmencie sieci lokalnej.</span><span class="sxs-lookup"><span data-stu-id="37374-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="37374-119">Ponieważ routery nigdy nie przesyłają dalej komunikatów wysyłanych do tego adresu, tylko hosty w segmencie sieci odbierają komunikat emisji.</span><span class="sxs-lookup"><span data-stu-id="37374-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="37374-120">Emisje mogą być kierowane do określonych części sieci, ustawiając wszystkie bity identyfikatora hosta.</span><span class="sxs-lookup"><span data-stu-id="37374-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="37374-121">Na przykład aby wysłać emisję do wszystkich hostów w sieci identyfikowanych przez adresy IP zaczynające się od 192.168.1, użyj adresu 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="37374-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="37374-122">Poniższy przykład kodu używa metody, <xref:System.Net.Sockets.UdpClient> aby nasłuchiwać datagramów UDP na porcie 11 000.</span><span class="sxs-lookup"><span data-stu-id="37374-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="37374-123">Klient odbiera ciąg komunikatu i zapisuje komunikat w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="37374-123">The client receives a message string and writes the message to the console.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000

   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener

   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
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
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);

        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);

                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }

    public static void Main()
    {
        StartListener();
    }
}
```

<span data-ttu-id="37374-124">Poniższy przykład kodu używa <xref:System.Net.Sockets.Socket> do wysyłania datagramów UDP do bezpośredniego adresu emisji 192.168.1.255, przy użyciu portu 11 000.</span><span class="sxs-lookup"><span data-stu-id="37374-124">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="37374-125">Klient wysyła ciąg komunikatu określony w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="37374-125">The client sends the message string specified on the command line.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
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
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("192.168.1.255");

        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);

        s.SendTo(sendbuf, ep);

        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="37374-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37374-126">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
