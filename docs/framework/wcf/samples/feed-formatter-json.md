---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 7b535a5090d3c7df59b7faada35fc324a77b5651
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594676"
---
# <a name="feed-formatter-json"></a>Program formatujący kanału informacyjnego (format JSON)
Ten przykład pokazuje, jak serializować wystąpienie <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy w formacie JavaScript Object Notation (JSON) przy użyciu niestandardowych <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .  
  
## <a name="architecture-of-the-sample"></a>Architektura przykładu  
 Przykład implementuje klasę o nazwie `JsonFeedFormatter` , która dziedziczy z <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . `JsonFeedFormatter`Klasa polega na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> odczytywaniu i zapisywaniu danych w formacie JSON. Wewnętrznie program formatujący używa niestandardowego zestawu typów kontraktu danych o nazwie `JsonSyndicationFeed` i `JsonSyndicationItem` do sterowania FORMATEM danych JSON tworzonych przez serializator. Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, co pozwala na nawiązywanie wywołań względem standardowych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klas.  
  
## <a name="writing-json-feeds"></a>Zapisywanie źródeł danych JSON  
 Pisanie kanału informacyjnego JSON można wykonać przy użyciu `JsonFeedFormatter` (zaimplementowane w tym przykładzie), <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tak jak pokazano w poniższym przykładowym kodzie.  
  
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
 Uzyskiwanie <xref:System.ServiceModel.Syndication.SyndicationFeed> ze strumienia danych w formacie JSON można wykonać przy użyciu `JsonFeedFormatter` jak pokazano w poniższym kodzie.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
