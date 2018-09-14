---
title: Tworzenie aplikacji multiemisji za pomocą transportu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587327"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="85d15-102">Tworzenie aplikacji multiemisji za pomocą transportu UDP</span><span class="sxs-lookup"><span data-stu-id="85d15-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="85d15-103">Aplikacje korzystające z multiemisji wysyłać małych dużej liczby odbiorców w tym samym czasie, bez konieczności ustanawiania połączeń punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="85d15-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="85d15-104">Szczególnym takich aplikacji to szybkość niezawodności.</span><span class="sxs-lookup"><span data-stu-id="85d15-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="85d15-105">Innymi słowy jest niezwykle ważne wysłać aktualnych danych niż aby upewnić się, że faktycznie odebraniu szczegółowy komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="85d15-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="85d15-106">Usługi WCF teraz obsługuje pisanie aplikacji multiemisji za pomocą <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="85d15-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="85d15-107">Tego transportu jest przydatne w scenariuszach, gdzie usługa musi wysyłać małych komunikatów do wielu klientów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="85d15-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="85d15-108">Aplikacja giełdowej jest przykładem takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="85d15-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="85d15-109">Wdrażanie aplikacji multiemisji</span><span class="sxs-lookup"><span data-stu-id="85d15-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="85d15-110">Aby wdrożyć aplikację multiemisji, definiowanie kontraktu usługi i dla poszczególnych składników oprogramowania, wymagającego odpowiada na komunikaty multiemisji, należy zaimplementować kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="85d15-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="85d15-111">Na przykład aplikacja giełdowej może definiowanie kontraktu usługi:</span><span class="sxs-lookup"><span data-stu-id="85d15-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="85d15-112">Każda aplikacja, która chce odbierać komunikaty multiemisji musi być hostem usługi, który udostępnia ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="85d15-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="85d15-113">Na przykład poniżej przedstawiono przykładowy kod, który ilustruje, jak odbierać komunikaty multiemisji:</span><span class="sxs-lookup"><span data-stu-id="85d15-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="85d15-114">Aplikacja określa adres UDP, który będzie nasłuchiwać wszystkich usług.</span><span class="sxs-lookup"><span data-stu-id="85d15-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="85d15-115">Nowy <xref:System.ServiceModel.ServiceHost> jest tworzony i punkt końcowy usługi jest udostępniana przy użyciu <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="85d15-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="85d15-116"><xref:System.ServiceModel.ServiceHost> Otwarciu i rozpocznie się nasłuchiwanie przychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="85d15-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="85d15-117">W tego rodzaju scenariusza jest klient, który faktycznie wysyła komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="85d15-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="85d15-118">Każda usługa, która nasłuchuje na prawidłowy adres protokołu UDP będzie odbierać komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="85d15-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="85d15-119">Poniżej przedstawiono przykładowy klient, który wysyła komunikaty multiemisji:</span><span class="sxs-lookup"><span data-stu-id="85d15-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="85d15-120">Ten kod generuje podstawowe informacje, a następnie używa kontraktu usługi IStockTicker do wysyłania komunikatów multiemisji do wywołania usługi nasłuchuje na prawidłowy adres protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="85d15-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="85d15-121">UDP i niezawodna obsługa komunikatów</span><span class="sxs-lookup"><span data-stu-id="85d15-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="85d15-122">Powiązanie protokołu UDP nie obsługuje niezawodną obsługę komunikatów ze względu na charakter uproszczonego protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="85d15-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="85d15-123">Jeśli potrzebujesz upewnić się, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu, który obsługuje niezawodną obsługę komunikatów, takich jak HTTP lub TCP.</span><span class="sxs-lookup"><span data-stu-id="85d15-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="85d15-124">Aby uzyskać więcej informacji na temat niezawodnej obsługi komunikatów, zobacz https://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="85d15-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="85d15-125">Dwukierunkowe komunikaty multiemisji</span><span class="sxs-lookup"><span data-stu-id="85d15-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="85d15-126">Komunikaty multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługuje żądanie/nietypizowana odpowiedź wymianę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="85d15-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="85d15-127">Komunikaty wysyłane za pomocą transportu UDP zawierają zarówno od adresów.</span><span class="sxs-lookup"><span data-stu-id="85d15-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="85d15-128">Należy zachować ostrożność podczas przy użyciu adresu From, ponieważ może to być złośliwie zmienione na trasie.</span><span class="sxs-lookup"><span data-stu-id="85d15-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="85d15-129">Adres można sprawdzić, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="85d15-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="85d15-130">Ten kod sprawdza, czy pierwszy bajt adres nadawcy, aby zobaczyć, czy zawiera wartość 0xE0, co oznacza, że adres jest adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="85d15-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="85d15-131">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="85d15-131">Security Considerations</span></span>  
 <span data-ttu-id="85d15-132">Gdy nasłuchiwanie komunikaty multiemisji pakiet ICMP są wysyłane do routera powiadamiania ją, z której korzystasz na adres multiemisji.</span><span class="sxs-lookup"><span data-stu-id="85d15-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="85d15-133">Każda osoba w podsieci lokalnej, który ma uprawnienia może nasłuchiwać tych typów pakietów, a także określić, której adres i port multiemisji nasłuchują na.</span><span class="sxs-lookup"><span data-stu-id="85d15-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="85d15-134">Nie należy używać dowolnego ze względów bezpieczeństwa adres IP nadawcy.</span><span class="sxs-lookup"><span data-stu-id="85d15-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="85d15-135">Te informacje mogą być sfałszowane i może spowodować, że aplikacja do wysyłania odpowiedzi do niewłaściwej maszyny.</span><span class="sxs-lookup"><span data-stu-id="85d15-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="85d15-136">Jednym ze sposobów, aby osłabić to zagrożenie jest włączyć zabezpieczenia na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="85d15-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="85d15-137">W sieci poziomu protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci) można również użyć.</span><span class="sxs-lookup"><span data-stu-id="85d15-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
