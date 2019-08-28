---
title: Przykład strumieniowych kanałów informacyjnych
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: f37e7791bc407a57432fb9f6900ad8f19ff4eb52
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044691"
---
# <a name="streaming-feeds-sample"></a>Przykład strumieniowych kanałów informacyjnych
Ten przykład pokazuje, jak zarządzać źródłami zespolonymi zawierającymi dużą liczbę elementów. Na serwerze przykład pokazuje, jak opóźnić tworzenie pojedynczych <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów w kanale informacyjnym do momentu, gdy element zostanie zapisany do strumienia sieciowego.  
  
 Na kliencie przykład pokazuje, jak niestandardowe elementy formatujące źródło danych zespolonych mogą być używane do odczytywania poszczególnych elementów ze strumienia sieciowego, dzięki czemu odczytywane źródło danych nigdy nie jest w pełni buforowane w pamięci.  
  
 Aby najlepiej przedstawić możliwości przesyłania strumieniowego interfejsu API zespolonego, w tym przykładzie jest używany nieco mało prawdopodobny scenariusz, w którym serwer uwidacznia źródło danych zawierające nieskończoną liczbę elementów. W takim przypadku serwer kontynuuje generowanie nowych elementów w kanale informacyjnym do momentu określenia, że klient odczytał określoną liczbę elementów ze źródła danych (domyślnie 10). Dla uproszczenia zarówno klient, jak i serwer są zaimplementowane w tym samym procesie i używają udostępnionego `ItemCounter` obiektu do śledzenia liczby elementów, które wygenerował klient. `ItemCounter` Typ istnieje tylko w celu umożliwienia czyszczenia przykładowego scenariusza i nie jest elementem podstawowym wzorca, który jest demonstrowany.  
  
 Demonstracja korzysta z iteratorów C# wizualnych (przy użyciu `yield return` konstrukcji słowa kluczowego). Aby uzyskać więcej informacji na temat iteratorów, zobacz temat "Używanie iteratorów" w witrynie MSDN.  
  
## <a name="service"></a>Usługa  
 Usługa implementuje podstawową <xref:System.ServiceModel.Web.WebGetAttribute> umowę, która składa się z jednej operacji, jak pokazano w poniższym kodzie.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Usługa implementuje ten kontrakt przy użyciu `ItemGenerator` klasy, aby utworzyć potencjalnie nieskończony <xref:System.ServiceModel.Syndication.SyndicationItem> strumień wystąpień przy użyciu iteratora, jak pokazano w poniższym kodzie.  
  
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
  
 Po utworzeniu źródła danych przez implementację usługi, zamiast buforowanej kolekcji elementów `ItemGenerator.GenerateItems()` jest używany wynik.  
  
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
  
 W efekcie strumień elementu nigdy nie jest w pełni buforowany do pamięci. Możesz obsłużyć to zachowanie, ustawiając punkt przerwania `yield return` w instrukcji wewnątrz `ItemGenerator.GenerateItems()` metody i zwracając uwagę, że ten punkt przerwania jest wyświetlany po raz pierwszy od momentu, gdy usługa `StreamedFeed()` zwróci wynik metody.  
  
## <a name="client"></a>Klient  
 Klient w tym przykładzie używa niestandardowej <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementacji, która opóźnia materializację poszczególnych elementów w kanale informacyjnym zamiast buforowania ich do pamięci. Wystąpienie niestandardowe `StreamedAtom10FeedFormatter` jest używane w następujący sposób.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Zwykle wywołanie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nie zwraca, dopóki cała zawartość kanału informacyjnego nie została odczytana z sieci i zbuforowana w pamięci. Jednak obiekt przesłania <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> iterator, zamiast buforowanej kolekcji, jak pokazano w poniższym kodzie. `StreamedAtom10FeedFormatter`  
  
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
  
 W związku z tym każdy element nie jest odczytywany z sieci do momentu, gdy aplikacja `ReadItems()` kliencka przestanie być gotowa do użycia. To zachowanie można obsłużyć przez ustawienie punktu przerwania `yield return` w instrukcji `StreamedAtom10FeedFormatter.DelayReadItems()` wewnątrz i obserwowanie, że ten punkt przerwania jest wywoływany po raz pierwszy po `ReadFrom()` wywołaniu.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Zobacz także

- [Autonomiczne źródło danych diagnostycznych](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
