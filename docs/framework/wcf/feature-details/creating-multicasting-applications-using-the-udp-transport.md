---
title: Tworzenie aplikacji multiemisji za pomocą transportu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 6825aaafe87ae362fd9266f7c7a82a36d054a69f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185251"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Tworzenie aplikacji multiemisji za pomocą transportu UDP
Aplikacje multiemisji wysyłają małe wiadomości do dużej liczby adresatów w tym samym czasie bez konieczności ustanawiania połączeń typu punkt-punkt. Nacisk na takie aplikacje jest szybkość nad niezawodność. Innymi słowy, ważniejsze jest wysyłanie danych w odpowiednim czasie niż zapewnienie, że każda konkretna wiadomość jest rzeczywiście odbierana. WCF obsługuje teraz pisanie aplikacji <xref:System.ServiceModel.UdpBinding>multiemisji przy użyciu pliku . Ten transport jest przydatny w scenariuszach, w których usługa musi wysyłać małe wiadomości do wielu klientów jednocześnie. Aplikacja stock ticker jest przykładem takiej usługi.  
  
## <a name="implementing-a-multicast-application"></a>Implementowanie aplikacji multiemisji  
 Aby zaimplementować aplikację multiemisji, należy zdefiniować umowę serwisową i dla każdego składnika oprogramowania, który musi odpowiadać na komunikaty multiemisji, zaimplementuj umowę serwisową. Na przykład aplikacja giełdowa może zdefiniować umowę serwisową:  
  
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
  
 Każda aplikacja, która chce odbierać komunikaty multiemisji musi obsługiwać usługę, która udostępnia ten interfejs.  Na przykład oto przykładowy kod, który ilustruje sposób odbierania wiadomości multiemisji:  
  
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
  
 Aplikacja określa adres UDP, na który będą nasłuchiwanie wszystkich usług. Tworzony <xref:System.ServiceModel.ServiceHost> jest nowy, a punkt końcowy <xref:System.ServiceModel.UdpBinding>usługi jest narażony przy użyciu pliku . Następnie <xref:System.ServiceModel.ServiceHost> zostanie otwarty i rozpocznie nasłuchiwanie wiadomości przychodzących.  
  
 W tego typu scenariuszu jest klient, który faktycznie wysyła komunikaty multiemisji. Każda usługa nasłuchiwania przy prawidłowym adresie UDP otrzyma komunikaty multiemisji. Oto przykład klienta, który wysyła komunikaty multiemisji:  
  
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
  
 Ten kod generuje informacje o magazynie, a następnie używa umowy serwisowej IStockTicker do wysyłania wiadomości multiemisji do usług wywołujących nasłuchiwanie na poprawny adres UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP i niezawodne wiadomości  
 Powiązanie UDP nie obsługuje niezawodnej obsługi wiadomości ze względu na lekki charakter protokołu UDP. Jeśli chcesz potwierdzić, że wiadomości są odbierane przez zdalny punkt końcowy, należy użyć transportu, który obsługuje niezawodne wiadomości, takie jak HTTP lub TCP. Aby uzyskać więcej informacji na temat niezawodnych wiadomości, zobaczhttps://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Dwukierunkowe wiadomości multiemisji  
 Podczas gdy wiadomości multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługuje wymianę żądań/odpowiedzi. Wiadomości wysyłane przy użyciu transportu UDP zawierają adres Od i Do. Należy zwrócić uwagę podczas korzystania z adresu Od, ponieważ może to być złośliwie zmienione w drodze.  Adres można sprawdzić za pomocą następującego kodu:  
  
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
  
 Ten kod sprawdza pierwszy bajt adresu Od, aby sprawdzić, czy zawiera 0xE0, co oznacza, że adres jest adresem wielokrotnego rzutowania.  
  
### <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 Podczas nasłuchiwania wiadomości multiemisji pakiet ICMP jest wysyłany do routera z powiadomieniem, że nasłuchujesz na adres multiemisji. Każda osoba w podsieci lokalnej, która ma uprawnienia, może nasłuchiwanie tego typu pakietów i określać adres multiemisji i port, na który nasłuchujesz.  
  
 Nie używaj adresu IP nadawcy do celów bezpieczeństwa. Te informacje mogą być sfałszowane i może spowodować, że aplikacja do wysyłania odpowiedzi do niewłaściwego komputera. Jednym ze sposobów ograniczenia tego zagrożenia jest włączenie zabezpieczeń na poziomie wiadomości. Na poziomie sieci można również używać protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci).
