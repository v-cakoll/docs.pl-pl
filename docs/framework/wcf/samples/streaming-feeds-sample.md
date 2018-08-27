---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 50fa7ccfde544ac9e0ab762434ccc5c3b94958ea
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929250"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="ad820-102">Przykład strumieniowych kanałów informacyjnych</span><span class="sxs-lookup"><span data-stu-id="ad820-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="ad820-103">Niniejszy przykład pokazuje, jak zarządzać zespolone kanały informacyjne, które zawierają dużą liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="ad820-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="ad820-104">Na serwerze, w przykładzie pokazano sposób opóźnić tworzenie poszczególnych <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w ramach źródła danych do momentu natychmiast przed zapisaniem elementu w strumieniu sieci.</span><span class="sxs-lookup"><span data-stu-id="ad820-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="ad820-105">Na komputerze klienckim przykład pokazuje, jak niestandardowy kanał element formatujący może służyć do odczytania pojedynczych elementów strumienia sieci, tak, aby odczytywanego nigdy nie pełni są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad820-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="ad820-106">Aby zademonstrować najlepsze możliwości przesyłania strumieniowego syndykacji interfejsu API, w tym przykładzie użyto nieco w mało prawdopodobnym scenariuszu, w którym serwer udostępnia źródło danych, który zawiera nieskończona liczba elementów.</span><span class="sxs-lookup"><span data-stu-id="ad820-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="ad820-107">W takim przypadku serwer kontynuuje Generowanie nowych elementów do źródła danych, dopóki nie określa, że klient ma odczytu określoną liczbę elementów z kanału informacyjnego (domyślnie 10).</span><span class="sxs-lookup"><span data-stu-id="ad820-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="ad820-108">Dla uproszczenia zarówno klient, jak i serwera są implementowane w tym samym procesie i użyj udostępnionego `ItemCounter` tworzył obiektu, aby śledzić liczbę elementów klienta.</span><span class="sxs-lookup"><span data-stu-id="ad820-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="ad820-109">`ItemCounter` Typu istnieje tylko w celu umożliwienia przykładowy scenariusz zakończyć prawidłowo i nie jest elementem core wzorca demonstrowany.</span><span class="sxs-lookup"><span data-stu-id="ad820-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="ad820-110">Wykazanie korzysta z programu Visual C# Iteratory (przy użyciu `yield return` konstrukcja — słowo kluczowe).</span><span class="sxs-lookup"><span data-stu-id="ad820-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="ad820-111">Aby uzyskać więcej informacji dotyczących iteratorów zobacz temat "Przy użyciu iteratorów" w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="ad820-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="ad820-112">Usługa</span><span class="sxs-lookup"><span data-stu-id="ad820-112">Service</span></span>  
 <span data-ttu-id="ad820-113">Usługa implementuje podstawową <xref:System.ServiceModel.Web.WebGetAttribute> kontraktu, który składa się z jednej operacji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad820-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="ad820-114">Usługa implementuje ten kontrakt przy użyciu `ItemGenerator` klasy, aby utworzyć strumień potencjalnie nieskończonej <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpień za pomocą iteratora, tak jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad820-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="ad820-115">Podczas implementacji usługi tworzy dane wyjściowe w źródle danych `ItemGenerator.GenerateItems()` jest używana zamiast buforowanego kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="ad820-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```  
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
  
 <span data-ttu-id="ad820-116">W rezultacie strumienia elementu nigdy nie pełni są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad820-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="ad820-117">To zachowanie można zaobserwować, przez ustawianie punktu przerwania `yield return` instrukcji wewnątrz `ItemGenerator.GenerateItems()` metody i biorąc pod uwagę, że napotkano tego punktu przerwania po raz pierwszy po Usługa zwróciła wynik `StreamedFeed()` metody.</span><span class="sxs-lookup"><span data-stu-id="ad820-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="ad820-118">Klient</span><span class="sxs-lookup"><span data-stu-id="ad820-118">Client</span></span>  
 <span data-ttu-id="ad820-119">Klient w tym przykładzie używa niestandardowego <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementację, która opóźnia materializacja poszczególnych elementów w źródle danych, zamiast buforowanie ich do pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad820-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="ad820-120">Niestandardowy `StreamedAtom10FeedFormatter` wystąpienie jest używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ad820-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="ad820-121">Zwykle po wywołaniu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie powróci do momentu całego źródła danych zostały odczytane z sieci i buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad820-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="ad820-122">Jednak `StreamedAtom10FeedFormatter` obiektu zastąpienia <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> do zwrócenia iterator zamiast buforowanego kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad820-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="ad820-123">W rezultacie, każdy element nie został odczytany z sieci do aplikacji klienckiej, przechodzenie przez wyniki `ReadItems()` jest gotowy do użycia go.</span><span class="sxs-lookup"><span data-stu-id="ad820-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="ad820-124">To zachowanie można zaobserwować, przez ustawianie punktu przerwania `yield return` instrukcji wewnątrz `StreamedAtom10FeedFormatter.DelayReadItems()` i obserwowanie, że ten punkt przerwania jest napotkał po raz pierwszy po wywołaniu `ReadFrom()` kończy.</span><span class="sxs-lookup"><span data-stu-id="ad820-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="ad820-125">Poniższe instrukcje przedstawiają sposób tworzenia i uruchamianie aplikacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="ad820-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="ad820-126">Należy pamiętać, że chociaż serwer przestaje generowania elementów, gdy klient może odczytywać 10 elementów, dane wyjściowe pokazują, że klient odczytuje znacznie więcej niż 10 elementów.</span><span class="sxs-lookup"><span data-stu-id="ad820-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="ad820-127">Jest to spowodowane sieci powiązania, używany przez przykładowy przesyła dane w segmentach (KB) 4 KB.</span><span class="sxs-lookup"><span data-stu-id="ad820-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="ad820-128">Jako takie klient odbierze 4KB danych elementu, zanim ma możliwość odczytu nawet jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="ad820-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="ad820-129">Jest to normalne zachowanie (wysyłanie dane przesyłane strumieniowo HTTP jest rozmiar segmentów zwiększa wydajność).</span><span class="sxs-lookup"><span data-stu-id="ad820-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad820-130">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="ad820-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ad820-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad820-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ad820-132">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad820-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ad820-133">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ad820-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad820-134">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ad820-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ad820-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ad820-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ad820-136">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="ad820-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad820-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ad820-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="ad820-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad820-138">See Also</span></span>  
 [<span data-ttu-id="ad820-139">Autonomiczne źródło danych diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ad820-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
