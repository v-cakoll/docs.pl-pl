---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143970"
---
# <a name="streaming-feeds-sample"></a>Przykład strumieniowych kanałów informacyjnych
W tym przykładzie pokazano, jak zarządzać źródła danych zesłania, które zawierają dużą liczbę elementów. Na serwerze przykład pokazuje, jak opóźnić <xref:System.ServiceModel.Syndication.SyndicationItem> tworzenie poszczególnych obiektów w kanale informacyjnym, aż bezpośrednio przed element jest zapisywany do strumienia sieciowego.  
  
 Na kliencie przykład pokazuje, jak niestandardowy formater źródła danych syndykacji może służyć do odczytywania poszczególnych elementów ze strumienia sieciowego, dzięki czemu odczytywany kanał danych nigdy nie jest w pełni buforowany w pamięci.  
  
 Aby najlepiej zademonstrować możliwości przesyłania strumieniowego interfejsu API syndykacji, w tym przykładzie użyto nieco mało prawdopodobnego scenariusza, w którym serwer udostępnia źródło danych, który zawiera nieskończoną liczbę elementów. W takim przypadku serwer kontynuuje generowanie nowych elementów do kanału informacyjnego, dopóki nie ustali, że klient odczytał określoną liczbę elementów z pliku danych (domyślnie 10). Dla uproszczenia zarówno klient, jak i serwer są implementowane w tym samym procesie i używać obiektu udostępnionego, `ItemCounter` aby śledzić, ile elementów klient wyprodukował. Typ `ItemCounter` istnieje tylko w celu umożliwienia scenariusza próbki zakończyć czysto i nie jest podstawowym elementem wzorca, który jest demonstrowany.  
  
 Demonstracja korzysta z visual c# iterators (przy użyciu konstrukcji `yield return` słowa kluczowego). Aby uzyskać więcej informacji na temat iteratorów, zobacz temat "Używanie iteratorów" w u usługi MSDN.  
  
## <a name="service"></a>Usługa  
 Usługa implementuje podstawową <xref:System.ServiceModel.Web.WebGetAttribute> umowę, która składa się z jednej operacji, jak pokazano w poniższym kodzie.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Usługa implementuje ten kontrakt `ItemGenerator` przy użyciu klasy do <xref:System.ServiceModel.Syndication.SyndicationItem> tworzenia potencjalnie nieskończony strumień wystąpień przy użyciu iteratora, jak pokazano w poniższym kodzie.  
  
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
  
 Gdy implementacja usługi tworzy źródło `ItemGenerator.GenerateItems()` danych, dane wyjściowe jest używany zamiast buforowane kolekcji elementów.  
  
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
  
 W rezultacie strumień elementu nigdy nie jest w pełni buforowane w pamięci. Można zaobserwować to zachowanie, ustawiając `yield return` punkt przerwania na instrukcji wewnątrz `ItemGenerator.GenerateItems()` metody i zauważając, że ten punkt przerwania `StreamedFeed()` jest napotkany po raz pierwszy po usługa zwróciła wynik metody.  
  
## <a name="client"></a>Klient  
 Klient w tym przykładzie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> używa niestandardowej implementacji, która opóźnia materializacji poszczególnych elementów w źródle danych zamiast buforowania ich w pamięci. Wystąpienie `StreamedAtom10FeedFormatter` niestandardowe jest używane w następujący sposób.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Zwykle wywołanie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie zwraca, dopóki cała zawartość kanału informacyjnego nie została odczytana z sieci i buforowana w pamięci. Jednak `StreamedAtom10FeedFormatter` obiekt zastępuje <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> zwracać iteratora zamiast buforowane kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W rezultacie każdy element nie jest odczytywany z sieci, `ReadItems()` dopóki aplikacja kliencka przechodząca przez wyniki jest gotowa do użycia. Można zaobserwować to zachowanie, ustawiając `yield return` punkt `StreamedAtom10FeedFormatter.DelayReadItems()` przerwania na instrukcji wewnątrz i zauważając, że ten punkt `ReadFrom()` przerwania występuje po raz pierwszy po zakończeniu wywołania.  
  
 Poniższe instrukcje pokazują, jak skompilować i uruchomić przykład. Należy zauważyć, że chociaż serwer zatrzymuje generowanie elementów po odczytu przez klienta 10 elementów, dane wyjściowe pokazują, że klient odczytuje znacznie więcej niż 10 elementów. Dzieje się tak, ponieważ powiązanie sieciowe używane przez przykład przesyła dane w segmentach kb (kb). W związku z tym klient otrzymuje 4KB danych elementu, zanim będzie miał możliwość odczytu nawet jednego elementu. Jest to normalne zachowanie (wysyłanie przesyłanych strumieniowo danych HTTP w segmentach o rozsądnym rozmiarze zwiększa wydajność).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Zobacz też

- [Autonomiczne źródło danych diagnostycznych](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
