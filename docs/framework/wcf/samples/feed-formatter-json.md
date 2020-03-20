---
title: Program formatujący kanału informacyjnego (format JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183651"
---
# <a name="feed-formatter-json"></a>Program formatujący kanału informacyjnego (format JSON)
W tym przykładzie pokazano, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> serializować wystąpienie klasy w formacie Notacji <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> obiektu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>JavaScript (JSON) przy użyciu niestandardowego i .  
  
## <a name="architecture-of-the-sample"></a>Architektura próbki  
 Przykład implementuje klasę `JsonFeedFormatter` o nazwie, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>która dziedziczy po . Klasa `JsonFeedFormatter` opiera się <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> na do odczytu i zapisu danych w formacie JSON. Wewnętrznie formater używa niestandardowego zestawu typów kontraktów `JsonSyndicationFeed` `JsonSyndicationItem` danych o nazwie i do kontrolowania formatu danych JSON produkowanych przez serializatora. Te szczegóły implementacji są ukryte przed użytkownikiem końcowym, <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> dzięki czemu wywołania mają być wykonane względem standardu i klas.  
  
## <a name="writing-json-feeds"></a>Pisanie kanałów JSON  
 Pisanie źródła danych JSON można wykonać `JsonFeedFormatter` przy użyciu (zaimplementowane w tym przykładzie) z <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak pokazano w poniższym kodzie przykładowym.  
  
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
  
## <a name="reading-a-json-feed"></a>Czytanie kanału JSON  
 Uzyskanie <xref:System.ServiceModel.Syndication.SyndicationFeed> z strumienia danych w formacie JSON można wykonać `JsonFeedFormatter` za pomocą as show w poniższym kodzie.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
