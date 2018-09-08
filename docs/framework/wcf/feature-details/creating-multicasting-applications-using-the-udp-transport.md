---
title: Tworzenie aplikacji multiemisji za pomocą transportu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178042"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Tworzenie aplikacji multiemisji za pomocą transportu UDP
Aplikacje korzystające z multiemisji wysyłać małych dużej liczby odbiorców w tym samym czasie, bez konieczności ustanawiania połączeń punkt-punkt. Szczególnym takich aplikacji to szybkość niezawodności. Innymi słowy jest niezwykle ważne wysłać aktualnych danych niż aby upewnić się, że faktycznie odebraniu szczegółowy komunikat o błędzie. Usługi WCF teraz obsługuje pisanie aplikacji multiemisji za pomocą <xref:System.ServiceModel.UdpBinding>. Tego transportu jest przydatne w scenariuszach, gdzie usługa musi wysyłać małych komunikatów do wielu klientów jednocześnie. Aplikacja giełdowej jest przykładem takiej usługi.  
  
## <a name="implementing-a-multicast-application"></a>Wdrażanie aplikacji multiemisji  
 Aby wdrożyć aplikację multiemisji, definiowanie kontraktu usługi i dla poszczególnych składników oprogramowania, wymagającego odpowiada na komunikaty multiemisji, należy zaimplementować kontrakt usługi. Na przykład aplikacja giełdowej może definiowanie kontraktu usługi:  
  
```  
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
  
 Każda aplikacja, która chce odbierać komunikaty multiemisji musi być hostem usługi, który udostępnia ten interfejs.  Na przykład poniżej przedstawiono przykładowy kod, który ilustruje, jak odbierać komunikaty multiemisji:  
  
```  
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
  
 Aplikacja określa adres UDP, który będzie nasłuchiwać wszystkich usług. Nowy <xref:System.ServiceModel.ServiceHost> jest tworzony i punkt końcowy usługi jest udostępniana przy użyciu <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Otwarciu i rozpocznie się nasłuchiwanie przychodzących wiadomości.  
  
 W tego rodzaju scenariusza jest klient, który faktycznie wysyła komunikaty multiemisji. Każda usługa, która nasłuchuje na prawidłowy adres protokołu UDP będzie odbierać komunikaty multiemisji. Poniżej przedstawiono przykładowy klient, który wysyła komunikaty multiemisji:  
  
```  
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
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 Ten kod generuje podstawowe informacje, a następnie używa kontraktu usługi IStockTicker do wysyłania komunikatów multiemisji do wywołania usługi nasłuchuje na prawidłowy adres protokołu UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP i niezawodna obsługa komunikatów  
 Powiązanie protokołu UDP nie obsługuje niezawodną obsługę komunikatów ze względu na charakter uproszczonego protokołu UDP. Jeśli potrzebujesz upewnić się, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu, który obsługuje niezawodną obsługę komunikatów, takich jak HTTP lub TCP. Aby uzyskać więcej informacji na temat niezawodnej obsługi komunikatów, zobacz https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Dwukierunkowe komunikaty multiemisji  
 Komunikaty multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługuje żądanie/nietypizowana odpowiedź wymianę komunikatów. Komunikaty wysyłane za pomocą transportu UDP zawierają zarówno od adresów. Należy zachować ostrożność podczas przy użyciu adresu From, ponieważ może to być złośliwie zmienione na trasie.  Adres można sprawdzić, używając następującego kodu:  
  
```  
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
  
 Ten kod sprawdza, czy pierwszy bajt adres nadawcy, aby zobaczyć, czy zawiera wartość 0xE0, co oznacza, że adres jest adresem multiemisji.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Gdy nasłuchiwanie komunikaty multiemisji pakiet ICMP są wysyłane do routera powiadamiania ją, z której korzystasz na adres multiemisji. Każda osoba w podsieci lokalnej, który ma uprawnienia może nasłuchiwać tych typów pakietów, a także określić, której adres i port multiemisji nasłuchują na.  
  
 Nie należy używać dowolnego ze względów bezpieczeństwa adres IP nadawcy. Te informacje mogą być sfałszowane i może spowodować, że aplikacja do wysyłania odpowiedzi do niewłaściwej maszyny. Jednym ze sposobów, aby osłabić to zagrożenie jest włączyć zabezpieczenia na poziomie komunikatu. W sieci poziomu protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci) można również użyć.
