---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 551a97f3cc54915a831fc28eca6ae0ff23101e0b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589789"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="4be60-102">Przykład strumieniowych kanałów informacyjnych</span><span class="sxs-lookup"><span data-stu-id="4be60-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="4be60-103">Ten przykład pokazuje, jak zarządzać źródłami zespolonymi zawierającymi dużą liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="4be60-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="4be60-104">Na serwerze przykład pokazuje, jak opóźnić tworzenie pojedynczych <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w kanale informacyjnym do momentu, gdy element zostanie zapisany do strumienia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="4be60-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="4be60-105">Na kliencie przykład pokazuje, jak niestandardowe elementy formatujące źródło danych zespolonych mogą być używane do odczytywania poszczególnych elementów ze strumienia sieciowego, dzięki czemu odczytywane źródło danych nigdy nie jest w pełni buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4be60-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="4be60-106">Aby najlepiej przedstawić możliwości przesyłania strumieniowego interfejsu API zespolonego, w tym przykładzie jest używany nieco mało prawdopodobny scenariusz, w którym serwer uwidacznia źródło danych zawierające nieskończoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="4be60-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="4be60-107">W takim przypadku serwer kontynuuje generowanie nowych elementów w kanale informacyjnym do momentu określenia, że klient odczytał określoną liczbę elementów ze źródła danych (domyślnie 10).</span><span class="sxs-lookup"><span data-stu-id="4be60-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="4be60-108">Dla uproszczenia zarówno klient, jak i serwer są zaimplementowane w tym samym procesie i używają udostępnionego `ItemCounter` obiektu do śledzenia liczby elementów, które wygenerował klient.</span><span class="sxs-lookup"><span data-stu-id="4be60-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="4be60-109">`ItemCounter`Typ istnieje tylko w celu umożliwienia czyszczenia przykładowego scenariusza i nie jest elementem podstawowym wzorca, który jest demonstrowany.</span><span class="sxs-lookup"><span data-stu-id="4be60-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="4be60-110">Demonstracja wykorzystuje Iteratory języka Visual C# (przy użyciu `yield return` konstrukcji słowa kluczowego).</span><span class="sxs-lookup"><span data-stu-id="4be60-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="4be60-111">Aby uzyskać więcej informacji na temat iteratorów, zobacz temat "Używanie iteratorów" w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="4be60-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="4be60-112">Usługa</span><span class="sxs-lookup"><span data-stu-id="4be60-112">Service</span></span>  
 <span data-ttu-id="4be60-113">Usługa implementuje podstawową umowę, <xref:System.ServiceModel.Web.WebGetAttribute> która składa się z jednej operacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4be60-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="4be60-114">Usługa implementuje ten kontrakt przy użyciu klasy, `ItemGenerator` Aby utworzyć potencjalnie nieskończony strumień <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpień przy użyciu iteratora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4be60-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="4be60-115">Po utworzeniu źródła danych przez implementację usługi, `ItemGenerator.GenerateItems()` zamiast buforowanej kolekcji elementów jest używany wynik.</span><span class="sxs-lookup"><span data-stu-id="4be60-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="4be60-116">W efekcie strumień elementu nigdy nie jest w pełni buforowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="4be60-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="4be60-117">Możesz obsłużyć to zachowanie, ustawiając punkt przerwania w `yield return` instrukcji wewnątrz `ItemGenerator.GenerateItems()` metody i zwracając uwagę, że ten punkt przerwania jest wyświetlany po raz pierwszy od momentu, gdy usługa zwróci wynik `StreamedFeed()` metody.</span><span class="sxs-lookup"><span data-stu-id="4be60-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="4be60-118">Klient</span><span class="sxs-lookup"><span data-stu-id="4be60-118">Client</span></span>  
 <span data-ttu-id="4be60-119">Klient w tym przykładzie używa niestandardowej <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementacji, która opóźnia materializację poszczególnych elementów w kanale informacyjnym zamiast buforowania ich do pamięci.</span><span class="sxs-lookup"><span data-stu-id="4be60-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="4be60-120">Wystąpienie niestandardowe `StreamedAtom10FeedFormatter` jest używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="4be60-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="4be60-121">Zwykle wywołanie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie zwraca, dopóki cała zawartość kanału informacyjnego nie została odczytana z sieci i zbuforowana w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4be60-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="4be60-122">Jednak `StreamedAtom10FeedFormatter` obiekt przesłania <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> iterator, zamiast buforowanej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4be60-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="4be60-123">W związku z tym każdy element nie jest odczytywany z sieci do momentu, gdy aplikacja kliencka przestanie `ReadItems()` być gotowa do użycia.</span><span class="sxs-lookup"><span data-stu-id="4be60-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="4be60-124">To zachowanie można obsłużyć przez ustawienie punktu przerwania w `yield return` instrukcji wewnątrz `StreamedAtom10FeedFormatter.DelayReadItems()` i obserwowanie, że ten punkt przerwania jest wywoływany po raz pierwszy po wywołaniu `ReadFrom()` .</span><span class="sxs-lookup"><span data-stu-id="4be60-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="4be60-125">Poniższe instrukcje pokazują, jak skompilować i uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="4be60-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="4be60-126">Należy zauważyć, że mimo że serwer przestaje generować elementy po odczytaniu 10 elementów przez klienta, dane wyjściowe pokazują, że klient odczytuje znacznie więcej niż 10 elementów.</span><span class="sxs-lookup"><span data-stu-id="4be60-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="4be60-127">Wynika to z faktu, że powiązanie sieciowe używane przez przykład przesyła dane w segmentach czterech kilobajtów (KB).</span><span class="sxs-lookup"><span data-stu-id="4be60-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="4be60-128">W związku z tym klient otrzymuje 4 KB danych elementu, zanim będzie miał możliwość odczytania nawet jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="4be60-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="4be60-129">Jest to normalne zachowanie (wysyłanie strumieniowych danych HTTP w przypadku segmentów o rozsądnym rozmiarze zwiększa wydajność).</span><span class="sxs-lookup"><span data-stu-id="4be60-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4be60-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="4be60-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4be60-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4be60-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4be60-132">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4be60-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4be60-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4be60-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4be60-134">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4be60-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4be60-135">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4be60-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4be60-136">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4be60-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4be60-137">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4be60-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="4be60-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4be60-138">See also</span></span>

- [<span data-ttu-id="4be60-139">Autonomiczny kanał diagnostyczny</span><span class="sxs-lookup"><span data-stu-id="4be60-139">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
