---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 17639273ece804dc531cbbc3ab9135c814ea632d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800031"
---
# <a name="streaming-feeds-sample"></a>Przykład strumieniowych kanałów informacyjnych
Niniejszy przykład pokazuje, jak zarządzać zespolone kanały informacyjne, które zawierają dużą liczbę elementów. Na serwerze, w przykładzie pokazano sposób opóźnić tworzenie poszczególnych <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w ramach źródła danych do momentu natychmiast przed zapisaniem elementu w strumieniu sieci.  
  
 Na komputerze klienckim przykład pokazuje, jak niestandardowy kanał element formatujący może służyć do odczytania pojedynczych elementów strumienia sieci, tak, aby odczytywanego nigdy nie pełni są buforowane w pamięci.  
  
 Aby zademonstrować najlepsze możliwości przesyłania strumieniowego syndykacji interfejsu API, w tym przykładzie użyto nieco w mało prawdopodobnym scenariuszu, w którym serwer udostępnia źródło danych, który zawiera nieskończona liczba elementów. W takim przypadku serwer kontynuuje Generowanie nowych elementów do źródła danych, dopóki nie określa, że klient ma odczytu określoną liczbę elementów z kanału informacyjnego (domyślnie 10). Dla uproszczenia zarówno klient, jak i serwera są implementowane w tym samym procesie i użyj udostępnionego `ItemCounter` tworzył obiektu, aby śledzić liczbę elementów klienta. `ItemCounter` Typu istnieje tylko w celu umożliwienia przykładowy scenariusz zakończyć prawidłowo i nie jest elementem core wzorca demonstrowany.  
  
 Wykazanie korzysta z programu Visual C# Iteratory (przy użyciu `yield return` konstrukcja — słowo kluczowe). Aby uzyskać więcej informacji dotyczących iteratorów zobacz temat "Przy użyciu iteratorów" w witrynie MSDN.  
  
## <a name="service"></a>Usługa  
 Usługa implementuje podstawową <xref:System.ServiceModel.Web.WebGetAttribute> kontraktu, który składa się z jednej operacji, jak pokazano w poniższym kodzie.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Usługa implementuje ten kontrakt przy użyciu `ItemGenerator` klasy, aby utworzyć strumień potencjalnie nieskończonej <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpień za pomocą iteratora, tak jak pokazano w poniższym kodzie.  
  
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
  
 Podczas implementacji usługi tworzy dane wyjściowe w źródle danych `ItemGenerator.GenerateItems()` jest używana zamiast buforowanego kolekcję elementów.  
  
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
  
 W rezultacie strumienia elementu nigdy nie pełni są buforowane w pamięci. To zachowanie można zaobserwować, przez ustawianie punktu przerwania `yield return` instrukcji wewnątrz `ItemGenerator.GenerateItems()` metody i biorąc pod uwagę, że napotkano tego punktu przerwania po raz pierwszy po Usługa zwróciła wynik `StreamedFeed()` metody.  
  
## <a name="client"></a>Klient  
 Klient w tym przykładzie używa niestandardowego <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementację, która opóźnia materializacja poszczególnych elementów w źródle danych, zamiast buforowanie ich do pamięci. Niestandardowy `StreamedAtom10FeedFormatter` wystąpienie jest używane w następujący sposób.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Zwykle po wywołaniu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie powróci do momentu całego źródła danych zostały odczytane z sieci i buforowane w pamięci. Jednak `StreamedAtom10FeedFormatter` obiektu zastąpienia <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> do zwrócenia iterator zamiast buforowanego kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W rezultacie, każdy element nie został odczytany z sieci do aplikacji klienckiej, przechodzenie przez wyniki `ReadItems()` jest gotowy do użycia go. To zachowanie można zaobserwować, przez ustawianie punktu przerwania `yield return` instrukcji wewnątrz `StreamedAtom10FeedFormatter.DelayReadItems()` i obserwowanie, że ten punkt przerwania jest napotkał po raz pierwszy po wywołaniu `ReadFrom()` kończy.  
  
 Poniższe instrukcje przedstawiają sposób tworzenia i uruchamianie aplikacji przykładowej. Należy pamiętać, że chociaż serwer przestaje generowania elementów, gdy klient może odczytywać 10 elementów, dane wyjściowe pokazują, że klient odczytuje znacznie więcej niż 10 elementów. Jest to spowodowane sieci powiązania, używany przez przykładowy przesyła dane w segmentach (KB) 4 KB. Jako takie klient odbierze 4KB danych elementu, zanim ma możliwość odczytu nawet jednego elementu. Jest to normalne zachowanie (wysyłanie dane przesyłane strumieniowo HTTP jest rozmiar segmentów zwiększa wydajność).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Zobacz też  
 [Autonomiczne źródło danych diagnostycznych](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
