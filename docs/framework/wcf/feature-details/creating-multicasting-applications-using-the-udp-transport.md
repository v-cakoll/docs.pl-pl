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
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="8544c-102">Tworzenie aplikacji multiemisji za pomocą transportu UDP</span><span class="sxs-lookup"><span data-stu-id="8544c-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="8544c-103">Aplikacje multiemisji wysyłają małe wiadomości do dużej liczby odbiorców w tym samym czasie bez konieczności ustanawiania połączeń punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="8544c-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="8544c-104">Naciskanie takich aplikacji jest szybsze niż niezawodność.</span><span class="sxs-lookup"><span data-stu-id="8544c-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="8544c-105">Innymi słowy, ważne jest wysyłanie danych czasowych, niż w celu upewnienia się, że określony komunikat jest rzeczywiście odbierany.</span><span class="sxs-lookup"><span data-stu-id="8544c-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="8544c-106">Usługa WCF obsługuje teraz zapisywanie aplikacji multiemisji przy użyciu <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="8544c-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="8544c-107">Ten transport jest użyteczny w scenariuszach, w których usługa musi wysyłać małe komunikaty jednocześnie do wielu klientów.</span><span class="sxs-lookup"><span data-stu-id="8544c-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="8544c-108">Przykładem takiej usługi jest aplikacja giełdowa.</span><span class="sxs-lookup"><span data-stu-id="8544c-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="8544c-109">Implementowanie aplikacji multiemisji</span><span class="sxs-lookup"><span data-stu-id="8544c-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="8544c-110">Aby zaimplementować aplikację multiemisji, zdefiniuj kontrakt usługi i dla każdego składnika oprogramowania, który musi odpowiedzieć na komunikaty multiemisji, zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="8544c-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="8544c-111">Na przykład aplikacja taktcy giełdowego może zdefiniować kontrakt usługi:</span><span class="sxs-lookup"><span data-stu-id="8544c-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="8544c-112">Każda aplikacja, która chce odbierać komunikaty multiemisji, musi obsługiwać usługę, która uwidacznia ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="8544c-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="8544c-113">Na przykład Oto przykładowy kod, który ilustruje sposób odbierania komunikatów multiemisji:</span><span class="sxs-lookup"><span data-stu-id="8544c-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="8544c-114">Aplikacja określa adres UDP, na którym będą nasłuchiwanie wszystkie usługi.</span><span class="sxs-lookup"><span data-stu-id="8544c-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="8544c-115"><xref:System.ServiceModel.ServiceHost>Tworzony jest nowy, a punkt końcowy usługi jest ujawniany przy użyciu <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="8544c-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="8544c-116">Zostanie <xref:System.ServiceModel.ServiceHost> otwarty i rozpocznie nasłuchiwanie komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="8544c-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="8544c-117">W tym typie scenariusza jest to klient wysyłający komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8544c-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="8544c-118">Każda usługa, która nasłuchuje na prawidłowym adresie UDP, będzie odbierać komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8544c-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="8544c-119">Oto przykład klienta wysyłającego komunikaty multiemisji:</span><span class="sxs-lookup"><span data-stu-id="8544c-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="8544c-120">Ten kod generuje informacje o zapasach, a następnie używa IStockTicker kontraktu usługi do wysyłania komunikatów multiemisji w celu wywołania usług nasłuchujących na prawidłowym adresie UDP.</span><span class="sxs-lookup"><span data-stu-id="8544c-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="8544c-121">UDP i niezawodne komunikaty</span><span class="sxs-lookup"><span data-stu-id="8544c-121">UDP and Reliable Messaging</span></span>  
  <span data-ttu-id="8544c-122">Powiązanie UDP nie obsługuje niezawodnej obsługi komunikatów z powodu lekkiego charakteru protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="8544c-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="8544c-123">Jeśli musisz potwierdzić, że komunikaty są odbierane przez zdalny punkt końcowy, użyj transportu obsługującego niezawodne wiadomości, takie jak HTTP lub TCP.</span><span class="sxs-lookup"><span data-stu-id="8544c-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="8544c-124">Aby uzyskać więcej informacji na temat niezawodnej obsługi komunikatów, zobacz <https://go.microsoft.com/fwlink/?LinkId=231830> .</span><span class="sxs-lookup"><span data-stu-id="8544c-124">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="8544c-125">Dwukierunkowa obsługa komunikatów multiemisji</span><span class="sxs-lookup"><span data-stu-id="8544c-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="8544c-126">Gdy komunikaty multiemisji są ogólnie jednokierunkowe, UdpBinding obsługuje wymianę komunikatów żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8544c-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="8544c-127">Komunikaty wysyłane za pośrednictwem transportu UDP zawierają zarówno adres od, jak i do.</span><span class="sxs-lookup"><span data-stu-id="8544c-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="8544c-128">Należy zachować ostrożność w przypadku używania adresu od, ponieważ może on zostać złośliwie zmieniony w trasie.</span><span class="sxs-lookup"><span data-stu-id="8544c-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="8544c-129">Adres można sprawdzić przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="8544c-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="8544c-130">Ten kod sprawdza pierwszy bajt adresu od, aby sprawdzić, czy zawiera on wartość 0xE0, który oznacza, że adres jest adresem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8544c-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="8544c-131">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="8544c-131">Security Considerations</span></span>  
 <span data-ttu-id="8544c-132">Podczas nasłuchiwania komunikatów multiemisji pakiet ICMP jest wysyłany do routera z informacją, że nasłuchuje na adresie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="8544c-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="8544c-133">Każda osoba w podsieci lokalnej z uprawnieniami może nasłuchiwać tych typów pakietów i określić, który adres multiemisji i port, na którym nasłuchuje nasłuchiwanie.</span><span class="sxs-lookup"><span data-stu-id="8544c-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="8544c-134">Nie należy używać adresu IP nadawcy do żadnych celów związanych z bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="8544c-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="8544c-135">Te informacje mogą być sfałszowane i mogą spowodować, że aplikacja wyśle odpowiedzi do niewłaściwej maszyny.</span><span class="sxs-lookup"><span data-stu-id="8544c-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="8544c-136">Jednym ze sposobów na ograniczenie tego zagrożenia jest włączenie zabezpieczeń na poziomie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8544c-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="8544c-137">Można również użyć protokołu IPSec na poziomie sieci (zabezpieczenia protokołu internetowego) i/lub NAP (ochrona dostępu do sieci).</span><span class="sxs-lookup"><span data-stu-id="8544c-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
