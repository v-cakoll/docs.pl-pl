---
title: Tworzenie aplikacji multiemisji za pomocą transportu UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 84b36029416a66ef03768aed7d0c789a41eed8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490428"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="491a5-102">Tworzenie aplikacji multiemisji za pomocą transportu UDP</span><span class="sxs-lookup"><span data-stu-id="491a5-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="491a5-103">Aplikacje korzystające z multiemisji wysyłać mała do wielu odbiorców w tym samym czasie bez konieczności ustanawiania połączenia punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="491a5-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="491a5-104">Nacisk takich aplikacji jest szybkość nad niezawodności.</span><span class="sxs-lookup"><span data-stu-id="491a5-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="491a5-105">Innymi słowy ma większe znaczenie dla wysyłania aktualnych danych niż aby upewnij się, że faktycznie nieodebrania żadnych określonego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="491a5-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="491a5-106">Usługi WCF obsługuje teraz pisanie aplikacji multiemisji za pomocą <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="491a5-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="491a5-107">Ten transport jest przydatne w scenariuszach, w którym usługa musi wysyłać małych komunikatów do wielu klientów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="491a5-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="491a5-108">Aplikacja giełdowych jest przykładem takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="491a5-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="491a5-109">Wdrażanie aplikacji multiemisji</span><span class="sxs-lookup"><span data-stu-id="491a5-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="491a5-110">Aby wdrożyć aplikację multiemisji, definiowanie kontraktu usługi i dla poszczególnych składników oprogramowania, który musi odpowiadać na komunikaty multiemisji, implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="491a5-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="491a5-111">Na przykład aplikacja giełdowych zdefiniować kontrakt usługi:</span><span class="sxs-lookup"><span data-stu-id="491a5-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="491a5-112">Każda aplikacja, która chce odbierać komunikaty multiemisji musi być hostem usługi, który ujawnia tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="491a5-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="491a5-113">Na przykład poniżej przedstawiono przykładowy kod, która ilustruje sposób odbierania komunikatów multiemisji:</span><span class="sxs-lookup"><span data-stu-id="491a5-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="491a5-114">Aplikacja określa adres UDP, który będzie nasłuchiwanie wszystkich usług.</span><span class="sxs-lookup"><span data-stu-id="491a5-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="491a5-115">Nowy <xref:System.ServiceModel.ServiceHost> jest tworzony i punktu końcowego usługi jest udostępniany przy użyciu <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="491a5-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="491a5-116"><xref:System.ServiceModel.ServiceHost> Następnie jest otwarty i rozpocznie się nasłuchiwanie dla komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="491a5-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="491a5-117">W tym typie scenariusza jest klienta, który faktycznie wysyła komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="491a5-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="491a5-118">Każda usługa, która prowadzi nasłuchiwanie na poprawny adres UDP otrzyma komunikatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="491a5-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="491a5-119">Oto przykład klienta, który wysyła wiadomości multiemisji:</span><span class="sxs-lookup"><span data-stu-id="491a5-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="491a5-120">Ten kod generuje informacje o akcji, a następnie używa kontraktu usługi IStockTicker wysyłanie komunikatów multiemisji do wywoływania usług nasłuchiwanie poprawny adres protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="491a5-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="491a5-121">UDP i niezawodna obsługa komunikatów</span><span class="sxs-lookup"><span data-stu-id="491a5-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="491a5-122">Powiązanie UDP nie obsługuje niezawodna obsługa komunikatów z powodu lekkie rodzaj protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="491a5-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="491a5-123">Jeśli potrzebujesz upewnić się, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu, który obsługuje niezawodna obsługa komunikatów HTTP lub TCP.</span><span class="sxs-lookup"><span data-stu-id="491a5-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="491a5-124">Aby uzyskać więcej informacji o niezawodnej obsługi komunikatów, zobacz http://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="491a5-124">For more information about reliable messaging see http://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="491a5-125">Dwukierunkowe komunikatów multiemisji</span><span class="sxs-lookup"><span data-stu-id="491a5-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="491a5-126">Komunikaty multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługi wymiany wiadomości żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="491a5-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="491a5-127">Komunikatów wysyłanych za pomocą transportu UDP zawierają zarówno od i do adresu.</span><span class="sxs-lookup"><span data-stu-id="491a5-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="491a5-128">Należy uważać, gdy przy użyciu adresu From może być złośliwy zmieniona trasie.</span><span class="sxs-lookup"><span data-stu-id="491a5-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="491a5-129">Adres można sprawdzić przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="491a5-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="491a5-130">Ten kod sprawdza pierwszy bajt adres nadawcy, aby zobaczyć, czy zawiera wartość 0xE0, co oznacza, że adres jest adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="491a5-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="491a5-131">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="491a5-131">Security Considerations</span></span>  
 <span data-ttu-id="491a5-132">Podczas nasłuchiwania dla komunikatów multiemisji pakiet ICMP jest wysyłany do routera, powiadamiania go, której korzystasz na adres multiemisji.</span><span class="sxs-lookup"><span data-stu-id="491a5-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="491a5-133">Każdy komputer w podsieci lokalnej, który ma uprawnienia można nasłuchiwać te typy pakietów, aby ustalić, które adres i port multiemisji nasłuchują na.</span><span class="sxs-lookup"><span data-stu-id="491a5-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="491a5-134">Nie należy używać dowolnego ze względów bezpieczeństwa adres nadawcy.</span><span class="sxs-lookup"><span data-stu-id="491a5-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="491a5-135">Te informacje mogą być sfałszowane i może spowodować aplikacji do wysyłania odpowiedzi do niewłaściwej maszyny.</span><span class="sxs-lookup"><span data-stu-id="491a5-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="491a5-136">Jednym ze sposobów na uniknięcie tego zagrożenia jest umożliwienie zabezpieczeniami na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="491a5-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="491a5-137">W sieci poziomu protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci) może być również używane.</span><span class="sxs-lookup"><span data-stu-id="491a5-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
