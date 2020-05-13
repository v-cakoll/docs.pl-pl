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
# <a name="use-udp-services"></a>Korzystanie z usług UDP

<xref:System.Net.Sockets.UdpClient>Klasa komunikuje się z usługami sieciowymi przy użyciu protokołu UDP. Właściwości i metody <xref:System.Net.Sockets.UdpClient> klasy są abstrakcyjne Szczegóły tworzenia <xref:System.Net.Sockets.Socket> żądania i otrzymywania danych przy użyciu protokołu UDP.

UDP (User Datagram Protocol) to prosty protokół, który najlepiej nadaje się do dostarczania danych do hosta zdalnego. Ponieważ jednak protokół UDP jest protokołem bezpołączeni, datagramy UDP wysyłane do zdalnego punktu końcowego nie są gwarantowane, ani nie są gwarantowane w takiej samej kolejności, w jakiej zostały wysłane. Aplikacje korzystające z protokołu UDP muszą być przygotowane do obsługi brakujących, zduplikowanych i nieaktualnych datagramów.

Aby wysłać datagram przy użyciu protokołu UDP, musisz znać adres sieciowy urządzenia sieciowego obsługującego potrzebną usługę oraz numer portu UDP, którego usługa używa do komunikacji. Organizacja Internet Assigned Numbers Authority (IANA) definiuje numery portów dla typowych usług (patrz [nazwa usługi i rejestr numeru portu protokołu transportu](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Usługi, które nie znajdują się na liście IANA, mogą mieć numery portów z zakresu od 1 024 do 65 535.

Specjalne adresy sieciowe są używane do obsługi komunikatów emisji UDP w sieciach opartych na protokole IP. W poniższej dyskusji użyto rodziny adresów IP w wersji 4 używanej w Internecie jako przykładu.

Adresy IP w wersji 4 używają 32 bitów do określenia adresu sieciowego. W przypadku adresów klasy C przy użyciu maski sieci 255.255.255.0 te bity są rozdzielone na cztery oktety. W przypadku wartości wyrażonej w postaci dziesiętnej Cztery oktety tworzą dobrze znaną notację kropkowaną, taką jak 192.168.100.2. Pierwsze dwa oktety (192,168 w tym przykładzie) tworzą numer sieci, Trzeci oktet (100) definiuje podsieć, a końcowy oktet (2) jest identyfikatorem hosta.

Ustawienie wszystkich bitów adresu IP na jeden lub 255.255.255.255 powoduje ograniczenie adresu emisji. Wysyłanie datagramu UDP na ten adres zawiera komunikat do dowolnego hosta w segmencie sieci lokalnej. Ponieważ routery nigdy nie przesyłają dalej komunikatów wysyłanych do tego adresu, tylko hosty w segmencie sieci odbierają komunikat emisji.

Emisje mogą być kierowane do określonych części sieci, ustawiając wszystkie bity identyfikatora hosta. Na przykład aby wysłać emisję do wszystkich hostów w sieci identyfikowanych przez adresy IP zaczynające się od 192.168.1, użyj adresu 192.168.1.255.

Poniższy przykład kodu używa metody, <xref:System.Net.Sockets.UdpClient> aby nasłuchiwać datagramów UDP na porcie 11 000. Klient odbiera ciąg komunikatu i zapisuje komunikat w konsoli programu.

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

Poniższy przykład kodu używa <xref:System.Net.Sockets.Socket> do wysyłania datagramów UDP do bezpośredniego adresu emisji 192.168.1.255, przy użyciu portu 11 000. Klient wysyła ciąg komunikatu określony w wierszu polecenia.

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
