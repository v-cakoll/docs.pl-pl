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
ms.openlocfilehash: 477095ada6e44f66cbc60cd80375da9a87f38e39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180599"
---
# <a name="using-udp-services"></a>Stosowanie usług UDP
Klasa <xref:System.Net.Sockets.UdpClient> komunikuje się z usługami sieciowymi przy użyciu protokołu UDP. Właściwości i metody <xref:System.Net.Sockets.UdpClient> klasy abstrakcyjne szczegóły tworzenia <xref:System.Net.Sockets.Socket> dla żądania i odbierania danych przy użyciu protokołu UDP.

User Datagram Protocol (UDP) to prosty protokół, który dokłada wszelkich starań, aby dostarczać dane do zdalnego hosta. Jednak ponieważ protokół UDP jest protokołem bezłączenia, datagramy UDP wysyłane do zdalnego punktu końcowego nie są gwarantowane do przybycia, ani nie są gwarantowane, aby dotrzeć w tej samej kolejności, w której są wysyłane. Aplikacje korzystające z protokołu UDP muszą być przygotowane do obsługi brakujących, duplikatów i datagramów pozasekwowania.

Aby wysłać datagram przy użyciu protokołu UDP, musisz znać adres sieciowy urządzenia sieciowego obsługującego usługę, której potrzebujesz, oraz numer portu UDP używany do komunikowania się przez usługę. Urząd numerów przypisanych do Internetu (Iana) definiuje numery portów dla usług wspólnych (patrz [Nazwa usługi i Rejestr numerów portów protokołu transportu).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) Usługi nienajmowe na liście Iana mogą mieć numery portów w zakresie od 1024 do 65 535.

Specjalne adresy sieciowe są używane do obsługi komunikatów emisji UDP w sieciach opartych na protokãoła IP. W poniższej dyskusji użyto rodziny adresów IP w wersji 4 używanej w Internecie jako przykładu.

Adresy IP w wersji 4 używają 32 bitów do określania adresu sieciowego. W przypadku adresów klasy C przy użyciu maski sieciowej 255.255.255.0 bity te są podzielone na cztery oktety. Wyrażone w przecinku cztery oktety tworzą znaną notację kropkowana-quad, taką jak 192.168.100.2. Pierwsze dwa oktety (192.168 w tym przykładzie) tworzą numer sieci, trzeci oktet (100) definiuje podsieć, a końcowy oktet (2) jest identyfikatorem hosta.

Ustawienie wszystkich bitów adresu IP na jeden lub 255.255.255.255, tworzy ograniczony adres emisji. Wysłanie datagramu UDP na ten adres dostarcza wiadomość do dowolnego hosta w segmencie sieci lokalnej. Ponieważ routery nigdy nie przesyłają dalej wiadomości wysyłanych na ten adres, tylko hosty w segmencie sieci odbierają komunikat emisji.

Emisje można kierować do określonych części sieci, ustawiając wszystkie bity identyfikatora hosta. Na przykład, aby wysłać emisję do wszystkich hostów w sieci identyfikowanych przez adresy IP zaczynające się od 192.168.1, użyj adresu 192.168.1.255.

Poniższy przykład kodu <xref:System.Net.Sockets.UdpClient> używa do nasłuchiwać datagramów UDP na porcie 11,000. Klient odbiera ciąg wiadomości i zapisuje wiadomość do konsoli.

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

Poniższy przykład kodu <xref:System.Net.Sockets.Socket> używa do wysyłania datagramów UDP do adresu emisji kierowanej 192.168.1.255 przy użyciu portu 11,000. Klient wysyła ciąg komunikatu określony w wierszu polecenia.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
