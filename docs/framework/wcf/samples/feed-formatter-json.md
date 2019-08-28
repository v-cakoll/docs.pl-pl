---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 028d2f9abd7e23f18eb90e5ecae8c57da3a871d1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039641"
---
# <a name="feed-formatter-json"></a>Program formatujący kanału informacyjnego (format JSON)
Ten przykład pokazuje, jak serializować wystąpienie <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy w formacie JavaScript Object Notation (JSON) przy użyciu niestandardowych <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura przykładu  
 Przykład implementuje klasę o nazwie `JsonFeedFormatter` , która dziedziczy z. <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> `JsonFeedFormatter` Klasa polega <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> na odczytywaniu i zapisywaniu danych w formacie JSON. Wewnętrznie program formatujący używa niestandardowego zestawu typów kontraktu danych o nazwie `JsonSyndicationFeed` i `JsonSyndicationItem` do sterowania formatem danych JSON tworzonych przez serializator. Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, co pozwala na nawiązywanie wywołań względem standardowych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klas.  
  
## <a name="writing-json-feeds"></a>Zapisywanie źródeł danych JSON  
 Pisanie kanału informacyjnego JSON można wykonać przy użyciu `JsonFeedFormatter` (zaimplementowane w tym przykładzie) <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , tak jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
 Uzyskiwanie `JsonFeedFormatter` ze strumienia danych w formacie JSON można wykonać przy użyciu jak pokazano w poniższym kodzie. <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
