---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 9d40a07b81474a283a8edbeb7aca1aa7ab3993b2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716639"
---
# <a name="streaming-feeds-sample"></a>Przykład strumieniowych kanałów informacyjnych
Ten przykład pokazuje, jak zarządzać źródłami zespolonymi zawierającymi dużą liczbę elementów. Na serwerze przykład ilustruje, jak opóźnić tworzenie pojedynczych obiektów <xref:System.ServiceModel.Syndication.SyndicationItem> w kanale informacyjnym aż do momentu zapisania elementu w strumieniu sieciowym.  
  
 Na kliencie przykład pokazuje, jak niestandardowe elementy formatujące źródło danych zespolonych mogą być używane do odczytywania poszczególnych elementów ze strumienia sieciowego, dzięki czemu odczytywane źródło danych nigdy nie jest w pełni buforowane w pamięci.  
  
 Aby najlepiej przedstawić możliwości przesyłania strumieniowego interfejsu API zespolonego, w tym przykładzie jest używany nieco mało prawdopodobny scenariusz, w którym serwer uwidacznia źródło danych zawierające nieskończoną liczbę elementów. W takim przypadku serwer kontynuuje generowanie nowych elementów w kanale informacyjnym do momentu określenia, że klient odczytał określoną liczbę elementów ze źródła danych (domyślnie 10). Dla uproszczenia zarówno klient, jak i serwer są zaimplementowane w tym samym procesie i używają udostępnionego obiektu `ItemCounter` do śledzenia liczby elementów, które wygenerował klient. Typ `ItemCounter` istnieje tylko w celu umożliwienia czyszczenia przykładowego scenariusza i nie jest elementem podstawowym wzorca, który jest demonstrowany.  
  
 Demonstracja korzysta z iteratorów C# wizualnych (przy użyciu konstrukcji słowa kluczowego `yield return`). Aby uzyskać więcej informacji na temat iteratorów, zobacz temat "Używanie iteratorów" w witrynie MSDN.  
  
## <a name="service"></a>NDES  
 Usługa implementuje podstawową umowę <xref:System.ServiceModel.Web.WebGetAttribute>, która składa się z jednej operacji, jak pokazano w poniższym kodzie.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Usługa implementuje ten kontrakt przy użyciu klasy `ItemGenerator`, aby utworzyć potencjalnie nieskończony strumień wystąpień <xref:System.ServiceModel.Syndication.SyndicationItem> przy użyciu iteratora, jak pokazano w poniższym kodzie.  
  
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
  
 Podczas tworzenia źródła danych przez implementację usługi, zamiast buforowanej kolekcji elementów zostanie użyta wartość wyjściowa `ItemGenerator.GenerateItems()`.  
  
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
  
 W efekcie strumień elementu nigdy nie jest w pełni buforowany do pamięci. Możesz obsłużyć to zachowanie, ustawiając punkt przerwania w instrukcji `yield return` wewnątrz metody `ItemGenerator.GenerateItems()` i zwracając uwagę, że ten punkt przerwania jest wyświetlany po raz pierwszy od momentu, gdy usługa zwróci wynik metody `StreamedFeed()`.  
  
## <a name="client"></a>Klient  
 Klient w tym przykładzie używa niestandardowej implementacji <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>, która opóźnia materializację poszczególnych elementów w kanale informacyjnym zamiast buforowania ich do pamięci. Niestandardowe wystąpienie `StreamedAtom10FeedFormatter` jest używane w następujący sposób.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Zwykle wywołanie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie zwraca, dopóki cała zawartość kanału informacyjnego nie została odczytana z sieci i zbuforowana w pamięci. Jednak obiekt `StreamedAtom10FeedFormatter` zastępuje <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29>, aby zwracał iterator zamiast buforowanej kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W związku z tym każdy element nie jest odczytywany z sieci do momentu, gdy aplikacja kliencka przejdzie wyniki `ReadItems()` jest gotowa do użycia. Aby obsłużyć to zachowanie, należy ustawić punkt przerwania w instrukcji `yield return` wewnątrz `StreamedAtom10FeedFormatter.DelayReadItems()` i obserwowanie, że ten punkt przerwania jest wywoływany po raz pierwszy po wywołaniu `ReadFrom()`.  
  
 Poniższe instrukcje pokazują, jak skompilować i uruchomić przykład. Należy zauważyć, że mimo że serwer przestaje generować elementy po odczytaniu 10 elementów przez klienta, dane wyjściowe pokazują, że klient odczytuje znacznie więcej niż 10 elementów. Wynika to z faktu, że powiązanie sieciowe używane przez przykład przesyła dane w segmentach czterech kilobajtów (KB). W związku z tym klient otrzymuje 4 KB danych elementu, zanim będzie miał możliwość odczytania nawet jednego elementu. Jest to normalne zachowanie (wysyłanie strumieniowych danych HTTP w przypadku segmentów o rozsądnym rozmiarze zwiększa wydajność).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Zobacz także

- [Autonomiczne źródło danych diagnostycznych](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
