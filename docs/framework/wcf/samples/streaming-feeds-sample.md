---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 2c420bad9ad96107f56b5435efa6fffd6941cdaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505540"
---
# <a name="streaming-feeds-sample"></a>Przykład strumieniowych kanałów informacyjnych
W tym przykładzie pokazano, jak zarządzać zespolonego źródła danych, które zawierają dużą liczbę elementów. Na serwerze, przykładzie pokazano, jak opóźnienie tworzenia poszczególnych <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w ramach źródła danych do bezpośrednio przed elementu są zapisywane do strumienia sieci.  
  
 Na komputerze klienckim próbki pokazuje, jak niestandardowy program formatujący źródło zespolone może służyć do odczytania poszczególne elementy strumienia sieci, dzięki czemu odczytywanego pełni nigdy nie są buforowane w pamięci.  
  
 Aby zademonstrować najlepiej przesyłania strumieniowego możliwości zespolonego interfejsu API, w tym przykładzie użyto nieco prawdopodobne scenariusz, w którym serwer udostępnia źródło z nieograniczoną liczbę elementów. W takim przypadku serwer kontynuuje generowania nowych elementów w źródle danych, dopóki nie określa, że klient ma odczytu określoną liczbę elementów ze źródła strumieniowego (domyślnie 10). Dla uproszczenia zarówno klient, jak i serwera są zaimplementowane w tym samym procesie i używać udostępnionej `ItemCounter` obiekt, aby śledzić liczbę elementów klienta został utworzony. `ItemCounter` Typu istnieje tylko w celu umożliwienia przykładowy scenariusz zakończenie prawidłowo i nie jest elementem core wzorca jest uruchomiona.  
  
 Pokazu korzysta z programu Visual C# Iteratory (przy użyciu `yield``return` konstrukcja — słowo kluczowe). Aby uzyskać więcej informacji na temat Iteratory zobacz temat "Przy użyciu Iteratory" w witrynie MSDN.  
  
## <a name="service"></a>Usługa  
 Usługa implementuje podstawowego <xref:System.ServiceModel.Web.WebGetAttribute> kontraktu, który składa się z jednej operacji, jak pokazano w poniższym kodzie.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Usługa implementuje tego kontraktu przy użyciu `ItemGenerator` klasy w celu utworzenia potencjalnie nieskończone strumienia <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpienia przy użyciu iteratora, jak pokazano w poniższym kodzie.  
  
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
  
 Podczas wdrażania usługi tworzy dane wyjściowe w źródle danych `ItemGenerator.GenerateItems()` jest używany zamiast buforowanego kolekcję elementów.  
  
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
  
 W związku z tym strumienia elementu pełni nigdy nie są buforowane w pamięci. To zachowanie można zaobserwować, ustawiając punkt przerwania dla `yield``return` instrukcji wewnątrz `ItemGenerator.GenerateItems()` — metoda i zauważyć, że ten punkt przerwania napotkano po raz pierwszy po usługi zwrócił wynik `StreamedFeed()` metody.  
  
## <a name="client"></a>Klient  
 W tym przykładzie klient używa niestandardowego <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementacji, który wybrano opcję opóźnienia materialization poszczególnych elementów w źródle danych, zamiast buforowania ich do pamięci. Niestandardowa `StreamedAtom10FeedFormatter` wystąpienia jest używane w następujący sposób.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Zazwyczaj wywołanie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie może zwracać dopóki całą zawartość źródła danych zostały odczytu z sieci i buforowane w pamięci. Jednak `StreamedAtom10FeedFormatter` obiekt zastąpienia <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> do zwrócenia iteratora zamiast buforowanego kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W związku z tym każdy element nie został odczytany z sieci do aplikacji klienckiej, przechodzenie przez wyniki `ReadItems()` jest gotowe do użycia go. To zachowanie można zaobserwować, ustawiając punkt przerwania dla `yield``return` instrukcji wewnątrz `StreamedAtom10FeedFormatter.DelayReadItems()` i że napotkano po raz pierwszy po wywołaniu tego punktu przerwania po raz pierwszy `ReadFrom()` zakończeniu.  
  
 Poniższe instrukcje przedstawiają sposób skompilować i uruchomić próbki. Należy pamiętać, że chociaż serwer przestaje generowania elementów, gdy klient może odczytywać 10 elementów, dane wyjściowe zawierają czy klient otrzymuje znacznie więcej niż 10 elementów. Jest to spowodowane powiązanie sieciowe używane przez próbki przesyła dane w czterech kilobajtów (KB) segmentów. Tak klient odbierze 4KB danych elementu przed ma możliwość odczytu nawet jednego elementu. Jest to normalne zachowanie (wysyłania strumienia danych HTTP w rozsądnych rozmiarach segmentów zwiększa wydajność).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Zobacz też  
 [Autonomiczne źródło danych diagnostycznych](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
