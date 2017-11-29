---
title: "Tworzenie aplikacji multiemisji za pomocą transportu UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a743f7da4984c5b434de6cedb44bd4c9d9382cf
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2017
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Tworzenie aplikacji multiemisji za pomocą transportu UDP
Aplikacje korzystające z multiemisji wysyłać mała do wielu odbiorców w tym samym czasie bez konieczności ustanawiania połączenia punkt-punkt. Nacisk takich aplikacji jest szybkość nad niezawodności. Innymi słowy ma większe znaczenie dla wysyłania aktualnych danych niż aby upewnij się, że faktycznie nieodebrania żadnych określonego komunikatu. Usługi WCF obsługuje teraz pisanie aplikacji multiemisji za pomocą <xref:System.ServiceModel.UdpBinding>. Ten transport jest przydatne w scenariuszach, w którym usługa musi wysyłać małych komunikatów do wielu klientów jednocześnie. Aplikacja giełdowych jest przykładem takiej usługi.  
  
## <a name="implementing-a-multicast-application"></a>Wdrażanie aplikacji multiemisji  
 Aby wdrożyć aplikację multiemisji, definiowanie kontraktu usługi i dla poszczególnych składników oprogramowania, który musi odpowiadać na komunikaty multiemisji, implementowanie kontraktu usługi. Na przykład aplikacja giełdowych zdefiniować kontrakt usługi:  
  
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
  
 Każda aplikacja, która chce odbierać komunikaty multiemisji musi być hostem usługi, który ujawnia tego interfejsu.  Na przykład poniżej przedstawiono przykładowy kod, która ilustruje sposób odbierania komunikatów multiemisji:  
  
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
  
 Aplikacja określa adres UDP, który będzie nasłuchiwanie wszystkich usług. Nowy <xref:System.ServiceModel.ServiceHost> jest tworzony i punktu końcowego usługi jest udostępniany przy użyciu <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Następnie jest otwarty i rozpocznie się nasłuchiwanie dla komunikatów przychodzących.  
  
 W tym typie scenariusza jest klienta, który faktycznie wysyła komunikaty multiemisji. Każda usługa, która prowadzi nasłuchiwanie na poprawny adres UDP otrzyma komunikatów multiemisji. Oto przykład klienta, który wysyła wiadomości multiemisji:  
  
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
  
 Ten kod generuje informacje o akcji, a następnie używa kontraktu usługi IStockTicker wysyłanie komunikatów multiemisji do wywoływania usług nasłuchiwanie poprawny adres protokołu UDP.  
  
### <a name="udp-and-reliable-messaging"></a>UDP i niezawodna obsługa komunikatów  
 Powiązanie UDP nie obsługuje niezawodna obsługa komunikatów z powodu lekkie rodzaj protokołu UDP. Jeśli potrzebujesz upewnić się, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu, który obsługuje niezawodna obsługa komunikatów HTTP lub TCP. Aby uzyskać więcej informacji na temat niezawodna obsługa komunikatów zobacz http://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Dwukierunkowe komunikatów multiemisji  
 Komunikaty multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługi wymiany wiadomości żądania/odpowiedzi. Komunikatów wysyłanych za pomocą transportu UDP zawierają zarówno od i do adresu. Należy uważać, gdy przy użyciu adresu From może być złośliwy zmieniona trasie.  Adres można sprawdzić przy użyciu następującego kodu:  
  
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
  
 Ten kod sprawdza pierwszy bajt adres nadawcy, aby zobaczyć, czy zawiera wartość 0xE0, co oznacza, że adres jest adresem multiemisji.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Podczas nasłuchiwania dla komunikatów multiemisji pakiet ICMP jest wysyłany do routera, powiadamiania go, której korzystasz na adres multiemisji. Każdy komputer w podsieci lokalnej, który ma uprawnienia można nasłuchiwać te typy pakietów, aby ustalić, które adres i port multiemisji nasłuchują na.  
  
 Nie należy używać dowolnego ze względów bezpieczeństwa adres nadawcy. Te informacje mogą być sfałszowane i może spowodować aplikacji do wysyłania odpowiedzi do niewłaściwej maszyny. Jednym ze sposobów na uniknięcie tego zagrożenia jest umożliwienie zabezpieczeniami na poziomie wiadomości. W sieci poziomu protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci) może być również używane.
