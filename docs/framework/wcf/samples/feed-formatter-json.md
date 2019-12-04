---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: dfdcd0920980e7e5cc1fe1c8910ee7cfbe59b5a0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715840"
---
# <a name="feed-formatter-json"></a>Program formatujący kanału informacyjnego (format JSON)
Ten przykład pokazuje, jak serializować wystąpienie klasy <xref:System.ServiceModel.Syndication.SyndicationFeed> w formacie JavaScript Object Notation (JSON) przy użyciu niestandardowej <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura przykładu  
 Przykład implementuje klasę o nazwie `JsonFeedFormatter`, która dziedziczy po <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Klasa `JsonFeedFormatter` opiera się na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do odczytywania i zapisywania danych w formacie JSON. Wewnętrznie program formatujący używa niestandardowego zestawu typów kontraktu danych o nazwie `JsonSyndicationFeed` i `JsonSyndicationItem` do sterowania formatem danych JSON tworzonych przez serializator. Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, co pozwala na nawiązywanie wywołań względem standardowych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klas.  
  
## <a name="writing-json-feeds"></a>Zapisywanie źródeł danych JSON  
 Pisanie kanału informacyjnego JSON można wykonać przy użyciu `JsonFeedFormatter` (zaimplementowane w tym przykładzie) z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>Odczytywanie źródła danych JSON  
 Uzyskanie <xref:System.ServiceModel.Syndication.SyndicationFeed> ze strumienia danych w formacie JSON można wykonać przy użyciu `JsonFeedFormatter`, jak pokazano w poniższym kodzie.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
