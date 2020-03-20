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
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="bc1a8-102">Tworzenie aplikacji multiemisji za pomocą transportu UDP</span><span class="sxs-lookup"><span data-stu-id="bc1a8-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="bc1a8-103">Aplikacje multiemisji wysyłają małe wiadomości do dużej liczby adresatów w tym samym czasie bez konieczności ustanawiania połączeń typu punkt-punkt.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="bc1a8-104">Nacisk na takie aplikacje jest szybkość nad niezawodność.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="bc1a8-105">Innymi słowy, ważniejsze jest wysyłanie danych w odpowiednim czasie niż zapewnienie, że każda konkretna wiadomość jest rzeczywiście odbierana.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="bc1a8-106">WCF obsługuje teraz pisanie aplikacji <xref:System.ServiceModel.UdpBinding>multiemisji przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="bc1a8-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="bc1a8-107">Ten transport jest przydatny w scenariuszach, w których usługa musi wysyłać małe wiadomości do wielu klientów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="bc1a8-108">Aplikacja stock ticker jest przykładem takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="bc1a8-109">Implementowanie aplikacji multiemisji</span><span class="sxs-lookup"><span data-stu-id="bc1a8-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="bc1a8-110">Aby zaimplementować aplikację multiemisji, należy zdefiniować umowę serwisową i dla każdego składnika oprogramowania, który musi odpowiadać na komunikaty multiemisji, zaimplementuj umowę serwisową.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="bc1a8-111">Na przykład aplikacja giełdowa może zdefiniować umowę serwisową:</span><span class="sxs-lookup"><span data-stu-id="bc1a8-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="bc1a8-112">Każda aplikacja, która chce odbierać komunikaty multiemisji musi obsługiwać usługę, która udostępnia ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="bc1a8-113">Na przykład oto przykładowy kod, który ilustruje sposób odbierania wiadomości multiemisji:</span><span class="sxs-lookup"><span data-stu-id="bc1a8-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="bc1a8-114">Aplikacja określa adres UDP, na który będą nasłuchiwanie wszystkich usług.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="bc1a8-115">Tworzony <xref:System.ServiceModel.ServiceHost> jest nowy, a punkt końcowy <xref:System.ServiceModel.UdpBinding>usługi jest narażony przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="bc1a8-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="bc1a8-116">Następnie <xref:System.ServiceModel.ServiceHost> zostanie otwarty i rozpocznie nasłuchiwanie wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="bc1a8-117">W tego typu scenariuszu jest klient, który faktycznie wysyła komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="bc1a8-118">Każda usługa nasłuchiwania przy prawidłowym adresie UDP otrzyma komunikaty multiemisji.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="bc1a8-119">Oto przykład klienta, który wysyła komunikaty multiemisji:</span><span class="sxs-lookup"><span data-stu-id="bc1a8-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="bc1a8-120">Ten kod generuje informacje o magazynie, a następnie używa umowy serwisowej IStockTicker do wysyłania wiadomości multiemisji do usług wywołujących nasłuchiwanie na poprawny adres UDP.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="bc1a8-121">UDP i niezawodne wiadomości</span><span class="sxs-lookup"><span data-stu-id="bc1a8-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="bc1a8-122">Powiązanie UDP nie obsługuje niezawodnej obsługi wiadomości ze względu na lekki charakter protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="bc1a8-123">Jeśli chcesz potwierdzić, że wiadomości są odbierane przez zdalny punkt końcowy, należy użyć transportu, który obsługuje niezawodne wiadomości, takie jak HTTP lub TCP.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="bc1a8-124">Aby uzyskać więcej informacji na temat niezawodnych wiadomości, zobaczhttps://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="bc1a8-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="bc1a8-125">Dwukierunkowe wiadomości multiemisji</span><span class="sxs-lookup"><span data-stu-id="bc1a8-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="bc1a8-126">Podczas gdy wiadomości multiemisji są zazwyczaj jednokierunkowe, UdpBinding obsługuje wymianę żądań/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="bc1a8-127">Wiadomości wysyłane przy użyciu transportu UDP zawierają adres Od i Do.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="bc1a8-128">Należy zwrócić uwagę podczas korzystania z adresu Od, ponieważ może to być złośliwie zmienione w drodze.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="bc1a8-129">Adres można sprawdzić za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="bc1a8-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="bc1a8-130">Ten kod sprawdza pierwszy bajt adresu Od, aby sprawdzić, czy zawiera 0xE0, co oznacza, że adres jest adresem wielokrotnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="bc1a8-131">Zagadnienia związane z zabezpieczeniami</span><span class="sxs-lookup"><span data-stu-id="bc1a8-131">Security Considerations</span></span>  
 <span data-ttu-id="bc1a8-132">Podczas nasłuchiwania wiadomości multiemisji pakiet ICMP jest wysyłany do routera z powiadomieniem, że nasłuchujesz na adres multiemisji.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="bc1a8-133">Każda osoba w podsieci lokalnej, która ma uprawnienia, może nasłuchiwanie tego typu pakietów i określać adres multiemisji i port, na który nasłuchujesz.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="bc1a8-134">Nie używaj adresu IP nadawcy do celów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="bc1a8-135">Te informacje mogą być sfałszowane i może spowodować, że aplikacja do wysyłania odpowiedzi do niewłaściwego komputera.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="bc1a8-136">Jednym ze sposobów ograniczenia tego zagrożenia jest włączenie zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bc1a8-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="bc1a8-137">Na poziomie sieci można również używać protokołu IPSec (Internet Protocol Security) i/lub ochrony dostępu do sieci (Ochrona dostępu do sieci).</span><span class="sxs-lookup"><span data-stu-id="bc1a8-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
