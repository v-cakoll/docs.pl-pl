---
title: Tworzenie aplikacji multiemisji za pomocą transportu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 40944129ce3b01d8422d5aba4cfbf913c56265ed
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144633"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Tworzenie aplikacji multiemisji za pomocą transportu UDP
Aplikacje multiemisji wysyłają małe wiadomości do dużej liczby odbiorców w tym samym czasie bez konieczności ustanawiania połączeń punkt-punkt. Naciskanie takich aplikacji jest szybsze niż niezawodność. Innymi słowy, ważne jest wysyłanie danych czasowych, niż w celu upewnienia się, że określony komunikat jest rzeczywiście odbierany. Usługa WCF obsługuje teraz zapisywanie aplikacji multiemisji przy użyciu <xref:System.ServiceModel.UdpBinding> . Ten transport jest użyteczny w scenariuszach, w których usługa musi wysyłać małe komunikaty jednocześnie do wielu klientów. Przykładem takiej usługi jest aplikacja giełdowa.  
  
## <a name="implementing-a-multicast-application"></a>Implementowanie aplikacji multiemisji  
 Aby zaimplementować aplikację multiemisji, zdefiniuj kontrakt usługi i dla każdego składnika oprogramowania, który musi odpowiedzieć na komunikaty multiemisji, zaimplementuj kontrakt usługi. Na przykład aplikacja taktcy giełdowego może zdefiniować kontrakt usługi:  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 Każda aplikacja, która chce odbierać komunikaty multiemisji, musi obsługiwać usługę, która uwidacznia ten interfejs.  Na przykład Oto przykładowy kod, który ilustruje sposób odbierania komunikatów multiemisji:  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 Aplikacja określa adres UDP, na którym będą nasłuchiwanie wszystkie usługi. <xref:System.ServiceModel.ServiceHost>Tworzony jest nowy, a punkt końcowy usługi jest ujawniany przy użyciu <xref:System.ServiceModel.UdpBinding> . Zostanie <xref:System.ServiceModel.ServiceHost> otwarty i rozpocznie nasłuchiwanie komunikatów przychodzących.  
  
 W tym typie scenariusza jest to klient wysyłający komunikaty multiemisji. Każda usługa, która nasłuchuje na prawidłowym adresie UDP, będzie odbierać komunikaty multiemisji. Oto przykład klienta wysyłającego komunikaty multiemisji:  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 Ten kod generuje informacje o zapasach, a następnie używa IStockTicker kontraktu usługi do wysyłania komunikatów multiemisji w celu wywołania usług nasłuchujących na prawidłowym adresie UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP i niezawodne komunikaty  
  Powiązanie UDP nie obsługuje niezawodnej obsługi komunikatów z powodu lekkiego charakteru protokołu UDP. Jeśli musisz potwierdzić, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu obsługującego niezawodne wiadomości, takie jak HTTP lub TCP. Aby uzyskać więcej informacji na temat niezawodnej obsługi komunikatów, zobacz <https://go.microsoft.com/fwlink/?LinkId=231830> .  
  
### <a name="two-way-multicast-messaging"></a>Dwukierunkowa obsługa komunikatów multiemisji  
 Gdy komunikaty multiemisji są ogólnie jednokierunkowe, UdpBinding obsługuje wymianę komunikatów żądania/odpowiedzi. Komunikaty wysyłane za pośrednictwem transportu UDP zawierają zarówno adres od, jak i do. Należy zachować ostrożność w przypadku używania adresu od, ponieważ może on zostać złośliwie zmieniony w trasie.  Adres można sprawdzić przy użyciu następującego kodu:  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 Ten kod sprawdza pierwszy bajt adresu od, aby sprawdzić, czy zawiera on wartość 0xE0, który oznacza, że adres jest adresem multiemisji.  
  
### <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 Podczas nasłuchiwania komunikatów multiemisji pakiet ICMP jest wysyłany do routera z informacją, że nasłuchuje na adresie multiemisji. Każda osoba w podsieci lokalnej z uprawnieniami może nasłuchiwać tych typów pakietów i określić, który adres multiemisji i port, na którym nasłuchuje nasłuchiwanie.  
  
 Nie należy używać adresu IP nadawcy do żadnych celów związanych z bezpieczeństwem. Te informacje mogą być sfałszowane i mogą spowodować, że aplikacja wyśle odpowiedzi do niewłaściwej maszyny. Jednym ze sposobów na ograniczenie tego zagrożenia jest włączenie zabezpieczeń na poziomie komunikatów. Można również użyć protokołu IPSec na poziomie sieci (zabezpieczenia protokołu internetowego) i/lub NAP (ochrona dostępu do sieci).
